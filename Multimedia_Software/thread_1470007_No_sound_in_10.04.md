---
title: "No sound in 10.04"
date: 2010-05-02
forum: Multimedia Software
---

### Post by yuv656 on 2010-05-02
Everything seems to be detected and configured, levels turned up in alsamixer, yet no sound is coming out of the headphones/speakers. Please help.

**aplay -l**
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

**lspci -v**
```

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: Intel Corporation Device 3001
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at e3220000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

---

### Post by smartbei on 2010-05-02
Have you tried alsamixer?

EDIT - just now noticed that you listed it as something you have tried... :-\

---

### Post by yuv656 on 2010-05-02
Solved it by installing the alsa backports package

---

