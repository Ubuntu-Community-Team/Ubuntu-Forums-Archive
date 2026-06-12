---
title: "Subwoofer not working"
date: 2008-05-02
forum: Multimedia Software
---

### Post by tjb891 on 2008-05-02
Hello, I can not get any sound out of my subwoofer that came with my computer from dell (Dimension E310). This is what lspci -v outputs for my sound car.

0:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
	Subsystem: Dell Unknown device 01c4
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dff3c000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

I have tried turning LFE up but it isn't working. Anyone have any idea?

---

### Post by tjb891 on 2008-05-02
I did this and found this output if this help

aplay -l
*** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

---

