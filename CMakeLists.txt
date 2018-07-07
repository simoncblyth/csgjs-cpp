cmake_minimum_required (VERSION 3.5)
set(name CSGBSP)
project(${name} VERSION 0.1.0)

include(OpticksBuildOptions)  # finds BCM 

include(GNUInstallDirs)
set(CMAKE_INSTALL_INCLUDEDIR "externals/include/${name}")
set(CMAKE_INSTALL_LIBDIR     "externals/lib")
set(CMAKE_INSTALL_BINDIR     "lib")

set(SOURCES
   csgjs.cpp
)

set(HEADERS
   csgjs.hh
)

add_library(${name} SHARED ${SOURCES})

install(TARGETS ${name}  DESTINATION ${CMAKE_INSTALL_LIBDIR})
install(FILES ${HEADERS} DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})
bcm_deploy(TARGETS ${name} NAMESPACE Opticks:: SKIP_HEADER_INSTALL)

