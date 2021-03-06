#
# Copyright (c) 2020 Nordic Semiconductor ASA
#
# SPDX-License-Identifier: Apache-2.0
#

cmake_minimum_required(VERSION 3.8.2)
include($ENV{ZEPHYR_BASE}/cmake/app/boilerplate.cmake NO_POLICY_SCOPE)
add_subdirectory(../../.. ${PROJECT_BINARY_DIR}/cddl_gen)

project(NONE)

target_cddl_source(app manifest-moran3.cddl
  ENTRY_TYPES OuterWrapper
  DECODE
  ${VERBOSE}
  ${CANONICAL}
  )
target_cddl_source(app manifest-moran4.cddl
  ENTRY_TYPES SUIT_Outer_Wrapper
  DECODE
  ${VERBOSE}
  ${CANONICAL}
  )

FILE(GLOB app_sources src/*.c)
target_sources(app PRIVATE
  ${app_sources})

zephyr_compile_options(-Werror)
