---
title: "Sound cuts out"
date: 2010-08-19
forum: Multimedia Software
---

### Post by janothar on 2010-08-19
I've recently upgraded to 10.04, and never had any problems in 9.10, but now, sometimes when Banshee attempts to play a sound file, it will kill my sound output until I reboot.  Haven't been able to get anywhere by fiddling with ALSAmixer or the like, and everything is just fine on reboot, but the files don't always cause problems, and they were all fine back in 9.10.  Has anyone else encountered this? I've been unable to find any other references to this problem.

---

### Post by Yfrwlf on 2010-09-10
> **janothar said:**
> I've recently upgraded to 10.04, and never had any problems in 9.10, but now, sometimes when Banshee attempts to play a sound file, it will kill my sound output until I reboot.  Haven't been able to get anywhere by fiddling with ALSAmixer or the like, and everything is just fine on reboot, but the files don't always cause problems, and they were all fine back in 9.10.  Has anyone else encountered this? I've been unable to find any other references to this problem.

Is it only Banshee, or is it all programs?  What about Ubuntu desktop sound effects?  What about Totem, Mplayer, VLC, Amarok, Rythembox, etc?

---

### Post by Yellow Pasque on 2010-09-10
Instead of restarting the entire system, try restarting pulseaudio, A simple:
```
pulseaudio --kill
```
should do it since pulse will auto-respawn.

Also, you might want to start banshee from the terminal to see if it throws any interesting errors there.

---

