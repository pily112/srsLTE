#
# Copyright 2013-2019 Software Radio Systems Limited
#
# This file is part of srsLTE
#
# srsLTE is free software: you can redistribute it and/or modify
# it under the terms of the GNU Affero General Public License as
# published by the Free Software Foundation, either version 3 of
# the License, or (at your option) any later version.
#
# srsLTE is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU Affero General Public License for more details.
#
# A copy of the GNU Affero General Public License can be found in
# the LICENSE file in the top-level directory of this distribution
# and at http://www.gnu.org/licenses/.
#

include_directories(
        ${Boost_INCLUDE_DIRS}
        ${SEC_INCLUDE_DIRS}
        ${PROJECT_SOURCE_DIR}
)

link_directories(
        ${Boost_LIBRARY_DIRS}
        ${SEC_LIBRARY_DIRS}
)

add_executable(scell_search_test scell_search_test.cc)
target_link_libraries(scell_search_test
        srsue_phy
        srsue_stack
        srsue_upper
        srsue_mac
        srsue_rrc
        srslte_common
        srslte_phy
        srslte_radio
        srslte_upper
        rrc_asn1
        ${CMAKE_THREAD_LIBS_INIT}
        ${Boost_LIBRARIES})
add_test(scell_search_test scell_search_test --duration=1 --phy_lib_log_level=0 --intra_meas_log_level=none --nof_enb=2 --cell.nof_prb=25)
