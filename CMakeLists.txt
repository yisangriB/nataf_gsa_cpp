cmake_minimum_required(VERSION 3.10)

project(nataf_gsa_project)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup(TARGETS)

set(SOURCES main.cpp
	    ERADist.cpp
	    exponentialDist.cpp
	    normalDist.cpp
	    ERANataf.cpp
	    gammaDist.cpp
	    runGSA.cpp
	    runForward.cpp
	    RVDist.cpp
	    gumbelDist.cpp
	    truncExponentialDist.cpp
	    betaDist.cpp
	    jsonInput.cpp
	    uniformDist.cpp
	    chiSquaredDist.cpp
	    lognormalDIst.cpp
	    weibullDist.cpp
	    discreteDist.cpp)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/lib_armadillo/armadillo-10.1.0/include)

add_executable(nataf_gsa ${SOURCES})
target_link_libraries(nataf_gsa
	CONAN_PKG::boost
	CONAN_PKG::jsonformoderncpp	
	CONAN_PKG::nlopt
	CONAN_PKG::mkl-static)

#target_link_libraries(nataf_gsa
#	CONAN_PKG::boost
#	CONAN_PKG::jsonformoderncpp	
#	CONAN_PKG::nlopt
#	CONAN_PKG::mkl-static
#	CONAN_PKG::eigen)

install(TARGETS nataf_gsa DESTINATION bin)

add_definitions(-D_ITERATOR_DEBUG_LEVEL=0) 

