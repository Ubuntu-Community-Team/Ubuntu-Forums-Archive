---
title: "Issues with Hauppauge analog capture"
date: 2010-10-31
forum: Multimedia Software
---

### Post by Sagoober on 2010-10-31
Hello all,

I just bought an Hauppauge WinTV-HVR 950Q to use on my laptop, running Lucid, to play my Playstation 2 on.  I had read that Hauppauge devices work well on linux, and the wiki listed the 950q as fully supported, but could not get it to work at first.  Unfortunately, I discovered that the digital input works great for people, not the analog, which is all the psx2 offers.  After searching around quite a bit, I found this thread ([http://ubuntuforums.org/showthread.php?t=1340117](http://ubuntuforums.org/showthread.php?t=1340117)) which led me to this command

mplayer -tv driver=v4l2:input=2:device=/dev/video1:norm=NTSC:channel=3: tv://1

and now at least there is a viable signal coming into the computer, the only problem being that the image is black and white, and pretty poor quality.  It is at least possible to play GT4 now, but not very satisfying.  Any advice on how to fix this?

---

