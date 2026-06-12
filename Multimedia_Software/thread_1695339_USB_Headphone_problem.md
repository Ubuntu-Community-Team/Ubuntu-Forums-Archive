---
title: "USB Headphone problem"
date: 2011-02-25
forum: Multimedia Software
---

### Post by glittleman on 2011-02-25
USB headphones work with some programs, but not with others.

I have Linux Mint with KDE and system settings to USB heaphones as default. Juk and Rhythmbox use the headphones, but Songbird and Flash on Konquerer and Firefox use the laptop speakers.

output of

> aplay -l
gives

> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: default [C-Media USB Audio Device   ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

