---
title: "ATI X700 Compiz + Tv out"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by peakshysteria on 2008-01-23
After a lot of problems i now have a clean Gutsy install. Strangely with a splash screen with the wrong resolution. But once i'm logged in i get my 1280 x 1024 resolution which is the correct one for me. Compiz is also working very smooth. But i'm missing tv out. Which is the one and only thing that keeps me from making the complete switch to Ubuntu from XP.

Once again i tried to enable the ATI accelerated graphics driver via the restricted drivers option. I'm kinda new to Ubuntu so i'm mostly comfortable with graphical tools. After restarting the system the driver was enabled. But the resolution was all wrong.

Setting the resolution in the screens and graphics option and rebooting once again gave me the wrong resolution. Doing it one more time gave me the right resolution on my desktop (not my log in screen).

Runned the fglrxinfo command in terminal told me that the ATI driver still wasn't running. It said Vendor: MESA. The ATI accelerated graphics driver still was enabled. Going to the graphics and screens menu told me that the driver was VESA. Tried to choose different drivers in the menu. Like fglrx, ATI radeon etc. But came up with the same result.

So tv out wasn't possible. No ATI CCC. And compiz wasn't possible to enable. Reverted back to the default driver. Est voila; compiz is working once again. And my desktop has the right resolution (still not the login screen). But not tv out. Once again i give up.

I've been around the block more than once, looking at all the howto's. As far as i can see the system isn't starting with the driver even though it's apparently enabled. Can anyone explain this in a simple way for me? Saving me from the MESA hell.

Let's say i enable the ATI accelerated graphics driver once again. This demands a restart. So, from there on, what how can i proceed to get a working Compiz, Tv-out and Ati CCC??

---

