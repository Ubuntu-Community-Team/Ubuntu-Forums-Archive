---
title: "Make Speaker work on Asus N53Jn"
date: 2011-01-09
forum: Multimedia Software
---

### Post by metropolice on 2011-01-09
I has just got Asus N53JN, i have tried to installed both Ubuntu 10.04 and 10.10 but the speaker not work.
[B]lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)

[/B]cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.23

 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: Intel [HDA Intel], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Pls help me to make Speaker Work.
Thanks so much !

---

### Post by tep200377 on 2011-02-11
I have the same problem. 
At first it work after using this fix:
[http://blog.tersmitten.nl/archives/1082](http://blog.tersmitten.nl/archives/1082)

But then i installed the new kernel, and the sound is gone again.
uname -a : Linux Asus 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux


Any thougst would be wery appreciated..

---

