---
title: "No Digital Audio Outputs Detected (Intel HDA, Chrontel HDMI)"
date: 2015-12-26
forum: Multimedia Software
---

### Post by AndrewBucklin on 2015-12-26
Hi all, I've been scouring the web for months now trying to get my  digital outputs to be detected. 

Here's my aplay -l results.

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Here's my alsa-info.sh

[http://www.alsa-project.org/db/?f=cc58b2e54b2023cc604cd3d1eae68a35cb808fbb](http://www.alsa-project.org/db/?f=cc58b2e54b2023cc604cd3d1eae68a35cb808fbb)

Ironically alsa-mixer shows the mixer device as:

Chrontel Chrontel HDMI

but no sub-device or codec information seems to be detected.

Any help from all you ALSA masters out there is greatly appreciated.

Thanks!

---

