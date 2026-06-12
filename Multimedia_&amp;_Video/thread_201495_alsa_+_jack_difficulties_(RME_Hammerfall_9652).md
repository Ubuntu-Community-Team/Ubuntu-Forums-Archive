---
title: "alsa + jack difficulties (RME Hammerfall 9652)"
date: 2006-06-21
forum: Multimedia &amp; Video
---

### Post by dmerrill on 2006-06-21
Hello everyone -

I am having trouble getting jackd started with my RME Hammerfall 9652 card..  Has anyone seen this message before, and know where to point me to fix it? Thanks very much in advance - Here's what I get:

>jackd -d alsa
jackd 0.100.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
nperiods = 2 for capture
ALSA: cannot set hardware parameters for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
no message buffer overruns

..and here is my output from hdspconf:
Card 0 : RME Digi9636 (Rev 1.5) at 0xde000000, irq 11
Card 1 : SBLive! Value [CT4832] (rev.8, serial:0x80271102) at 0xd000, irq 11

---

### Post by dolson on 2006-06-22
Have you tried with other settings for the sampling rate, the period, and buffer sizes?

I had a similar error early on in Dapper beta stages, where I had to rm -rf ~/.asound* and then it would work... Not sure if it'll help.

Can you play sounds on your RME under Linux normally? If not, do you have firmware loaded for it?

---

### Post by metasymbol on 2006-07-05
Here the same, but different: I had temporaly changed my audio hardware from a envy24 to a Hammerfall, but jackd dosn`t start with that card. (Sorry, can`t start Jack)

The Hammerfall is working with alsa without any problems.

In SUSE 10.0 on the same computer this card is working properly with jack.

---

