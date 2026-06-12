---
title: "Getting Dual-head with Compaq Presario R3000"
date: 2006-06-14
forum: Multimedia &amp; Video
---

### Post by Karbonik on 2006-06-14
I'm going nucking futz.

I've been trying to manually configure my xorg.conf according to 
[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

and it's a no-go.

Running Kubuntu Dapper 6.06 i386 version (the hell with 86-64 until I know what I'm doing, as I am kindof a n00b)


Here's my working xorg.conf, for one screen working, the second (CrystalScan) is connected, on, and registering the top ~20 pixels  of my screen, albeit distorted vertically across the whole monitor (and color's off)

Section "Device"
  identifier "NVIDIA Corporation NV17 [GeForce4 420 Mac 32M/GeForce 440 Go 64M]"
  boardname "nv"
  busid "PCI:1:0:0"
  driver "nv"
  screen 0
EndSection

Section "Monitor"
  identifier "Generic Monitor"
  vendorname "Generic"
  modelname "1280x1024 @ 60 Hz"
  HorizSync 31.5-64.3
  VertRefresh 50-70
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "NVIDIA Corporation NV17 [GeForce4 420 Mac 32M/GeForce 440 Go 64M]"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1152x768@54" "1280x854" "1024x768@60" "1280x960@60" "1024x768@70" "1280x1024@60" "800x600@60" "800x600@56" "640x480@60"
  EndSubSection
EndSection

Section "DRI"
  Mode 0666
EndSection

Section "device" #   
  identifier "device1"
  boardname "nv"
  busid "PCI:1:0:0"
  driver "nv"
  screen 1
EndSection

Section "screen" #   
  identifier "screen1"
  device "device1"
  defaultdepth 24
  monitor "monitor1"
  SubSection "Display"
    depth 24
    modes "800x600@60" "832x624@75" "800x600@85" "1024x768@75" "800x600@75" "1024x768@70" "800x600@72" "1024x768@60" "800x600@56" "1024x768@43" "640x480@85" "1152x768@54" "640x480@75" "1280x854" "640x480@72" "1280x960@60" "640x480@60" "1280x1024@60"
  EndSubSection
EndSection

Section "monitor" #   
  identifier "monitor1"
  vendorname "Gateway"
  modelname "Gateway CrystalScan 500"
  HorizSync 30-64
  VertRefresh 50-100
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  gamma 1.0
EndSection

Section "ServerLayout"
  Identifier "Dual Layout"
  screen 0 "Default Screen" 0 0
#  screen 1 "screen1" leftof "Default Screen"
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
  InputDevice "Synaptics Touchpad"
EndSection

Section "ServerFlags"
#  option "Xinerama" "false"
EndSection





I thought maybe to update the Nvidia drivers, but that's also causing problems with a non-compiled kernel for this, and asking for cc.  

I'm thinking that because they are different resolutions, I can't use Xinerama.  That's fine - the solution for having independent desktops is certainly viable.

---

### Post by karthik085 on 2006-06-27
With nv driver, I didn't have any success. But, with proprietary nvidia driver, I had. Try that.

[QUOTE=Karbonik]I'm going nucking futz.

I've been trying to manually configure my xorg.conf according to 
[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

and it's a no-go.

Running Kubuntu Dapper 6.06 i386 version (the hell with 86-64 until I know what I'm doing, as I am kindof a n00b)


Here's my working xorg.conf, for one screen working, the second (CrystalScan) is connected, on, and registering the top ~20 pixels  of my screen, albeit distorted vertically across the whole monitor (and color's off)

Section "Device"
  identifier "NVIDIA Corporation NV17 [GeForce4 420 Mac 32M/GeForce 440 Go 64M]"
  boardname "nv"
  busid "PCI:1:0:0"
  driver "nv"
  screen 0
EndSection

Section "Monitor"
  identifier "Generic Monitor"
  vendorname "Generic"
  modelname "1280x1024 @ 60 Hz"
  HorizSync 31.5-64.3
  VertRefresh 50-70
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "NVIDIA Corporation NV17 [GeForce4 420 Mac 32M/GeForce 440 Go 64M]"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1152x768@54" "1280x854" "1024x768@60" "1280x960@60" "1024x768@70" "1280x1024@60" "800x600@60" "800x600@56" "640x480@60"
  EndSubSection
EndSection

Section "DRI"
  Mode 0666
EndSection

Section "device" #   
  identifier "device1"
  boardname "nv"
  busid "PCI:1:0:0"
  driver "nv"
  screen 1
EndSection

Section "screen" #   
  identifier "screen1"
  device "device1"
  defaultdepth 24
  monitor "monitor1"
  SubSection "Display"
    depth 24
    modes "800x600@60" "832x624@75" "800x600@85" "1024x768@75" "800x600@75" "1024x768@70" "800x600@72" "1024x768@60" "800x600@56" "1024x768@43" "640x480@85" "1152x768@54" "640x480@75" "1280x854" "640x480@72" "1280x960@60" "640x480@60" "1280x1024@60"
  EndSubSection
EndSection

Section "monitor" #   
  identifier "monitor1"
  vendorname "Gateway"
  modelname "Gateway CrystalScan 500"
  HorizSync 30-64
  VertRefresh 50-100
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  gamma 1.0
EndSection

Section "ServerLayout"
  Identifier "Dual Layout"
  screen 0 "Default Screen" 0 0
#  screen 1 "screen1" leftof "Default Screen"
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
  InputDevice "Synaptics Touchpad"
EndSection

Section "ServerFlags"
#  option "Xinerama" "false"
EndSection





I thought maybe to update the Nvidia drivers, but that's also causing problems with a non-compiled kernel for this, and asking for cc.  

I'm thinking that because they are different resolutions, I can't use Xinerama.  That's fine - the solution for having independent desktops is certainly viable.[/QUOTE]

---

### Post by This_is_me on 2006-07-08
Install the build-essential package, then you should be able to use the binary nvidia driver. GCC (one of the dependents of the build-essential package) is needed to compile things. (also the kernel headers and other stuff.)

---

### Post by jstroot on 2006-07-20
Does anyone know if it's possible to get any resolution better than 1280x800?
I think max resolution is supposed to be 1680x1050.

I've been trying with no success.

-jstroot

---

