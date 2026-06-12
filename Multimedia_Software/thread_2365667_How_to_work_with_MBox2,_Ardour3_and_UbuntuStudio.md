---
title: "How to work with MBox2, Ardour3 and UbuntuStudio"
date: 2017-07-09
forum: Multimedia Software
---

### Post by zano on 2017-07-09
Hi,
I would like to work with the 2-channel USB audio peripheral MBox2.
It should work with Linux (my kernel 3.19.0-15-lowlatency) due to [http://www.zamaudio.com/?p=97](http://www.zamaudio.com/?p=97) (¨the Mbox2 driver stuff is part of Linux kernel after 3.8! Just plug in your device, lights come on and it works. Any config issues with JACK, make sure you are using the ALSA backend and 2 ins and 2 outs, >256 buffer size and 3 periods").
And (see attachment) it looks good!
But I don't understand how to let MBox work with Ardour3.
I've tried to start a new session, in the Audio/MIDI setup popup Ie choosed Mbox as device (Audio System: Jack, Driver: Alsa, Frequency: 44,1Khz, buffer: 1024 samples. But a popup says: Could not reconnect to the Audio/MIDI engine.

Sorry, I'm new with an external audio peripheral and to Ardour

---

### Post by zano on 2017-07-09
Instead I've tested Audacity: in this case I can record from MBox...

---

### Post by zano on 2017-07-11
I've also tried to kill pulseaudio and start jack

```
pulseaudio --kill
```

```
jackd -t 200 -p 2048 -R -T -d alsa -n 2 -r 44100 -p 1024 -d hw:MBox,0

```

but

```
jackdmp 1.9.10
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2014 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
no message buffer overruns
`default' server already active
Failed to open server
```

---

### Post by zano on 2017-07-13
a partial solution was:

- Open QjackCtl
- Click on SetUp (Impostazioni): both input and output (dispositivo d'entrata e dispositivo d'uscita): hw:MBox
- Close SetUp
- Start JACK

- open Ardour
- create two new Tracks for the two audio line of MBox
- click on the record button on both tracks, on record button on the top-bar and then play... it'll record!

now I cannot hear any sound, that's the next problem.

---

