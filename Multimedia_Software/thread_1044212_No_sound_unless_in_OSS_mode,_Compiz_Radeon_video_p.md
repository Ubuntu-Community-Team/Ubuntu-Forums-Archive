---
title: "No sound unless in OSS mode, Compiz Radeon video problems"
date: 2009-01-19
forum: Multimedia Software
---

### Post by naelphin on 2009-01-19
I have installed Ubuntu 8.10 AMD64 to try it out. The sound worked fine at first, but after a few reboots to install ATI's drivers, the sound stopped working.

[quote=aplay -l]
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/quote]

The only option in System/prefs/sound that works is OSS, but then only sound from a single app works at a time.

The second problem is that videos in VLC and the default media player flicker badly, I have a Radeon HD 4850, and the latest drivers from ATI's website don't help the problem either.

---

