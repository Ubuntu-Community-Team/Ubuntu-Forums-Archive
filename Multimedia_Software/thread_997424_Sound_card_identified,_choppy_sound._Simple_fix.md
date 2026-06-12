---
title: "Sound card identified, choppy sound. Simple fix?"
date: 2008-11-29
forum: Multimedia Software
---

### Post by bluenotesoul on 2008-11-29
Installation of 64-bit 8.10 was a breeze on my new machine and all hardware (video, wireless, etc) recognized and working, though sound is choppy/laggy and sounds like a skipping record. I think this is just a simple config issue but could be wrong. 

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30f7
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at dc800000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

_Other specs:_
HP Pavilion dv4-1144us
Intel Core 2 Duo P7350 (2.0 GHz)
4096MB SDRAM

First post in the forum and new to Ubuntu. Any help is greatly appreciated!

Thanks,
Tim

---

### Post by bluenotesoul on 2008-11-29
Also, video and flash are behaving the same way.

---

### Post by psyke83 on 2008-11-30
First, configure PulseAudio correctly: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

If you get PulseAudio working correctly but your stuttering continues, be sure to read the guide carefully - especially Appendix B.

---

