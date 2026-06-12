---
title: "No sound 8.04 LTS, toshiba U205 laptop w/ intel sound card"
date: 2008-08-07
forum: Multimedia Software
---

### Post by yakinikku on 2008-08-07
Hey guys,

    I am new to ubuntu and the whole linux world in general.  I have done research trying to resolve my sound issues, but I have not been able to come across a solution.

aplay -l reveals this

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

So its showing to me that the card driver is installed (so I think).  Then, I checked alsamixer, none of the devices are muted.  Also, my sound icon by the clock does not have a red slash thru it.  Also, I don't know how it happened (again, new to the linux and ubuntu community), but I have both the .14 kernel and .19 kernels installed, and sound does not work in both.  Any help you guys can offer would be greatly appreciated.  TIA!

---

### Post by yakinikku on 2008-08-08
anyone?  :(

---

### Post by lmg444 on 2009-03-18
did you every resolve this issue?  I'm having the same problem, same machine.  still searching...

---

### Post by markbuntu on 2009-03-18
Open this file
```

sudo gedit /etc/modprobe.d/alsa-base

```
at the end of the file add this line
```

options snd-hda-intel model=toshiba

```
save the file, close it and reboot

---

### Post by lmg444 on 2009-03-18
followed the instructions, but no joy.  I had already started another thread:

[http://ubuntuforums.org/showthread.php?p=6917241#post6917241](http://ubuntuforums.org/showthread.php?p=6917241#post6917241)

does that information help you understand the problem?

lmg444

---

### Post by markbuntu on 2009-03-18
Well, that is what people who own that laptop have reported as fixing their problem. Perhaps you have a more basic problem. Extensive troubleshooting help is here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

