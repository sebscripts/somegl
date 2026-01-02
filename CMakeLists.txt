cmake_minimum_required(VERSION 4.2.1)

project(GL_boilerplate VERSION 1.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)



# includes
include_directories(${CMAKE_SOURCE_DIR}/build/include/)

#libs

add_library(libglad SHARED IMPORTED)
add_library(libglfw SHARED IMPORTED)

set_target_properties(libglad PROPERTIES
	IMPORTED_LOCATION "${CMAKE_SOURCE_DIR}/build/lib/libglad.so"
)

set_target_properties(libglfw PROPERTIES
        IMPORTED_LOCATION "${CMAKE_SOURCE_DIR}/build/lib/libglfw.so"
)

add_executable(${PROJECT_NAME} main.cpp)
target_link_libraries(${PROJECT_NAME} PRIVATE libglad libglfw)
