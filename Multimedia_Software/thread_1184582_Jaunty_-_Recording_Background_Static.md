---
title: "Jaunty - Recording Background Static"
date: 2009-06-11
forum: Multimedia Software
---

### Post by mastermindg on 2009-06-11
I'm recording streaming broadcasts locally and I'm getting static on my recording. I've played around with the mixer settings but I haven't been able to figure out where the static is coming from.

I'm on a Dell E-521, 64-bit, with an HDA-NVIDIA (STAC92xx).

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: Dell Device 01ed
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping Enable+ Fixed+
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

---

### Post by mastermindg on 2009-06-11
This has something to do with the IEC958 Playback Source settings because when I change this during recording I'm getting different degrees of static and noise. How do I mute this?

---

