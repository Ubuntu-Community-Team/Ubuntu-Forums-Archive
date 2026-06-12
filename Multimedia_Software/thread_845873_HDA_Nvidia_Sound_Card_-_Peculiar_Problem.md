---
title: "HDA Nvidia Sound Card - Peculiar Problem"
date: 2008-07-01
forum: Multimedia Software
---

### Post by sakthi on 2008-07-01
Hi All

I am running hardy heron (32 bit desktop) on my AMD Athlon X2 64 desktop.

I have a peculiar problem like the sound works well with headphones but not normally. Without headphones there is not a bit of sound coming out. I have done various things like compiling alsa-base, alsa-lib and alsa-utils.....adding some lines in alsabase and all. I have also tried installing linux backport generic drivers which comes for hardy. But nohting helped to get sound without the headphones. Can someone help me please.....

here are my aplay and lspci outputs:


~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

~$ lspci | grep Audio
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

---

### Post by sakthi on 2008-07-01
Solved:

right-clicked on the volume, opened the3 volume control, went to edit and included the mono in the visible list and sound came bang!!!!!!!!! Arrrggghhh.....simple thing I missed out before questioning u guys :(

---

### Post by divercetgd on 2008-11-29
thanks! same problem same answer :)

---

