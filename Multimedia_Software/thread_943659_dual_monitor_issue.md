---
title: "dual monitor issue"
date: 2008-10-10
forum: Multimedia Software
---

### Post by anystupidname on 2008-10-10
Could somebody please help? I'm so close to having it the way I want it. Right now it is quite weird actually. I have 2 completely separate desktops and taskbars on each monitor but my mouse can transition from one monitor to the other. I just can't drag applications across...

ATI HD 2400 XT
fglrx binary driver downloaded from ati.amd.com
Dell P991
Dell M993s
(these two monitors are almost identical except for refresh rates and external appearance)

xorg.conf
```

#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" LeftOf "Screen0"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "GLcore"
	Load  "glx"
	Load  "dbe"
	Load  "v4l"
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
	VendorName   "Dell"
	ModelName    "Dell M993s"
	HorizSync    30.0 - 96.0
	VertRefresh  50.0 - 160.0
	Gamma        1
	ModeLine     "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
	ModeLine     "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
	ModeLine     "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
	ModeLine     "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
	ModeLine     "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	ModeLine     "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
	ModeLine     "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
	ModeLine     "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
	ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	ModeLine     "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
	ModeLine     "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
	ModeLine     "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
	ModeLine     "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
	ModeLine     "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
	ModeLine     "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	ModeLine     "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
	ModeLine     "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
	ModeLine     "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
	ModeLine     "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	ModeLine     "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
	ModeLine     "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	ModeLine     "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
	ModeLine     "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
	ModeLine     "2048x1536@60" 266.9 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Dell"
	ModelName    "Dell P991"
	HorizSync    30.0 - 107.0
	VertRefresh  48.0 - 120.0
	Gamma        1
	ModeLine     "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
	ModeLine     "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
	ModeLine     "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
	ModeLine     "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
	ModeLine     "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	ModeLine     "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
	ModeLine     "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
	ModeLine     "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
	ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	ModeLine     "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
	ModeLine     "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
	ModeLine     "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
	ModeLine     "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
	ModeLine     "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
	ModeLine     "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	ModeLine     "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
	ModeLine     "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
	ModeLine     "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
	ModeLine     "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	ModeLine     "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
	ModeLine     "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@85" 229.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1792x1344@75" 261.0 1792 1888 2104 2456 1344 1345 1348 1417 -hsync +vsync
	ModeLine     "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	ModeLine     "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
	ModeLine     "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
	ModeLine     "2048x1536@60" 266.9 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
EndSection

Section "Device"
	Identifier  "Device0"
	Driver      "fglrx"
	BoardName   "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "Device1"
	Driver      "fglrx"
	BoardName   "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Device0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1600x1200@60" "1600x1200@75" "1600x1200@65" "1600x1200@70" "1400x1050@75" "1792x1344@60" "1400x1050@60" "1856x1392@60" "1280x960@75" "1920x1440@60" "1280x1024@60" "2048x1536@60" "1280x1024@85" "1280x960@85" "1280x960@60" "1280x1024@75" "1152x864@75" "1024x768@43" "1024x768@60" "1024x768@70" "1024x768@75" "1024x768@85" "832x624@75" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Device1"
	Monitor    "Monitor1"
	DefaultDepth     24
	SubSection "Display"
		Virtual   3200 1200
		Depth     24
		Modes    "1600x1200@75" "1600x1200@70" "1600x1200@60" "1600x1200@85" "1600x1200@65" "1792x1344@75" "1400x1050@75" "1792x1344@60" "1400x1050@60" "1856x1392@60" "1280x960@75" "1920x1440@60" "1280x1024@60" "2048x1536@60" "1280x1024@85" "1280x960@85" "1280x960@60" "1280x1024@75" "1152x864@75" "1024x768@43" "1024x768@60" "1024x768@70" "1024x768@75" "1024x768@85" "832x624@75" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56"
	EndSubSection
EndSection


```

lshw -C video
```

  *-display
       description: VGA compatible controller
       product: Radeon HD 2400 XT
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: driver=fglrx_pci latency=0 module=fglrx
```

lspci
```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 2400 XT (prog-if 00 [VGA controller])
        Subsystem: Dell Unknown device 0d02
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Region 2: Memory at fe9f0000 (64-bit, non-prefetchable) [size=64K]
        Region 4: I/O ports at dc00 [size=256]
        Expansion ROM at fea00000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 3
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [58] Express Legacy Endpoint IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
                Device: Latency L0s <4us, L1 unlimited
                Device: AtnBtn- AtnInd- PwrInd-
                Device: Errors: Correctable- Non-Fatal- Fatal+ Unsupported-
                Device: RlxdOrd+ ExtTag+ PhantFunc- AuxPwr- NoSnoop+
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed 2.5Gb/s, Width x16, ASPM L0s L1, Port 0
                Link: Latency L0s <64ns, L1 <1us
                Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
                Link: Speed 2.5Gb/s, Width x16
        Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000

```

---

### Post by jamesrl on 2008-10-10
I have a somewhat similar setup (ATI HD2600) and was able to get everything working with compiz.  I also use the proprietary ati monitors, and I think I had to go through aticonfig a bit at the beginning.

Read through "sudo aticonfig --help" and you should start getting somewhere.  You probably want something like:
```
aticonfig --dtop=horizontal --overlay-on=1
```

For reference here's my xorg.conf which has several things that I needed to get compiz working.
```
# xorg.conf (X.Org X Window System server configuration file)

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        Option      "AIGLX" "on"
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
#       Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
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
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "XAANoOffscreenPixmaps" "on"
	Option	    "UseFastTLS" "1"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "off"
	Option	    "EnablePrivateBackZ" "yes"
	Option	    "TexturedVideo" "True"
	Option	    "TexturedVideoSync" "True"
	Option	    "OverlayOnCRTC2" "1"
	Option	    "BackingStore" "on"
	Option	    "Textured2D" "on"
	Option	    "TexturedXrender" "off"
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
		Modes    "1920x1200"
	EndSubSection
EndSection

Section "Extensions"
	Option	    "RENDER" "Enable"
	Option	    "DAMAGE" "Enable"
	Option	    "Composite" "Enable"
EndSection

```

Also when using aticonfig make sure that there actually is an executable there.  I had a Dell pre-installed ubuntu setup that basically had aticonfig as a bash script that just exited (test and see that "sudo aticonfig --help display something")

---

### Post by anystupidname on 2008-10-16
I've been putzing around with this xorg.conf forever and finally got what I want short of two things. Dual monitor and compiz is working but:

-The left monitor's resolution is huge
-KDE only thinks there is one actual monitor

Here is my xorg.conf

```

#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen	0	 "Screen0" 0 0
#	Screen	1	"Screen1" LeftOf "Screen0"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "GLcore"
	Load  "glx"
	Load  "dbe"
	Load  "v4l"
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
	VendorName   "Dell"
	ModelName    "Dell M993s"
	HorizSync    30.0 - 96.0
	VertRefresh  50.0 - 160.0
	Gamma        1
	ModeLine     "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
	ModeLine     "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
	ModeLine     "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
	ModeLine     "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
	ModeLine     "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	ModeLine     "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
	ModeLine     "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
	ModeLine     "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
	ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	ModeLine     "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
	ModeLine     "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
	ModeLine     "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
	ModeLine     "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
	ModeLine     "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
	ModeLine     "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	ModeLine     "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
	ModeLine     "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
	ModeLine     "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
	ModeLine     "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	ModeLine     "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
	ModeLine     "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	ModeLine     "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
	ModeLine     "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
	ModeLine     "2048x1536@60" 266.9 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Dell"
	ModelName    "Dell P991"
	HorizSync    30.0 - 107.0
	VertRefresh  48.0 - 120.0
	Gamma        1
	ModeLine     "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
	ModeLine     "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
	ModeLine     "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
	ModeLine     "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
	ModeLine     "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	ModeLine     "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
	ModeLine     "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
	ModeLine     "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
	ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	ModeLine     "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
	ModeLine     "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
	ModeLine     "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
	ModeLine     "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
	ModeLine     "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
	ModeLine     "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	ModeLine     "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
	ModeLine     "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
	ModeLine     "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
	ModeLine     "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	ModeLine     "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
	ModeLine     "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@85" 229.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1792x1344@75" 261.0 1792 1888 2104 2456 1344 1345 1348 1417 -hsync +vsync
	ModeLine     "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	ModeLine     "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
	ModeLine     "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
	ModeLine     "2048x1536@60" 266.9 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
EndSection

Section "Device"
	Identifier  "Device0"
	Driver      "fglrx"
	Option		"UseFBDev"	"true"
	Option		"MergedFB"	"true"
	Option		"MonitorLayout"	"CRT,CRT"
	Option		"DesktopSetup"	"horizontal"
	Option		"OverlayOnCRTC2"	"true"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "Device1"
	Driver      "fglrx"
	BoardName   "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Device0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1600x1200@60" "1600x1200@75" "1600x1200@65" "1600x1200@70" "1400x1050@75" "1792x1344@60" "1400x1050@60" "1856x1392@60" "1280x960@75" "1920x1440@60" "1280x1024@60" "2048x1536@60" "1280x1024@85" "1280x960@85" "1280x960@60" "1280x1024@75" "1152x864@75" "1024x768@43" "1024x768@60" "1024x768@70" "1024x768@75" "1024x768@85" "832x624@75" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Device1"
	Monitor    "Monitor1"
	DefaultDepth     24
	SubSection "Display"
		Viewport	0 0
		Depth     24
		Modes    "1600x1200@75" "1600x1200@70" "1600x1200@60" "1600x1200@85" "1600x1200@65" "1792x1344@75" "1400x1050@75" "1792x1344@60" "1400x1050@60" "1856x1392@60" "1280x960@75" "1920x1440@60" "1280x1024@60" "2048x1536@60" "1280x1024@85" "1280x960@85" "1280x960@60" "1280x1024@75" "1152x864@75" "1024x768@43" "1024x768@60" "1024x768@70" "1024x768@75" "1024x768@85" "832x624@75" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56"
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option	"Composite"	"Enable"
EndSection

```

Any assistance would be much appreciated!

P.S. The video card is an ATI HD 2400 XT

---

### Post by anystupidname on 2008-10-16
Thanks that got me a little closer.
[http://ubuntuforums.org/showthread.php?t=949953](http://ubuntuforums.org/showthread.php?t=949953)

---

### Post by BMWDriver on 2008-10-16
Try this link here : [http://wiki.cchtml.com/index.php/Configuring]("http://wiki.cchtml.com/index.php/Configuring")

There is a tremendous amount of info about the ATI drivers in many other parts of the site.

---

### Post by overdrank on 2008-10-17
> **anystupidname said:**
> Thanks that got me a little closer.
[http://ubuntuforums.org/showthread.php?t=949953](http://ubuntuforums.org/showthread.php?t=949953)

Threads merged :)

---

### Post by anystupidname on 2008-10-17
@BMWdriver: Thanks but that resulted in no change. I had tried that before unsuccessfully, but I gave it another go.

@overdrank: I created the new thread so somebody would actually answer. With this type of problem, it is difficult to get an answer unless a variety of people answer you which won't happen now.

---

### Post by JPorter on 2008-10-31
Are you using Catalyst 8.10?  It's in the repos for Intrepid, no need to download manually from ATI.

You can set the behavior of your multi-monitor setup using Catalyst Control Center, xorg.conf is no longer used for this stuff for the ATI binary drivers.


Also, you should check with the folks on the forums at Phoronix first for video card driver issues... some of the ATI developers participate there and give direct assistance.

---

