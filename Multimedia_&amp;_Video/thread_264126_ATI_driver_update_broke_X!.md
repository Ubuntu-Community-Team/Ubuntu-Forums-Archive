---
title: "ATI driver update broke X!"
date: 2006-09-24
forum: Multimedia &amp; Video
---

### Post by jperez on 2006-09-24
Hey guys,

Can anyone help me to recover X?  I updated the drivers according to one of the stickies and now, X won't start anymore.  I even removed the drivers and nothing.  The computer's stats are:

Gateway 433c Tower
CPU: 433Mhz Celeron
RAM: 128MB
Video: ATI Rage 128 RL/VR AGP

How do I restore X so that I can get back into Xubuntu?  Thanks guys!

Jesse~

---

### Post by fanta on 2006-09-25
Any more specific information? Like error messages from X?

Anyway, my guess is your xorg.conf file still points to the old driver you deinstalled. Open /etc/X11/xorg.conf in an editor with admin rights:

sudo vi /etc/X11/xorg.conf

Search for the "Device" section that shows your card in "Identifier". There should be a line called "Driver". Change the driver there to "ati" (the default one from ubuntu). It's probably "fglrx" for you right now (that's the official one from ATI). Start the Xserver or reboot.

---

