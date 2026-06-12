---
title: "nVidia with ASUS MS227"
date: 2010-03-13
forum: Multimedia Software
---

### Post by robfindlay on 2010-03-13
I just upgraded to an ASUS MS227 on a Ubuntu 9.10 box with a "NV34 [GeForce FX 5200] (rev a1)" video card. 

Here's the problem, the only two resolutions it will work in is either 1900x1200 OR 1440x900. 

Anything in between shoves the display about 5 inches to the left, so far over that it's not correctable by the monitors own horizontal control. 

This is my xorg.conf: 
 
 ```
Section "Screen"
 Identifier "Default Screen"
 Device "Configured Video Device"
 Monitor "Configured Monitor"
 SubSection "Display"
 Depth 16
 Modes "1280x1024" "1024x768"
 Option "AddARGBGLXVisuals" "True"
 EndSubSection

 Option "AddARGBGLXVisuals" "True"
 Defaultdepth 24
 EndSection
 Section "Module"
 Load "glx"
 Load "GLcore"
 Load "v4l"
 EndSection
 Section "Device"
 Identifier "Configured Video Device"
 Boardname "vesa"
 Busid "PCI:1:0:0"
 Driver "nvidia"
 Screen 0
 EndSection
 
 Section "Device"
 Identifier "Device0"
 BoardName "Generic Geforce 5500"
 Driver "nvidia"
 Vendorname "NVIDIA Corporation"
 Option "DualHead" "1"
 Option "ShadowFB" "1"
 Option "FPScale" "1"
 Option "TwinView" "True"
 Option "TwinViewOrientation" "RightOf"
 Option "UseEdidFreqs" "True"
 Option "Metamodes" "1024x768,1024x768"
 Option "UseDisplayDevice" "DFP"
 EndSection
 
 Section "Device"
 Identifier "Videocard0"
 Driver "nv"
 VendorName "NVIDIA Corporation"
 BoardName "GeForce 7600 GT"
 EndSection
 
 Section "InputDevice"
 Identifier "Generic Keyboard"
 Driver "kbd"
 Option "XkbRules" "xorg"
 Option "XkbModel" "pc105"
 Option "XkbLayout" "us"
 EndSection

 Section "InputDevice"
 Identifier "Configured Mouse"
 Driver "mouse"
 EndSection
 Section "ServerLayout"
 Identifier "Default Layout"
 screen 0 "Default Screen" 0 0
 EndSection
 
 Section "Extensions"
 Option "Composite" "Enable"
 EndSection

```

The two extremes are generally driving me batty, does anyone have any advice? 

Thanks muchly in advance! 

-Rob

---

### Post by robfindlay on 2010-03-14
Any thoughts on this one guys?

---

### Post by robfindlay on 2010-03-15
Guys ANYTHING here? Thoughts? 

> **robfindlay said:**
> I just upgraded to an ASUS MS227 on a Ubuntu 9.10 box with a "NV34 [GeForce FX 5200] (rev a1)" video card. 

Here's the problem, the only two resolutions it will work in is either 1900x1200 OR 1440x900. 

Anything in between shoves the display about 5 inches to the left, so far over that it's not correctable by the monitors own horizontal control. 

This is my xorg.conf: 
 
 ```
Section "Screen"
 Identifier "Default Screen"
 Device "Configured Video Device"
 Monitor "Configured Monitor"
 SubSection "Display"
 Depth 16
 Modes "1280x1024" "1024x768"
 Option "AddARGBGLXVisuals" "True"
 EndSubSection

 Option "AddARGBGLXVisuals" "True"
 Defaultdepth 24
 EndSection
 Section "Module"
 Load "glx"
 Load "GLcore"
 Load "v4l"
 EndSection
 Section "Device"
 Identifier "Configured Video Device"
 Boardname "vesa"
 Busid "PCI:1:0:0"
 Driver "nvidia"
 Screen 0
 EndSection
 
 Section "Device"
 Identifier "Device0"
 BoardName "Generic Geforce 5500"
 Driver "nvidia"
 Vendorname "NVIDIA Corporation"
 Option "DualHead" "1"
 Option "ShadowFB" "1"
 Option "FPScale" "1"
 Option "TwinView" "True"
 Option "TwinViewOrientation" "RightOf"
 Option "UseEdidFreqs" "True"
 Option "Metamodes" "1024x768,1024x768"
 Option "UseDisplayDevice" "DFP"
 EndSection
 
 Section "Device"
 Identifier "Videocard0"
 Driver "nv"
 VendorName "NVIDIA Corporation"
 BoardName "GeForce 7600 GT"
 EndSection
 
 Section "InputDevice"
 Identifier "Generic Keyboard"
 Driver "kbd"
 Option "XkbRules" "xorg"
 Option "XkbModel" "pc105"
 Option "XkbLayout" "us"
 EndSection

 Section "InputDevice"
 Identifier "Configured Mouse"
 Driver "mouse"
 EndSection
 Section "ServerLayout"
 Identifier "Default Layout"
 screen 0 "Default Screen" 0 0
 EndSection
 
 Section "Extensions"
 Option "Composite" "Enable"
 EndSection

```

The two extremes are generally driving me batty, does anyone have any advice? 

Thanks muchly in advance! 

-Rob

---

