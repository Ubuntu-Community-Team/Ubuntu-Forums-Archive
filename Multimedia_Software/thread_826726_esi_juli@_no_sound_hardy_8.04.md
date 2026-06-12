---
title: "esi juli@ no sound hardy 8.04"
date: 2008-06-12
forum: Multimedia Software
---

### Post by 9to9 on 2008-06-12
hoii..hello there..uum i have a problem with my esi juli@ soundcard on ubuntu 8.04 hardy, which is there no sound came from it..i try every step from this thread..

from 1st step aplay -l, result is :

**** List of PLAYBACK Hardware Devices ****
card 0: Juli [ESI Juli@], device 0: ICE1724 [ICE1724]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Juli [ESI Juli@], device 1: IEC1724 IEC958 [IEC1724 IEC958]
Subdevices: 1/1
Subdevice #0: subdevice #0

and from 2nd step lspci -v

i didnt find any esi juli@ related thingi..and i already uninstall n install alsa..n there is nothing came up, still no sound, or there is some setting from volume preferences??..please someone help me...

ps: iam using spidf/ optical out

---

### Post by Pjotr123 on 2008-06-12
Try this:
[http://ubuntutip.googlepages.com/sound](http://ubuntutip.googlepages.com/sound)

---

### Post by Yellow Pasque on 2008-06-17
OSS4 has a new build out (v1016) that supports this card: [http://ubuntuforums.org/showthread.php?t=780961](http://ubuntuforums.org/showthread.php?t=780961)

---

