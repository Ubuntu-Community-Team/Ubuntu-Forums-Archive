---
title: "Sound:here today,gone tomorrow."
date: 2008-06-15
forum: Multimedia Software
---

### Post by FrostBlue on 2008-06-15
Hello everyone,
I never had sound from my speakers in Gutsy.After upgrading to Hardy and installing Realtek HDA drivers and compiling latest Alsa,I had sound coming from speakers.Now after a few more upgrades (I dont know exactly what things got upgraded),the speakers dont work.
The only difference when I had sound was in Kmix, in switches I had a fourth option alongside Headphone,Speaker and IEC958.When that was on the speakers used to work.But now that option is gone.

Could someone help?

the output from `aplay -l` is as follows,

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by FrostBlue on 2008-06-16
Solved this from this thread.

[http://ubuntuforums.org/showthread.php?t=830102](http://ubuntuforums.org/showthread.php?t=830102)

Thanks to the community.

---

