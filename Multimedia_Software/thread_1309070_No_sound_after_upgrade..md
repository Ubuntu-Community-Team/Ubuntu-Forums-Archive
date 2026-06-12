---
title: "No sound after upgrade."
date: 2009-11-01
forum: Multimedia Software
---

### Post by TheNTW on 2009-11-01
I had a nice 7.1 system connected. But when I upgraded to Karmic - it died. 

lspci -v showed me this:
```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 8277
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f5ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

When I go to sound preferences -> Hardware, there is no hardware. I am pretty confused and I have no idea what just happened. I will try googling, but since this happened due upgrade, I don't think google will return any results for me (for now)

Please help me.
TY.

---

### Post by arst06d on 2009-11-01
Same here - not much help from me, I'm afraid.  I burned a livecd and booted from that just to see if it would work - it did - so i bit the bullet and did a fresh install of 9.10.
I then had sound but with a popping sound before the sound started - apparently my intel HDA soundcard has a sleep function and made the noise when waking.  I had to turn this off.

Sound is now perfect.

---

