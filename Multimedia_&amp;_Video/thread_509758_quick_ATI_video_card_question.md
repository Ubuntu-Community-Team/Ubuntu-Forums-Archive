---
title: "quick ATI video card question"
date: 2007-07-25
forum: Multimedia &amp; Video
---

### Post by chaos2286 on 2007-07-25
Hey,

Hopefully this will be quick, but as I was going through my xorg.conf file to try and figure out why I couldn't get a refresh higher than 60hz, I noticed this about my video card.

Section "Device"
	Identifier  "ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection


Now...Why would it say PCI, when the card is clearly an AGP card?  I also noticed in the BIOS config it was listed as a PCI so I changed it to AGP.  If anyone could help me out on this it might be huge because I've got a game I'm trying to get working that keeps freezing in the middle.  Thanks!

---

