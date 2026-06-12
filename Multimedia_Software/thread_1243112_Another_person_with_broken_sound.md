---
title: "Another person with broken sound"
date: 2009-08-17
forum: Multimedia Software
---

### Post by gogyra on 2009-08-17
Recently I re-installed VLC. After re-installing, I found that my sound no longer works. The drivers seem to be installed, and nothing is muted in alsa-mixer. I'm using spdif out. Everything was working perfectly fine before I reinstallded VLC. Does anyone know what might be wrong?



System information:

```
jslocum@joshnixdesk:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``````
jslocum@joshnixdesk:~$ lspci -v
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
    Subsystem: Giga-byte Technology Device a022
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at e8400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```

Using Ubuntu version 9.04

---

