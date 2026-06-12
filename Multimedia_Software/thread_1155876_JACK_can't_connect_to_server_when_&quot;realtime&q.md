---
title: "JACK can't connect to server when &quot;realtime&quot; checked"
date: 2009-05-11
forum: Multimedia Software
---

### Post by humphreybc on 2009-05-11
Hi there,

Firstly let me start off by saying I have no idea what JACK does or what it is for. It got installed alongside Hydrogen Drum Machine, which I think is awesome. Unfortunately under Hydrogen my sample sounds have glitches and don't sound clean at all, so I went to settings to try to change the output to JACK instead of ALSA and it said I can't connect to the server.

So, into JACK audio config and tried to click "Start" and it gave me this:

```

jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread 1440704240, from thread 1440704240] (1: Operation not permitted)
cannot create engine
00:03:29.883 JACK was stopped successfully.
00:03:29.883 Post-shutdown script...
00:03:29.883 killall jackd
jackd: no process killed
00:03:30.291 Post-shutdown script terminated with exit status=256.
00:03:31.917 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

```

So I disabled "realtime" and sure enough it works, it connects fine but when I change the setting in Hydrogen (with JACK running behind it) Hydrogen freezes... I think it has something to do with this realtime thing...

Help please :)

---

### Post by markbuntu on 2009-05-11
You need an rt kernel to run jack with rt.

What setting are you trying to change in hydrogen?

---

### Post by ohmysql on 2010-02-20
I have the real time kernal and it's not working at all.

---

### Post by Toon81 on 2012-05-12
> **markbuntu said:**
> You need an rt kernel to run jack with rt
Blatant and utter nonsense. I have the option checked in JACK and I can record and playback with Audacity fine, and I certainly don't have an RT kernel. As a matter of fact, I don't even have a Preemptive one.

---

