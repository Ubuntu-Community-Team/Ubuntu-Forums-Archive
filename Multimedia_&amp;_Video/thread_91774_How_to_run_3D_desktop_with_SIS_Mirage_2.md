---
title: "How to run 3D desktop with SIS Mirage 2"
date: 2005-11-18
forum: Multimedia &amp; Video
---

### Post by mithion on 2005-11-18
I saw the other day that there is a cool application called 3D desktop that comes with ubuntu which enables us to have a 3d rotating and zooming desktop.  So i tried installing it an running it only to get stumped cause my hardware acceleration isn't turned on.  I use an SIS Mirage 2 intregrated graphic thingy that came with my laptop.  Does anybody know if it's possible to turn on the hardware acceleration for this chipset?  Ans if it is possible, how is it done?  I also checked that the hardware is detected, and it seems so.  In xorg.conf, this is the section for the graphics.

Section "Device"
	Identifier	"Silicon Integrated Systems (SiS) SiS Default Card"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection

Anybody have a clue as to how I can make 3D desktop work?

---

