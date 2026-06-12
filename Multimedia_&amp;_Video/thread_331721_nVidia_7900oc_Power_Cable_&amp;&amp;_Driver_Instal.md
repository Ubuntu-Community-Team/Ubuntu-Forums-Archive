---
title: "nVidia 7900oc Power Cable &amp;&amp; Driver Installation"
date: 2007-01-05
forum: Multimedia &amp; Video
---

### Post by Jaygo333 on 2007-01-05
I am trying to install my nVidia Drivers onto my computer but keep getting an error about power management.

When I install the drivers, Xserver crashes and tells me that  should connect the extra power cable to the card.
The card iteself does not have a place to plug in the power cable. 
When used in Windows, the card complains that it is not receiveing enough power and must be lowered.
I have BFG 7900 OC card which through online many are claiming that it does have a port to plug in a power cord. Also all reviews are saying it uses PCI-eXpress as the main connector but I am stuck using the AGP side of it to connect to my PC as the PCI-e side cannot fit into my computer.

What is going on or do I have a busted Graphics card. All components are reading it as an nVidia 7900 OC - whether in Linux or Windows.

---

### Post by MetalMusicAddict on 2007-01-05
Im sure that card has a place for power. I have the EVGA model.

---

### Post by Jaygo333 on 2007-01-05
What do you mean. And how do I check..

---

### Post by Jaygo333 on 2007-01-05
I jsut checked the card. It does have a place to connect a cord. 
I have connected a cord which seemed to be the only one to fit the area. 
Looks like the secondary power supply cable but black.

---

### Post by tseliot on 2007-01-06
Type this command:
```
sudo nvidia-xconfig --no-power-connector-check
```

and restart the xserver or reboot

---

### Post by Jaygo333 on 2007-01-09
Thank you all for your help.
I did manage to find the problem. 
The video card requied two IDE power cables, not just 1 that I had plugged in.

Thank you tseliot for a new command in my directory.

---

