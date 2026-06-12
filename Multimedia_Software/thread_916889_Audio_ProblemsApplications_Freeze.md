---
title: "Audio Problems/Applications Freeze"
date: 2008-09-11
forum: Multimedia Software
---

### Post by iamthemicrowave on 2008-09-11
Hi everyone. I am having some sort of sound problem on my linux rig. Occasionally audio files freeze my computer and the program running it.

Rhythmbox, Youtube.com, Pandora.com...None of these will play audio files. I hit play but the track will not start, and no sound comes out. Rhythmbox will crash and I have to restart it.

The problem can be fixed by restarting my computer.

I followed the audio sticky to install everything, including medibuntu. This problem does only happen occasionally, but it is a large nuisance.

Thank you for reading this, and any input/advice you have. I am running openJDK with icedTea and icedTea browser plug-in.

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

lspci -v
(only relevant device shown)
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Dell Unknown device 01c2
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
```

---

