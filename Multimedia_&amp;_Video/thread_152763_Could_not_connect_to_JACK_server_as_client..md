---
title: "Could not connect to JACK server as client."
date: 2006-03-30
forum: Multimedia &amp; Video
---

### Post by ImperialStout on 2006-03-30
I get the following message when i try to Start the JACK service through QJackCtl:

----------
jackd 0.99.0
Copyright 2001-2003 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
loading driver ..
apparent rate = 44100
creating alsa driver ... default|default|64|2|44100|0|0|nomon|swmeter|-|16bit
configuring for 44100Hz, period = 64 frames, buffer = 2 periods
You appear to be using the ALSA software "plug" layer, probably
a result of using the "default" ALSA device. This is less
efficient than it could be. Consider using a hardware device
instead rather than using the plug layer. Usually the name of the
hardware device that corresponds to the first soun
ALSA: cannot set period size to 64 frames for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
23:12:45.943 JACK was stopped successfully.
23:12:47.875 Could not connect to JACK server as client.
----------

My System Specs are:
P4 1.4 / 512 MB RD RAM / Ubuntu 5.10
Sound Card: Sound Fusion CS46xx

---

### Post by dolson on 2006-03-30
I don't know about that sound card you have there, but in QjackCtl, for input and output devices, are there different ones listed that you could try selecting directly? Like hw0,0 and so forth?

Your output there shows stuff about the plug layer, which I'm not familiar with... I don't know how JACK would be able to work around this without hacking some config files or something... I'm still very new, but try my first suggestion and see. We can go from there.

---

### Post by ImperialStout on 2006-03-30
hey dolson, thanks for the prompt reply. I had tried them earlier but prior to posting i thought it would be a good idea to stick to the configuration you had mentioned in one of the ubuntu studio articles. However, changing the Input and Output devices to hw:0,0 and hw:0,1 prints the following errors:
-----
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0,1|hw:0,0|64|2|44100|0|0|nomon|swmeter|-|16bit
control device hw:0
configuring for 44100Hz, period = 64 frames, buffer = 2 periods
jack_create_thread: error -1 switching current thread to rt for inheritance: Unknown error 4294967295
cannot start watchdog thread
cannot load driver module alsa
00:28:12.964 JACK was stopped successfully.
00:28:14.931 Could not connect to JACK server as client.
-----

I am also considering buying a new soundcard if this doesnt work so I might putup a "recommended/working" soundcards thread soon. I think that would be beneficial to everyone here. Thanks once again.

---

### Post by dolson on 2006-03-30
Hmm, that's curious... Did you set up your system for RT access with PAM or set_rlimits or even realtime-lsm?

The wiki page was suggested for a SB Live! 5.1 card, I'm not sure what your card would require for setup... But anyhow, yeah. Your thread idea is a good one, methinks.

---

### Post by OmahaVike on 2006-04-24
not quite a fix, but perhaps a place to investigate...

i ended up with the same error after installing USB large storage capability.  used to work flawlessly before.  installed the modules, and now she won't run at all.

time for me to reinstall.

---

