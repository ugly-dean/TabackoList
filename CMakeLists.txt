cmake_minimum_required(VERSION 3.0.0)
project(TabackoList VERSION 0.1.0)

include(CTest)
enable_testing()

# GLOBAL FLAGS ======================
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# ===================================



# GLOBAL VARS =======================
set(MAIN_SERVER ${PROJECT_SOURCE_DIR}/MainServer.cpp)
set(MAIN_CLIENT ${PROJECT_SOURCE_DIR}/MainClient.cpp)
set(SOURCE_DIR_SERVER ${PROJECT_SOURCE_DIR}/Server)
set(INCLUDE_DIRS_COMMON ${PROJECT_SOURCE_DIR}/Common)
set(NAME_SERVER ${PROJECT_NAME}_SERVER)
set(COMMON_LIBS_NAME Hello)
set(MAIN Main)
# ===================================

function(setup_target TARGET_POSTFIX)
    set(SOURCE ${MAIN}${TARGET_POSTFIX}.cpp)
    
endfunction()

# Common ============================
add_subdirectory(${INCLUDE_DIRS_COMMON})
add_subdirectory(Client)

# ===================================

# SERVER target =====================
add_subdirectory(${SOURCE_DIR_SERVER})
add_executable(${NAME_SERVER} ${MAIN_SERVER})
target_link_libraries(${NAME_SERVER} PUBLIC "${COMMON_LIBS_NAME}")
target_include_directories(${NAME_SERVER} PUBLIC "${PROJECT_BINARY_DIR}" "${INCLUDE_DIRS_COMMON}")

# ===================================


# set(CPACK_PROJECT_NAME ${PROJECT_NAME})
# set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
# include(CPack)


