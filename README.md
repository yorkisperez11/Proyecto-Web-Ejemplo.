#!/bin/bash

# =========================================================================
# ACTIVIDAD: INTEGRANDO HTML CON GIT Y GITHUB
# =========================================================================

# CONFIGURACIÓN INICIAL (Cambia esto con tus datos)
USUARIO_GITHUB="TU_USUARIO_DE_GITHUB"
REPOSITORIO="Proyecto-Web-Ejemplo"
URL_REPO="https://github.com/YourUsername/Proyecto-Web-Ejemplo.git"

echo "🚀 Iniciando el proceso de automatización..."

# 1. Clonar el repositorio recién creado en GitHub
echo "📂 Clonando el repositorio remoto..."
git clone $URL_REPO
cd $REPOSITORIO

# 2. Crear archivos base simulados (HTML y CSS inicial)
echo "📝 Creando archivos HTML y CSS iniciales..."
echo '<!DOCTYPE html><html><head><link rel="stylesheet" href="styles.css"></head><body><h1>Mi Proyecto Web</h1><p>Hola Mundo</p></body></html>' > index.html
echo 'body { font-family: Arial; background-color: white; color: black; }' > styles.css

# 3. Primer Commit y Push a Main
echo "📤 Subiendo el proyecto inicial a la rama main..."
git add .
git commit -m "Añadido proyecto web inicial"
git push origin main

# 4. Crear rama feature-mejora-estilo y trabajar en ella
echo "🌿 Creando y cambiando a la rama feature-mejora-estilo..."
git checkout -b feature-mejora-estilo

# Modificar el CSS en la rama de estilos
echo "🎨 Aplicando mejoras de diseño en la rama feature..."
echo 'body { font-family: "Helvetica Neue", sans-serif; background-color: #f0f0f0; color: #333; }' > styles.css

git add styles.css
git commit -m "Mejora del diseño visual y paleta de colores"
git push origin feature-mejora-estilo

# 5. SIMULACIÓN DEL CONFLICTO (Modificar main al mismo tiempo)
echo "🔄 Regresando a main para simular un cambio de otro colaborador..."
git checkout main

# El otro colaborador cambia el fondo a azul en la misma línea
echo 'body { font-family: Arial; background-color: blue; color: white; }' > styles.css
git add styles.css
git commit -m "Cambio rápido de estilo en main por otro colaborador"

# 6. INTENTO DE MERGE Y RESOLUCIÓN DEL CONFLICTO
echo "💥 Intentando hacer merge de feature-mejora-estilo en main (Esto va a fallar a propósito)..."
git merge feature-mejora-estilo

echo "🛠️ Resolviendo el conflicto automáticamente eligiendo la mejor combinación..."
# Creamos el estado final limpio del archivo sin las marcas de conflicto
echo 'body { font-family: "Helvetica Neue", sans-serif; background-color: #f0f0f0; color: #333; }' > styles.css

# Concluir el merge
git add styles.css
git commit -m "Conflictos resueltos: fusionando rama feature con éxito"
git push origin main

# 7. ACTUALIZACIÓN DEL README.MD (Documentación Puntos 3 y 4)
echo "📖 Actualizando el archivo README.md con la documentación requerida..."

cat << 'EOF' > README.md
# Proyecto-Web-Ejemplo

Este es un proyecto web educativo diseñado para practicar la integración de flujos de trabajo con HTML, CSS, Git y GitHub.

## 🚀 Cómo clonar y ejecutar el proyecto localmente

Sigue estos pasos para tener una copia del proyecto funcionando en tu máquina local:

1. **Clonar el repositorio:**
   Abre la terminal y ejecuta el siguiente comando:
   ```bash
   git clone [https://github.com/TU_USUARIO/Proyecto-Web-Ejemplo.git](https://github.com/TU_USUARIO/Proyecto-Web-Ejemplo.git)
