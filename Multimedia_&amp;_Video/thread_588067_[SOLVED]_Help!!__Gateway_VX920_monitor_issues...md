---
title: "[SOLVED] Help!!  Gateway VX920 monitor issues.."
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by trooperchix on 2007-10-23
I am running an old Gateway vx920 on my server (new to linux, I'm trying guys..) and for some reason I do not get the full options regarding resolution.  I have Cirrus video chipset..  If you need more info, let me know how to get it and I'll post it.  I am running an Intel Server Board L440GX+ (w/ dual slot 1 850 MHz processors) and using a Gateway VX 920 monitor.  I have it set on 24 meg color, and I suspect I have to go down to 16meg color to get more desktop size options, but I'm not sure.  Total newbie to Linux...  
:lolflag:

---

### Post by trooperchix on 2007-10-24
Ok, figured it out.  If you are running the Intel Server Board L440GX+, you need to pick 16 bit color and not 24 (32).  The onboard integrated video (Cirrus GD 5480) will run only as VGA and not SVGA therefore you have to pick 16 bit color.  Then you will see more screen resolution options.  I am running Gutsy...

---

