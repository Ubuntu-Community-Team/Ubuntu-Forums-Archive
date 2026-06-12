---
title: "little problem with fluxbox and audacious"
date: 2008-10-20
forum: Multimedia Software
---

### Post by profeta81 on 2008-10-20
Hi everybody,

I'm having a small problem with audacious: if I run it during a gnome session it all works fine. If I log in into the fluxbox wm audacious experiences some problems and prints:

> 
me@my_pc:~$ audacious 
amidi-plug(amidi-plug.c:amidiplug_init:97): init, read configuration
amidi-plug(i_backend.c:i_backend_load:107): loading backend '/usr/lib/audacious/Input/amidi-plug/ap-alsa.so'
amidi-plug(i_backend.c:i_backend_load:145): backend /usr/lib/audacious/Input/amidi-plug/ap-alsa.so (name 'alsa') successfully loaded

** (audacious:25320): WARNING **: Failed to connect to server: Connection refused
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

** (audacious:25320): WARNING **: Failed to connect to server: Connection refused
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

** (audacious:25320): WARNING **: Failed to connect to server: Connection refused
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin
amidi-plug(i_backend.c:i_backend_unload:164): unloading backend 'alsa'
amidi-plug(i_backend.c:i_backend_unload:167): backend 'alsa' unloaded
LASTFM: (cleanup) Cleanup finished


This was when trying to play an MP3; when audacious is trying to play a FLAC file the output is slightly different:

> 

[...]

** (audacious:25337): WARNING **: Failed to connect to server: Connection refused
ERROR: libflacng.so: plugin.c:339 (flac_play_loop): Could not open output plugin!

** (audacious:25337): WARNING **: Failed to connect to server: Connection refused
ERROR: libflacng.so: plugin.c:339 (flac_play_loop): Could not open output plugin!

** (audacious:25337): WARNING **: Failed to connect to server: Connection refused
ERROR: libflacng.so: plugin.c:339 (flac_play_loop): Could not open output plugin!
Audacious has received SIGINT and is shutting down.
amidi-plug(i_backend.c:i_backend_unload:164): unloading backend 'alsa'
amidi-plug(i_backend.c:i_backend_unload:167): backend 'alsa' unloaded
LASTFM: (cleanup) Cleanup finished




does anybody know how I fix this?

cheers
Lorenzo

---

### Post by profeta81 on 2008-10-20
well.. this is just after a fresh install of ubuntu 8.04 with fluxbox and audacious (extra plug in are also installed)...

cheers again ;)

---

### Post by ganzor on 2009-01-28
I'm seeing the same problem with fluxbox and audacious on my brand new installation of ubuntu 8.10 with fluxbox on my really old 450MHz desktop. I get:

>  amidi-plug(amidi-plug.c:amidiplug_init:97): init, read configuration
amidi-plug(i_backend.c:i_backend_load:107): loading backend '/usr/lib/audacious/Input/amidi-plug/ap-alsa.so'
amidi-plug(i_backend.c:i_backend_load:145): backend /usr/lib/audacious/Input/amidi-plug/ap-alsa.so (name 'alsa') successfully loaded

** (audacious:10407): WARNING **: Failed to connect to server: Connection refused
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

** (audacious:10407): WARNING **: Failed to connect to server: Connection refused
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

** (audacious:10407): WARNING **: Failed to connect to server: Connection refused
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin


when trying to play mp3's.
Same question as above. Does anyone know whats causing this?

---

### Post by fabled_1 on 2009-02-28
I had this same problem with a fresh install of xubuntu 8.10 intrepid ibex

its because pulseaudio isnt installed but for some reason audacious still sets pulses as the default output plugin. All i did was go to the Menu>Prefences>Audio and changed the output plugin to ALSA output plugin.

---

### Post by arch_o_median on 2009-03-05
Thanks I had the same problem on with wmii and audacious and setting the output to alsa as suggested fixed it!

---

### Post by patogalla on 2009-10-26
It worked for me!! Thank you!!

Cheers!

---

