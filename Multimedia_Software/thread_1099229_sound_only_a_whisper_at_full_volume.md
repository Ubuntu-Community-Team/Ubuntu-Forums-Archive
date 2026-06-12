---
title: "sound only a whisper at full volume"
date: 2009-03-17
forum: Multimedia Software
---

### Post by ymp on 2009-03-17
My system plays sound but I cannot get it to be above a whisper using amplified speakers.
aplay -l returns the following information about my sound card:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Controls for sound show that sound is at maximum, but I can barely hear anything.
Advice on how to fix this very welcome.

---

### Post by lovinglinux on 2009-03-18
Make sure you have "Master", "PCM" and "Front" volume options at maximum.

---

