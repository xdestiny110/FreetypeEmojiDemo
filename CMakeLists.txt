cmake_minimum_required(VERSION 3.18)
project(EmojiRender LANGUAGES CXX)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_STANDARD 17)

include(cmake/conan.cmake)
conan_cmake_run(REQUIRES
                freetype/2.11.1
                BASIC_SETUP 
                BUILD missing)
include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

file(GLOB Src *.h *.cpp)
add_executable(EmojiRenderDemo ${Src})
target_include_directories(
    EmojiRenderDemo PRIVATE
    ${CMAKE_SOURCE_DIR}
)
target_link_libraries(
    EmojiRenderDemo
    ${CONAN_LIBS}
)