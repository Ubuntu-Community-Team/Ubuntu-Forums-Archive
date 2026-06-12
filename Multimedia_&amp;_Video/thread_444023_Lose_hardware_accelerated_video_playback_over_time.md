---
title: "Lose hardware accelerated video playback over time."
date: 2007-05-15
forum: Multimedia &amp; Video
---

### Post by benmcmillan on 2007-05-15
After running X for a few days, or sometimes even hours, I lose hardware accelerated video.  It works (videos run smoothly at ~5-10% CPU) on a fresh X (reboot X or whatever). Then, after a while (non-deterministically it seems), mplayer struggles to keep up, pinning my CPU at 100% (on my P4 1.8 ).  Oh, and this happens when mplayer is fullscreened - at a 640x480 (or a typical video size) CPU usage goes to about 50%. I'm using the xv video output driver in mplayer. 

Glxinfo still says direct rendering is functional, and glxgears gives 3000 FPS (with 100% cpu). 

I'm just wondering if anyone has had the same issue -- am I alone? If I am, so be it - I'll replace my video card or something. But if this is a common problem, or at least has an easy solution, help would be greatly appreciation.

Feisty (xorg 7.2), nVidia Corporation NV34 [GeForce FX 5200 Ultra], x86-1.0-9755 driver.

---

### Post by Sokertes on 2008-02-14
I am having a similar issue with my GeForce FX 5200

After a fresh boot all works fine and glx works with no problems. After watching a movie or the screen suspends my glxgears slow way down to about 1.?? fps and games (ET, UT, etc.) punk out with no errors.

mplayer continues to play fine and tvtime continues to run fine. If I want to play ET I have to restart X and it will play just fine. Then if I watch a movie or the screen suspends then it is the same routine.

I recompiled my kernel with 2.6.24 and installed  NVIDIA-Linux-x86-169.09-pkg1.run and to no avail the same thing happens.

It is a major pisser having to restart X to run anything with glx. That is one of the many reason why I got away from windows.

Sokertes

---

### Post by Mblackwell on 2008-02-14
It's a Nvidia driver bug. There's a beta driver that fixes the issue but causes applications that use multiple GLSL threads (like Wine) to have problems sometimes. I'm not sure if the latest of the latest beta drivers fixes both issues or not.

I've noticed this problem is lessened somewhat by using Firefox 3.0 (beta 3 is in backports), which eats less ram and cpu time and keeps X from freaking out as often.

Also, if you don't use/turn off Compiz you should still be able to play the video.

---

### Post by Sokertes on 2008-03-03
I don't understand why it is an nvidia bug when it works just fine and do not have the problem in Gentoo.

I ended up finding a cpu for my workstation that has gentoo on it and am using it now due to this so called nvidia bug. I have had my machine up for over a week and have not had this issue yet with gentoo.

---

