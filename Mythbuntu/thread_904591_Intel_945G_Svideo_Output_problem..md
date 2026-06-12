---
title: "Intel 945G Svideo Output problem."
date: 2008-08-29
forum: Mythbuntu
---

### Post by dabone on 2008-08-29
I'm trying to get 8.04 running on a Gigabyte H663 Pc.
This machine has  intergrated 945g video graphics


[http://www.gigabyte.com.tw/Products/DigitalHome/Products_Spec.aspx?ProductID=2236&ProductName=H663](http://www.gigabyte.com.tw/Products/DigitalHome/Products_Spec.aspx?ProductID=2236&ProductName=H663)

I need svideo for output, and I can get desktop and the myth menus working with the i810 driver, but when I go to watch tv, the screen scrambles (Like it goes to a wierd video mode that is displaying a low res garbled and repeated display)

This also happens when trying to play a movie with mplayer.
xine playing to the desktop works.
So it's when it going to a full screen mode.


Exiting watch tv still leaves the video scrambled and I have to restart the xserver.


I've not been able to get svideo out working with the intel video driver (xorg).

Can anyone give me a hint, I've seen people using this driver for svideo with laptops but with my config, the tv is the only monitor.

Btw, when hooked to a regular monitor video playback is correct.


Thanks,
Mark

---

### Post by danbodoh on 2008-08-29
I think the 945 should use the i915 kernel driver with the 'intel' X driver.  If so, then my how-to for GM965 probably will help you (at [http://ubuntuforums.org/showthread.php?t=822606](http://ubuntuforums.org/showthread.php?t=822606)).  The 'intel' driver has been written so that not much is needed in Xorg.conf; just a basic config should get you going.

Dan Bodoh

---

