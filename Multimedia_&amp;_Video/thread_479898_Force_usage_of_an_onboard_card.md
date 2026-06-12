---
title: "Force usage of an onboard card"
date: 2007-06-20
forum: Multimedia &amp; Video
---

### Post by Xbehave on 2007-06-20
ive been trying to use the on-board graphics on my intel board, and my nvidia card at the same time, but when my card is in my on-board stops working.

IS there anyway to force the on-board graphics to be used

in my bios ive set the preferred grafics to pci but this has had no effect!
im fairly sure the motherboard is doing something to hide the onboard card, if there is no card in then the livecd / onboard xorg.conf runs fine, using the on-board card, but whenever a card is in the livecd or onboard xorg is used then the onboard card just doesn't do anything (at any stage POST,grub,pre-kde,kde)

i think the hiding of the onboard card is a feature to stop the os getting confused and save ram but is there anyway to force access to the onboard GFX

here are some of the relevant files doubt itll help unless its possible to force it
relevant parts from diff lspci's
```

< 00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
> 00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
13,16c13,18
> 01:00.0 VGA compatible controller: nVidia Corporation NV31 [GeForce FX 5600] (rev a1)


the xorg.conf for intel
[CODE]
Section "Device"
	Identifier	"Intel Corporation 82865G Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

```

the xorg.conf for nvidia
```

Section "Device"
	Identifier	"Nvidia"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

```

---

### Post by josesanders on 2007-06-21
Is your NVidia card AGP or PCI?  The only way that you can use the onboard video is if you have a PCI card.  Whenever you put in an AGP card, the motherboard video is automatically disabled.  I'm not sure why, but I would guess it has to do with resource conflicts.  I really don't think there's any way around it.

---

