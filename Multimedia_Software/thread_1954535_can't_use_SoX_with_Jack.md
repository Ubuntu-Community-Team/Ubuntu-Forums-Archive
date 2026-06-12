---
title: "can't use SoX with Jack"
date: 2012-04-08
forum: Multimedia Software
---

### Post by ubusc on 2012-04-08
Hello,

I'm only 3 months old newbie with Ubuntu/Linux, so please be gentle...;)

I'm using Ubuntu 10.10 and I'm trying to use SoX with Jack audio driver. (while I'm using Jack for all the other audio applications)

But SoX just won't output any sound. I've tried some options described in the manual (such as set AUDIODRIVER or play -t alsa....etc.)but it won't give me any errors, just not output audio. 

It's very frustrating. I can't even play an audio file...

here's the information when I start my jackd with command: 'jackd -R -d alsa -s -r 48000 -X seq'

Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    737577
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|soft-mode|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback


How can I run SoX command without quitting my jack environment?

any help would be appreciated.

thank you.

---

