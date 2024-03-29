cmake_minimum_required(VERSION 3.16)

project(ThinkingMinds VERSION 0.1 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Qt6 6.4 REQUIRED COMPONENTS Quick)

qt_standard_project_setup()

qt_add_executable(appThinkingMinds
    src/main.cpp src/minds.cpp src/minds.h
)

qt_add_qml_module(appThinkingMinds
    URI ThinkingMinds
    VERSION 1.0
    QML_FILES app/Main.qml app/Dashboard.qml app/About.qml app/Footer.qml app/Help.qml app/Android.qml app/MyRage.qml app/WLExploit.qml app/Wifi.qml app/SideBar.qml app/IOT.qml app/Server.qml app/Set.qml
)

set_target_properties(appThinkingMinds PROPERTIES
    MACOSX_BUNDLE_GUI_IDENTIFIER my.example.com
    MACOSX_BUNDLE_BUNDLE_VERSION ${PROJECT_VERSION}
    MACOSX_BUNDLE_SHORT_VERSION_STRING ${PROJECT_VERSION_MAJOR}.${PROJECT_VERSION_MINOR}
    MACOSX_BUNDLE TRUE
    WIN32_EXECUTABLE TRUE
)

target_link_libraries(appThinkingMinds
    PRIVATE Qt6::Quick
)

install(TARGETS appThinkingMinds
    BUNDLE DESTINATION .
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)
