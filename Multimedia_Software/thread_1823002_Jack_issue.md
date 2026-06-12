---
title: "Jack issue"
date: 2011-08-11
forum: Multimedia Software
---

### Post by zull0017 on 2011-08-11
Hi to all

i have Apodio 8 installed on my desktop witch is based on ubuntu 10.04 LTS.
Sound works fine and jack connects with this message:

p, li { white-space: pre-wrap; } [COLOR=#999999]18:56:57.997 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]18:56:58.082 Statistics reset.[/COLOR]
 [COLOR=#999999]18:56:58.095 JACK is starting...[/COLOR]
 [COLOR=#990099]18:56:58.095 /usr/bin/jackd -u -dalsa -dhw:0 -r44100 -p1024 -n3[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66CC99]18:56:58.104 ALSA connection graph change.[/COLOR]
 no message buffer overruns
 no message buffer overruns
 jackdmp 1.9.6
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 10
 Cannot lock down memory area (Cannot allocate memory)
 [COLOR=#999999]18:56:58.177 JACK was started with PID=20250.[/COLOR]
 audio_reservation_init
 Acquire audio card Audio0
 creating alsa driver ... hw:0|hw:0|1024|3|44100|0|0|nomon|swmeter|-|32bit
 Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xfebf8000 irq 22
 configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
 ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: use 3 periods for capture
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 3 periods for playback
 Cannot use real-time scheduling (RR/10)(1: Operation not permitted)
 AcquireSelfRealTime error
 [COLOR=#CCCC99]18:56:58.305 ALSA connection change.[/COLOR]
 [COLOR=#999933]18:57:00.335 Server configuration saved to "/home/apo33/.jackdrc".[/COLOR]
 [COLOR=#999999]18:57:00.336 Statistics reset.[/COLOR]
 [COLOR=#999999]18:57:00.356 Client activated.[/COLOR]
 [COLOR=#9999CC]18:57:00.387 JACK connection change.[/COLOR]
 [COLOR=#CC9966]18:57:00.390 JACK connection graph change.[/COLOR]
 Cannot lock down memory area (Cannot allocate memory)


Then i connect some programms to it like supercollider an puredata and the connect properly, but when i try to run some examples i get no sound.
I have realtime priority enabled and added my self to audio group.



Any ideas?


Thanks in advance

---

