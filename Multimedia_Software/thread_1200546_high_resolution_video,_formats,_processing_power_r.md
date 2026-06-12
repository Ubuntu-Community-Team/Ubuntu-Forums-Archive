---
title: "high resolution video, formats, processing power required"
date: 2009-06-30
forum: Multimedia Software
---

### Post by Superkuh on 2009-06-30
I have a script that collects 1408*1624px images from the GOES weather sats. and regional radar composites then compiles daily movies. It stresses my system to watch the large resolution movies with mpg format. (I have been using imagemagic's convert called by a perl script)

For an 8.04 AMD64 system with nvidia hardware acceleration (Geforce 7600GS AGP) in gnome in xinerama mode are there any hardware accelerated compressed video formats that would minimize processor load? If so, what specific encoding programs and options would you use?```
   xorg.conf: ...Identifier     "Videocard0"
    Driver         "nvidia"
```I specify hardware accelerated because I have found that using uncompressed video formats does not decrease the load of high resolution movies. It significantly increases it.

I'll use any player. I've tried vlc, mplayer, bmp+, and totem.

[EDIT] I eventually found that using mplayer, but setting it to drop frames was an acceptable solution.
mplayer -framedrop -vfm 
ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all videoetcetc.mpeg

---

### Post by fooman on 2009-06-30
not sure if this will help,  but have a read here:

[http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)

just one thing though..."**Before you proceed: VDPAU does not work with Xinerama, but does work with Twinview."**

---

