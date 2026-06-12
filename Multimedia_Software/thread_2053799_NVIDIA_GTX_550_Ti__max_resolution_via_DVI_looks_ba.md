---
title: "NVIDIA GTX 550 Ti : max resolution via DVI looks bad"
date: 2012-09-06
forum: Multimedia Software
---

### Post by Rob F on 2012-09-06
Hi all,

I have a Dell U3011 ultrasharp 30" monitor, which is very nice, and was previously being driven by my Dell precision M4600 laptop at its max resolution of 2560 x 1600 (via docking station and HDMI). It worked very well.

The laptop has now moved onto new pastures and has been replaced by a fairly high spec Viglen genie desktop PC sporting a NVIDIA GTX 550 Ti graphics card. Through VGA the card can't drive the U3011 max resolution so I switched to DVI. The output basically looks horrible. I can switch to the max resolution, 2560 x 1600, but its unusable, with very poor rendering of fonts. Even now, with it set on 1920 x 1200 so that its usable, it looks out of focus and generally not very nice. Makes the screen on my laptop look "ultrasharp", not the monitor.

I've tried googling and search the forums, can't find anything. Have tried downloading latest drives, checked cables, connectors and inputs, no progress. Doesn't really make sense, since I'm pretty sure the GTX 550 Ti (which is a LARGE card) is more powerful than the one in the Dell precision laptop).

This is a work machine, and the only thing we have left to try is to see if we can try and go out via the displayport rather than DVI.

Anyway, any help appreciated.

thanks,

RF

---

### Post by BicyclerBoy on 2012-09-06
Are you using the nVidia proprietary driver ?
version 275 (or maybe earlier) supports glx550Ti.
You have to use nvidia-settings or xrandr to change resolution etc.

You are connected using dual link DVI port & cable ?
Not using an HDMI adapter (single link) ?

---

### Post by Rob F on 2012-09-06
Hi, 

thanks for the quick reply.

> **BicyclerBoy said:**
> Are you using the nVidia proprietary driver ?
version 275 (or maybe earlier) supports glx550Ti.
You have to use nvidia-settings or xrandr to change resolution etc.

You are connected using dual link DVI port & cable ?
Not using an HDMI adapter (single link) ?

Yes, am using nvidia proprietary driver 295.40. I'm familiar with nvidia-settings - that's how I change the resolution. Doesn't fix the problem that it looks crappy. Am using DVI to DVI cable from the graphics card port to the monitor.

cheers,
Rob

---

### Post by BicyclerBoy on 2012-09-07
Have a look in the /var/log/Xorg.0.log file for clues/hints related to modes/modelines etc..

There is a keyword that can be used in /etc/X11/xorg.conf or cmd-line with nVidia driver to make it output more verbose modeline debugging:

nvidia-xconfig --mode-debug

or add to /etc/X11/xorg.conf:
 Option "ModeDebug" "True"

---

### Post by pqwoerituytrueiwoq on 2012-09-07
my 24" display looks flawless with my 550 ti, i have been using it since i got it last black friday, always used the latest driver in the xswap ppa
i am using the hdmi port
most 550 tis have 2 DVI and one HDMI, give the other DVI a try
one supports a dvi to vga adapter one does not

---

