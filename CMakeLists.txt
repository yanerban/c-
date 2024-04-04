cmake_minimum_required(VERSION 3.16)

project(data_structure_algorithm C CXX )

SET (CMAKE_CXX_COMPILER  "/usr/bin/clang++")
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CXX_FLAGS
    "${CMAKE_CXX_FLAGS} -g -pthread -pedantic -Wall -Wextra -Wconversion  -Wno-unused-parameter -Wold-style-cast -Woverloaded-virtual  -Wshadow -Wpointer-arith -fsanitize=address -fsanitize=undefined -rdynamic  -std=c++20"
)

if(CMAKE_BUILD_BITS EQUAL 32)
  list(APPEND CXX_FLAGS "-m32")
endif()

if(CMAKE_CXX_COMPILER_ID STREQUAL "Clang")
  message(STATAUS "use Clang compiler")
  list(APPEND CXX_FLAGS "-Wno-null-dereference")
  list(APPEND CXX_FLAGS "-Wno-sign-conversion")
  list(APPEND CXX_FLAGS "-Wno-unused-local-typedef")
  list(APPEND CXX_FLAGS "-Wthread-safety")
  list(REMOVE_ITEM CXX_FLAGS "-rdynamic")
endif()

string(REPLACE ";" " " CMAKE_CXX_FLAGS "${CXX_FLAGS}")

set(CMAKE_CXX_FLAGS_DEBUG "-O0")
set(CMAKE_CXX_FLAGS_RELEASE "-O2 -DNDEBUG")
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin)
set(LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR}/lib)


add_subdirectory(data_structure)