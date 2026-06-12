---
title: "Ati driver from live CD"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by Sirkent on 2006-06-03
Hi all,

I expect this has already been covered, but here are my experiences from using the Live Dapper CD. I've got relatively new hardware - An Nvidia4 motherboard with built in LAN and Radeon X850XT, as well as an old sound blaster compatible sound card.

The only problem I had was that Ubuntu attempted to load the dreaded 'ati' driver module. I changed this in the xorg.conf to 'vesa' and here I am, posting 5 minutes later with everything working. Obviously the last step for you guys it to get improve the detection of ati graphics cards, but otherwise I've very impressed. Even Debian (my favourite distro) got my sound card and network wrong and required a great deal of hacking.

---

### Post by kakashi on 2006-06-03
[QUOTE=Sirkent]Hi all,

I expect this has already been covered, but here are my experiences from using the Live Dapper CD. I've got relatively new hardware - An Nvidia4 motherboard with built in LAN and Radeon X850XT, as well as an old sound blaster compatible sound card.

The only problem I had was that Ubuntu attempted to load the dreaded 'ati' driver module. I changed this in the xorg.conf to 'vesa' and here I am, posting 5 minutes later with everything working. Obviously the last step for you guys it to get improve the detection of ati graphics cards, but otherwise I've very impressed. Even Debian (my favourite distro) got my sound card and network wrong and required a great deal of hacking.[/QUOTE]
really sorry. i was supposed to file a  buig report for x8xxx cards a few months back but i totally forgot (due to exams). i had the same issue with my ati x800gt and dfi nf4 sli mobo. if you can please do file a report.

---

### Post by BaffledMollusc on 2006-06-03
[QUOTE=Sirkent]Hi all,

I expect this has already been covered, but here are my experiences from using the Live Dapper CD. I've got relatively new hardware - An Nvidia4 motherboard with built in LAN and Radeon X850XT, as well as an old sound blaster compatible sound card.

The only problem I had was that Ubuntu attempted to load the dreaded 'ati' driver module. I changed this in the xorg.conf to 'vesa' and here I am, posting 5 minutes later with everything working. Obviously the last step for you guys it to get improve the detection of ati graphics cards, but otherwise I've very impressed. Even Debian (my favourite distro) got my sound card and network wrong and required a great deal of hacking.[/QUOTE]
Is this the same as my problem? With the default driver (ati) my resolution is stuck at 600x480 and there's no way to change it. If install the fglrx driver the resolution problem is fixed, but everytime I shut down or stop the gdm the computer hangs. I need to cycle the power to reboot.

If this is the same problem, are you saying I should change the driver in xorg.conf from "fglrx" or "ati" to "vesa"? Should I do this with the default driver or with the binary ATI driver installed?

Any suggestions appreciated - I'm tearing my hair out here!

Edit: I have an ATI X800 Pro video card.

---

### Post by kakashi on 2006-06-03
don't manuallt change anything in the file. 
use
sudo dpkg-reconfigure xserver-xorg

edit. 
i think that the command. been a while since i had to do it.

---

### Post by Sirkent on 2006-06-03
Well, it looks like I have a bigger problem! It just randomly freezes (using vesa), and as it's booting from the CD I can't go into the logs to figure out why. Maybe it isn't the graphics card, but at this point I have no way of finding out. I'll try to scour the forums for a way to boot into console instead of the GUI...

---

