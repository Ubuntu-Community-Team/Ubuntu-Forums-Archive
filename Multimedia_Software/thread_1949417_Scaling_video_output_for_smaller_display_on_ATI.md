---
title: "Scaling video output for smaller display on ATI?"
date: 2012-03-30
forum: Multimedia Software
---

### Post by zzarko on 2012-03-30
The machine I was using for a long time was connected to 1280x1024 monitor and 1024x768 projector (ATI card). Projector could handle 1280x1024 resolution, and clone mode worked OK. Recently I acquired a larger monitor (1920x1200), but now I'm unable to properly scale that image. The best I got was displaying upper left part of the screen on projector. I know I could temporarily change resolution to something the projector could handle, but I'm searching for a better solution.

I found about xrandr parameter scale, and tried it like this:```
xrandr --output DFP9 --scale 2x2
```but all I got was```
xrandr: screen cannot be larger than 2944x1920 (desired size 3968x1536)
```and similar with scale values bigger than 1. If I put scale values <1, I get enlarged screen, as expected. I also tried several variants from examples at [http://www.x.org/archive/X11R7.5/doc/man/man1/xrandr.1.html](http://www.x.org/archive/X11R7.5/doc/man/man1/xrandr.1.html), but none of them worked. I also searched the forums (here and other places), but I didn't found anythng that helped. Does someone maybe have similar setup and has found solution to screen scaling?

---

