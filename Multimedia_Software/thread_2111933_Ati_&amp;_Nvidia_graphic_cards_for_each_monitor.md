---
title: "Ati &amp; Nvidia graphic cards for each monitor"
date: 2013-02-03
forum: Multimedia Software
---

### Post by pinochan on 2013-02-03
Hello all.

It's one week since I have been trying to configure my dual screen desktop. I followed thousands of guides but with no luck.

I have two graphic cards:
(lspci result)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Barts XT [ATI Radeon HD 6800 Series]
02:00.0 VGA compatible controller: NVIDIA Corporation G71 [GeForce 7900 GS] (rev a1)

And two screens. AMD is giving signal to the first screen, and the desktop is shown correctly.
NVidia is supposed to give signal to the secondary screen, but I'm only able to see "Ubunto" logo, and all consoles (Crtl+alt+{F1-F6}). 

It is a clear installation of ubuntu on a new SSD.

This is my xorg.conf

Section "ServerLayout"
Identifier "aticonfig Layout"
Screen 0 "aticonfig-Screen[0]-0" 0 0
Screen "Screen0" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
Option "Xinerama" "off"
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[0]-0"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
Option "DPMS" "true"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Unknown"
ModelName "Unknown"
HorizSync 28.0 - 33.0
VertRefresh 43.0 - 72.0
Option "DPMS"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]-0"
Driver "fglrx"
Option "SwapScreens" "off"
BusID "PCI:1:0:0"
EndSection

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BusID "PCI:2:0:0"
Screen 1
EndSection

Section "Screen"
Identifier "aticonfig-Screen[0]-0"
Device "aticonfig-Device[0]-0"
Monitor "aticonfig-Monitor[0]-0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Depth 24
EndSubSection
EndSection

These parameters are taken by unplugging the graphical cards and configuring each card separately. Once for ADM and another for Nvidia.
Afterwards I used aticonfig tool:
aticonfig --initial=dual-head --screen-layout=left
and with the result xorg.conf modified the parameters to mach my hardware.

I tried with xinerama on and off, but nothing happens.
I don’t have any active additional device.
If I enter catalyst control center, It doesnt detect secondary screen(nvidia)
(With Windows, catalyst control center, detects both screens)
It seems I cant have nvidia driver and Amd simultaneously.

Do you know if it is possible to set up both screens using different graphic cards? What am i doing rong?

Thank you!

---

