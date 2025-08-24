cmake_minimum_required(VERSION 3.13)
project(vhfvoiceradio)

set(CMAKE_INSTALL_PREFIX "/usr/")
SET(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${PROJECT_SOURCE_DIR}/cmake/")

#file(GLOB_RECURSE SRC "src/*.cpp" "src/*.h" "src/*.hpp" "src/*.c" "mbelib/*.c")
file(GLOB_RECURSE SRC 
    "src/main.cpp"
    "src/radio_module.h"
    "src/radio_interface.h"
    "src/demod.h"
    
    "src/demodulators/nfm.h"
    "src/demodulators/wfm.h"
    "src/demodulators/am.h"
    "src/demodulators/usb.h"
    "src/demodulators/lsb.h"
    "src/demodulators/raw.h"
    
    "src/dsp/common.h"
    "src/dsp/ctcss.h"
    "src/dsp/dcs.h"
)

#find_package(ITPP REQUIRED)

if (NOT SDRPP_MODULE_CMAKE)
    set(SDRPP_MODULE_CMAKE "/usr/share/cmake/Modules/sdrpp_module.cmake")
endif ()

include(${SDRPP_MODULE_CMAKE})

#target_link_libraries(vhfvoiceradio PRIVATE fftw3 ${ITPP_LIBRARY})
target_link_libraries(vhfvoiceradio PRIVATE fftw3)
target_include_directories(vhfvoiceradio PRIVATE "src/")
