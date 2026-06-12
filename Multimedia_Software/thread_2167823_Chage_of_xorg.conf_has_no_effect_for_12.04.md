---
title: "Chage of xorg.conf has no effect for 12.04"
date: 2013-08-15
forum: Multimedia Software
---

### Post by ODBWilson on 2013-08-15
Hi all,

I used to use /etc/X11/xorg.conf to change the resolution and rotate screen on Mythbuntu 10.10.
Now I upgrade the system to 12.04, and I create xorg.conf with "X -configure".  But I found that there 
is no effect when I change the resolution of rotate the screen.

For example,
Section "Device"
     Identifier "Card0"
     Driver     "intel"
     BusID     "PCI:0:2:0"
     Option    "Rotate" "left"
EndSection

Is it the correct way to rotate screen with xorg.conf in 12.04.  Or I need to change other files?

P.S.  I am able to change resolution or rotate screen with GUI.  
But I just need to do it with conf file for my application

Thanks,
Wilson

---

### Post by tgalati4 on 2013-08-15
Create an xorg.conf file with each rotation (done through the gui) and compare them.  It's possible that your video driver changed slightly and now the option line syntax is different.

---

### Post by ODBWilson on 2013-08-21
from the Xorg.0.log

[     5.448] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     5.448] (==) intel(0): DPMS enabled
[     5.448] (==) intel(0): Intel XvMC decoder enabled
[     5.448] (II) intel(0): Set up textured video
[     5.448] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[     5.448] (II) intel(0): direct rendering: DRI2 Enabled
[     5.448] (WW) intel(0): Option "Rotate" is not used
[     5.448] (WW) intel(0): Option "metamodes" is not used
[     5.448] (==) intel(0): hotplug detection: "enabled"
[     5.448] (--) RandR disabled

Option "Rotate" "left" is simply not used.
Any clues?
Again, I can use xrandr to rotate screen or change resolution.

---

