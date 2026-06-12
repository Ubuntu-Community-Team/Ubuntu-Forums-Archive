---
title: "Keyboard Volume and Mute not working after updates"
date: 2009-08-25
forum: Multimedia Software
---

### Post by Arcturus691 on 2009-08-25
On my system when I press the volume up/down key, the on screen volume display appears and moves in the corresponding direction. If I press the mute key, the on screen display reflects this, but the sound level does not change and the mute does not mute. If you left click on the volume control in the top panel, the volume has not moved (IE: not in sync w/ the on screen display) and is not muted even though the OSD shows as muted. This problem started for me after updates in July. I also had bad sound distortion when moving my mouse but that was fixed with the latest image update: linux-generic (2.6.28.14.19) to 2.6.28.15.20.

Ubuntu 9.04 64Bit AMD64
2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux
NVIDIA NFORCE SLI CK804 ALC850
Desktop system

---

### Post by Arcturus691 on 2009-08-25
I have attached the log of all my updates for past two months.

---

### Post by Arcturus691 on 2009-08-26
bump 
Anyone else having this issue?

---

### Post by tgeer43 on 2009-08-26
Didn't see your post here. I posted the exact same media softkeys problem in the Hardware & Laptops forum here:

[http://ubuntuforums.org/showthread.php?t=1250489](http://ubuntuforums.org/showthread.php?t=1250489)

I'm keeping an eye on your thread for a resolution. You might want to do the same.

Good luck,

tgeer

---

### Post by tgeer43 on 2009-08-26
I found the cure - in my case at least, but I think it will fix you up too.

See the link in my previous post.

tgeer

---

### Post by Arcturus691 on 2009-08-28
Hey thanks, going into sound preferences and changing everything back to  alsa worked.  I am concerned that this will be an issue down the road though, because from what I understand, ubuntu is migrating towards pulse audio.  Maybe I should submit a bug on pulse audio not supporting multimedia keys.

---

