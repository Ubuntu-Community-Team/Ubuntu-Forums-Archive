---
title: "No Sound - Ubuntu 10.10"
date: 2011-07-25
forum: Multimedia Software
---

### Post by Ashkwil on 2011-07-25
Hi I have an offline Ubuntu 10.10 install which has decided to suddenly stop playing sound!

It has a sound card and the build in output however neither are working!

It is a HP compaq computer and is pretty old!

Here are a few things from what ive seen on threads might help?

```
dale@dale-K7S41GX:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dale@dale-K7S41GX:~$ 


```

And also

ALSA INFORMATION

[http://www.alsa-project.org/db/?f=2f635f4607f5b632f86ceda095835e4ae0a76a45](http://www.alsa-project.org/db/?f=2f635f4607f5b632f86ceda095835e4ae0a76a45)


Thanks I really need to get this resolved!!!

Ash :)

---

### Post by Ashkwil on 2011-07-25
BUMP! Any help is really appreciated i have no clue what went wrong!

---

### Post by Ashkwil on 2011-07-26
BUMP again i really need to get this sorted today as it goes back to its owner today!

---

### Post by Ashkwil on 2011-07-26
After some more tweaking I ended up with no sound cards visible in sound preferences and only a dummy output. 

[http://ubuntuforums.org/showthread.php?t=1475185&page=1](http://ubuntuforums.org/showthread.php?t=1475185&page=1)

this thread solved this problem and got my sound back
:guitar::popcorn:

---

### Post by lkjoel on 2011-07-26
Try Sound Troubleshooting in my signature.

---

