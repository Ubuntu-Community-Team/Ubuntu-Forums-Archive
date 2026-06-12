---
title: "glxgears, games - problem with 3D graphic??"
date: 2007-08-26
forum: Multimedia &amp; Video
---

### Post by hagar_am on 2007-08-26
Everything started here:
[http://ubuntuforums.org/showthread.php?t=534376&highlight=tce]("http://ubuntuforums.org/showthread.php?t=534376&highlight=tce")
Now I know that Regnum Online crashes too with SIGSEGV (signal 11).
Glxgears after several minutes takes me back to login screen, or even hungs my X, after reset I saw a lot of numbers and somthing like kernel panic: attempting to kill init and my PC turned off..Luckyly after turning it on I was able to login without problems, but glxgears still hangs and turn off my PC or taking me back to login screen and games still crush with signal 11 -SIGSEGV. What I should do to solve that problem and get games working fine like they used to?

---

### Post by kissg1988 on 2007-08-26
I have problems with 3D games, too... What kind of video adapter do you have? Cards using VIA and SIS chips have a lot of problems with 3D applications. This is because the DRI drivers for these chips are very buggy.

---

### Post by hagar_am on 2007-08-26
Nvidia GeForce 7300GT. And that games used to run. Only thing I did was updating my ubuntu.
Doom3 demo for linux crushes with:signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
--------- Game Map Shutdown ----------
--------------------------------------
Shutting down sound hardware
------ OSS Sound Shutdown ------
close sound device
--------------------------------
idRenderSystem::Shutdown()
------------ Game Shutdown -----------
--------- Game Map Shutdown ----------
--------------------------------------
Shutdown event system
--------------------------------------
shutdown terminal support

---

