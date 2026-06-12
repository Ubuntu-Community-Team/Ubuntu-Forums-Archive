---
title: "Screen periodically blinking off"
date: 2010-11-04
forum: Multimedia Software
---

### Post by bill@kilgallonfamily.com on 2010-11-04
I fought with this a few days, and finally figured it out, and thought I would post to save the next person some trouble...

This is for Ubuntu 10.10 desktop, on a Dell laptop, with an LCD monitor on the SVGA port (not the DVI port).  This particular laptop had the built in screen ripped off, but I don't think that made a difference for this problem.  It was scrap to the owner, so I'll use it for a low power consumption compact print / web server.

Basically, upon setup, the screen would blink about once every 10 seconds, and blink every time you ran xrandr.  This is only when the VGA port was in use.  When the DVI port was used, it was fine.

After a bunch of searching and flailing, I finally found this:
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

This laptop has a radeon, so the one that worked was:
# ATI Radeon:
echo options radeon modeset=0 > /etc/modprobe.d/radeon-kms.conf

Of course you must sudo to be able to write that file, I just navigated to that 
directory and edited the file manually.

That solved my problem.  Hope this helps someone!

---

