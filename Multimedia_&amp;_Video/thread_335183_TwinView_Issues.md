---
title: "TwinView Issues"
date: 2007-01-09
forum: Multimedia &amp; Video
---

### Post by Icemanyurt on 2007-01-09
I have been following some of the HowTos to get TwinView working, but so far no luck

My card is a VisionTek Xtasy Everything, which has a stand alone box for the outputs that is auxiliary to the video card ([http://www.hothardware.com/viewarticle.aspx?articleid=497&cid=2](http://www.hothardware.com/viewarticle.aspx?articleid=497&cid=2))

The video card itself is a GeForce2 MX/MX 400

I am trying to use a CRT monitor and a TV (connected through the composite out on the box)
Here is how I have setup
> 
Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nv"
	BusID		"PCI:1:5:0"
	Option          "TwinView" "True"
	Option		"TwinViewOrientation" "RightOf"
	Option		"UseEdidFreqs" "False
	Option		"MetaModes" "1024x768; 1280x1024"
	Option		"UseDisplayDevice" "CRT, TV"
	EndSection


Any ideas would great, thanks

---

### Post by Jdog1928 on 2007-01-10
Being a newb I don;t know much... but I think you may need nvidia as the driver and aswell you are missing a quotation mark at the end of False

Section "Device"
Identifier "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
Driver "[COLOR="Red"]nv[/COLOR]"
BusID "PCI:1:5:0"
Option "TwinView" "True"
Option "TwinViewOrientation" "RightOf"
Option "UseEdidFreqs" "False[COLOR="Red"]"[/COLOR]
Option "MetaModes" "1024x768; 1280x1024"
Option "UseDisplayDevice" "CRT, TV"
EndSection

---

