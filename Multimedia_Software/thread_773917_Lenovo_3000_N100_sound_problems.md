---
title: "Lenovo 3000 N100 sound problems"
date: 2008-04-29
forum: Multimedia Software
---

### Post by His Eminence on 2008-04-29
Hi!

There is following problem with my Lenovo 3000 N100 after the upgrade from Kubuntu 7.10 to Kubuntu 8.04.

**Before the upgrade** the sound played through headphones and speakers, the problem was that pluging the headphones in didn't mute the speakers. 

Now **after the upgrade** the speakers are muted when a device is plugged into the headphone jack but the sound is not coming out of headphones - or any other device connected through the jack.

Any clues?

root@lazy:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Zorael on 2008-04-29
In the off chance that this is similar to what happened to my Acer laptop, try opening /etc/modprobe.d/alsa-base and add the following line to the end of it.
```
options snd-hda-intel model=lenovo
```
Restarting ALSA may apply the changes, not sure, else just reboot.

---

