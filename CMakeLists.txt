cmake_minimum_required(VERSION 2.8.3)
project(beginner_tutorials)

## Find catkin and any catkin packages
find_package(catkin REQUIRED COMPONENTS roscpp rospy std_msgs genmsg)

## Declare ROS messages and services
add_message_files(FILES Num.msg)
add_service_files(FILES AddTwoInts.srv)

## Generate added messages and services
generate_messages(DEPENDENCIES std_msgs)

## Declare a catkin package
catkin_package()

## Build talker and listener
include_directories(include ${catkin_INCLUDE_DIRS})

add_executable(talker src/talker.cpp)
target_link_libraries(talker ${catkin_LIBRARIES})
add_dependencies(talker beginner_tutorials_generate_messages_cpp)

add_executable(bool_pub src/bool_pub.cpp)
target_link_libraries(bool_pub ${catkin_LIBRARIES})
add_dependencies(bool_pub beginner_tutorials_generate_messages_cpp)

add_executable(bool_sub src/bool_sub.cpp)
target_link_libraries(bool_sub ${catkin_LIBRARIES})
add_dependencies(bool_sub beginner_tutorials_generate_messages_cpp)


add_executable(listener src/listener.cpp)
target_link_libraries(listener ${catkin_LIBRARIES})
add_dependencies(listener beginner_tutorials_generate_messages_cpp)
