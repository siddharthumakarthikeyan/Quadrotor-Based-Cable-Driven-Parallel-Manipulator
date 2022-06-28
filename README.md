# Quadrotor-Based-Cable-Driven-Parallel-Manipulator
Simulation of Mobile Cable Driven Parallel Manipulator using Quadrotors and Omni Directional Drive using Coppeliasim (VREP) and ROS

## System configuration
- Ubuntu : 20.04
- ROS : noetic+
- CPU : ARM7+ or Intel i5+ or AMD R4+
- RAM : 4GB+
- Memory : 10GB+
- Coppeliasim - V4.2.0 rev5

## Installation setup 

- Download Coppeliasim [Coppeliasim V4.2.0](https://www.coppeliarobotics.com/downloads).
- Extract the coppeliasim folder in the root folder.
- Add following line to ~/.bash.rc : `export COPPELIASIM_ROOT_DIR=~/CoppeliaSim_Edu_V4_2_0_Ubuntu20_04/`   
- `git clone https://github.com/siddharthumakarthikeyan/Quadrotor-Based-Cable-Driven-Parallel-Manipulator.git`
- `cd cdpr`
- `catkin_make`
- `source devel/setup.bash`

## Execution steps

- **Terminal 1 :** Start `roscore` in one terminal.
- **Terminal 2 :** Launch coppeliasim
- Load scenes from the repository `~/src/coppeliasim_ws/vrep_scenes`
- **Terminal 3 : Depth images to PointCLoud** `roslaunch coppeliasim_ws camera.launch` 
- **Terminal 4 : PointCloud to map ** `roslaunch coppeliasim_ws mapping.launch`

## End effector detection

- **Terminal 1 :** Start `roscore` in one terminal.
- **Terminal 2 :** Launch coppeliasim
- Load scenes from the repository `~/src/coppeliasim_ws/vrep_scenes/final2robottags.ttt`
- **Terminal 3 : Depth images to PointCLoud** `roslaunch coppeliasim_ws tag_detection.launch` 
- Open Rviz and view tf


## ROS Topics

- Drones 
  - `~/force` - **subscriber** - external linear forces and angular torques. 
  - `~/kinect_n/camera/camera_info` - **publisher** - camera info.
  - `~/kinect_n/camera/depth_image` - **publisher** - depth image.
  - `~/kinect_n/camera/rgb_image` - **publisher** - rgb image.
  - `~/pose` - **subscriber** - send target pose to the drone.
  - `~/rope` - **subscriber** - send target position for the rope.
- Robots
  - `~/force` - **subscriber** - external linear forces and angular torques. 
  - `~/kinect_n/camera/camera_info` - **publisher** - camera info.
  - `~/kinect_n/camera/depth_image` - **publisher** - depth image.
  - `~/kinect_n/camera/rgb_image` - **publisher** - rgb image.
  - `~/pose` - **subscriber** - send target pose to the drone.
  - `~/position_control` - **subscriber** - enable/disable control loop.
  - `~/twist` - **subscriber** - send velocities to the robot.
  - `~/rope` - **subscriber** - send target position for the rope.
- Ropes 
  - `~/rope` - **subscriber** - Combined control the height of all the ropes.



