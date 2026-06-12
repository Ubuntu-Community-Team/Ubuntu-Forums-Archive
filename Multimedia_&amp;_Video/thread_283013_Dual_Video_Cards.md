---
title: "Dual Video Cards"
date: 2006-10-23
forum: Multimedia &amp; Video
---

### Post by dozerl on 2006-10-23
I have two different video cards in my box. One is an AGP ATi 9600xt and the other is a PCI ATi 7000.  I changed my xorg.conf file to allow both to run at the same time.  The problem is, on the PCI video card, the monitor says P/N 113-PC0200-05E.  I looked on google and could not find anything important/useful.

This might be of some help.

> 
Section "Device"
	Identifier	"Generic Video Card 2"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:2:9:0"
EndSection


Thanks for the help.

---

### Post by dozerl on 2006-10-23
I got it to display on the other screen.  I changed the driver from vesa to ati.  But another problem arose.  On the 9600xt I cannot setup dual head on it.  I have tried many different combos, and they all crash X.

---

