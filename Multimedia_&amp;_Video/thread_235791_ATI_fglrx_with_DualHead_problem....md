---
title: "ATI fglrx with DualHead problem..."
date: 2006-08-13
forum: Multimedia &amp; Video
---

### Post by Nite23 on 2006-08-13
hello...

this thing really drives me mad... i just spent few hours trying to get dual head to work, tryed a lot of stuff i found on web, but without success...

i use latest version of fglrx, installed via apt-get. graphic card is Radeon 9700 PRO, both displays are CRTs

first fscked up thing was, that when i connected my secondary monitor, my primary monitor ignored whatever resolution settings there were and just switched to default resolution (1024x768@60Hz)... and secondary monitor didn't work at all. so i cleared xorg.conf and used default settings:```
aticonfig --initial=dual-head --screen-layout=right
```...but that didn't help.
then i tryed disabling tv-out:```
aticonfig --force-monitor=notv
```which solved a part of the problem: primary now works fine, but secondary is cloned, instead of a separate desktop...

in Xorg.0.log are following errors:```
(WW) fglrx(0): DALEnableDriverInstance on secondary failed: 2
...
(==) fglrx(1): TMDS coherent mode is enabled
Cannot find any valid mode
(EE) fglrx(1): PreInitModes failed
(EE) fglrx(1): R200PreInit failed

```rest of the file is in attachment

and this is my xorg.conf:```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen         0 "aticonfig-Screen[0]" 0 0
        Screen         "aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]"
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        ModeLine     "1280x1024" 185.6 1280 1376 1600 2024 1024 1024 1028 1079
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[1]"
        ModeLine     "1024x768" 81.5 1024 1064 1168 1352 768 768 770 804
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "ForceMonitors" "notv"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[1]"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
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
                Modes    "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
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
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

```

---

### Post by Ziox on 2006-08-14
> **Nite23 said:**
> hello...

this thing really drives me mad... i just spent few hours trying to get dual head to work, tryed a lot of stuff i found on web, but without success...

i use latest version of fglrx, installed via apt-get. graphic card is Radeon 9700 PRO, both displays are CRTs

first fscked up thing was, that when i connected my secondary monitor, my primary monitor ignored whatever resolution settings there were and just switched to default resolution (1024x768@60Hz)... and secondary monitor didn't work at all. so i cleared xorg.conf and used default settings:```
aticonfig --initial=dual-head --screen-layout=right
```...but that didn't help.
then i tryed disabling tv-out:```
aticonfig --force-monitor=notv
```which solved a part of the problem: primary now works fine, but secondary is cloned, instead of a separate desktop...

in Xorg.0.log are following errors:```
(WW) fglrx(0): DALEnableDriverInstance on secondary failed: 2
...
(==) fglrx(1): TMDS coherent mode is enabled
Cannot find any valid mode
(EE) fglrx(1): PreInitModes failed
(EE) fglrx(1): R200PreInit failed

```rest of the file is in attachment

and this is my xorg.conf:```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen         0 "aticonfig-Screen[0]" 0 0
        Screen         "aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]"
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        ModeLine     "1280x1024" 185.6 1280 1376 1600 2024 1024 1024 1028 1079
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[1]"
        ModeLine     "1024x768" 81.5 1024 1064 1168 1352 768 768 770 804
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "ForceMonitors" "notv"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[1]"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
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
                Modes    "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
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
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

```

Either add this section to your file:

```
Section "ServerFlags"
Option "Xinerama" "true"
EndSection
```

or try using either ATI's Big Desktop or MergedFB.

Reboot, and It should work

Hopefully this helps...

---

### Post by Nite23 on 2006-08-14
that didn't help...

i tryed mergedFB, that works fine with "radeon" open source drivers.

with fglrx the whole virtual desktop is only on one monitor, and it is scrollable by moving cursor to edge of the screen... secondary monitor is disabled...

updated xorg.conf:
```
Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	#Driver      "fglrx"
	Driver      "radeon"
	Option "MergedFB" "true" 
	Option "MonitorLayout" "LCD, CRT"
	Option "CRT2Hsync" "30-186"
	Option "CRT2VRefresh" "50-86"
	Option "OverlayOnCRTC2" "true"
	Option "CRT2Position" "RightOf"
	Option "MetaModes" "1280x1024-1280x1024"
	BusID       "PCI:1:0:0"
	Screen      0
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
		Virtual  2560 1024
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         0 "aticonfig-Screen[0]" 0 0	
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

```

---

### Post by jonathanjg on 2006-08-16
I experienced the same difficulty recently. This problem occurred when I upgraded to the 8.27.10 driver. 

Luckily, I still had the 8.24.8 Ati driver at hand still from a previous install which still worked. Note that when installing the older driver you need to fool it into thinking your xorg version is 6.90, ie.  X_VERSION=x690 ./ati-driver-installer-8.24.8-x86.run --keep, also, if you installed the new driver you may need to make sure that the following files from 8.27.10 are overwritten by the older version :

/usr/lib/xorg/modules/linux/libfglrxdrm.so

also 

/usr/X11R6/lib/modules/drivers/fglrx_drv.o (in fact, take the whole of fglrx-install/x690/usr/X11R6/lib/ and put it in /usr/X11R6/lib)

[the old files you need get left behind after the install if you used the --keep parameter]

---

