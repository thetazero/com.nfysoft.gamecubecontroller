cmake_minimum_required(VERSION 3.22)
project(gamecube_controller)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS ON)
set(SOURCE_FILES src/gcc_adapter.cpp)


include_directories(
        ${LIBUSB_PATH}/include
        ${CMAKE_CURRENT_SOURCE_DIR}/src
)

link_directories(
        ${LIBUSB_PATH}/lib
)

add_library(gamecube_controller SHARED ${SOURCE_FILES})

target_link_libraries(gamecube_controller)

include(GenerateExportHeader)
generate_export_header(gamecube_controller EXPORT_FILE_NAME ${CMAKE_CURRENT_SOURCE_DIR}/src/export_header.h)