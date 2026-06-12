---
title: "Out of ideas... ATI TV out"
date: 2006-10-27
forum: Multimedia &amp; Video
---

### Post by crc58 on 2006-10-27
Hello all,

Video card: ATI Radeon 9600 Pro with s-video out.

My goal for today was to get a living room PC built using Edgy but TV out is not working right for me. During setup everything went fine; had an lcd monitor and a tv connected. I followed the guide at [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) for installing the 8.28.8 drivers. The problems started happening when I removed the monitor and left only the TV connected. Here is a brief outline of what I have observed:

1) One monitor with or without the tv connected works perfect.
2) The tv connected by itself causes the system to take forever to boot up (trying to find the monitor maybe?). Also, attempting to run Xine or mplayer results in 'Floating point exception(core dumped)'. VLC, however, works.

I tried disabling the monitor by using 'aticonfig --enable-monitor=tv,none' but that had no effect on bootup time or the crashes. I also tried using --overlay-on (0 and 1) to no effect. If I connect both the monitor and the tv, but disable the monitor with '--enable-monitor=tv,none' xine begins crashing again. Reenable the lcd and the problem is gone...

What am I doing wrong?

---

### Post by Enclavet on 2006-10-28
Same exact problems. With Monitor everything works fine. Boot up with monitor and remove it after getting into ubuntu, everything works fine (mythfrontend, xine etc). If the X server is restarted it becomes messed up though.

If I boot up without monitor I get FPE on both mythfrontend and xine. FGLRX drivers are all working fine with glxgears, fgl_glxgears, glxinfo (direct rendering), fglrxinfo gives me the correct output. 

If I cant figure it out i'm gonna switch to KnoppMyth because I have a feeling its because of edgy.

---

