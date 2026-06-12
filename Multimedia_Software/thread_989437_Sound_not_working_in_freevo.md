---
title: "Sound not working in freevo"
date: 2008-11-21
forum: Multimedia Software
---

### Post by wjhildreth on 2008-11-21
Hello all,

I am running 8.10 and have installed freevo 1.8.1. It starts fine and plays my movies but I cannot get sound to work.

Other applications seem to work fine, mplayer, vlc, realtime, tuxguitar, etc. I have tried changing the device setting in the config file with no luck. When I do a lspci -v I get the following information for the sound card.

<code>
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
	Subsystem: Tyan Computer Device 2662
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1400 [size=256]
	I/O ports at 1800 [size=64]
	Memory at e0000c00 (32-bit, non-prefetchable) [size=512]
	Memory at e0000800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0
</code>


Any guidance would be greatly appreciated.

Warm Regards,

Joe

---

### Post by MCrittenden on 2008-12-11
Did you ever get this working?

---

### Post by wjhildreth on 2008-12-15
No, I ended up replacing the sound card with a sound blaster.

Joe

---

