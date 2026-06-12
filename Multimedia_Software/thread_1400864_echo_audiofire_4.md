---
title: "echo audiofire 4"
date: 2010-02-07
forum: Multimedia Software
---

### Post by nacho al horno on 2010-02-07
I've a problem with my echo audiofire 4 in ubuntu studio 9.10. When i start jack with the driver "firewire" after a few seconds it shut down alone,this is the message that i get:


 19:35:00.254 Script de inicio...
19:35:00.255 artsshell -q terminate
sh: artsshell: not found
19:35:00.657 El script de inicio finalizó con estado 32512.
19:35:00.657 JACK está iniciándose...
19:35:00.657 /usr/bin/jackd -R -P70 -dfirewire -dhw:0 -r44100 -p1024 -n2
19:35:00.660 JACK se inició con PID=5903.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
07058808970:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.43 built Sep 17 2009 20:06:09
19:35:02.689 Configuración del servidor salvada en "/home/nacho/.jackdrc".
19:35:02.691 Reiniciar estadísticas.
19:35:02.728 Cliente activado.
19:35:02.730 Cambios en las conexiones JACK.
19:35:02.732 Cambió el gráfico de conexiones de JACK.
SSE2 detected
19:35:02.931 Escaneo del patchbay JACK activo...
19:35:18.185 XRUN callback (1).
firewire ERR: wait status < 0! (= -1)
DRIVER NT: could not run driver cycle
19:35:20.955 Cambió el gráfico de conexiones de JACK.
jack main caught signal 12
no message buffer overruns
19:35:21.150 Escaneo del patchbay JACK activo...
19:35:21.151 Cambios en las conexiones JACK.
19:35:21.179 Notificación de apagado.
19:35:21.182 JACK está deteniéndose...
19:35:21.209 JACK está siendo forzado...
zombified - calling shutdown handler
19:35:21.351 Escaneo del patchbay JACK activo...
19:35:21.410 JACK ha sido detenido satisfactoriamente.
19:35:21.410 Script de post - apagado...
19:35:21.412 killall jackd
jackd: proceso no encontrado
19:35:21.824 El script de post - apagado finalizó con estado 256.
 

I've fallowed the instructions to use firewire, and the ffado-mixer recognize the device, so i think there's must be a problem with jack but i can't work it out...any ideas? i'll apreciate any help you could give me
thanks

---

