cmake_minimum_required(VERSION 3.4.1)

file(GLOB SOURCE src/main/cpp/*.cpp)

add_library(
        wyplayer
        SHARED
        ${SOURCE})

find_library(
        log-lib
        log)

include_directories(src/main/cpp/include)

set(my_lib_path  ${CMAKE_SOURCE_DIR}/libs/${ANDROID_ABI})
set(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} -L${my_lib_path}")

target_link_libraries(
        wyplayer
        avfilter avformat avcodec avutil swresample swscale
        ${log-lib}
        z
        OpenSLES
        android
        )