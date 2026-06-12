---
title: "FGLRX Refresh Rate Issues"
date: 2008-11-02
forum: Multimedia Software
---

### Post by Pyroja on 2008-11-02
Hi everybody. I've had this problem ever since installing Ubuntu on this system, but I figured I may as well ask around and hope I find an answer.

I have an AGP ATi 9600 in this system. The generic video driver that is chosen by default doesn't allow for hardware acceleration, but does allow me to choose my preferred resolution and refresh rate for this old CRT monitor, specifically: 1152x864x24 @ 75hz. It's the highest this poor old thing can do before reverting to 60hz, which makes me want to clasw my eyes out.

My problem is, since switching to FGLRX, I can't choose anything other than 60hz at this resolution. I've resorted to, temporarily, stepping down to 1024x768, which works fine at 75hz, but is obviously not what I want.

I've tried editing xorg.conf, but it seems like the driver ignores that almost entirely, as it hasn't made the slightest bit of difference.

All I want is to be able to use 1152x864x24 @ 75hz with hardware acceleration. Do I have any option here, or is the driver borked?

Thanks for the help!

---

