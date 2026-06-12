---
title: "fresh installation VIA VT82xx, no sound at all"
date: 2009-05-09
forum: Multimedia Software
---

### Post by Awareness on 2009-05-09
i followed the "Comprehensive Sound Problem Solutions Guide" on this forum, and nothing

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: VT1708 Analog [VT1708 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: VT1708 Digital [VT1708 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Ive checked and double checked all the volumes, i followed threats... and nothing... some help please... damn sound is quite frustrating... I always have problems with it...

---

### Post by Awareness on 2009-05-10
bump!

---

### Post by Awareness on 2009-05-10
[http://www.alsa-project.org/db/?f=8d55f7f130e76f7bb92a6f457862c279b64d72ef](http://www.alsa-project.org/db/?f=8d55f7f130e76f7bb92a6f457862c279b64d72ef)

This is the info of my system gathered via [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh)

---

### Post by codymyth on 2009-05-14
i to am having that same problem(bump).

---

### Post by Awareness on 2009-05-14
> **codymyth said:**
> i to am having that same problem(bump).

I got sound now... I dont know what I did... but after 3 reboots the sound is back...

I dunnno what i touched... sorry im not of more help :/ I opened a bug in launchpad in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/374475](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/374475)

Report there ur specs... maybe in ubuntu 9.10 is fixed... i had this problem with this motherboard sound card since 7.10.... :)

---

### Post by codymyth on 2009-05-14
mine worked originaly one 8.4 (not very loud, but usable enough) but when i did upgrades one day it just stopped working. i upped all the mixer settings in gnome volume mixer and got just enough sound to be able to hear it. 

I read on a different thread once that the sound came back for them if they did not use the nvidia driver, but when they used it still didn't worl. I also tried that, but to no avail.

---

