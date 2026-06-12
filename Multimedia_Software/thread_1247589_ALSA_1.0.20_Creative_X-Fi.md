---
title: "ALSA 1.0.20 Creative X-Fi"
date: 2009-08-23
forum: Multimedia Software
---

### Post by justiceerolin on 2009-08-23
Hey guys,

Currently running Ubuntu 9.04.  When I go to Sound Preferences, the Test button produces a sound.  When I go to alsamixer, nothing is muted and everything is up all the way.

However, when I play music/video/Youtube/etc, I get no sound at all!

Here's some relevant information:

uname -r 
```
2.6.28-15-generic
```

lspci -vnn (truncated for sound card)
```
02:06.0 Multimedia audio controller [0401]: Creative Labs SB X-Fi [1102:0005]
	Subsystem: Creative Labs Device [1102:002c]
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at ac00 [size=32]
	Memory at ebc00000 (64-bit, non-prefetchable) [size=2M]
	Memory at e4000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: SB-XFi
	Kernel modules: snd-ctxfi, ctxfi
```

cat /proc/asound/version
```
Advanced Linux Sound Architecture Driver Version 1.0.20.
Compiled on Aug 23 2009 for kernel 2.6.28-15-generic (SMP).
```

I've also ran the alsa-info.sh script.  The results is in the following link:  [http://pastebin.com/f4180dd68]("http://pastebin.com/f4180dd68")

Thanks for all the future help.

---

### Post by justiceerolin on 2009-08-23
UPDATE:

Sound works in the following:  Test button in Sound Preferences, and Totem Movie Player.

However, sound does not work in VLC, Flash, or Adobe AIR (Pandora).  

This happened because I reinstalled gstreamer.  Still figuring out how to get sound in Firefox and Adobe AIR.

---

### Post by bigdee973 on 2009-09-12
im having the same problem even with the younger version of alsa that was already installed.  im trying to figure out why it doesnt work neither

---

