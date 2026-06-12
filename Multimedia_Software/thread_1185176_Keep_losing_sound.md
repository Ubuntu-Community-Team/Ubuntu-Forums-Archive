---
title: "Keep losing sound"
date: 2009-06-12
forum: Multimedia Software
---

### Post by W2IBC on 2009-06-12
I dont know why but all of a sudden sound has become a real problem. keep getting a notification about analog sound failed to load reverting back to digital.

aplay -l output

ddog@nsa-495823:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: VT1708 Analog [VT1708 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: VT1708 Digital [VT1708 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

problem is Analog is the only one that works. but it keeps saying analog failed to load and reverts back to digital.

is there any way to force it to analog and blacklist the digital?

im almost sure this is a "pulse audio" problem as I have never had sound issues until pulse audio started getting used.

---

