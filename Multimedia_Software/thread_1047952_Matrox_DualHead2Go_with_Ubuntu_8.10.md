---
title: "Matrox DualHead2Go with Ubuntu 8.10"
date: 2009-01-22
forum: Multimedia Software
---

### Post by akoz002 on 2009-01-22
Hi, I'm using a DELL Latitude D620 laptop with Ubuntu 8.10. I have an NVIDIA Quadro NVS 110M card, and I use X-Server settings to communicate with the DualHead2Go device. I have an analog version, and as I understand it supports:

2048 x 768 @ 60, 75, 85Hz
2560 x 1024 @ 60Hz

([http://www.matrox.com/graphics/en/products/gxm/dh2go/](http://www.matrox.com/graphics/en/products/gxm/dh2go/) , then "Specifications", then "Click here for complete list" for the Analog version)

Previously, in Ubuntu 8.04 I could set the mode in the xorg.conf file, using 2048 x 768, and it worked fine. Now, in Ubuntu 8.10, the right side output only shows half of what it should. The left side output is fine. On the right side output, the rightmost half is black, but I can still move the mouse pointer over it and see the pointer. The 2560 x 1024 mode does not work. Here are extracts from "xorg.conf":

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Matrox"
    HorizSync       31.5 - 91.1
    VertRefresh     60.0 - 85.0
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 2048x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "ServerLayout"
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
# commented out by update-manager, HAL is now used
#    InputDevice    "Generic Keyboard"
# commented out by update-manager, HAL is now used
#    InputDevice    "Configured Mouse"
# commented out by update-manager, HAL is now used
#    InputDevice    "Synaptics Touchpad"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
EndSection

This configuration worked previously. I can also see in "Xorg.0.log":

...
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Device1"
...
(--) NVIDIA(1): Connected display device(s) on Quadro NVS 110M at PCI:1:0:0:
(--) NVIDIA(1):     Matrox (CRT-0)
(--) NVIDIA(1):     LPL (DFP-0)
(--) NVIDIA(1): Matrox (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(1): LPL (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(1): LPL (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(1): Display Device found referenced in MetaMode: CRT-0
(II) NVIDIA(1): Assigned Display Device: CRT-0
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "CRT:2048x768+0+0"
(II) NVIDIA(1): Virtual screen size determined to be 2048 x 768
...
(II) NVIDIA(1): Setting mode "CRT:2048x768+0+0"

So it seems this mode is valid and it is being set. I'm also sure the connecting cables are not faulty. Is there anything at all anyone could suggest please?

---

### Post by Hans Bogar on 2009-01-24
Hi akoz002,

I have a Triplehead2Go in dualhead mode connected to a nvidia videocard.
I've never been able to get both my monitors to work in Twinview with the nvidia driver. That the reason I've bought the Triplehead2Go.

To connect this properly, the xorg.conf should be configured to only ONE monitor, no twinview or Xinerama configuration options whatsoever. 
Only to switch twinview or Xinerama off ;)

Because with a Dualhead2Go or a Triplehead2Go connected, xorg.conf sees only ONE big monitor with 2560x1024 or 3840x1024 dimensions...

In the server layout of your xorg.conf I see "Screen 1 "Screen1" RightOf "Screen0"" That is an option which have to do with Twinview/Xinerama.
Maybe you have to disable this line and other lines like these ...

Hope this helps.

---

