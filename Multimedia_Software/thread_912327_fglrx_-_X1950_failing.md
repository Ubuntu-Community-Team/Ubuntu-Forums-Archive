---
title: "fglrx - X1950 failing"
date: 2008-09-06
forum: Multimedia Software
---

### Post by Pale01 on 2008-09-06
Hi.

I had dual screen setup working with restricted drivers just fine with ATI X1950XTX card. I got one bigger screen (Samsung SyncMaster 950b) and I changed on single display. After that I have had big problems...

 For some reason it seems that card or restricted drivers "remember" the old setup. Booting up with ati is fine but I won't get 3D and speed. I've been playing with restricted drivers and xorg.conf (uninstalling, installing, setting options, etc...) but with fglrx the best (mostly I don't even get to the kdm) I get is desktop that goes black with big mouse cursor. When I get to the point where desktop is visible I do have time enough to see that the desktop is large - like it was on dual display setup. With non restricted drivers desktop resolution is fine. I've been playing with restricted drivers and xorg.conf (uninstalling, installing, setting options, etc...) I have set resolution right in xorg.conf. I have run aticonfig --initial -f. I have done many things... but propietary drivers just don't seem to work right any more. Any thoughts are appreciated.

Attached "basic" xorg.conf that works:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fi"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Extensions"
EndSection
```

And my latest try that doesn't work:
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "fi"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "ServerFlags"
Option "AIGLX" "off"
EndSection
```

As I mentioned I have already tried quite a many things but any help would be nice :KS

Thanks

Kubuntu Hardy Heron 8.04
Asus P5W DH Deluxe
ATI X1950XTX

---

### Post by CHaoSlayeR on 2008-12-04
Hi Pale01,

have you tried the **aticonfig** utility? To set up the basic (horizontal) xorg.conf for dual-head type:
```

aticonfig --initial=dual-head --screen-layout=right

```

Specifiy **right** or **left** depending on where your second display is positioned relative to the first one.

That should give you a basic xorg.conf that "should" work. If not post again.

Greetz and good luck,

C]-[aoZ

---

