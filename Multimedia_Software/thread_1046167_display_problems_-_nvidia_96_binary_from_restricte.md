---
title: "display problems - nvidia 96 binary from restricted drivers manager"
date: 2009-01-21
forum: Multimedia Software
---

### Post by b4b4_j4g4 on 2009-01-21
I installed today the binary nvidia driver 96 via the restricted drivers manager.
System:Intrepid Ibex
Graphics: GeForce MX 440

Problem is my Samsung SyncMaster 941MW flatscreen LCD TV is complaining about the resolution.

GDM is displayed properly, but the X-Session not. Not even the Gnome-failsafe, so now I'm working in the Failsafe Terminal.

I manually edited the xorg.conf to contain my native resolution 1440x900.
didn't help
I launched the nvidia-settings via the Failsafe Terminal and it detects everything perfectly(monitor as well as the resolution)...

Seems like some script is overriding the correct nvidia/xorg.conf settings when the X-session is started.

Any ideas?

---

### Post by b4b4_j4g4 on 2009-01-21
So, xrandr seems to confirm that in a Failsafe Terminal Session - my resolution is 1440x900 50 54
which explains why is it running.
Unfortunately in a regular Gnome session xrandr shows a res
960 x Something with a refresh rate of 30 (My LCD has 60 MHz)
event though 1440x900 is recognized by xrandr as my 'preferred' res.

I tried to change the res with xrandr with

xrandr --output default --mode 1440x900
as well as
xrandr --output default --auto

both leading to a IO ERROR 11 and terminating the X-Session.
(since I'm in a console, I have set $DISPLAY=:0.0)

Any idea why the gnome session would start in an unfitting res.?
and how to get rid of it?
Recently I read some post that it could be connected to xinerama..

Thanks

---

