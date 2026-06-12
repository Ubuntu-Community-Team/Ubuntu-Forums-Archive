---
title: "Ubuntu 9.10 Weird Sound Problem"
date: 2009-11-23
forum: Multimedia Software
---

### Post by arda7 on 2009-11-23
Hello, I am new to Ubuntu and I have been facing a weird sound problem since I have updated to 9.10 from 9.04. My problem is that the sound feels like it is all over the place. It is not quite, low or loud but after listening to any audio player for over 1-2 minutes my ears are hurt even in low volume. I have been trying different alsamixer settings like dropping down LFE, Surround and PCM but none of it worked. I also tried other outputs like OSS, ESD and tried a PulseAudio equalizer (tried to lower everything)  even tried to use it in mono but still no use. After couple of minutes it sounds like all frequencies are messed up or maybe there is some problem in channels. I am posting my driver information through lspci -v. Thank you very much in advance.

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
    Subsystem: Intel Corporation Device 2008
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at 93220000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```

---

### Post by arda7 on 2009-11-23
This is what I get from [SIZE=2]aplay -l[/SIZE]

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by arda7 on 2009-11-24
Could it be frequencies or channels? Anyone?

---

