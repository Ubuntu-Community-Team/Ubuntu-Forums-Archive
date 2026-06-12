---
title: "driver..."
date: 2008-03-08
forum: Multimedia &amp; Video
---

### Post by abhisheknegi on 2008-03-08
here is my xconf.org

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:0:16:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "ServerFlags"
EndSection

Please suggest why i m not able to install driver for the Geforce 7100 GPU card and the monitor resolution is stuck on 800*600????

I m on gutsy from past a week tried almost all the ways ppl told....but still no benefit.

---

### Post by 1010011010 on 2008-03-08
Did you try Envy?

[Envy]("http://www.albertomilone.com/")

---

### Post by abhisheknegi on 2008-03-08
yes....it was unable to detect the hardware so i tried installing manually but still no luck..

---

