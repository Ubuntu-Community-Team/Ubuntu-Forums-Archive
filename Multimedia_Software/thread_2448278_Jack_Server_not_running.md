---
title: "Jack Server not running"
date: 2020-08-05
forum: Multimedia Software
---

### Post by pianotango on 2020-08-05
Hi, I searched a lot but I couldn't find a solution for my problem on the net. 

When I put:
```
$ jackd -d alsajackdmp 1.9.12
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2016 Grame.
Copyright 2016-2017 Filipe Coelho.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
self-connect-mode is "Don't restrict self connect requests"
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: cannot set period size to 1024 frames for capture
ALSA: cannot configure capture channel
Released audio card Audio0
audio_reservation_finish
Cannot initialize driver
JackServer::Open failed with -1
Failed to open server




```

I`ve tried different period sizes for ALSA without success.

Any help there?
I`m using a HP Envy x360 Notebook with Ubuntu Studio 20.04 

THANKS IN ADVANCE!
Javier

---

