---
title: "vsync Issues with ATI X1400 on Dell E1505"
date: 2007-05-16
forum: Multimedia &amp; Video
---

### Post by legzelda on 2007-05-16
Ever since I made the switch to Ubuntu Linux starting with Edgy Eft and now running Feisty Fawn, I've suffered with a rather annoying problem.  The refresh on my laptop's display does not sync well.  As such, I get tearing during video rendering, everything from movies (played in multiple programs, including Totem and VLC) to OpenGL 3D applications (running emulators, using a 3D desktop through Beryl or Compiz, etc.).  I am running an Xgl session with the latest ATI drivers (8.36.5).  I have tried the aticonfig --vs and --sync-video switches, but these either completely crash my xorg.conf file or offer no improvement.  I tried the same thing in a regular Gnome session and experienced the same problem.  I am running at 1680x1050 resolution, but I've noticed the same problem at lower resolutions.  I also sent the video to an external LCD monitor running at 1024x768 and experienced the same graphical tearing on that display.  This makes me think it's some setting with my video card, but I am unsure as to where to go from here.  Has anyone experienced this same problem, and does anyone have suggestions or solutions?

---

### Post by legzelda on 2007-05-27
I'm still suffering from this problem.  Does anyone know the horizontal and vertical sync ranges of the display?  Perhaps these values have something to do with the choppiness, tearing, and un-synced video.

---

### Post by legzelda on 2007-06-05
Even after successfully installing the newly released ATI drivers, I am still suffering from this problem.  Any advice?  Any one?

---

### Post by LongLife on 2007-09-19
did you try this?

[http://forums.gentoo.org/viewtopic-t-570888.html?sid=88d7748faf43e346ba953e5d9678f386]("http://forums.gentoo.org/viewtopic-t-570888.html?sid=88d7748faf43e346ba953e5d9678f386")
I had the same problem on my Dell Inspiron 6400 atix1400 mobility
It try it, and it seems to work for the moment....

Wait and see!

---

### Post by legzelda on 2007-09-20
Thanks for the tips.  It seems the latest version of the ATI driver has fixed the tearing problem.  As of today, I'm using 8.39.4.

---

### Post by legzelda on 2007-10-03
Well, I installed the latest ATI drivers and am back to the same tearing problems, but they seem worse than ever.

```
neal@dell-linux:/etc/ati$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6849 Release
```

Any ideas?

---

