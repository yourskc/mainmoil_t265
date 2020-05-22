# License: Apache 2.0. See LICENSE file in root directory.
# Copyright(c) 2019 Intel Corporation. All Rights Reserved.
#  minimum required cmake version: 3.1.0
# sudo apt install freeglut3-dev
cmake_minimum_required(VERSION 3.1.0)
set(LZ4_DIR lz4)
project(RealsenseMotion_skc)
find_package(OpenGL REQUIRED COMPONENTS OpenGL)
find_package(GLUT REQUIRED)
include_directories( include ${OPENGL_INCLUDE_DIRS} ${GLUT_INCLUDE_DIRS} ${LZ4_DIR})
add_subdirectory(glfw)
add_executable(rs-motion rs-motion.cpp)
set_property(TARGET rs-motion PROPERTY CXX_STANDARD 11)
target_link_libraries(rs-motion ${DEPENDENCIES} ${OPENGL_LIBRARIES} ${GLUT_LIBRARY} realsense2 glfw)
install(TARGETS rs-motion RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR})

