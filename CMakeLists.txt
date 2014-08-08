project(pvr.filmon)

cmake_minimum_required(VERSION 2.6)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${PROJECT_SOURCE_DIR})

enable_language(CXX)

find_package(xbmc REQUIRED)
find_package(xbmcplatform REQUIRED)
find_package(Crypto++ REQUIRED)
find_package(CURL REQUIRED)
find_package(JsonCpp REQUIRED)

include_directories(${xbmcplatform_INCLUDE_DIRS}
                    ${CRYPTOPP_INCLUDE_DIRS}
                    ${CURL_INCLUDE_DIRS}
                    ${JSONCPP_INCLUDE_DIRS}
                    ${XBMC_INCLUDE_DIR})

set(DEPLIBS ${xbmcplatform_LIBRARIES} ${CRYPTOPP_LIBRARIES}
            ${CURL_LIBRARIES} ${JSONCPP_LIBRARIES})

set(FILMON_SOURCES src/client.cpp
                   src/FilmonAPI.cpp
                   src/PVRFilmonData.cpp)

build_addon(pvr.filmon FILMON DEPLIBS)
