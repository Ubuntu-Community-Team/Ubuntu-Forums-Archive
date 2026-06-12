---
title: "No sound with Feisty"
date: 2007-05-09
forum: Multimedia &amp; Video
---

### Post by ekmandyn on 2007-05-09
Hi there,

I'm new with linux and I just installed ubuntu Feisty in my toshiba A135. All is working just fine except for the sound. I have read other post about this problems and tried different things without luck. I think my modem and soundcard are sharing the configuration (see bellow). I don't use the modem so I was thinking uninstall it but I don't know how. Any idea what's going on? 

$ aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Thanks:(

---

### Post by chilidawg87 on 2007-05-18
try 
```
alsamixer
```
thats your volume and everything you need make sure nothing is muted. It sounds simple but i had the same problem somethings are muted by default. 

If that doesn't work i got some other ideas.

---

### Post by Bodizzle on 2007-05-19
I had the same problem and all it took was typing alsamixer from a terminal and adjusting all of the volumes to max.  Everything is working fine now.

---

### Post by Healing on 2007-05-19
I have the same problem, with the same computer.  When I go into alsamixer all I see are Off-Hook and Caller ID.  I've tried enabling both but to no avail...please help!  Thanks in advance.

---

