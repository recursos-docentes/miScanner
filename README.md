# 📄 miScanner
 
Escáner de documentos que funciona en el navegador del celular. Convierte fotos de hojas en PDF limpios y extrae el texto, sin instalar nada y sin subir las imágenes a ningún servidor.
 
**👉 Usarlo:** `https://<tu-usuario>.github.io/<nombre-del-repo>/`
 
---
 
## ✨ Funciones
 
| | Función | Detalle |
|---|---|---|
| 📷 | **Cámara o galería** | Saca una foto o elige varias de la galería y las procesa una por una. |
| 🎯 | **Detección automática de bordes** | Ubica las 4 esquinas de la hoja apenas se carga la foto. |
| ✋ | **Ajuste manual** | Las esquinas se arrastran con el dedo, con lupa para mayor precisión. |
| 📐 | **Corrección de perspectiva** | Endereza la hoja aunque la foto esté sacada en ángulo. |
| 🎨 | **Filtros** | Mejorada (blanquea el papel), Grises, Blanco y negro, Original. |
| 🗂️ | **Páginas** | Reordenar, rotar y eliminar antes de exportar. |
| 📑 | **PDF multipágina** | En tamaño A4 o del tamaño de la imagen. Descargar o compartir (WhatsApp, Drive, correo). |
| 🔤 | **OCR en español** | Reconoce el texto para copiarlo o descargarlo como `.txt`. |
 
## 🔒 Privacidad
 
Todo el procesamiento ocurre **en el dispositivo**. Las fotos nunca salen del celular: no hay servidor, ni cuenta, ni almacenamiento en la nube.
 
Solo se descargan de internet dos librerías, y solo la primera vez que se usan:
 
- [jsPDF](https://github.com/parallax/jsPDF), para armar el PDF.
- [Tesseract.js](https://github.com/naptha/tesseract.js), para el OCR, junto con los datos del idioma español.
## 📱 Cómo usarlo
 
1. Abrir la página en el navegador del celular (Chrome o Safari).
2. Tocar **Cámara** y fotografiar la hoja, o **Galería** para elegir fotos existentes.
3. Revisar las esquinas detectadas y corregirlas si hace falta. **Auto** vuelve a detectar y **Completa** usa toda la imagen.
4. Tocar **Siguiente**, elegir un filtro y **Guardar página**.
5. Repetir con las demás hojas.
6. Tocar **PDF** para exportar o **Texto** para extraer el contenido.
> 💡 **Tip:** desde el menú del navegador, la opción **"Agregar a pantalla de inicio"** permite abrirlo como si fuera una app.
 
### Consejos para mejores resultados
 
- Apoyar la hoja sobre un fondo que contraste (una mesa oscura o de color).
- Buscar buena luz y evitar la sombra del propio celular sobre la hoja.
- Dejar un poco de margen alrededor de la hoja en la foto.
## 🚀 Publicarlo en GitHub Pages
 
1. Crear un repositorio nuevo y subir el archivo `index.html`.
2. Ir a **Settings → Pages**.
3. En **Source**, elegir la rama `main` y la carpeta `/ (root)`.
4. Guardar y esperar un minuto. La dirección aparece en esa misma pantalla.
> ⚠️ La cámara requiere **HTTPS**. GitHub Pages ya lo provee. Si se abre el archivo directamente desde la computadora, usar el botón Galería.
 
## 🛠️ Cómo funciona
 
Es un único archivo HTML con JavaScript puro. No usa frameworks ni necesita un paso de compilación.
 
- **Detección de bordes:** reduce la foto a unos 320 px y separa la hoja del fondo con tres criterios: brillo (umbral de Otsu), diferencia con el color del borde de la imagen y contornos (gradiente de Sobel). Después toma la región más grande, calcula su envolvente convexa y elige el cuadrilátero de área máxima. Se queda con el candidato más "rectangular".
- **Perspectiva:** calcula una homografía a partir de las 4 esquinas y remuestrea la imagen con interpolación bilineal.
- **Filtros:** normalizan cada píxel según el promedio local de brillo (imagen integral). Así el papel queda blanco aunque la iluminación sea despareja. El modo blanco y negro usa umbral adaptativo.
## ⚠️ Limitaciones
 
- Las páginas se guardan **solo mientras la pestaña está abierta**. Al cerrarla se pierden (el navegador avisa antes).
- La detección automática puede fallar con hoja blanca sobre fondo blanco o si la hoja ocupa casi toda la foto. En ese caso, ajustar las esquinas a mano.
- El OCR funciona mejor con texto impreso que con letra manuscrita.
- El PDF y el OCR necesitan conexión la primera vez, para descargar las librerías.
## 📄 Licencia
 
Uso personal y educativo. Las librerías externas mantienen sus propias licencias (MIT para jsPDF y Apache 2.0 para Tesseract.js).
 
---
 
Hecho por **Elizabeth Izquierdo** 🇺🇾
 
