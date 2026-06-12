---
title: "No sound with Intel N10/ICH 7 in 10.04"
date: 2011-03-28
forum: Multimedia Software
---

### Post by dmizer on 2011-03-28
Results of aplay -l
```
$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Had a look at this thread which provided no solution for my problem: [http://ubuntuforums.org/showthread.php?t=1661716](http://ubuntuforums.org/showthread.php?t=1661716)

Here is the results of the alsa-info-script: [http://www.alsa-project.org/db/?f=692f99b39d70a58bfa4a62df389ba46eac28381c](http://www.alsa-project.org/db/?f=692f99b39d70a58bfa4a62df389ba46eac28381c)

I have double checked alsamixer to make sure that all the volume settings are correct and nothing is muted that shouldn't be.

I have been through this wiki (including upgrading alsa from source): [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by dmizer on 2011-03-29
Unfortunately, it looks like this one is bad hardware.

I tried about 12 different live CDs including Knoppix, Fedora, Hardy, and a number of others. I also finally tried installing Windows 7.

I pulled the laptop apart to make sure that the connections were good, and they were. So it looks like this is going to be a mute laptop. Everything else works perfectly in Ubuntu, and I assume that were it not for the bad hardware, the sound would also work fine.

Thanks for looking.

---

