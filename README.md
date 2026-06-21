# Centinela (versión sin build)

Esta es una versión de Centinela escrita en HTML + JavaScript plano (sin
React, sin Vite, sin paso de compilación). Todo el código vive en un único
archivo: `index.html`. Firebase se carga desde un CDN con etiquetas
`<script>` normales.

Se reescribió así a propósito, para que se pueda subir directo a GitHub
Pages sin instalar Node ni ejecutar ningún comando de compilación.

## ⚠️ Advertencia de seguridad

Igual que en la versión original:

- La contraseña del panel de propietario (`OWNER_PASSWORD`, dentro de
  `index.html`) queda visible para cualquiera que abra el código fuente de
  la página desde el navegador.
- Las reglas de `firestore.rules` permiten lectura y escritura a cualquiera
  (`allow read, write: if true`). Cualquiera con la configuración de
  Firebase del sitio (pública por diseño) puede leer y escribir directo en
  la base de datos, sin pasar por la app.

Para datos reales de terceros, conviene agregar Firebase Authentication y
restringir las reglas antes de compartir el link de la app.

Nota: a partir de esta versión, los reportes ya no incluyen el número de
teléfono de la persona reportada — solo su alias ficticio, la comunidad y
la descripción. Esto reduce (pero no elimina) el riesgo de tratar datos
personales de terceros sin su consentimiento.

## Publicar con GitHub Pages

1. Subí este `index.html` (y `firestore.rules`, si querés tenerlo en el repo
   como referencia) a un repositorio en GitHub.
2. En el repo: **Settings** → **Pages**.
3. En "Source" elegí **Deploy from a branch**, rama `main`, carpeta `/ (root)`.
4. Guardá. GitHub te da una URL tipo `https://tu-usuario.github.io/tu-repo/`
   en uno o dos minutos.

No hace falta instalar nada ni correr ningún comando: arrastrar el archivo
a GitHub (o subirlo desde "Add file → Upload files" en la web) alcanza.

## Desplegar las reglas de Firestore

Las reglas (`firestore.rules`) no se suben solas con GitHub Pages — viven en
Firebase, no en tu sitio. Para aplicarlas hace falta Firebase CLI (eso sí
requiere Node) o copiarlas y pegarlas a mano en:
Firebase Console → Firestore Database → Reglas → pegar el contenido →
Publicar.
