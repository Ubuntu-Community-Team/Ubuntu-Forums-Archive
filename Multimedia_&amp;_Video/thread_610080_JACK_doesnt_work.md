---
title: "JACK doesnt work"
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by pavel989 on 2007-11-11
well after hours of searching,.ive found nothing that helps. Jack simply doesnt work for me. and i really would love for it to so that i can mess around with guitar effects. but regardless, there isnt much documentation on it, if any, so i dont know how to solve this. running jack --debug gives me:

This is jack 3.1.1 (C)2004 Arne Zellentin <zarne@users.sf.net>
 *debug* global_cf: {}
 *debug* user_cf: {}
 *debug* argv_cf: {'debug': {'val': True}}
 *warning* You have no standard location set, putting files into the current
           directory. Please consider setting base_dir in ~/.jack3rc.
 *debug* username is pavel
 *debug* hostname is pavel-desktop
 *debug* mail is pavel@pavel-desktop, was default / @
 *debug* multi_mode:0
 *error* Access of CD device /dev/cdrom resulted in error: No medium found

---

### Post by bakeneko on 2007-11-11
The jack you have installed is a python script for extracting audio tracks from CDs.  If you are interested in recording your own audio, you probably want to look at the JACK audio connection kit in package **libjack0**, with documentation at [http://jackaudio.org/documentation](http://jackaudio.org/documentation)

---

### Post by pavel989 on 2007-11-13
well indeed you are correct and thank you, got that cleared up. but jack still doesnt work, only now im getting the "correct" error


pavel@pavel-desktop:~$ jackd -d alsa
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: cannot set period size to 1024 frames for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
no message buffer overruns

---

### Post by bakeneko on 2007-11-14
An article about setting up JACK:
[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/#more-57](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/#more-57)
A thread about problems setting up JACK:
[http://ubuntuforums.org/showthread.php?t=76204](http://ubuntuforums.org/showthread.php?t=76204)
Maybe you can find some useful suggestions.

---

### Post by clubsoda on 2007-12-28
> **pavel989 said:**
> ALSA: cannot set period size to 1024 frames for capture
ALSA: cannot configure capture channel
cannot load driver module alsaI had that too, "solved" by setting **Frames/Period** to 512 instead of 1024.  This is easily adjusted in the qjackctl setup panel.  The reason for the inverted commas is that now I'm getting plenty of XRUNs, so jack is not really usable.

My antiqueware is a Cirrus Logic CS4280, identified by lspci as CS 4614/22/24/30.
Modules snd_cs46xx, snd_ac97_codec etc.

About this chip I find at [http://www.linuxhq.com/kernel/v2.4/4-ac9/cs46xx](http://www.linuxhq.com/kernel/v2.4/4-ac9/cs46xx) > +DMA playback buffer size is configurable from 16k (defaultorder=2) up to 2Meg 
+(defaultorder=11).  DMA capture buffer size is fixed at a single 4k page as
+two 2k fragments.So it seems these old chipsets are a bit short in the buffer department.

I'm not using a realtime kernel, maybe that would help with the XRUNs.

---

