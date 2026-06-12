---
title: "Problemas con ecasound"
date: 2008-08-05
forum: Multimedia Software
---

### Post by luisferbaq on 2008-08-05
Hola amigos:

necesito capturar audio desde una tarjeta DELTA 1010LT de 8 canales, yo utilizo ecasound, el problema es que hasta Feisty lo hacia sin problemas con el siguiente comando:

$ ecasound -f:32,8,44100 -a 1,2 -i:alsa -a:1 -erc:1,1 -o:file1.mp3 -a:2 -erc:2,1 -o:file2.mp3 -t 10

Con esto la aplicación me generaba un archivo por cada canal seleccionado, pero a partir de Gusty cuando termina la captura la aplicación no finaliza el proceso y se queda esperando nunca se cierra.

[COLOR="DarkOrange"]- [ Controller/Batch processing finished (0) ] ---------------------------------
(eca-control-objects) Disconnecting chainsetup: "command-line-setup"[/COLOR].

He probado en Gusty y Hardy y no funciona correctamente.

Si alguien tiene una idea de como solucionarlo y lo quiera compartir se lo agradecería mucho.

Saludos,

Luis

---

