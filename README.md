# Introduction
This package can send control commands to a real Go1 robot from ROS2. You can do low-level control (namely, control all joints of the robot) and high-level control (namely, control the walking direction and speed of the robot).

This version is suitable for unitree_legged_sdk v3.5.11.

## Packages:
Basic message function: `unitree_legged_msgs`

The interface between ROS and real robot: `unitree_legged_real`

## Environment
We recommand users to run this package in Ubuntu 24.04 and ROS2 eloquent environment

# Dependencies
* [unitree_legged_sdk](https://github.com/sljunkie/unitree_legged_sdk): v3.5.11

# Configuration
First, creat a workspace directory:

```bash
mkdir -p ~/ws/src
```
Then download this package into this `~/ws/src` folder.

Now download unitree_legged_sdk v3.5.11 into the path `~/ws/src/unitree_ros2_to_real` and rename the directory to `unitree-legged-sdk-master`.

Finally, move the `ros2_unitree_legged_msgs` directory to the `~/ws/src` folder.

Your directory tree should be like this:

```
~/
|
- ws/
  |
  - src
    |
    + ros2_unitree_legged_msgs/
    + unitree_ros2_to_real/
      |
      - unitree_legged_sdk-master/
```

# Build
```bash
cd ~/ws
colcon build
```

# Setup the net connection
TODO

# Run the package
Before any low-level control, press L2+A on the controller pad to lock the robot position and then press L1+L2+START to tell the robot to accept joint-level control.

First, source the `unitree_ros2_to_real` package:
    
```bash
source install/setup.bash
```
    
Then run the `ros2_udp` node, a bridge that connects user-software and the robot, with
    
```bash
ros2 run unitree_legged_real ros2_udp highlevel
```
    
for high-level control or
    
```bash
ros2 run unitree_legged_real ros2_udp lowlevel
```
    
for low-level control.
    
To run the high-level example:
    
```bash
ros2 run unitree_legged_real ros2_walk_example
```
    
And to run the low-level example:
    
```bash
ros2 run unitree_legged_real ros2_position_example
```    
