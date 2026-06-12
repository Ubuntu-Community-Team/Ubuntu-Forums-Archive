---
title: "Error running alsaconf"
date: 2010-04-03
forum: Multimedia Software
---

### Post by schlitz100 on 2010-04-03
I had issues with sound so I updated alsa and lost all sound afterwards. I get errors running alsaconf and am not finding anything online that helps. I am really frustrated with this and about to reinstall... any ideas? 

jason@Sinistar:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

jason@Sinistar:~$ alsamixer

jason@Sinistar:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr  2 2010 for kernel 2.6.31-20-generic (SMP).

jason@Sinistar:~$ sudo alsaconf
ERROR: modinfo: could not find module snd-opl3sa2
ERROR: modinfo: could not find module snd-cs4236
ERROR: modinfo: could not find module snd-cs4232
ERROR: modinfo: could not find module snd-cs4231
ERROR: modinfo: could not find module snd-es18xx
ERROR: modinfo: could not find module snd-es1688
ERROR: modinfo: could not find module snd-sb16
ERROR: modinfo: could not find module snd-sb8

---

