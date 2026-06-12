---
title: "3 Monitor setup - ati/intel mix - intel not displaying"
date: 2014-08-18
forum: Multimedia Software
---

### Post by mtotho on 2014-08-18
Hello guys,

My question boils down to this:
      Any ideas on how to make a 3rd monitor, driven by integrated intel, work alongside the other 2 monitors driven by ATI graphics card while using the proprietary ATI drivers?

I am running Ubuntu 14.04 with Cinnamon desktop on my desktop computer.

My set up has 3 monitors :
  2x monitors on Radeon HD 6850 (via DVI)
  1x monitor on integrated intel graphics (core i5)

After installing linux, all 3 monitors will work using open source drivers. However, after installing the fglrx (via command line) it would appear the 3rd monitor connected to the intel chip is not detected. I would assume this is because either fglrx is now the only graphical driver being loaded or at least is not configured for the 3rd monitor.

The third monitor does actually detect input, turns on after I boot and becomes backlit, however no display shows up. Additionally, the monitor does not show up in the settings.

I suppose I could revert back to the open source drivers - everyone says the 2D performance is better anyway - but I would like the 3D performance gains of the proprietary driver.

I have tried googling this intensely but most of my results seem to be obfuscated by those who are setting up hybrid graphics (one or the other) or dual graphics (2 ati) but I cant seem to find much on using both graphic cards at the same time across different monitors.

Thanks in advance and let me know if there are any logs I should upload

Mike

---

### Post by Burak_Ongay on 2014-10-23
Hi, 

I have the exact problem. I don't want to use open source drivers because my mouse is flicking without fglrx.
I couldn't find any solution yet, if I do, I will write here. I hope you will do the same.

Burak

---

### Post by Vladlenin5000 on 2014-10-24
You can't use both integrated and PCIe.

---

