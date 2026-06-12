---
title: "Help with Dual Monitors (Laptop Screen &amp; Projector)"
date: 2010-04-09
forum: Multimedia Software
---

### Post by bellyoffire on 2010-04-09
I visited this Dual Monitor thread [http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

It says to back up this file /etc/x11/xorg.conf  I have the latest version of ubuntu and this file doesn't exist.  So does this thread no longer work for newer versions?

I tried posting there but I can't, maybe its locked.

I'm fairly new to ubuntu.  I just installed it this week.  I need to use this Acer 3002lci for presentations on a projector.

It has the SiS M760GX.

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

I plug in the projector to the VGA port.  Both the laptop screen and the projector are on and it is cloned (everything I see on the laptop screen shows on the projector).  I want the laptop screen to be the main screen and the projector to be the 2nd screen so I can project the open office presentations on it and drag things over to the 2nd screen (projector).

I looked in System > Display and it says unknown and only shows 1 monitor.  How do I get to what I need to accomplish?

Thank you for your help

---

### Post by allenck on 2010-04-12
try looking at the man xorg.conf page. It lists a number of alternative locations where the xorg.conf file resides. 

Open a terminal screen and type: man xorg.conf

---

