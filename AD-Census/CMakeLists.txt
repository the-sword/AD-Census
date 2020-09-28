cmake_minimum_required(VERSION 3.5)
set (CMAKE_CXX_STANDARD 11)

project(AD-Cenus)
set(CMAKE_BUILD_TYPE Release)
option(GPU "Build the project using macro" ON)

include_directories(/usr/include/python3.6m)

find_package(OpenCV REQUIRED)

find_package(Threads)

include_directories( ${OPENCV_INCLUDE_DIR} )
include_directories(${PROJECT_SOURCE_DIR})

link_directories(/usr/local/cuda-10.0/lib64)
link_directories(/usr/local/lib)

add_executable(${PROJECT_NAME}
${PROJECT_SOURCE_DIR}/main.cpp
${PROJECT_SOURCE_DIR}/ADCensusStereo.cpp
${PROJECT_SOURCE_DIR}/adcensus_util.cpp
${PROJECT_SOURCE_DIR}/adcensus_types.h
${PROJECT_SOURCE_DIR}/cost_computor.cpp
${PROJECT_SOURCE_DIR}/cross_aggregator.cpp
${PROJECT_SOURCE_DIR}/multistep_refiner.cpp
${PROJECT_SOURCE_DIR}/scanline_optimizer.cpp
        )

target_link_libraries(${PROJECT_NAME} ${OpenCV_LIBS})

target_link_libraries(${PROJECT_NAME})
