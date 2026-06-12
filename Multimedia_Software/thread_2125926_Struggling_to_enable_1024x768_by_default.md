---
title: "Struggling to enable 1024x768 by default"
date: 2013-03-15
forum: Multimedia Software
---

### Post by etienne@Rofti on 2013-03-15
Hi! Thanks for reading!

I have an old desktop machine that I am attempting to repurpose as a home server. It's a very old, basic machine - an ASUS Terminator Pentium 4 with 245 MB of RAM with an itegrated SiS 650 motherboard. For more information on the hardware: [http://www.nativetechnologyinc.com/native/asus_terminator_p4.htm](http://www.nativetechnologyinc.com/native/asus_terminator_p4.htm)

However, I am quite a n00b when it comes to command-line usage, so I decided to install a few basic pieces of desktop software so that I'm not totally lost when I need to do something. I started with the Ubuntu 12.04 minimal image, and then, following the prompts, installed the Ubuntu server packages. I then installed a basic Lubunu desktop (NOT the lubuntu-desktop package!) inluding lxterminal, Chromium, and a couple of other really basic things to keep it light-weight, but to make it easier for someone like me to use.

However, I have really been struggling to attach a screen and effectively use the machine. I have an old CRT monitor, and when I attach it and start the machine, I get a perfectly usable 1024x768 resolution desktop, or at least, the login screen. When I attach my flatscreen LCD monitor that also supports 1024x768 amongst other resolutions, it boots but the LCD screen shows an "Out of Range" message. I then have to unplug the LCD, plug in the CRT, and I see a command line waiting instead of a desktop.

If I unplug both screens, and then boot the machine, it boots fine, and then when I plug in a screen, I have a usable desktop, but only with a maximum resolution of 960x680. I cannot increase this resolution, no matter what I do, and the only way to get back a 1024x768 resolution is to reboot with the CRT screen attached.

I want to get rid of the old, big, bulky CRT, and be able to reboot this machine at any time, with or without a screen attached, yet be able to easily and effectively use the desktop if I need to. Is there some sort of setting that I need to change, adjust, add or remove?

Thank you in advance for all your help!

E

---

### Post by ManamiVixen on 2013-03-15
SiS is not supported. The fact that you have a usable desktop is a virtual miracle. There really isn't much you can do. SiS and Linux as had a very bad relationship from the start. You can try running in VESA Graphics mode, but you probably already in it since it sounds like the PC failed to load a proper driver. Drivers for SiS hardware haven't existed since X Server version 4 as accoring to the SiS website.

---

### Post by etienne@Rofti on 2013-03-15
Thank you for the info, ManamiVixen! I appreciate the reply.

I wonder, if anyone else is reading this, if there is a way to force/workaround the resolution settings?

---

### Post by humpty88 on 2013-04-19
This is one of the gripes I have with new linux distros. 
In the old days, the monitor setup only followed what you specified in the config files. 
Nowadays it's the other way around, auto-detect, great as it has progressed, gets priority.

You can try xrandr commands in your startup scripts.

If that fails, it could be rare that the EDID firmware (the chip that identifies itself) in your LCD monitor is corrupt.
If that's the case try : [https://github.com/bulletmark/edid-rw](https://github.com/bulletmark/edid-rw)

---

