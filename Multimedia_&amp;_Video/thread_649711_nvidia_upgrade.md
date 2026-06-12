---
title: "nvidia upgrade"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by Damanther on 2007-12-25
I just did an upgrade from an old nvidia card, to a "newer" nvidia 6200. The computer seems to work fine, the only thing I seemt to be missing is the "TwinView" Option that should be available ont he 6200 for TV-Out. Do I need to reconfigure nvidia-settings or the driver in some way to make that option available?

I used envy to rebuild the driver just in case there was an update for it, but still no twinview option under nvidia-settings. I really don't want to tweak the xorg.conf manually if I don't have too.
__________________

---

### Post by logos34 on 2007-12-25
nvidia-settings should configure it for you.  That's what I use.  Here's the section from my xorg.conf as an example:
> 
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1024x768_85 +0+0; 1280x1024 +0+0; 1024x768 +0+0; 832x624 +0+0; 800x600 +0+0; 720x400 +0+0; 640x480 +0+0"
EndSection

I'm using a geforce 6100.  single monitor.

However, there's this thread which has you add the twinview options under 'Device' section:
[http://ubuntuforums.org/showthread.php?p=1773584](http://ubuntuforums.org/showthread.php?p=1773584)

---

