---
title: "quad head (4 monitor) ATI X1300 and X1900"
date: 2008-10-26
forum: Multimedia Software
---

### Post by ryandale56 on 2008-10-26
I have two video cards ATI X1300 and X1900.  Both have dual output.  I cannot for the life of me get 4 monitors working in ubuntu.

Here is my xorg.conf:

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Option	    "Clone"	"off"
	Option	    "Xinerama"  "off"
	Screen      0  "Screen0" 0 0
	Screen	    1  "Screen1" RightOf "Screen0"
EndSection

Section "Files"
EndSection

Section "Module"
	Load	"dbe"
	Load	"extmod"
	Load	"glx"
	Load	"freetype"
	Load	"dri"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "Monitor2"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Device0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Option	"DesktopSetup"	"horizontal"
EndSection

Section "Device"
        Identifier  "Device1"
        Driver      "fglrx"
        BusID       "PCI:2:0:0"
	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Device0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
        Identifier "Screen1"
        Device     "Device1"
        Monitor    "Monitor2"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Extensions"
	Option "Composite" "1"
EndSection

Section "Serverflags"
	Option "AIGLX" "off"
EndSection


```


And here is a "cat Xorg.0.log | grep "EE"":
```

	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(1): Multiview is not supported on the first adapter; this screen will now shutdown.
(EE) fglrx(1): PreInit failed

```


With the xorg.conf above I do have dual monitor working (its using the X1900).  But my other two monitors that are connect to the X1300 are black.


Does anybody have a setup like this working?  Please help if you can.  Thanks!

---

### Post by ryandale56 on 2008-10-28
Ok I fixed this problem.

Here is the solution: install Windows XP.  Everything works.

---

