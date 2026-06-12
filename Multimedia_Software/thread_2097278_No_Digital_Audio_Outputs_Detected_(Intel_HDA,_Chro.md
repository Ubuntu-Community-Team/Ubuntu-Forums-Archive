---
title: "No Digital Audio Outputs Detected (Intel HDA, Chrontel HDMI)"
date: 2012-12-22
forum: Multimedia Software
---

### Post by hellforgedheart on 2012-12-22
Hi all, I've been scouring the web for months now trying to get my digital outputs to be detected on my aOpen Digital Engine 965HE and 965HG. 

Here's my aplay -l results.

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

Here's my alsa-info.sh

[http://www.alsa-project.org/db/?f=a2ec8eaee30c6e4a6cd0d607b9ada24e1169b918]("http://www.alsa-project.org/db/?f=a2ec8eaee30c6e4a6cd0d607b9ada24e1169b918")

Ironically alsa-mixer shows the mixer device as:

Chrontel Chrontel HDMI

but no sub-device or codec information seems to be detected.

In Windows XP I'm able to get audio only after installing the chipset drivers, video drivers and audio drivers in that order. In Windows 7, everything works out of the box.

Any help from all you ALSA masters out there is greatly appreciated.

Thanks!

---

