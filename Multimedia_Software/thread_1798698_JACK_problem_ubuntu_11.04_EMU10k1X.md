---
title: "JACK problem ubuntu 11.04 EMU10k1X"
date: 2011-07-06
forum: Multimedia Software
---

### Post by mundoalinks on 2011-07-06
Hi everybody
i cant get jack working
soundcard chipset:  EMU10k1X

here Qjackctl log:

```
  p, li { white-space: pre-wrap; }  JACK server starting in non-realtime mode
 Cannot lock down memory area (Cannot allocate memory)
 control device hw:0
 control device hw:0
 audio_reservation_init
 Acquire audio card Audio0
 creating alsa driver ... hw:0|hw:0|1024|3|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 Using ALSA driver EMU10K1X running on card 0 - Dell Sound Blaster Live! at 0xec00 irq 17
 configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
 ALSA: final selected sample format for capture: 16bit little-endian
 ALSA: got smaller periods 2 than 3 for capture
 ALSA: cannot configure capture channel
 Cannot initialize driver
 JackServer::Open() failed with -1
 Failed to start server
 [COLOR=#999999]15:07:08.438 JACK ha sido detenido con estado 255.[/COLOR]
 [COLOR=#ff0000]15:07:10.027 No puede conectarse al servidor JACK como cliente. - La operación global falló. - No puede conectarse al servidor. Por favor revise la ventana de mensajes para mas información.[/COLOR]
 Cannot connect to server socket err = ConexiÃ³n rehusada
 Cannot connect to server socket
 jack server is not running or cannot be started

```already added 
@audio   -  rtprio     99 
@audio   -  memlock    unlimited 
@audio   -  nice      -19

[FONT=monospace]to [/FONT]
/etc/security/limits.conf 

im member of audio group

realtime option unchecked

i also reinstalled ubuntu in a fresh install and the same problem


Thanks

---

### Post by mundoalinks on 2011-07-10
bump

---

### Post by urielweb on 2011-07-30
I also can't get jack to work, please help us!

---

