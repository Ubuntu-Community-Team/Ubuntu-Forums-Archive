---
title: "Dual-head monitor with ATI Radeon"
date: 2009-01-05
forum: Multimedia Software
---

### Post by pmasiar on 2009-01-05
I tried to read sticky but it is rather poorly organized - IMHO better would be to split it into multiple FAQs specific to groups of related problems, and create a portal page with links to proper parts, as we did in "Programming Talk". But of course do as you wish.. 

FAQ for double-head monitors [http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174) is not even linked from there, AFAICT.

I have dual head video card (with 2 monitors) in my Dell Optiplex GX620. I cannot figure out exact model number. Seems like manufacturer is Topsearch?

Sticker on it says it is D33A27 ACN N136 , MIC: E-G012-05-2436

Google suggests it is Radeon X600, possibly SE, but card does not say that, AFAICT. Can some resident expert confirm model/variant? P/N is 102A62900300

[http://en.wikipedia.org/wiki/Radeon_R600](http://en.wikipedia.org/wiki/Radeon_R600) suggest many variants but it's not obvious to me which one I have (or if should I care).

I tried to run "sudo dkpg-reconfigure xserver-xorg" (terminal started while in Gnome) but it just replaced fglrx drivers with generic one, without asking or detecting like it usually does.

I got overwhelmed by reading [http://ubuntuforums.org/showthread.php?t=31686](http://ubuntuforums.org/showthread.php?t=31686) and not sure which way should I go.

Is there some GUI wizard to set it up? Or my only solution is to update xorg.conf by hand?

I don't need gaming performance, so free drivers are OK if they are stable.

---

### Post by markbuntu on 2009-01-05
Your Xorg.0.log should tell you what gpu it detected if you are using fglrx driver. If you are using fglrx there is the Catalyst Control Center for detecting and configuring your monitors. If you got the fglrx driver from hardware manager or the repos then you need to get the package fglrx-control or something like that.

If you got fglrx with envy or from the ati site the CCC is already installed and is most likely in your menus somewhere.

---

### Post by pmasiar on 2009-01-09
I was a long battle... but I can declare a glorious victory! :-) .. and withdraw all troops! :-)

I am still not exactly sure why my xorg.config works (and it is very unlike the .conf created by aticonfig according to FAQ - that one does not work at all, switches to Clone mode) and it is not perfect (and when I try to eliminate some warnings from log, I break in different, worse way, into Clone mode) but it is 99% OK. Catalyst helped me to make sure that what I said in .conf was accepted.

Last annoying issue what I would be curious if someone seen it: my 'log off' button in main menu bar does not work anymore. It is ignored: to log off/shut down, I need to kill the X (Ctrl-Alt-Backspace) and shtudown from there. So as result I cannot lock my screen. Oh well.

For curious readers, here's what gives me BigDesktop 2048*768 screen, exactly as I want:
```

Section "ServerLayout"

	Identifier     "Main Layout"

	Screen      0  "aticonfig-Screen[0]" 0 0

	InputDevice    "Mouse1" "CorePointer"

	InputDevice    "Keyboard1" "CoreKeyboard"

EndSection



Section "Module"

	Load  "dbe"

	SubSection "extmod"

		Option	    "omit xfree86-dga"

	EndSubSection

	Load  "freetype"

	Load  "dri"

	Load  "glx"

EndSection



Section "InputDevice"

	Identifier  "Keyboard1"

	Driver      "kbd"

	Option	    "AutoRepeat" "500 30"

	Option		"XkbModel" "pc104"

	Option		"XkbLayout" "us"

EndSection



Section "InputDevice"

	Identifier  "Mouse1"

	Driver      "mouse"

	Option	    "Device" "/dev/input/mice"

	Option "CorePointer"

EndSection



Section "Monitor"

	Identifier   "aticonfig-Monitor[0]"

	DisplaySize  380	310

	Option	    "VendorName" "ATI Proprietary Driver"

	Option	    "ModelName" "Generic Autodetecting Monitor"

	Option	    "DPMS" "true"

EndSection





Section "Device"

	Identifier  "aticonfig-Device[0]"

	Driver      "fglrx"

	Option	    "DesktopSetup" "horizontal"

	Option	    "XAANoOffscreenPixmaps" "true"

	BusID       "PCI:1:0:0"

EndSection



Section "Screen"

	Identifier "aticonfig-Screen[0]"

	Device     "aticonfig-Device[0]"

	Monitor    "aticonfig-Monitor[0]"

	DefaultDepth     24

	SubSection "Display"

		Viewport   0 0

		Depth     24

	Modes    "1600x1200@60" "1024x768" "800x600" "640x480"
	EndSubSection

EndSection



Section "DRI"

	Mode 0666

EndSection


```

---

### Post by rukna on 2009-04-20
I've tried using the fglrx driver on my Dell Optiplex as well, but for some reason the screen gets distorted during the login prompt. Tried a few times already, including installing the drivers manually using [1], but no cigar. I've got a dual-head monitor and ATI X600 card, too. Can you help?


```

[1] http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide

[2] #lspci | egrep -i vga
01:00.0 VGA compatible controller: ATI Technologies Inc RV380 [Radeon X600 (PCIE)]

```

Edit 1: FWIW, the issue started when I upgraded to Jaunty. The dual-head setup used to work just fine in Intrepid.

---

