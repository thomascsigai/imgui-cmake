cmake_minimum_required(VERSION 3.0)

# Nom du projet ImGui
project(ImGui)

# Ajouter les fichiers sources d'ImGui
set(IMGUI_SRC
    imgui.cpp
    imgui_draw.cpp
    imgui_tables.cpp
    imgui_widgets.cpp
)

# Ajouter les fichiers des backends en fonction de votre configuration
# Par exemple, pour OpenGL + GLFW, ajoutez ces fichiers :
list(APPEND IMGUI_SRC
    backends/imgui_impl_opengl3.cpp
    backends/imgui_impl_glfw.cpp
)

# Créer une cible statique pour ImGui
add_library(${PROJECT_NAME} STATIC ${IMGUI_SRC})

# Inclure les répertoires des headers d'ImGui et des backends
target_include_directories(${PROJECT_NAME} PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}/backends
    ${CMAKE_CURRENT_SOURCE_DIR}/../glad/include
    ${CMAKE_CURRENT_SOURCE_DIR}/../glfw/include
)
