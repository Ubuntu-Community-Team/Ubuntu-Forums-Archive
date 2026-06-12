---
title: "Internet DJ console won't start up."
date: 2011-05-28
forum: Multimedia Software
---

### Post by MachintoshCJ on 2011-05-28
I can't get it to start because Jack Sound Server won't work. I don't know what it's talking about, and non of the tutorials are helping me. I do what the program said to do, but I can't get it to work still. Here is what is say:```
christopher@christopher-EL1330:~$ jackd -d alsa -r 44100 -p 2048
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Cannot create thread 1 Operation not permitted
Cannot create thread 1 Operation not permitted
JACK server starting in realtime mode with priority 10
Cannot lock down memory area (Cannot allocate memory)
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|2048|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
Using ALSA driver HDA-Intel running on card 0 - HDA NVidia at 0xfe024000 irq 21
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server

```Someone please help, because I want to start my own Internet radio station before I change my mind.

---

### Post by knokkels on 2011-05-28
Hey there, 

not sure if it is of any use to you, but chances are you will get a bit further with this link

[http://ubuntuforums.org/showthread.php?p=5101085](http://ubuntuforums.org/showthread.php?p=5101085)
edit: damn shame about the time difference, i want to take up dj'ing again too

---

