---
title: "Difficulty Intel integrated graphics"
date: 2008-01-31
forum: Multimedia &amp; Video
---

### Post by bwaskiew on 2008-01-31
Hello,

First I will say that my graphics card is an Intel GMA X3500. Relatively new I think, but not *too* new.

First, let me describe what I would like:

I have a Samsung 226BW and an older Dell, the former can have 1680x1050 res, the latter 1280x1024. I would like to have them both sitting normal (no rotation), with the Dell set up right-of the Samsung, with the Samsung being the primary monitor. The Samsung is plugged in to a HDMI port through an HDMI-DVI converter, while the Dell is plugged into the secondary VGA port.

Now to my difficulty...

I have changed the virtual screen in xorg.conf to handle the width of both screens put together, and using xrandr to set up the screens in a double desktop configuration, however it won't let me use the Samsung as the primary. After some googling, it appears that for some reason, if you have anything plugged into the VGA port on an intel card, it is set as the primary no matter what. Is this true? How can they allow a dual monitor setup, but not let you choose the primary screen :(

But, it works... until I enable Compiz Fusion. When compiz fusion is enabled, then it enforces a limit of 2048x2048 for any 3d effects. I have also seen that around the web, but in almost all cases it appears the 2048x2048 limit was a hardware constraint, and only for older intel chipsets. The GMA X3500 is pretty new, so I would think you can have a larger area.

The only lead I have about my setup, is that it appears that Ubuntu thinks the chipset is an 865, when it should be X3500, and the driver it is using is called 'intel - experimental modesetting ...'. Could that cause any issues?  Other than that, I'm in the dark. I have some small knowledge of linux and ubuntu, but not enough to troubleshoot this.

Thanks for any help,
Brandon

---

### Post by grmmog on 2008-02-01
Just looking through the Xorg website and it doesn't look like that chipset is supported yet.  The new Intel Graphics Driver is scheduled for release in February.  Hopefully it'll get included in that.

---

### Post by bwaskiew on 2008-02-01
You know, it has seemed like that is the case since the very beginning. Can you give me a link of where that posting is? I've found similar postings that say the G35 chipset is supported, and am in the midst of trying out the xorg intel driver (i810) as opposed to the intel - experimental for modesetting one that was configured by default.

EDIT:

Tried the xorg intel driver, and it didn't even detect 2 monitors, let alone be able to do DRI on a screen larger than 2048x2048. Hopefully the new driver in February will fix all the issues :)

---

### Post by iramhernandez on 2008-02-01
It got the same integrated chipset.  I would consider it somewhat new  -- I had been waiting for the g35 to become available and some delays it was released about a month ago.

The good news is that intel released full documentation  to the community.  The documentation is available at: [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)

The bad news is that even if a new driver is released soonish, it will be some time before it is neatly packaged for ubuntu.  But then again, I could be wrong..

I'm currently experimenting with hacking at the xorg.conf manually.  I'll post any interesting finding here.

---

### Post by iramhernandez on 2008-02-01
See this thread: [http://ubuntuforums.org/showthread.php?t=647449&highlight=g35](http://ubuntuforums.org/showthread.php?t=647449&highlight=g35)

---

### Post by bwaskiew on 2008-02-01
Hehe, I'm all over the last two pages of that thread already :o

---

