---
title: "Audio Chipset AD1988B Separated Sound Help!"
date: 2009-12-15
forum: Multimedia Software
---

### Post by PhX89 on 2009-12-15
I know English very bad, so try to understand my trouble please.
I have motherboard M2N-E with Analog Devices 1988B sound chipset. In Windows i can separate my sound to 2 streams - in rear panel stream n1 and front panel stream n2. On Ubuntu 9.10 i have problem with separated stream.

I want (need) to separate stream! Help please. And i have a question, can i use only ALSA driver with separated streams?

phx@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

