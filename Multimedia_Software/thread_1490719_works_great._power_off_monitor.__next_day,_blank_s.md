---
title: "works great. power off monitor.  next day, blank screen"
date: 2010-05-22
forum: Multimedia Software
---

### Post by xls on 2010-05-22
My system:
I have a fresh install of 10.04 on an AMD 790GX system (GA-MA790GP-UD4H, integrated Radeon HD 3300).  I'm using a DVI to HDMI cable to a Toshiba Regza 42" LCD.  I use this computer to watch videos and play music.

My problem:
Everything works great, until I power off the television and leave it for a couple hours.  When turning the TV back on, it seems to have a signal (the TV would display a message otherwise) and the backlight is on but the screen is black.  I know the system is still live because I can ssh into it and poke around.  Prior to 10.04, I could revive the display by switching to a text terminal and then switching back to X (ctrl+alt+F6, wait for the login prompt, alt+F7).  This no longer works on my fresh install of 10.04.  Nothing I do will bring the display back and I've been rebooting it from ssh so it restarts properly.

What I've tried:
I've tried disabling DPMS (via xorg.conf file) and ACPI (using aticonfig) but that doesn't help.  I've disabled the screen saver and any display power management.  I've tried both the out-of-the box default display driver and the proprietary ATI drivers.  I wouldn't be surprised if it was something goofy with the TV because it's NOT an actual PC monitor but I just need to properly configure Ubuntu to not stop the graphics output just because I powered off the TV.  I'm wondering if an HDMI-HDMI would resolve this (motherboard has an HDMI port on it) but I don't have an HDMI cable.


Thanks for reading.  Any insight would be most appreciated.

---

