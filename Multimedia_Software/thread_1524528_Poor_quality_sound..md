---
title: "Poor quality sound."
date: 2010-07-05
forum: Multimedia Software
---

### Post by alchemy21 on 2010-07-05
Hi guys, just installed Ubuntu 10.04, but the sound output is pretty poor. The sound is about half the volume it usually is on previous OS installs, is very tinny, and sounds similar to audio that has undergone high compression (like <32kbit/s mp3), there's also a noticeable buzz at anything but the quietest volumes.

I'm using on-board sound on GA-P35-DS3L/S3L S-Series Ultra Durable 2, with Logitech 2.1 speakers.

Had a quick glance through the stickys but couldn't find anything relevant. 

Anyone shoot me some tips?

---

### Post by alchemy21 on 2010-07-06
Nobody has any ideas?

Also noticed there's no subwoofer output. The buzz doesn't go when the sound is muted in Ubuntu. Had a play with alsamixer, it's detecting my card as "hda intel", tried lowering PCM as per suggested in another thread but PCM won't change it just forces a change on the master and PCM stays maxed.

I'd really appreciate any help at all guys, I'm finding my desktop almost unusable with the lack of quality sound and I really don't want to move back to Vista.

---

### Post by Yarui on 2010-07-06
Have you fully updated your system since the install?  It could be a problem with the kernel that has since been corrected.  It could also be the opposite if you already have upgraded.  Your system may be having issues with the newest kernel that it wouldn't have with older kernels.  Have you tried booting into an older kernel to see if it will work better?  I had similar issues with one of the kernels.  My sound had an odd metalic buzzing noise.  It seemed to correct itself, but it resurfaces from time to time.

---

### Post by lidex on 2010-07-06
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by alchemy21 on 2010-07-08
Many thanks for the help guys!

Turned out to be a quite complex hardware issue: the 3.5mm jack had come loose.

---

### Post by lidex on 2010-07-08
Great, I wasn't looking forward to debugging that anyway ;)

---

