---
title: "dual graphic cards"
date: 2009-05-07
forum: Multimedia Software
---

### Post by sinclair86 on 2009-05-07
Ok so I am a little confused with everything Ive gone thru and everything I have read (xrandr, xinemia, ccc) Im trying to dual monitor with 2 ati graphic cards 7200 and 9200

```
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:01.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
02:02.0 VGA compatible controller: ATI Technologies Inc Radeon R100 QD [Radeon 7200] (rev 87)

```

(I gave up on Xpress. Lol that a whole story in itself)

heres my xorg (the parts that matter)

```

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "SNY"
	ModelName    "SDM-HS53"
	HorizSync    28.0 - 52.0
	VertRefresh  57.0 - 63.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "DEL"
	ModelName    "DELL 1907FP"
	HorizSync    30.0 - 81.0
	VertRefresh  56.0 - 76.0
	Option	    "DPMS"
	#DisplaySize	  380   300	# mm
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Module"
	Load  "dbe"
	Load  "dri"
	Load  "extmod"
	Load  "record"
	Load  "dri2"
	Load  "glx"
EndSection

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen1" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
#	Screen      1  "Screen1" RightOf "Screen0"
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "ati"
	VendorName  "ATI Technologies Inc"
	BoardName   "Radeon R100 QD [Radeon 7200]"
	BusID       "PCI:2:2:0"
EndSection

Section "Device"
	Identifier  "Card1"
	Driver      "ati"
	VendorName  "ATI Technologies Inc"
	BoardName   "RV280 [Radeon 9200 PRO]"
	BusID       "PCI:2:1:0"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
#	Option "Xinerama"	"true"
EndSection
```

when I uncomment 

```
Screen      1  "Screen1" RightOf "Screen0"
```

both screens go blank but if I change 
> 
Screen      0  "Screen1" 0 0

to Screen0 or Screen1 and then crtl alt bkspc the screen that in there loads. Any suggestions? Im on ubuntu 9.04

ive tried ccc but on reboot xorg fails to load same with xienima

---

