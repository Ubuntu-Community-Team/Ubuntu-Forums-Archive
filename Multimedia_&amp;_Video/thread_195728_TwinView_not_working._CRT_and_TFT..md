---
title: "TwinView not working. CRT and TFT."
date: 2006-06-13
forum: Multimedia &amp; Video
---

### Post by Jungleboss on 2006-06-13
I am trying to setup a twinview configuration with a 19" tft and a quite old 15" crt (Eizo F35). KDE is loading (and both monitors are active) but stops at "loading the desktop". My graphics card is GeForce 6800 GT (AGP) and i am using Kubuntu Dapper. Have installed Nvidia-glx drivers and working in single monitor mode and in multi monitor mode (when using Xinarama, not TwinView).

I've tried both 'busid "PCI:1:0:0"' and 'busid "AGP:1:0:0"', with the same result.

Xorg.conf:

Section "ServerLayout"
  Identifier "Default Layout"
  Screen 0 "Default Screen" 0 0
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
Option "Xinerama" "Off"
EndSection

Section "Device"
identifier "NVIDIA Corporation NV40 [GeForce 6800 GT]"
Driver "nvidia"
BoardName "NVIDIA GeForce 6800 GT"
VendorName "Videocard vendor"
Option "TwinView" "1"
busid "PCI:1:0:0"
Option "NoPowerConnectorCheck"
Option   "Metamodes" "1024x768,1024x768"
Option "NvAGP" "2"
Option "RenderAccel" "0"
Option "SecondMonitorHorizSync" "30-82"
Option "SecondMonitorVertRefresh" "56-76"
# Option "ConnectedMonitor" "CRT, DFP"
Option "TwinViewOrientation" "RightOf"
#Option     "AllowGLXWithComposite"
#Option "NoTwinViewXineramaInfo"
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "NVIDIA Corporation NV40 [GeForce 6800 GT]"
  Monitor "Eizo F35"
  DefaultDepth 24
  SubSection "Display"
 Depth 8
Modes "1024x768"
EndSubsection
Subsection "Display"
Depth 16
Modes "1024x768"
EndSubsection
Subsection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection

Section "monitor"
  identifier "Eizo F35"
  vendorname "Eizo"
  modelname "Eizo F35"
  HorizSync 27.0-70.0
  VertRefresh 50.0-120.0
 Option "dpms"
EndSection

---

### Post by Rosenrot on 2006-07-28
im only good with xinerama but at

Option "TwinView" "1"

shouldn't taht 1 be on? without quotations?

---

