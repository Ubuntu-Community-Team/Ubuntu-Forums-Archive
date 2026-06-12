---
title: "opengl corruption"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by SuperBOB on 2007-05-28
[http://ps-aux.org/screenshots/opengl_corruption.png](http://ps-aux.org/screenshots/opengl_corruption.png)

The above screenshot should be showing the ppracer menu.  Instead its .. well .. weird. :)
Whats causing it and how do I fix it? 

Thanks in advance for any help.

**Xorg.conf**
Section "Device"
        Identifier        "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
        Driver "radeon"
        BusID  "PCI:1:0:0"
        Option "XAANoOffscreenPixmaps"
        Option "AGPMode" "4"
        Option "AGPFastWrite" "true"
        Option "DisableGLXRootClipping" "true"
        Option "AddARGBGLXVisuals" "true"
        Option "AllowGLXWithComposite" "true"
        Option "EnablePageFlip" "true"
EndSection



**glxinfo output**
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2

---

### Post by SuperBOB on 2007-05-29
Im still having this problem, and its occuring in everything that uses opengl.

---

### Post by SuperBOB on 2007-06-04
Sought help on IRC and nobody has been able to explain it yet.. :popcorn:

---

### Post by schadfield on 2007-06-11
> **SuperBOB said:**
> Im still having this problem, and its occuring in everything that uses opengl.

I have OpenGL problems with my Matrox G550 (Feisty i386). No menus in ppracer and screen corruption with OpenGL apps from /usr/lib/xscreensaver.

---

### Post by rockingmtranch on 2007-06-11
Screen resolution too high or low maybe?

---

### Post by schadfield on 2007-06-11
> **rockingmtranch said:**
> Screen resolution too high or low maybe?

I have used exactly the same hardware with Debian Etch and OpenSuse 10.2 with no problems. It is an Ubuntu software problem.

---

### Post by ahickey on 2007-08-20
I have the same problem but I am using an NVIDIA based graphics card.
Attached is the image from BillardGL.  Sometimes it works perfectly an other times it is corrupted.

I'm using the Nvidia accelerated graphics driver installed using the Restricted Drivers Manager
It is an onboard 6100 Graphics card.

I'm running 7.04 64 Bit on a AMD Semperon based system

Below is section from my xorg.conf

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:0:13:0"
	Option		"mtrr"	"off"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-100
	Vertrefresh	43-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection


Any help greatly appreciated.

Thanks,
Albert.

---

