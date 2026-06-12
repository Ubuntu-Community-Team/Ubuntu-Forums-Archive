---
title: "Sound Working in Headphones but not in Speakers"
date: 2009-01-07
forum: Multimedia Software
---

### Post by SePhII2oTh on 2009-01-07
UBUNTU 8.10

Hello, I have a problem with my sound card, theres no sound in speakers, but in Headphones there is.....,ive been researching using google and i cant find anything to fix this. could you help me?

sephiroth@sephiroth-laptop:~$ lspci -nn | grep Audio
00:07.0 Audio device [0403]: nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec [10de:0774] (rev a1)

sephiroth@sephiroth-laptop:~$ dmesg | grep HDA
[   15.824763] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 19 (level, low) -> IRQ 19
[   15.824799] HDA Intel 0000:00:07.0: setting latency timer to 64
sephiroth@sephiroth-laptop:~$ 


sephiroth@sephiroth-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


my PC its a Compaq CQ50-103LA

---

### Post by SePhII2oTh on 2009-01-07
Sorry but Help :(

bump

---

### Post by SePhII2oTh on 2009-01-07
Bump

---

