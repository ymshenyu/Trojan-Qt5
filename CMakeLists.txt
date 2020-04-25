cmake_minimum_required(VERSION 3.0.0)
project(trojan-qt5)

find_package(Qt5 COMPONENTS Core Gui Network REQUIRED)


set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

add_definitions(-DAPP_VERSION="1.0.0" -DTCP_FASTOPEN -DENABLE_SSL_KEYLOG -DENABLE_TLS13_CIPHERSUITES)

# Qt Awesome
set(QT_AWESOME_DIR ${CMAKE_SOURCE_DIR}/src/QtAwesome/QtAwesome)
file(GLOB_RECURSE ${QT_AWESOME_DIR}/*.cpp QT_AWESOME_SOURCES)
file(GLOB_RECURSE ${QT_AWESOME_DIR}/*.h QT_AWESOME_HEADERS)
set(QT_AWESOME_RESOURCES ${QT_AWESOME_DIR}/QtAwesome.qrc)

if(WIN32)
    # TODO
endif()

if(APPLE)
    # TODO
endif()

if(UNIX AND NOT APPLE)
    # TODO
endif()

set(TROJAN_QT5_INCLUDE_PATH
    ${CMAKE_SOURCE_DIR}/src/plog/include
)

add_executable(${PROJECT_NAME} 
    ${QT_AWESOME_SOURCES}
    ${QT_AWESOME_HEADERS}
    ${QT_AWESOME_RESOURCES}
)

target_include_directories(${PROJECT_NAME} PRIVATE ${TROJAN_QT5_INCLUDE_PATH})

target_link_libraries(${PROJECT_NAME} PRIVATE 
    Qt5::Core
    Qt5::Gui
    Qt5::Network
)
