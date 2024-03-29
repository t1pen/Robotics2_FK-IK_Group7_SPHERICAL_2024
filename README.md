# Robotics2_FKandIK_Group7_SPHERICAL_2024
<h1 align="center"> Robotics 2 - Forward and Inverse Kinematics of Spherical Manipulator </h1>
<br>


## Table of Contents
  - [I. Abstract](#i.-abstract-)
  - [II. Introduction](#-ii.-introduction-)
  - [III. Degrees of Freedom](#-iii.-degrees-of-freedom-)
  - [IV. Kinematic Diagram and D-H Frame](#-iv.-kinematic-diagram-and-d-h-frame-)
  - [V. D-H Parametric Table](#-v.-d-h-parametric-table-)
  - [VI. Homogeneous Transformation Matrix](#-vi.-homogeneous-transformation-matrix-)
  - [VII. Inverse Kinematics](#-vii.-inverse-kinematics-)
  - [VIII. Forward and Inverse Kinematics (GUI calculator)](#-viii.-forward-and-inverse-kinematics-(gui-calculator)-)
  - [IX. References](#-ix.-references-)
  - [X. Members](#-x.-members)
<hr> 
<br>


## I. Abstract
    (description)
<hr> 
<br>


## II. Introduction

  <p align="center">
  <img src=https://github.com/MEXECardenas/SPHERICAL_G7_Assignment_2024/blob/0b0c965065028159e971cf92570e9344e1e41f4b/Kinematic%20Diagrams%20with%20D-H%20Parametric%20Tables/Spherical%20Manipulator%20-%20Modern%20Variant.png alt=Spherical-Manipulator-Modern-Variant style="height: 300px; float: left;">
  <img src=https://github.com/MEXECardenas/SPHERICAL_G7_Assignment_2024/blob/a9a0b089f3911adfcc915ab37b061117838ae024/Kinematic%20Diagrams%20with%20D-H%20Parametric%20Tables/Spherical%20Manipulator%20(Modern%20Variant).gif alt=Spherical-Manipulator-(Modern-Variant) style="height: 300px; float: right;">
  </p>
</div>
<br>

<p align="justify"> 
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<b><i>Spherical Manipulator</i></b> is a stationary manipulator featuring two revolute joints and one prismatic joint, with an arm attached to a robotic base, and a twisting joint. The spherical manipulator was also known as the <b><i>Polar Manipulator</i></b>. It has three mutually perpendicular axes and is well known in the history of robotics, because the first industrial robot, <b><i>Unimate</i></b>, was a spherical robot developed in the 1950s. It is also a type of robotic manipulator that operates with a spherical working envelope. Unlike traditional robotic arms that typically move in a planar or linear fashion, spherical manipulators can move in any direction within a three-dimensional space. These robots often consist of multiple joints arranged in a spherical configuration, allowing for movement along multiple axes simultaneously. This configuration enables them to reach points in 3D space with greater flexibility compared to traditional robotic arms.</p>

<p align="justify">
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Knowing that spherical manipulators have an arm which forms a spherical coordinate system. In mathematics, a spherical coordinate system is a three-dimensional coordinate system in which the position of a point is specified by three numbers: the radial distance from a fixed origin, the polar angle measured from a fixed zenith direction, and the azimuth angle of its orthogonal projection on a reference plane that passes through the origin and is orthogonal to the zenith, measured from a fixed reference direction. The radial distance is also known as the radius or radial coordinate. The polar angle is also known as the zenith angle, normal angle, colatitude, or inclination angle.</p>

  <p align="justify">
  &nbsp;&nbsp;&nbsp;&nbsp;Spherical Manipulators perform three distinct movements: rotation, elevation, and extension from a stationary base–giving them a spherical/polar working envelope. This configuration allows the robot to move freely and with great flexibility, making it ideal for a variety of jobs. Here is a breakdown of the movements:</p>

- **Rotation**: The robot can rotate around a vertical axis, which forms the base of the robot. This allows the robot to cover a wide horizontal range around its base.
- **Elevation**: The robot's arm can move up and down in a vertical plane, enabling it to reach different heights.
- **Extension**: The robot's arm can extend or retract, moving closer to or farther from the base.

<br>




## III. Degrees of Freedom

  <p align="justify"> 
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;In robotics, <b><i>Degrees of Freedom</i></b> (DOF) refer to the number of independent parameters that define the configuration or motion of a robot. Essentially, it indicates how many different ways a robot can move within its environment.The more the degree of freedom, the more flexible and adaptable the robot. A robot with high DOF can make more complex movements and perform a variety of tasks.</p>
  
<p class="blank-line">&nbsp;</p>

#### The Ideal Degrees of Freedom:
  - A <b>point</b> in 2D: 2-DOF; in 3D space: 3-DOF
  - A <b>rigid body</b> in 3D: 6-DOF
  - <b>Planar Manipulator</b>: 3-DOF
  - <b>Spatial manipulator</b>: 6-DOF
<br>

#### Types of Manipulator based on the number of Degrees of Freedom:
  - <b>Under-Actuated Manipulator</b>
      - _Spatial Manipulator_ with less than 6-DOF
      - _Planar Manipulator_ with less than 3-DOF
  - <b>Ideal manipulator</b>
      - _Spatial Manipulator_ with exactly 6-DOF
      - _Planar Manipulator_ with exactly 3-DOF
  - <b>Redundant manipulator</b>
      - _Spatial Manipulator_ with more than 6-DOF
      - _Planar Manipulator_ with more than 3-DOF
<br>

#### Grubler's Criterion for Mobility
  - Formula for the Mobility of _Spatial Manipulator_
    $$M = 6n - \sum_{i=1}^m (6-Ci)$$
  - Formula for the Mobility of _Planar Manipulator_
    $$M = 3n - \sum_{i=1}^m (3-Ci)$$
<br>

#### Grubler's Criterion for Mobility
<div align="center">
  
|  Formula for the Mobility of _Spatial Manipulator_  | Formula for the Mobility of _Planar Manipulator_ |
|         :---: |     :-----:      |
| $$M = 6n - \sum_{i=1}^m (6-Ci)$$ |  $$M = 3n - \sum_{i=1}^m (3-Ci)$$ |

</div>

<br>

#### Mechanical Manipulator Anatomy

<div align="center">
  
|  Joint type  | DOF *f* | Constraints *c* between two planar rigid bodies | Constraints *c* between two spatial rigid bodies |
|         ---: |     :-----:      |     :---:     |     :---:    |
|  Revolute (R)  |  1  |  2  |  5  |
|  Prismatic (P)  |  1  |  2  |  5  |
|  Helical (H)  |  1  |  N/A  |  5  |
|  Cylindrical (C)  |  2  |  N/A  |  4  |
|  Universal (U)  |  2  |  N/A  |  4  |
|  Spherical (S)  |  3  |  N/A  |  3  |

</div>

<br>








































## Table of Contents
- [Kinematic Diagram and Parametric Table of Spherical Manipulator](#-kinematic-diagram-and-parametric-table-of-spherical-manipulator-)
- [Derivation of Inverse Kinematics using Graphical Method](#-derivation-of-inverse-kinematics-using-graphical-method-)
- [Comparison of Forward and Inverse Kinematics in MATLAB and Phyton](#-comparison-of-forward-and-inverse-kinematics-in-matlab-and-phyton-)
   - [Trial Table of Forward Kinematics in MATLAB and Python](#-trial-table-of-forward-kinematics-in-matlab-and-python-)
   - [Trial Table of Inverse Kinematics in MATLAB and Python](#-trial-table-of-inverse-kinematics-in-matlab-and-python-)
- [Group Members](#group-members)
<br>

<h1 align="center"> Kinematic Diagram and Parametric Table of Spherical Manipulator </h1> 
<p align="center">
  <img src=https://github.com/t1pen/Robotics2_FKandIK_Group7_SPHERICAL_2024/assets/157677365/c0c481a4-3d7c-4005-83e1-21bc436ec15e alt=DH_Frame_and_Parametric_Table width="700"/>
<p align="center">
</p>
<br>
<br>

<h1 align="center"> Derivation of Inverse Kinematics using Graphical Method </h1> 
<p align="center">
   <img src=https://github.com/t1pen/Robotics2_FKandIK_Group7_SPHERICAL_2024/assets/157677365/b659b633-7068-412a-b9b0-58626bb0287f alt=Inverse_Kinematics_Graphical_Method_1 width="700"/>
<p align="center">
   <img src=https://github.com/t1pen/Robotics2_FKandIK_Group7_SPHERICAL_2024/assets/157677365/d8f43e6d-8a61-4257-808e-a8dff408b0ef alt=Inverse_Kinematics_Graphical_Method_2 width="700"/>
<br>
<br>

<h1 align="center"> Comparison of Forward and Inverse Kinematics in MATLAB and Phyton </h1>
<hr>

<h1 align="center"> Trial Table of Forward Kinematics in MATLAB and Python </h1> 
<p align="center">
  <img src=https://github.com/t1pen/Robotics2_FKandIK_Group7_SPHERICAL_2024/blob/0d4a1af26e3a6964fa47395ed9f41d56eaa53fae/Trial%20Table%20for%20Forward%20and%20Inverse%20Kinematics/Trial%20Table%20for%20Forward%20Kinematics.png alt=trial-table-of-forward-kinematics-in-matlab-and-python width="800"/>
</p>
<br>
<br>

<h1 align="center"> Trial Table of Inverse Kinematics in MATLAB and Python </h1> 
<p align="center">
  <img src=https://github.com/t1pen/Robotics2_FKandIK_Group7_SPHERICAL_2024/blob/440b5c7742bceab7f9bf815b060b93355776fd29/Trial%20Table%20for%20Forward%20and%20Inverse%20Kinematics/Trial%20Table%20for%20Inverse%20Kinamatics.png alt=trial-table-of-inverse-kinematics-in-matlab-and-python width="990"/>
</p>
<br>
<br>


### Group Members:
- Alojado, Stephen Gabriel S.
- Apostol, Jan Benedict D.
- Cardenas, Sofia Bianca J.
- Catapang, Jamil Darrius S.
- Umali, Ariane Mae D.
