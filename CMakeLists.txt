# declare version
cmake_minimum_required(VERSION 3.1...3.15)

if(${CMAKE_VERSION} VERSION_LESS 3.12)
    cmake_policy(VERSION ${CMAKE_MAJOR_VERSION}.${CMAKE_MINOR_VERSION})
endif()

# glad gl loader with all ARB and EXT functions.
project(glad)

# output folder
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)

# use those files for the project
set(HEADERS
	glad/glad.h
	KHR/khrplatform.h
)
set(SOURCES
	glad.c
)

# prepend directories to the files
list(TRANSFORM HEADERS PREPEND include/)
list(TRANSFORM SOURCES PREPEND src/)

# create the static library
add_library(glad STATIC ${SOURCES} ${HEADERS})
target_include_directories(glad PUBLIC include)
target_compile_features(glad PUBLIC cxx_std_11)