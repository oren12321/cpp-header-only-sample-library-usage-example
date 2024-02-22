cmake_minimum_required(VERSION 3.24.4)

project(app
    VERSION 1.0.0
    DESCRIPTION "Sample header only library usage example"
    HOMEPAGE_URL "https://github.com/oren12321/cpp-header-only-sample-library-usage-example")

include(FetchContent)

FetchContent_Declare(
    cpp-header-only-sample-library
    GIT_REPOSITORY https://github.com/oren12321/cpp-header-only-sample-library.git
    GIT_TAG main
    FIND_PACKAGE_ARGS NAMES sample)
FetchContent_MakeAvailable(cpp-header-only-sample-library)

add_executable(${PROJECT_NAME} src/app.cpp)
target_link_libraries(${PROJECT_NAME} sample::sample)
target_include_directories(${PROJECT_NAME} INTERFACE $<BUILD_INTERFACE:${cpp-sample-library_SOURCE_DIR}/include>)
set_property(TARGET ${PROJECT_NAME} PROPERTY CXX_STANDARD 20)

