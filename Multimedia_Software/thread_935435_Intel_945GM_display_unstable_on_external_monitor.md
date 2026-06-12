---
title: "Intel 945GM: display unstable on external monitor"
date: 2008-10-01
forum: Multimedia Software
---

### Post by scgroup on 2008-10-01
I have a couple of Dell Inspiron E1705 (a.k.a. 9400) laptops running Ubuntu 8.04 that are sometimes used as desktop replacements. When an external monitor is used alone, within a few minutes the display becomes corrupted and unreadable.

The machines have built-in Intel 945GM graphics and 1920x1200 LVDS LCD panels, and dual-boot Ubuntu or Windows XP.  In either OS, there is no problem using the internal screen alone, or using both internal and external screens simultaneously, and under Windows, an external monitor works fine.   But in Ubuntu, the internal LCD won't turn off, with Fn-F8, by closing the lid, or by booting with the lid closed.

I'd very much like to turn off the internal monitor, to save energy, avoid needless wear on the backlight, and avoid overheating when the lid is closed.  There are also application problems when two monitors with differing resolutions are both enabled.

The internal screen and backlight do shut down if I issue:
xrandr --output LVDS --off
but a few minutes thereafter the display goes bad.  One machine has a Hyundai 1920x1200 LCD monitor connected via DVI (TMDS-1); the screen starts to flicker and change rapidly, even when the intended display is static.  The other has an old iiyama CRT connected via VGA, typically set to 1600x1200.  It will go all black or all white, sometimes except for a few pixel rows at the top or bottom.  When the picture is bad, one can connect by VNC and still see the desktop correctly.  Sometimes, even restarting the X server won't revive the local display; only a reboot seems to help.

I have the latest (per synaptic) versions of xserver-xorg-video-i810 (2:1.7.4-0ubuntu7) and xserver-xorg-video-intel (2:2.2.1-1ubuntu3.6).  Are there different drivers or settings that I should try?

---

### Post by scgroup on 2008-10-02
Oops -- I had edited xorg.conf incorrectly, such that it was always using the default 'intel' driver.  With the 'i810' driver, the machine with the CRT now works fine.  Not only is the stability issue resolved, but the laptop panel turns off when it should, without help from xrandr.  The computer with the external LCD is also stable when using i810, but unfortunately 1920x1200 is not one of the offered resolutions, so the picture is stretched.  I suspect that a custom mode line will fix it.

---

