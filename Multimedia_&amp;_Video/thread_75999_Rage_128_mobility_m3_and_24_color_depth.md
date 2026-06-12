---
title: "Rage 128 mobility m3 and 24 color depth"
date: 2005-10-14
forum: Multimedia &amp; Video
---

### Post by ggeneraux on 2005-10-14
I have a Dell Inspiron 4000 laptop (native resolution is 1400x1050 on a SXGA+ TFT screen) with a Rage 128 Mobility M3 (8M Video RAM) which has a small quirk whenever I run it at a color depth of 24.  When moving windows, or scrolling within a window, the desktop background shows thin, short horizontal white flickers during the movement.  This is, of course, especially noticable with a dark background.  
If i change the color depth to 16, then these flickers go away.  This situation is the same on several distributions that I've tried that use Xorg (Ubuntu Hoary, Breezy (not final, but the release candidates), Slackware 10.1, SUSE 10.0, FreeBSD 5.4, etc...), but on Windows XP, which shows the True Color depth as being 32, I don't see the same flicker.  I've tried changing the color depth in the Xorg.conf to 32, but when restarting xwindows it gives an error stating that this color depth is not supported.  
I'm wondering if anyone else has had this experience, and if it's something that's correctable through changing a setting, or if it's an inherent problem with the r128 driver?  Any ideas would be greatly appreciated.

Thanks,

Grant

---

