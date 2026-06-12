---
title: "Ubuntu 10.04 networked sound to WIndows XP"
date: 2010-05-24
forum: Multimedia Software
---

### Post by BatteryKing on 2010-05-24
For 1Gb/s LAN usage, I set up XDMCP under Ubuntu 10.04 to display a desktop to my notebook in Windows XP mode using Xming 7.5.0.20 (yes I paid the man).  For work purposes (which this is primarily for) performance is excellent.  However I have not yet managed to get sound to traverse the network to Windows XP.  So far here is what I have tried:
1. Pulseaudio - There is what seems to be a very old port of Pulseaudio to Windows XP, but Ubuntu 10.04 doesn't seem to recognize it.  I did a baseline test between two Ubuntu 10.04 systems and Pulseaudio worked fine over the network while using XDMCP for the rest of the console.
2. ESD - I found that ESD comes with cygwin, but I couldn't seem to get this to work either from the online howtos I found.  The various commands I tried executed, but I could not verify a connection between the two systems as being established.

I noticed there is NoMachine's NX based client / server software out there which at least sounds superior in all respects to the XDMCP solution I am trying now (even has a suspend / resume function I could really use), but this looks to get real expensive real fast if I ever try to expand out usage.  For this reason I am trying to stick to free / low cost solutions if possible where performance over a LAN is still fast and multiple users can have full desktops running at the same time.

---

