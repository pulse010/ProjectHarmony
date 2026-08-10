cmake_minimum_required(VERSION 3.23)
project(PROJECTHARMONY)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

add_executable(PROJECTHARMONY
    src/main.cpp
    lib/imgui/imgui.cpp
    lib/imgui/imgui_draw.cpp
    lib/imgui/imgui_widgets.cpp
    lib/imgui/imgui_tables.cpp
    lib/imgui/imgui_impl_sdl2.cpp
    lib/imgui/imgui_impl_opengl3.cpp
    lib/imgui/imgui_demo.cpp
)

target_include_directories(PROJECTHARMONY PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}/src
    ${CMAKE_CURRENT_SOURCE_DIR}/lib/imgui
    ${CMAKE_CURRENT_SOURCE_DIR}/lib/miniaudio
)

if(WIN32)
    target_link_libraries(BREAKOUT PRIVATE

    )
elseif(APPLE)
    target_link_libraries(PROJECTHARMONY PRIVATE
        
    )
else() # Linux / Unix

    find_package(SDL2 REQUIRED)
    find_package(OpenGL REQUIRED)
    target_link_libraries(PROJECTHARMONY PRIVATE
        SDL2::SDL2
        OpenGL::GL
        pthread
        dl
        m
    )
endif()
