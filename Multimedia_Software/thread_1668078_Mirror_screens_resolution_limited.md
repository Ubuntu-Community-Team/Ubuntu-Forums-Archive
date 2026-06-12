---
title: "Mirror screens resolution limited"
date: 2011-01-15
forum: Multimedia Software
---

### Post by R.I.C. on 2011-01-15
I'm running Ubuntu 10.04 on a Dell Inspiron 6400 (1680x1050 screen resolution) with Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller.  I plug it into a Sony HDTV (screen resolution 1920x1080)to watch movies.

When I first plugged it in, it would use the full 1920x1080 resolution on the TV in mirror screens mode.  It did this for weeks.  Then, one day, I plugged the TV in after the laptop was already running, and forever after, it will only give me a maximum of 1280x960 resolution.

If I don't use the mirror screens option (making it possible to obtain full resolution on the TV), for some reason, video will not play at all (in VLC, Gnome, or Movie Player - full screen or not).

Any ideas?  I'd be happy to either:

a) be able to use the full 1920x1080 resolution in mirror screens mode

or

b) be able to play video when screens aren't mirrored

Thanks in advance.

---

### Post by BicyclerBoy on 2011-01-15
Perhaps when it was working full screen it was panning using twinview.

That works by having a meta-screen that is a rectangle box sized around both screens.
The panning occurs when the cursor is moved into virtual screen space.

You need to force the application to use the correct 'screen' or meta-screen position.

A simple way to make apps launch on a certain screen is by use separate X screens (configure button nvidia-settings).
You need the display attached when X server starts due to limitation of Xorg.
Set the resolution & save to xorg.conf.
Separate X screens is much easier to use. BUT with one catch...since 9.10 it has only been possible to put icons on the primary screen. 

Dynamic twinview could allow a metamode that could a mean hot plugging the display would work..but more difficult to config.

---

### Post by R.I.C. on 2011-01-15
I actually solved it by simply turning off the laptop monitor... for some reason, it works now.  I don't understand, but that's not the point :)

---

