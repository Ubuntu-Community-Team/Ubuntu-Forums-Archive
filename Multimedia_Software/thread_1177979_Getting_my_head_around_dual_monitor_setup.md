---
title: "Getting my head around dual monitor setup"
date: 2009-06-04
forum: Multimedia Software
---

### Post by joefish_only_one on 2009-06-04
I've installed kubuntu for the first time (although I have been using linux for a few years).

I'm trying to get dual monitor support (extended monitor and cloning) to work properly on my laptop, but don't seem to be having any luck (nothing works).

My laptop is a toshiba a50, my graphics card is identified as follows:
```
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```My xorg.conf currently looks like this:
```
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "ServerFlags"
    Option    "DontZap"    "False"
EndSection
```In the display option under system settings, both monitors are detected: the laptops LCD is showing up as LVDS and the external as VGA (I'm unable to try TV-out at this point).

I can play around with the options for both monitors (resolution and refresh rate), but cannot get the external monitor to go at all (yes, it does work fine). If I click "identify outputs", then I see that both LVDS and VGA appear on the laptop's monitor! In the green box on the right I can see "VGA" underneath LVDS.

Ultimately I'd like to have an extended monitor, using the secondary one for presentations etc. If I could even get cloning to work, that would be a start...

Thanks for your help.

---

### Post by polomint77 on 2010-10-08
Hi, were you able to get an external monitor working on your A50.. My external screen shows a garbled display. It's a known working monitor and leads..  Cloning is what I'm really after as my laptop screen is a bit damaged.
Thanks


PS: Does the tosh a50 have an option in bios to increase the shared video memory?

Thanks again.,.,

---

### Post by joefish_only_one on 2010-10-08
Hi, no unfortunately I didn't get it to work on Ubuntu on that laptop. I eventually got it working with Fedora, although I can't remember how as I'm not using that laptop any more, sorry!

---

### Post by polomint77 on 2010-10-08
Thanks for replying.  I'm going to try some different distros tomorrow anyway to see if I can get it working.

Failing that, I will be going back to Windows, :(

---

