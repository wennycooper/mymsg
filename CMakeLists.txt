
cmake_minimum_required(VERSION 2.8.12)

project("generated_code")

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_EXTENSIONS OFF)

# Find requirements
find_package(fastcdr REQUIRED)
find_package(fastrtps REQUIRED)


message(STATUS "Configuring MyMsg...")
add_library(MyMsg_lib MyMsg.cxx)
target_link_libraries(MyMsg_lib fastcdr fastrtps)

add_executable(MyMsg MyMsgPubSubTypes.cxx MyMsgPublisher.cxx MyMsgSubscriber.cxx MyMsgPubSubMain.cxx)
target_link_libraries(MyMsg fastcdr fastrtps
        MyMsg_lib )



