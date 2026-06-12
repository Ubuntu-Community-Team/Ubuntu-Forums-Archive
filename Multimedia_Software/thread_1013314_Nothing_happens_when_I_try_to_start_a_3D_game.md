---
title: "Nothing happens when I try to start a 3D game"
date: 2008-12-16
forum: Multimedia Software
---

### Post by Ursa on 2008-12-16
When I try to start the game, all I get is a single, quick, flicker. There's no resolution change, the screen never turns completely black.
I've got the latest drivers from ATI so that shouldn't be the problem.
My card is an ATI Radeon X1950 Pro, I don't know if it matters.

The games I've tried:
Egoboo
Supertuxkart
Warzone 2100

Any help would be greatly appreciated.

---

### Post by Ursa on 2008-12-17
I found out that none of my 3D screen savers work either, I've used a 2D one for quite a while so I have no idea when they stopped working.

I guess my graphics card isn't set up correctly, how do i do a 'perfect' setup? =)

---

### Post by binbash on 2008-12-17
paste the output of : 

fglrxinfo

or

glxinfo | grep render

---

### Post by Ursa on 2008-12-17
This is the output:

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

---

### Post by binbash on 2008-12-17
paste your xorg.conf

---

### Post by Ursa on 2008-12-17
First of all, thanks for your time.
Second, I noticed that I can't use the desktop "Visual Effects" either.

Here it is:

```
Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth	24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	BusID       "PCI:5:0:0"
	Driver	"fglrx"
EndSection
```

And also, compiz-check output:

```
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV570 [Radeon X1950 Pro]
 Driver in use:         fglrx
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect fglrx driver version in use.
```

---

### Post by Ursa on 2008-12-18
I'm not having any luck on my own, so I thought I would humbly bump. :)

---

