set(X11PLATFORM_SOURCES
    edge.cpp
    logging.cpp
    x11_platform.cpp
    screens_xrandr.cpp
)

if(HAVE_EPOXY_GLX)
    set(X11PLATFORM_SOURCES ${X11PLATFORM_SOURCES} glxbackend.cpp)
endif()

add_library(KWinX11Platform MODULE ${X11PLATFORM_SOURCES})
target_link_libraries(KWinX11Platform eglx11common kwin Qt5::X11Extras)

install(
    TARGETS
        KWinX11Platform
    DESTINATION
        ${PLUGIN_INSTALL_DIR}/org.kde.kwin.platforms/
)
