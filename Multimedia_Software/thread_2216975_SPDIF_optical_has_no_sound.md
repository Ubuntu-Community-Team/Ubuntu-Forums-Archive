---
title: "SPDIF optical has no sound"
date: 2014-04-15
forum: Multimedia Software
---

### Post by 1yan on 2014-04-15
So im running ubuntu 13.10 and i just bought a new pair of Turtle Beach XP510 Earphones which I thought would work since they dont use driver and connect directly to the optical SPDIF port.
I know it's not an issue with the earphones as I have booted to windows and it worked straight away.
I have unmuted it in alsamixer and tried quite a few things suggested from other pages but nothing seems to work, I honestly don't know much about pulse/alsa.

Please help! 

aplay -l if it helps:
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CA0132 Analog [CA0132 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: CA0132 Digital [CA0132 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by 1yan on 2014-05-11
In case anyone was wondering, I fixed the issue by updating to 3.15 kernal, after a restart it just worked. It also fixed my bluetooth dongle I had plugged in :P

---

