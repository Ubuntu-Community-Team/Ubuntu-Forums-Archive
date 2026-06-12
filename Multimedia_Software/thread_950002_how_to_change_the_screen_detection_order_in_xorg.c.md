---
title: "how to change the screen detection order in xorg.conf?"
date: 2008-10-16
forum: Multimedia Software
---

### Post by samepate on 2008-10-16
Hello to everybody,

I have configured a dual desktop using aticonfig (I have'nt touched the xorg.conf). My problem is that the "main screen" (the one that ubuntu detects first and asks for the login) is the tv and the second one is crt1. I would like to change that to put my first screen on crt1 and the second screen on TV (wchich seems more obvious).

It seems easy but I have'nt found the answer on the web.

Thanks for any help!

(sorry for my english this is not my mother tongue)

Samy

---

### Post by BMWDriver on 2008-10-17
Visit this page here, towards the bottom is what you want.

[http://wiki.cchtml.com/index.php/Configuring]("http://wiki.cchtml.com/index.php/Configuring")

An excellent website for the ATI drivers. Your English is just fine by the way !

---

### Post by samepate on 2008-10-17
Thank you BMWDriver for your answer,

unfortunately, the command that you suggest is for Big Desktop only (I have dual-head and I would like to keep it).

Quotation from the link you propose:
---------------------------------------------------------------------
Swap monitors on the fly when using big desktop mode

    * Assume you have two monitors already setup correctly (Dual monitor support at Ubuntuforums) 

    aticonfig --swap-monitor --effective=now

    * Note: This only works for big desktop setup. This will swap the contents on the two monitors.
----------------------------------------------------------------------

Does any body know if there is such a command for dual-head? This is very annoying to have TV as first screen since the resolution is not good for text (and I have to start the TV every time I want to log in). I am sure I am not the only one having this problem...

Thanks again for any help!

---

### Post by kpkeerthi on 2008-10-17
[http://www.nvnews.net/vbulletin/showthread.php?t=76764](http://www.nvnews.net/vbulletin/showthread.php?t=76764)

---

### Post by samepate on 2008-10-17
Thank you kpkeerthi for your reply,

I have read your link and I have tried all possible combination in the xorg.conf (as suggested in the link) but I think there is something (several things probably) that I don't understand. My first screen is ALWAYS the TV, whatever I change in the xorg.conf.

Here is my xorg.conf before the change, if somebody can explain to me how to put the TV as second screen, I would be very grateful.

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	Screen         "aticonfig-Screen[1]" RightOf "Default Screen"
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
	Option	    "XkbLayout" "fr"
	Option	    "XkbVariant" "oss"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection


Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:6:0:0"
	Screen      1
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	BusID       "PCI:6:0:0"
EndSection



Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

```

Thanks again for taking the time to reply to me!

---

