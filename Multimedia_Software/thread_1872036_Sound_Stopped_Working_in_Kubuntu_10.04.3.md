---
title: "Sound Stopped Working in Kubuntu 10.04.3"
date: 2011-10-29
forum: Multimedia Software
---

### Post by Jack Of Clubs on 2011-10-29
I've been happily running Kubuntu 10.04 on my Dell Mini Inspiron 910 for some time now.  This afternoon I started the computer and discovered there was no sound at all.  After browsing the comprehensive sound solutions guide and trying what I could, I'm no closer to a fix.

Output of aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Output of uname -a:

Linux quickman 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:40:53 UTC 2011 i686 GNU/Linux

AlsaMixer shows everything is currently unmuted and at full volume.

I'm at a loss.  Anyone else encountered this problem or have a fix?

---

### Post by Jack Of Clubs on 2011-11-14
Additional Info:

I tried booting from the Kubuntu Desktop CD and the sound worked no problem, so I'm pretty sure it's not the hardware.  Perhaps something in a recent update broke it?

---

### Post by Jack Of Clubs on 2011-11-23
Hey all, there was a solution posted in another thread.  If you're having the same issue, look here:

[http://ubuntuforums.org/showthread.php?t=1853206](http://ubuntuforums.org/showthread.php?t=1853206)

---

