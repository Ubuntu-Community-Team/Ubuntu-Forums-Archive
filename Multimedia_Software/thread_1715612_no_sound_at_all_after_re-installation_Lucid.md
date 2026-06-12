---
title: "no sound at all after re-installation Lucid"
date: 2011-03-27
forum: Multimedia Software
---

### Post by sham08 on 2011-03-27
Just installed a new motherboard (Gigabyte G31M-ES2L) on my PC. This is due to the on going, long and unsolved freeze/hang-up problem in Ubuntu before, that I've been encountered.   

However, this thread isn't about freeze/hang-up problem. After a clean installed yesterday, I found out there was no audio completely. Even the welcome sound wasn't heard. So, hope someone could help me out. Here are the :

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and the lspci -v :

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fdff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

Any response and help are really appreciated. And thanks in advance.

---

