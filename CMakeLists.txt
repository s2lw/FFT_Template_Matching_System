cmake_minimum_required(VERSION 3.10.0)
project(fft-project VERSION 0.1.0 LANGUAGES C CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(OpenCV_DIR "D:/OpenCV/build")  # Dostosuj jeśli build jest w innym podfolderze

# Pakiet OpenCV
find_package(OpenCV REQUIRED)
include_directories(${OpenCV_INCLUDE_DIRS})

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

# src
set(SOURCES
    src/main.cpp
    src/utils.cpp
    src/fft-seq.cpp
    src/fft-openmp.cpp
    src/utils.cpp
    src/ifft-seq.cpp
    # src/kolejny_plik.cpp
)

# OpenMP
find_package(OpenMP REQUIRED)

# executable
add_executable(fft-project ${SOURCES})

target_link_libraries(fft-project PUBLIC OpenMP::OpenMP_CXX ${OpenCV_LIBS})

