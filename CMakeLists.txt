# Pulled from https://cmake.org/cmake-tutorial/

cmake_minimum_required (VERSION 2.6)
project (playing-with-dlib)

# add the binary tree to the search path for include files
include_directories("${PROJECT_BINARY_DIR}/src")

# add the executable
add_executable (playing-with-dlib src/imageDisplay.cxx)

# For -std=c++11
target_compile_features(playing-with-dlib PRIVATE cxx_range_for)
add_compile_options(-O3 -Wl,-search_paths_first -Wl,-headerpad_max_install_names)
add_compile_options(-F/Library/Frameworks)

add_definitions(-DDLIB_JPEG_SUPPORT)
add_definitions(-DDLIB_USE_BLAS)
add_definitions(-DDLIB_USE_LAPACK)
add_definitions(-DDLIB_PNG_SUPPORT)
add_definitions(-DNDEBUG)
include_directories(/Users/lee_vettleson/code/3rdparty/dlib)
include_directories(/usr/local/Cellar/opencv3/HEAD-976ee44/include)
include_directories(/usr/local/Cellar/opencv3/HEAD-976ee44/include/opencv)

link_directories(/usr/X11R6/lib)
find_library(SM_LIB libSM.dylib)
find_library(ICE_LIB libICE.dylib)
find_library(X11_LIB libX11.dylib)
find_library(XEXT_LIB libXext.dylib)
target_link_libraries(playing-with-dlib "${SM_LIB}")
target_link_libraries(playing-with-dlib "${ICE_LIB}")
target_link_libraries(playing-with-dlib "${X11_LIB}")
target_link_libraries(playing-with-dlib "${XEXT_LIB}")

link_directories(/usr/lib)
target_link_libraries(playing-with-dlib libcblas.dylib)
target_link_libraries(playing-with-dlib liblapack.dylib)
target_link_libraries(playing-with-dlib libsqlite3.dylib)

target_link_libraries(playing-with-dlib /Users/lee_vettleson/code/3rdparty/dlib/build/dlib/libdlib.a)
target_link_libraries(playing-with-dlib /usr/local/lib/libpng.dylib)


