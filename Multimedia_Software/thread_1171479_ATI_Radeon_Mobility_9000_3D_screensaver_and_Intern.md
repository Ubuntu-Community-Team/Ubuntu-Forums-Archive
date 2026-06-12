---
title: "ATI Radeon Mobility 9000 3D screensaver and Internet Video problems"
date: 2009-05-27
forum: Multimedia Software
---

### Post by General-Gouda on 2009-05-27
Greetings!

First off, my system specs are listed in my signature.

I currently have WinXP on my laptop but I want to completely ditch it for Ubuntu.  Currently I have half of the hard drive dedicated to WinXP and the other half Ubuntu 9.04.

I haven't completely removed my WinXP partition due to some video problems I'm having within Ubuntu.  Namely, each time I want to run an internet video or let a complex 3D screensaver, such as Helios, run on my computer the processor shoots up to 100% usage.  The screensaver doesn't bug me so much as the internet videos do.  Whenever a video is played the Xorg.conf and Firefox processes rocket the processor usage up to 100%.  The videos then begins to studder and it cannot be watched easily (unless you like watching 3 fps videos).  It is almost as if the processor is attempting to calculate the video processing instead of letting the video card do it.  

I have checked the Hardware Drivers and no proprietary drivers show up for my video card.  However, I AM able to run some of the more advanced Appearance settings.  They do run a bit sluggish though.  

I know that I can run videos properly on the machine because they work fine within WinXP (apples and oranges I know but at least it demonstrates that it works) but I'm so sick of Windows XP I could puke.  I've done searches for fixes and all I've managed to do was ruin an installation of Ubuntu trying to install drivers that aren't completely compatible with my video card.

Aside from the video issue Ubuntu has breathed new life into my aging laptop and I'd really like to use it exclusively.  If anyone has any suggestions I'd be very appreciative.  

Thank you!

---

### Post by General-Gouda on 2009-05-27
Is my ATI Radeon Mobility 9000 just not supported any longer?

---

### Post by Game_Ender on 2009-06-04
9.04 does not support Mobility 9000 very well at all.  I have been able to get some decent performance by adding updated the Device section of my /etc/X11/xorg.conf:
```

Section "Device"
    Identifier	"Configured Video Device"
    Driver "ati"
    Option "AccelDFS" "on"
    Option "AccelMethod" "XAA"
    Option "MigrationHeuristic" "smart" # "greedy" works well also
    Option "EnablePageFlip" "on"
    Option "EnableDepthMoves" "on"
    Option "ColorTiling" "on"
    Option "FBTexPercent" "0"
    Option "RenderAccel" "on"
EndSection

```
So things like Google Earth and OpenGL based video with VLC work, but suck up a ton of CPU.  My custom OpenGL based 3D applications don't work though.

Essentially there have been major performance regressions for the older radeon cards between 8.10 and 9.04.  Someone on the Xorg team really dropped the ball.

---

