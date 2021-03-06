include(FetchContent)

###################################################################################################
# - cub -------------------------------------------------------------------------------------------

message("Fetching CUB")

FetchContent_Declare(
    cub
    GIT_REPOSITORY https://github.com/thrust/cub.git
    # August 28, 2020
    GIT_TAG        2442f44532ffcc53298c7e3a298feb5134563860
)

FetchContent_GetProperties(cub)
if(NOT cub_POPULATED)
  FetchContent_Populate(cub)
  # We are not using the cub CMake targets, so no need to call `add_subdirectory()`.
endif()
set(CUB_INCLUDE_DIR "${cub_SOURCE_DIR}" PARENT_SCOPE)

###################################################################################################
# - thrust ----------------------------------------------------------------------------------------

message("Fetching Thrust")

FetchContent_Declare(
    thrust
    GIT_REPOSITORY https://github.com/thrust/thrust.git
    # August 28, 2020
    GIT_TAG        52a8bda46c5c2128414d1d47f546b486ff0be2f0
)

FetchContent_GetProperties(thrust)
if(NOT thrust_POPULATED)
  FetchContent_Populate(thrust)
  # We are not using the thrust CMake targets, so no need to call `add_subdirectory()`.
endif()
set(THRUST_INCLUDE_DIR "${thrust_SOURCE_DIR}" PARENT_SCOPE)

###################################################################################################
# - jitify ----------------------------------------------------------------------------------------

message("Fetching Jitify")

FetchContent_Declare(
    jitify
    GIT_REPOSITORY https://github.com/rapidsai/jitify.git
    GIT_TAG        cudf_0.15
    GIT_SHALLOW    true
)

FetchContent_GetProperties(jitify)
if(NOT jitify_POPULATED)
  FetchContent_Populate(jitify)
  # We are not using the jitify CMake targets, so no need to call `add_subdirectory()`.
endif()
set(JITIFY_INCLUDE_DIR "${jitify_SOURCE_DIR}" PARENT_SCOPE)

###################################################################################################
# - libcudacxx ------------------------------------------------------------------------------------

message("Fetching libcudacxx")

FetchContent_Declare(
    libcudacxx
    GIT_REPOSITORY https://github.com/rapidsai/thirdparty-freestanding.git
    GIT_TAG        cudf
    GIT_SHALLOW    true
)

FetchContent_GetProperties(libcudacxx)
if(NOT libcudacxx_POPULATED)
  FetchContent_Populate(libcudacxx)
  # libcudacxx has no CMake targets, so no need to call `add_subdirectory()`.
endif()
set(LIBCUDACXX_DIR "${libcudacxx_SOURCE_DIR}" PARENT_SCOPE)
set(LIBCUDACXX_INCLUDE_DIR "${libcudacxx_SOURCE_DIR}/include/" PARENT_SCOPE)
set(LIBCXX_DIR "${libcudacxx_SOURCE_DIR}/libcxx/" PARENT_SCOPE)
set(LIBCXX_INCLUDE_DIR "${libcudacxx_SOURCE_DIR}/libcxx/include/" PARENT_SCOPE)
