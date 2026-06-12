---
title: "HDMI sound on NVidia NVS 3100M"
date: 2010-12-31
forum: Multimedia Software
---

### Post by fa2k on 2010-12-31
Hi, I was going to complain that hdmi audio does not work on the NVS 3100M, but it does 
when following this: [http://forum.xbmc.org/showthread.php?t=69601&page=11](http://forum.xbmc.org/showthread.php?t=69601&page=11) .

Basically, 1) find the **card** number of the HDMI devices using **aplay -l** 
```
[muon:~]$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card **2**: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card **2**: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card **2**: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card **2**: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Play to device#7 using speaker-test: **speaker-test -Dplughw:2,7**
Replace "2" with the number of the card (mine was 1 before).

Alas, this has to be done each time a HDMI cable is plugged in (or the computer is rebooted). not a big problem for me, but maybe for someone. I don't think the card number will change often.

Hope this helps someone who has the same problem.

---

### Post by fa2k on 2010-12-31
There is  a mismatch in sample rate so the sound is pretty bad.. Adequate for some comedy shows i'd say.  I think the TV thinks it's getting 44100 Hz but thhe computer is sending 48000 Hz

---

