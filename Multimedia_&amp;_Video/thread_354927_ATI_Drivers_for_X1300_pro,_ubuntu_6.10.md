---
title: "ATI Drivers for X1300 pro, ubuntu 6.10"
date: 2007-02-06
forum: Multimedia &amp; Video
---

### Post by calman on 2007-02-06
i have never in my life had a problem this difficult to solve

i have a Radeon X1300 pro, and Ubuntu 6.10 edgy...i cant for the life of me install the fglrx driver and get 3D / direct rendering to work.  i want beryl badly, but i cant get this to work!!! i have honestly looked at almost all of the forums on this website and other ones, but glxinfo | grep -i direct remains:

```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

```

i wouldnt call myself a noob, i know a good amount about linux, but NOBODY has responded to ANY of my other forums, so this forum is my last hope...at least give any kind of suggestion, i'm desperate.

---

### Post by calman on 2007-02-06
nevermind, i created these instructions from various pieces of infornation, the only ones that worked for me on the whole internet....if anyone has the same specs as i do, this worked like a charm..

```
# sudo apt-get install xorg-driver-fglrx
# sudo dpkg-reconfigure xserver-xorg (make sure to select the "fglrx" driver instead of "vesa")
# sudo gedit /etc/X11/xorg.conf

Make sure you have the following settings
--------------------------------------------

Section "Device"
	Identifier	"ATI Graphics Adapter"
	Driver		"fglrx"
	Option		"VideoOverlay" "on"
	BusID		"PCI:1:0:0"
EndSection

Section "DRI"
	Group 0
	Mode 0666
EndSection

Section "Extensions"
	Option "Composite" "False"
EndSection

--------------------------------------------
After reboot you can test that the accelerated driver is really used with the following command:

# glxinfo | grep -i direct
direct rendering: Yes
```

---

### Post by Maestro23 on 2007-02-07
I used the guide below to set up my X1600 with no problems.

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

