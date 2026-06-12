---
title: "dpkg-reconfigure won't ask about monitor or resolution - setting up 9600GT on 8.10"
date: 2009-02-12
forum: Multimedia Software
---

### Post by brianmrowe on 2009-02-12
I've followed just about every howto setup the nvidia drivers available except doing the envyNG thing because so  many other people got this to work with out it.
I'm trying to install an nVidia 9600GT on Ubuntu 8.10.
I did the driver install, clicked the recommend one and restarted.  Said everything was good.  no usb devices worked for a while, that 'fixed' itself along the way.
But now I have a resolution max of 640x480.  I try to dpkg-reconfigure -phigh xserver-xorg and without -phigh.  rebooting, etc.  reconfigure makes it worse.  It doesn't pick up nvidia at all and drops a basic 640x480 failsafe xorg.conf in there.
I wanted to just add the modlines myself at this point, but the file says not to now.  My goal was dual monitors but right now I just want the first one to work.

From Xorg.0.log
(II) LoadModule: "nvidia"

(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Video Driver
(II) v4l driver for Video4Linux
(II) NVIDIA dlloader X Driver  177.82  Tue Nov  4 13:42:45 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for v4l
(II) Loading sub module "fb"
(II) LoadModule: "fb"

from xorg.conf - I can't cut and paste it all right now.

modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync


Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Screen	0
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


I don't know how to get it to pick up the resolutions.

---

### Post by brianmrowe on 2009-02-12
As soon as this started to work, it worked super simple like it should, but I'm not really sure what I did to fix it.
I'm going to try to recap the longer version on my blog:
[http://technecity.blogspot.com/](http://technecity.blogspot.com/)

Basically, I deleted the entries in xorg.conf that set the resolution to 640x480.  The modeline and the screen entries.
I left the nvidia entry in the driver.  You need that one or nothing seems to work right.  That was the result of using dpkg-reconfigure that was messing me up.
I did ctrl-alt-backspace and it instantly just went to 1680x1050.
Then I chose twinview and setup my second monitor. 
Works like a champ so far, but it took 12 hrs from last night until this morning so I have a few open items if people know the answer.
1.  On the LCDs shows as a CRT.
2.  Compiz is not on yet, but I want to try.
3.  The background was stretched across both monitors, but I'd like it to be a single pic in each.  small but still, I want to be better Vista.

If you have any thoughts on those, that would be great, I'm off to search..

---

