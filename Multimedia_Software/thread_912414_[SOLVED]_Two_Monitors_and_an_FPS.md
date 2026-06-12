---
title: "[SOLVED] Two Monitors and an FPS"
date: 2008-09-06
forum: Multimedia Software
---

### Post by hocmin on 2008-09-06
I play this really old FPS with friends from time to time called Urban Terror ([www.urbanterror.net](www.urbanterror.net)).  It's a Quake 3 mod.  I just got a second monitor for my system and added it pretty easily adding the TwinView option to xorg (I use nvidia).  When I play the game, it tries to span across both monitors, using the old resolution, so one half was on on monitor and the other half was on the other.  The only solutions I seem to run it on one monitor is through windowed mode.  Do I have any other options?

---

### Post by ~LoKe on 2008-09-06
I believe that's a problem with TwinView; try xinerama.

---

### Post by ad_267 on 2008-09-06
I play UrbanTerror with TwinView on nVidia. TwinView lets you use Compiz too, which you can't with Xinerama.

You need to change the metamodes so that you have a mode with the first monitor set to the resolution you play in and the second one off. I think there's a way to do this by running "gksu nvidia-settings" and adding metamodes but that never seemed to work for me. I have one 19 inch monitor at 1280x1024 and a 15 inch at 1024x7689. I modified my xorg.conf (/etc/X11/xorg.conf) so the metamodes line looks like:

```

Option         "metamodes" "CRT-0: 1280x1024_60 +0+0, CRT-1: 1024x768_60 +1280+256; CRT-0: 1280x1024_60 +0+0, CRT-1: NULL; CRT-0: 1024x768_60 +0+0, CRT-1: NULL; CRT-0: 800x600_60 +0+0, CRT-1: NULL"

```

So pretty much just copy the mode that's already there and change the second monitor to say "NULL"

---

### Post by hocmin on 2008-09-08
I tweaked the line to:
```
Option		"metamodes" "CRT-0: 1680x1050_60, CRT-1: 1680x1050_60; CRT-0: 1680x1050_60, CRT-1: NULL;"
```

And it works great.  I wasn't sure what the +0+0 lines were but it seems like the default setting for that works fine.  Thanks.

---

### Post by ad_267 on 2008-09-08
Awesome. I think the +0+0 part just gives the position of the monitor.

---

