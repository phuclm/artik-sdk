CMAKE_MINIMUM_REQUIRED	( VERSION 2.8 )
PROJECT		  	( pwm-test )

FIND_PACKAGE ( ArtikBase )
FIND_PACKAGE ( ArtikSystemio )

SET ( CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wno-unused-parameter" )

SET ( EXE_PWM_TEST pwm-test )

SET ( PWM_TEST_SRC ${CMAKE_CURRENT_SOURCE_DIR}/test/pwm_test )

SET ( SRC_TEST_PWM	artik_pwm_test.c
    )

ADD_EXECUTABLE		( ${EXE_PWM_TEST} ${SRC_TEST_PWM} )

TARGET_INCLUDE_DIRECTORIES ( ${EXE_PWM_TEST}
								PUBLIC ${ARTIK_BASE_INCLUDE_DIR}
			     				PUBLIC ${ARTIK_SYSTEMIO_INCLUDE_DIR}
			   )

TARGET_LINK_LIBRARIES	( ${EXE_PWM_TEST}
								${ARTIK_BASE_LIBRARIES}
								${ARTIK_SYSTEMIO_LIBRARIES}
)

INSTALL ( TARGETS ${EXE_PWM_TEST} RUNTIME DESTINATION lib/artik-sdk/tests )
