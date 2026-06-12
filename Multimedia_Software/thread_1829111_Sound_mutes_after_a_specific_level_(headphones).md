---
title: "Sound mutes after a specific level (headphones)"
date: 2011-08-20
forum: Multimedia Software
---

### Post by Bakuhatsu on 2011-08-20
I've bumped into this weird situation where if I play music using my headphones through the frontpanel input it mutes them if it gets too loud, about 60% of the unamplified part.

When I use a pair of in-ears they can be completely maxed without anything muting, and it's not related to that it doesn't get enough power because if I run through the windows partition it works without no issues to max both the headphones and in-ears.

When I use the headphones with 60%+ volume it keeps auto-muting until I lower the volume before deciding to unmute it myself, if I click to unmute when about about 60%+ I hear sound really quick before it decides to auto-mute again.

Ubuntu 11.04
```
bakuhatsu@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
``````
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
        Subsystem: ASUSTeK Computer Inc. Device 8357
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at fbcf4000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```

---

