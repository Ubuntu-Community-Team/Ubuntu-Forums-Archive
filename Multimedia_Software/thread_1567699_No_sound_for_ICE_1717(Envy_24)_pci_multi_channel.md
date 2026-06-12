---
title: "No sound for ICE 1717(Envy 24) pci multi channel"
date: 2010-09-04
forum: Multimedia Software
---

### Post by deepakbm on 2010-09-04
hi i ve got a problem with my sound ,i installed ubuntu 10.04.
i dont get any sound in my system .when i  used this command in terminal aplay -l
i got this list

card 0: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


can anybody help me

---

### Post by lidex on 2010-09-05
See here:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442)

---

