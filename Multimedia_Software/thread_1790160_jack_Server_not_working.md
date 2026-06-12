---
title: "jack Server not working"
date: 2011-06-24
forum: Multimedia Software
---

### Post by daniel_w93 on 2011-06-24
I really enjoy making music with ubuntu currently with amSynth and Hydrogen...I connect those to my midi keyboard thru KAConnect because when I try to start the jackd server it never works.

This really sucks cause I would like to connect some effects to the sounds I make with Rakarrack for example and then output everything to ardour.
But both programms tell me jack server isn't running.
If i start qjacktctl and hit start it gives me the following output:

```
20:44:10.245 Patchbay deactivated.
20:44:10.271 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
20:44:10.303 ALSA connection graph change.
20:44:10.492 ALSA connection change.
20:44:19.955 Startup script...
20:44:19.956 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
20:44:20.359 Startup script terminated with exit status=32512.
20:44:20.359 JACK is starting...
20:44:20.359 /usr/bin/jackd -r -dalsa -dhw:0 -r44100 -p1024 -n2 -s -S
20:44:20.362 JACK was started with PID=4141.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in non-realtime mode
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|soft-mode|16bit
Using ALSA driver HDA-Intel running on card 0 - HDA NVidia at 0xdfef4000 irq 22
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
20:44:27.504 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.
JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
Driver is not running
Cannot create new client
JackSocketClientChannel read fail
Cannot open qjackctl client
```

any clue?

---

