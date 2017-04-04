# Minimum CMake required
cmake_minimum_required(VERSION 3.3)

# Project
project(dml C CXX)

# Set C++14 as standard for the whole project
set(CMAKE_CXX_STANDARD 14)

# External dependencies
set(CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake/External)

# Location where external projects will be downloaded
set (DOWNLOAD_LOCATION "${CMAKE_CURRENT_BINARY_DIR}/downloads"
    CACHE PATH "Location where external projects will be downloaded.")
mark_as_advanced(DOWNLOAD_LOCATION)

# External dependencies
include(zlib)
#include(eigen)
include(protobuf)
include(grpc)

set(dml_EXTERNAL_LIBRARIES
    ${zlib_STATIC_LIBRARIES}
    ${protobuf_STATIC_LIBRARIES}
    )
set(dml_EXTERNAL_DEPENDENCIES
    zlib_copy_headers_to_destination
    protobuf
#    eigen
    grpc
    )

include_directories(
    # Source and generated code.
    ${dml_source_dir}
    ${CMAKE_CURRENT_BINARY_DIR}
    # External dependencies.
    ${zlib_INCLUDE_DIR}
#    ${eigen_INCLUDE_DIRS}
    ${PROTOBUF_INCLUDE_DIRS}
    ${grpc_STATIC_LIBRARIES}
)