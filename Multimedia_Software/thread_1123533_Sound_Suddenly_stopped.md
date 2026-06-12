---
title: "Sound Suddenly stopped"
date: 2009-04-12
forum: Multimedia Software
---

### Post by Glen Darby on 2009-04-12
Hi,

I've recently installed ubuntu 8.10 - new install

Sound was working fine but then it dissapeared.

I did "aplay -l" and it seemed to come back with Duplicate script of the same card running

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I've done a Reinstall of the drivers : 
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils and then sudo apt-get install linux-sound-base alsa-base alsa-utils

Then replaced the desktop and GDM :
sudo apt-get install gdm ubuntu-desktop

Rebooted, but still there is no sound except a little crackeling and it still shows duplicate script on "aplay -l"

Any Ideas on this please.

Glen.

---

### Post by Glen Darby on 2009-04-12
Just a quick update on the above.

I tried out the ubuntu live CD and sound seems to be working on that ok, so it must have something to do with the drivers.

Glen.

---

