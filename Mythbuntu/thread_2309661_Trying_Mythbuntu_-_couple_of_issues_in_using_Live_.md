---
title: "Trying Mythbuntu - couple of issues in using Live CD"
date: 2016-01-12
forum: Mythbuntu
---

### Post by tim143 on 2016-01-12
I'm wanting to try out Mythbuntu, created a live CD on USB flash drive (boots fine), but have a couple of issues:

1.  Graphics card is a eVGA Geforce 210 (Nvidia 210 chipset), but can't see the screen due to overscanning.  I've got it fixed in Windoze, but not sure how to fix in Mythbuntu.  In fact, I'm fairly positive that the Nvidia drivers aren't installed yet, as I've only booted to the install screen.  How can the display be adjusted (HDMI out going to LCD TV - Samsung)?

2.  want to try without installing, but from what I can see (barely see the "Install Now" icon), it appears that there isn't a way to run the backend using the Live USB?

---

### Post by deadflowr on 2016-01-12
yeah, to utilize the backend, it has to be installed.
There are settings that cannot be set on a live system, which will require reboots and logouts to properly run.
these settings need to be written to the disk.The live session runs in RAM, so all settings disappear on shutdown/reboot.


That said, you can use a live cd as a frontend.


Also, your gpu problems will probably get fixed with an install, since your card might need nvidia's drivers instead of the open-source drivers that mythbuntu comes with.
Myth should have the program additional drivers installed. You can use that program to find better drivers;
In your cards case, I would think either the nividia-304 driver or nvidia-173.

My 2 cents, anyhoo.

---

