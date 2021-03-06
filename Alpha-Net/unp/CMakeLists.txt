cmake_minimum_required(VERSION 3.8)
project(alpha-net)

set(CMAKE_CXX_STANDARD  11)

set(SOURCE_FILES echoserver_multiio.cpp)
add_executable(alpha-net ${SOURCE_FILES})

set(SOURCE_FILES_DAYTIME_SERVER daytimeserver.cpp)
add_executable(daytimeserver ${SOURCE_FILES_DAYTIME_SERVER})

set(SOURCE_FILES_DAYTIME_CLIENT daytimeclient.cpp)
add_executable(daytimeclient ${SOURCE_FILES_DAYTIME_CLIENT})

set(SOURCE_FILES_ECHO_SERVER echoserver.cpp  unp.h unp.cpp)
add_executable(echoserver ${SOURCE_FILES_ECHO_SERVER})

set(SOURCE_FILES_ECHO_CLIENT echoclient.cpp unp.h unp.cpp epoll_server.cpp)
add_executable(echoclient ${SOURCE_FILES_ECHO_CLIENT})

set(SOURCE_FILES_ECHO_SERVER_MULTI_IO echoserver.cpp unp.h unp.cpp)
add_executable(echoserver_multi_io ${SOURCE_FILES_ECHO_SERVER_MULTI_IO})

set(SOURCE_FILES_TIME_SERVER_MULTI_THD timeserver_multithread.cpp ../Thread/Thread.cpp ../Thread/Thread.h)
add_executable(timeserver_multithd ${SOURCE_FILES_TIME_SERVER_MULTI_THD})

set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)
target_link_libraries(timeserver_multithd Threads::Threads)
