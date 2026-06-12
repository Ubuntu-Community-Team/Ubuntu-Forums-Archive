---
title: "JACK doesn't work"
date: 2013-04-12
forum: Multimedia Software
---

### Post by rva1945 on 2013-04-12
Hi:
I want to plug my electric guitar to the audio input and run an amplifier in my Ubuntu 12.04. I learned that I must have JACK running.

I installed QjackCtl, but when I run it, it will not work, I get this

[COLOR=#999999]11:01:42.494 Patchbay deactivated.[/COLOR]
[COLOR=#999999]11:01:42.498 Statistics reset.[/COLOR]
[COLOR=#cccc99]11:01:42.506 ALSA connection change.[/COLOR]
[COLOR=#999999]11:01:42.525 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
[COLOR=#66cc99]11:01:42.541 ALSA connection graph change.

when I click on Start, I get:

D-BUS: JACK server could not be started.

is there something with the configuration?

[/COLOR]

---

### Post by rva1945 on 2013-04-12
I tried to run it form the terminal window, it seemd to be working though I got messages indicating the opposite:
robert@robert-Lenovo-G560:~$ jackd -R -P70 -dalsa -dhw:0 -r48000 -p512 -n2
jackdmp 1.9.8
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2011 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Cannot create thread 1 Operation not permitted
Cannot create thread 1 Operation not permitted
Cannot create thread 1 Operation not permitted
JACK server starting in realtime mode with priority 70
Cannot lock down 82241434 byte memory area (Cannot allocate memory)
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|512|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 512 frames (10.7 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
Cannot use real-time scheduling (RR/70)(1: Operation not permitted)
AcquireSelfRealTime error

---

