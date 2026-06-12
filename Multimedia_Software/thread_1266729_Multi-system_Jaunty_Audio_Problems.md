---
title: "Multi-system Jaunty Audio Problems"
date: 2009-09-14
forum: Multimedia Software
---

### Post by Ash96 on 2009-09-14
Is there a basic problem with audio configuration in Jaunty? Because I have Jaunty installed on three computers in my house and the audio on all three computers doesn't work. I've tried fixing them a little, but I don't know where to start. The audio troubleshooting article at help.ubuntu.com isn't much help, it's not set up well. 

One of the computers is an old Toshiba laptop circa 2002, another is a newer Toshiba laptop bought last year. The last is a custom built desktop I'm using as a home server. I did install it from the server image, but I installed the Gnome/Ubuntu desktop environment on it. Why would the audio not work on all three computers?

Any help would be much appreciated.

---

### Post by FiVAL on 2009-09-16
Do U have on one of the systems maybe the same problem like me?

[http://ubuntuforums.org/showthread.php?p=7946322#post7946322]("http://ubuntuforums.org/showthread.php?p=7946322#post7946322")

I don't have any solution....

---

### Post by Ash96 on 2009-09-17
Nobody has any ideas? Again, I don't know where to start. There is absolutely no sound coming from any of the computers. I'm pretty sure all three "see" the sound cards. the *aplay -l* test was a positive on the new toshiba and the custom computer. Here is some data. Let me know if you need others.

New Toshiba laptop: lspci -v
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff64
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d6400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

Custom Desktop/Server Computer: lspci -v
```
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81f6
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

Old Toshiba laptop: lspci -v
```
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1000 [size=256]
	I/O ports at 1880 [size=64]
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0
```

---

### Post by markbuntu on 2009-09-17
Try this first

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

Go here if you are still having problems

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Ash96 on 2009-09-24
Those threads didn't really help me much. I tried some of the things from them on my old Toshiba and new Toshiba. The sound on the old one started working inexplicably. I don't think it was anything I did in your threads, because I did the same things on the new one and the sound still isn't working. It's has to be the same issue with all three though since all three (minus the old laptop now) had no sound what so ever, I just have no idea what the issue could be. I'm lost :(

---

### Post by Ash96 on 2009-10-13
Does Jaunty have any fundamental audio problems? It has to for three completely different computers to have the same exact problem. Anyone???

---

