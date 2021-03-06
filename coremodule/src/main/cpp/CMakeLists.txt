# For more information about using CMake with Android Studio, read the
# documentation: https://d.android.com/studio/projects/add-native-code.html

# Sets the minimum version of CMake required to build the native library.
cmake_minimum_required(VERSION 3.4.1)

## 添加编译选项
add_definitions(-std=c++11)
add_definitions(-DPLATFORM_ANDROID)
set(CMAKE_BUILD_TYPE Release)
set(ANDROID_STL "c++_static")

#include_directories(${PROJECT_SOURCE_DIR}/android-libs/xxx/include/)
#include_directories(${PROJECT_SOURCE_DIR}/android-libs/xxx/include/)

set(HEADERS
#        ${PROJECT_SOURCE_DIR}/common_log.h
        )

# Creates and names a library, sets it as either STATIC
# or SHARED, and provides the relative paths to its source code.
# You can define multiple libraries, and CMake builds them for you.
# Gradle automatically packages shared libraries with your APK.

add_library( # Sets the name of the library.
        core
        # Sets the library as a shared library.
        SHARED
        # Provides a relative path to your source file(s).
#        common_log.cpp
        coretest.cpp
        ${HEADERS}
        )

# Searches for a specified prebuilt library and stores the path as a
# variable. Because CMake includes system libraries in the search path by
# default, you only need to specify the name of the public NDK library
# you want to add. CMake verifies that the library exists before
# completing its build.

find_library( # Sets the name of the path variable.
        log-lib
        # Specifies the name of the NDK library that
        # you want CMake to locate.
        log)

# libs
SET(opencv_lib ${PROJECT_SOURCE_DIR}/android-libs/opencv/${ANDROID_ABI}/libopencv_java3.so)


# Specifies libraries CMake should link to your target library. You
# can link multiple libraries, such as libraries you define in this
# build script, prebuilt third-party libraries, or system libraries.

target_link_libraries( # Specifies the target library.
        core
        # Links the target library to the log library
        # included in the NDK.
        jnigraphics
        ${log-lib}
        #        ${opencv_lib}
        )