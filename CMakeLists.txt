# CMakeLists.txt for project ExploreIt

cmake_minimum_required(VERSION 2.8)

# Set 
set(PROJECT_NAME exploreit)
set(PROJECT_SRC_PATH src)

######## Project settings ########
project(${PROJECT_NAME})

######## RPM settings ########
set(LICENSE "Closed")

# Set compiler flags
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pthread -std=c++0x -std=gnu++0x")

include_directories(
    ${PROJECT_SRC_PATH}
)

link_directories(
   ${LINK_DIRECTORIES}
)

file(GLOB_RECURSE MODULE_SRC
   "${PROJECT_SRC_PATH}/*.cpp"
)

add_executable(${PROJECT_NAME}
    ${MODULE_SRC}
)

target_link_libraries(${PROJECT_NAME}
    ${CMAKE_THREAD_LIBS_INIT}
    rt)
    
# --- TESTING ---
enable_testing(false)

#install(TARGETS ${PROJECT_NAME} RUNTIME DESTINATION /usr/bin)
