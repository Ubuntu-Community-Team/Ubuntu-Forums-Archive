---
title: "Display driver not being recognized?"
date: 2011-01-02
forum: Mythbuntu
---

### Post by torpare on 2011-01-02
I've downloaded and burned to CD Mythbuntu ver. 10.10

My aim initially is to explore Mythbuntu by running it on two machines both (temporarily) on my desktop, simulating a frontend/backend setup.  I have them interconnected via a crossover network cable, and plan to install Mythbuntu to a 4 Gb usb stick plugged into the "backend" while I run the " frontend" directly from the CD.

First question:- is any problem foreseen with this (temporary) setup?  If all goes well I would dismantle it in favour of a conventional long-term arrangement with frontend and backend in different rooms, connected over my (wired) LAN.

Second question:- I have a problem with screen resolution, so that Mythbuntu fails to display when run from CD on my frontend machine.  Some of its details are:- Shuttle SN41G2, Athlon XP running at 1.8 Ghz, Chipset nForce2 IGP/nForce2 MCP-T, 512 MB DDR RAM.  Graphics (presumably the cause of the problem) GeForce MX Integrated GPU, AGP 4X, 32 MB RAM.  Antiquated spec of course.

The driver designated for this by NVidia is Forceware ver. 93.71, and is working normally.  My monitor is an LG L194WT, with native resolution 1440 x 900 @ 60 Hz.  The display running Windows XP works fine at this resolution but when I try to run Mythbuntu from the CD problems begin almost immediately.

To start with, the "Mythbuntu" progress-bar screen does display but "tears" horizontally all the time (without ever completely breaking up).  Screen then goes blank, until finally having loaded all the files the drive rests - but nothing whatever displays on the monitor.  I presume there must be some incompatibility which is causing my ancient NVidia display driver not to be detected by Mythbuntu.

Has anyone any suggestions, please?

---

### Post by snackjackal on 2011-02-11
Similar problems here with exact same system.  I did find that adding the -nomodeset option in grub when booting from CD (the F6 option) allowed the system to boot with standard VESA (I believe) drivers, and there was no graphical tearing.  So, that narrows it down to the video driver that the live cd system uses, since after installing, the system will just crash at the splash screen.  

Trying a 10.04 version cd, and going to try going back to a 9.04 version, should that not work.  I'll keep noting progress.

---

### Post by snackjackal on 2011-02-11
Just tried the 10.04 disc -- worked just fine.  Lots of tearing during installation, but it installed.  I had it install the Nvidia drivers during the main installation, and after reboot was solid.  I'll play around with it more tomorrow, and give another update.

---

