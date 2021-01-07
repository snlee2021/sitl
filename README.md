# sitl

1) 노트북에 Install Ubuntu 18.04.4 Desktop Version
*포맷 후 Ubuntu 18.04 설치하는 것 추천
 
2) Install ROS + Gazebo
> px4 developer guide website
> select master
> get install script
wget https://raw.githubusercontent.com/PX4/Devguide/master/build_scripts/ubuntu_sim_ros_melodic.sh
$ bash ubuntu_sim_ros_melodic.sh
* geographic_msgs
$ sudo apt-get install ros-melodic-geographic-msgs
* future library
$ pip install future
* GeographicLib
$ sudo apt-get install libgeographic-dev
$ sudo apt-get install geographiclib-tools
3) Install PX4 Stack
$ cd ~/
$  git clone https://github.com/PX4/Firmware.git      -b v1.8.2
$ cd ~/Firmware
$ git submodule update --init --recursive
$ make posix_sitl_default
$ make posix_sitl_default sitl_gazebo
$ cd ~/Firmware
$ make posix gazebo
 

4) bashrc 환경설정
$ gedit ~/.bashrc
> add following lines
cd ~/Firmware
source Tools/setup_gazebo.bash $(pwd) $(pwd)/build/posix_sitl_
export ROS_PACKAGE_PATH=$ROS_PACKAGE_
cd ~/
5) Install QGroundControl
> go to QGroundControl website
> download AppImage (save file)
$ chmod +x QGroundControl.AppImage
> double-click run
 
6) Install Pycharm Editor
> download community version (freeware)
> unzip to home folder
> make a script for running
 
7) catkin_ws/src에 예제파일 afa를 copy
$ cd /home/kafa01/catkin_ws
$ catkin build
build succeed 나오면
$ roscd afa
$ cd run
$ ./gazebo.sh
‘gazebo is ready’가 실행되고 gazebo안에 drone이 들어 있는지 확인
8) QGroundControl 실행하고, ‘takeoff’(hold mode),실행하여 gazebo에서
드론의 움직임, 위치 확인
> mission mode 등 다양한 flight mode 움직임 확인
 
9) ‘mavros’가 실행하여 전달메세지 확인
$ roscd afa
$ cd run
$ ./mavros.sh
 
10) 드론에게 다양한 demo 수행명령 하달 확인
$ rosrun afa setpoint_position_demo.py
> QGroundControl ‘hold’에서 ‘offboard’ mode 변경하여 코딩명령 전달
> 드론의 demo 수행여부 확인
