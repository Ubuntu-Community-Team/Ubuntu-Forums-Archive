---
title: "Video skipping in hardy and intrepid"
date: 2008-11-29
forum: Multimedia Software
---

### Post by c-shadow on 2008-11-29
Somewhere after upgrading to hardy video started skipping, periodically once every 30-60 seconds it just stops for 1/2 second. 
I did a clean install of intrepid (kept the /home partition) but it's even worse now. Video skips in vlc, mplayer and totem (gstreamer). I'm using two separate screens (CRT primary, LCD TV secondary) on nvidia 7600GS, AMD X2 3600+. I'm not using compiz, xorg.conf is generated with nvidia setings without xinerama (attched below).Both  top and htop show that in that moment xorg CPU usage gets very high (top shows xorg, and htop /usr/X11R6/bin/X). It happens on both screens, i usually use the TV for movies and while the movie is running, even minimizing/maximizing some window on the CRT monitor gets the video to skip. renice-ing the mplayer proces (to -15) doesn't help. I tried changing the nvidia video driver from the default 177 to 173, and the video driver from xv to X11, but no luck. In totem the skips are a bit shorter, but mplayer is really bugging me. In fact, everything in gnome seems a bit slower, moving windows,... 
This CPU spiking in xorg got me worried.
Help, I'm clueless here :confused:

---

### Post by randlieb on 2008-12-01
Try installing Totem-xine.

---

