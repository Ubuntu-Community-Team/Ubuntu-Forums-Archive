---
title: "Screen Resolution"
date: 2008-07-11
forum: Multimedia Software
---

### Post by modchamp on 2008-07-11
Well I just got ubuntu installed, I'm totally new to Ubuntu and Linux so please bare with me. When I try and change the screen resolution the highest it can go is 1024x768 I'd like to set it higher than that. So I searched around and found something about xorg.conf but in mine all it has under monitor settings is: 

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

So I guess I'm looking for some help in being able to change my resolution to something higher. Oh on my other partition i've got windows xp home edition 2 installed and I can set the resolution higher just fine.

Specs of my computer:
MSI K9VGM-V AM2 VIA K8M890 Micro ATX AMD Motherboard
AMD Athlon 64 X2 4400+ Brisbane 2.3GHz Socket AM2 65W Dual-Core Processor Model ADO4400DOBOX
Western Digital Caviar SE16 WD3200AAKS 320GB 7200 RPM SATA 3.0Gb/s Hard Drive
WINTEC AMPO 2GB 240-Pin DDR2 SDRAM DDR2 667 (PC2 5300) Desktop Memory Model 3AMD2667-2G2-R
Windows XP Home Edition Service Pack 2 on first partition
Ubuntu 8.04.1 on second partition

Thanks for any and all help.

-modchamp

---

### Post by modchamp on 2008-07-12
Anyone able to help with this?

---

### Post by wolfen69 on 2008-07-12
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
then restart x or reboot.

if that doesnt work, also try
```
gksu displayconfig-gtk
```

---

