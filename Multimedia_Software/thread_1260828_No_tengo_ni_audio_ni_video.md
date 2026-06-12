---
title: "No tengo ni audio ni video"
date: 2009-09-08
forum: Multimedia Software
---

### Post by smrubio on 2009-09-08
Hola!

Quisiera saber si me pueden apoyar... soy nuevo con Linux y no tengo audio ni vídeo, en algún post vi que el comando gstreamer-properties podría detectar el problema, y así fue... ahora no sé como solventarlo, este es el resultado del comando:

[I]gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'ALSA - Advanced Linux Sound Architecture': No se pudo abrir el dispositivo de audio para reproducción. El dispositivo está siendo usado por otra aplicación. [gstalsasink.c(689): gst_alsasink_open (): /GstPipeline:pipeline1/GstAlsaSink:alsasink3:
Device 'hw:0,0' is busy]
The program 'gstreamer-properties' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 61 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)[/I]

Les agradeceré mucho en lo que me puedan asesorar.

Saludos.

---

