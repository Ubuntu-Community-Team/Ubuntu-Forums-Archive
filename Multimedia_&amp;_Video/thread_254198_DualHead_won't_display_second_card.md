---
title: "DualHead won't display second card"
date: 2006-09-09
forum: Multimedia &amp; Video
---

### Post by richmulhern on 2006-09-09
I've read all the stickies, and tried everything but I cannot get my second monitor to work. It's an ATI Radeon 9550 card. The monitor just displays 'No Input'. I've [installed the ATI drivers]("http://ubuntuforums.org/showthread.php?t=204910") and searched the forums and google, but nothing seems to get getting it. When i 'fglrxinfo' I still get:

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```

My xorg.conf looks like this:

```
Section "Monitor"
	Identifier   "Monitor0"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "Monitor1
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI0"
	Driver      "ati"
	BusID       "PCI:0:13:0"
	Screen	    0
EndSection

Section "Device"
	Identifier  "ATI1
	Driver      "ati"
	BusID  	    "PCI:1:0:1"
	Screen	    1
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"ATI0"
	Monitor		"Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"ATI1"
	Monitor		"Monitor1"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection

EndSection

Section "ServerLayout"
	Identifier	"DualHead"
	Screen		"Screen0"
	Screen		"Screen1" LeftOf "Screen0"

	Option	    "Xinerama" "on"
	Option	    "Clone" "off"

	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
```

This is what I get when I 'lpsci':
```

0000:00:0d.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200]  (rev 01)
0000:00:0d.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200] (Secondary) (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 ?? [Radeon 9550] (Secondary)

```

The Radeon 9200 works fine, just not the Radeon 9550. Thanks, and I appreciate the help.

---

### Post by wieman01 on 2006-09-09
This is an example of my xorg.conf file... Check it out:

[http://www.ubuntuforums.org/showthread.php?t=237640]("http://www.ubuntuforums.org/showthread.php?t=237640")

One obvious thing in your file is this line:
> BusID       "PCI:0:13:0"
Both devices have to use the exact same pipe as far as I remember. I am using a laptop so I cannot tell for sure, but you might give it a try.

---

### Post by richmulhern on 2006-09-09
Hmm they have to be on the same card? Are you sure? I've read plenty of places that seem to insist they don't. On that note though with this xorg.conf I was able to get both monitors to display, but they both displayed the same thing. Also when I was outside of X it wanted to display the terminal through the other video card. Is there any way to adjust so the terminal also uses this card and make them not clone? 

```

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"	
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "ati"
	BusID      "PCI:1:0:1"
	Screen      1
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         	0 "aticonfig-Screen[0]" 0 0
	Screen		1 "aticonfig-Screen[1]" LeftOf "aticonfig-Screen[0]"

	Option	    "Xinerama" "on"
	Option	    "Clone" "off"

	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

```

If I change either monitor to
```
BusID       "PCI:0:13:0"
```

I get nada on the second screen. It will always just display on the first one.

---

### Post by richmulhern on 2006-09-09
And a few tweaks later... it works!! I thought it'd never happen! :eek: 

```

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"	

EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:0:13:0"
	#Screen      1
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         	"aticonfig-Screen[0]" 0 0
	Screen		"aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]"

	Option	    "Xinerama" "on"
	Option	    "Clone" "off"

	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

```

---

### Post by Ziox on 2006-09-09
how can their be two different BusID's for one single card?

---

### Post by richmulhern on 2006-09-09
Ziox, I have 2 cards both with 2 outputs. I'm assuming each BusID represents an output. So I have 0:13:0, 0:13:1, 1:0:0, and 1:0:1

```

0000:00:0d.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200]  (rev 01)
0000:00:0d.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200] (Secondary) (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 ?? [Radeon 9550] (Secondary)

```

Maybe, I'm wrong though and that's why I couldn't get it to work :wink:

---

### Post by Ziox on 2006-09-10
> **richmulhern said:**
> Ziox, I have 2 cards both with 2 outputs. I'm assuming each BusID represents an output. So I have 0:13:0, 0:13:1, 1:0:0, and 1:0:1

```

0000:00:0d.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200]  (rev 01)
0000:00:0d.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200] (Secondary) (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 ?? [Radeon 9550] (Secondary)

```

Maybe, I'm wrong though and that's why I couldn't get it to work :wink:

Ok, I was unaware of you having two cards...thanks for clearing that up :-D

---

