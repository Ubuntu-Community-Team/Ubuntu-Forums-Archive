---
title: "Green screens in mythvideo with avi files"
date: 2008-04-07
forum: Mythbuntu
---

### Post by agent5150 on 2008-04-07
Mythbuntu 7.10 Mythtv 0.21

1. both mplayer and xine take good 10 secs to load a 600 mb avi.
2. 1st movie plays file, exit, select another avi... both mplayer and xine show green screen with dots (audio plays fine).. at this point I can't exit the player... have to ssh into the box and kill the process. 

I did run apt-get install mythvideo and it removed mythdvd and updated mythvideo to .21 (as the update utility missed that plugin)

This sounds like compiz issue but I don't have desktop effects enabled.  Where can I look to confirm.  Is there a flag/option in Xorg.conf?

Any one else getting green screens in mythvideo with avi files?

SOLVED:
proprietary codec "w64" was enabled in mythbuntu setup.   Also, disabled then re-enabled ffmpeg codec and now all is well.

---

