---
title: "Problem with GeForce 177.80 on Ubuntu 8.10 and a second monitor"
date: 2008-11-10
forum: Multimedia Software
---

### Post by DaSilva on 2008-11-10
I have two TFTs connected to my PC. The primary display is connected via DVI, the secondary via VGA. I have installed the 177.80 drivers from nVidia on my Ubuntu 8.10.
The problem with that configuration is that I cannot set the native resolution for the secondary display. If I set it to auto it switches to 1366x768, 1024x768 works, too. If I set it manually in the xorg.conf to 1280x1024 the secondary display stays black.
I had the same problem with kubuntu 8.10.

Segment of my xorg.conf:

> Section "InputDevice" # generated from default Identifier "Keyboard0" Driver "kbd" EndSection
Section "Monitor" Identifier "Monitor0" VendorName "Unknown" ModelName "CRT-0" HorizSync 28.0 - 55.0 VertRefresh 43.0 - 72.0 Option "DPMS" EndSection
Section "Device" Identifier "Device0" Driver "nvidia" VendorName "NVIDIA Corporation" BoardName "GeForce 8800 GTX" EndSection
Section "Screen" Identifier "Screen0" Device "Device0" Monitor "Monitor0" DefaultDepth 24 Option "TwinView" "1" Option "TwinViewXineramaInfoOrder" "DFP-1" Option "metamodes" "CRT: 1024x768 +1280+0, DFP: nvidia-auto-select +0+0" SubSection "Display" Depth 24 EndSubSection EndSection

What can I do to solve this problem?
Thanks in advance.

---

