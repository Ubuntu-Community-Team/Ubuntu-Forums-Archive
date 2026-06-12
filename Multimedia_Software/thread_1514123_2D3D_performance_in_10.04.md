---
title: "2D/3D performance in 10.04"
date: 2010-06-20
forum: Multimedia Software
---

### Post by Andy1982 on 2010-06-20
Hi all

I recently upgraded my computer (by doing a complete fresh install) from 8.04 to 10.04.

While the general GNOME environment feels much snappier than on 8.04 (even with Compiz enabled), the performance of 2D and 3D games and apps seems to have regressed massively.

As examples, the following were completely usable when I ran them on 8.04, but can hardly be played at all on 10.04:
Battle for Wesnoth (really slow and jerky even to select units)
Neverputt (now way too dark to see what's going on)
Pingus (slow and jerky)
SuperTux 2 (again, just very slow)

Video playback is fine, and Compiz is ok. Normal usage (web browsing, OpenOffice, Rhythmbox) is great. It's just games it seems.
Also 3D stuff (e.g. GTA) is fine on WinXP on the same machine.

I haven't changed the hardware at all, so I wondered if this is something to do with video driver changes, and if anyone has any suggestions for how to fix/work round it? Has anyone else experienced something similar?

My setup (admittedly ageing) is as follows:
AMD Athlon XP 2600+ 1.9Ghz
1GB RAM
Radeon 9200SE graphics
Creative Audigy 2 sound
Soyo Dragon Ultra KT600 motherboard
1x 80GB & 1x 250GB IDE HDD
DVD-RW drive

Many thanks for any suggestions.

---

### Post by Mark Phelps on 2010-06-20
There are no 3D hardware accelerated drivers that will work with your card and Ubuntu 10.04.  So, you will never be able to get the performace that used to be available with 8.10 and prior.

However, if you want to do some research on tweaking that you might be able to do, go over to the Phoroniz forums.  They do a LOT of work with the open source drivers.

---

### Post by Andy1982 on 2010-06-20
Hi Mark

Thanks for your reply. I was using the open-source drivers on 8.04 as well - AMD haven't provided drivers for my card for quite a while now.

So I guess it could be some kind of problem in that driver. I'll have a look at those forums as you suggest, but if other Ubuntu users on here have any further suggestions too that would be very welcome.

P.S. If it helps anyone with some kind of diagnosis, the output of glxinfo | grep render is as follows:
direct rendering: Yes
OpenGL renderer string: Mesa DRI R200 (RV280 5961) 20090101 x86/MMX+/3DNow!+/SSE TCL DRI2

And when I run glxgears it's averaging about 5000 frames per 5 seconds.

Cheers
Andy

---

