---
title: "ATI and issues with Mesa"
date: 2008-06-24
forum: Multimedia Software
---

### Post by mrbiggl3s on 2008-06-24
I have read several posts on this topic but none have helped. I am trying to get my ATI X800 PRO (R420) to work properly on a clean install of Ubuntu Hardy. I first tried to use the open source drivers ("ati" and "radeon") since I was under the impression that these were 'easy' to use. 

I carefully followed the steps here:
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

and everything was fine until: 
```
glxinfo | grep "direct rendering"
```
to which I received:
```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```

I tried to fix this by following:
[http://ubuntuforums.org/showthread.php?p=2558967#post2558967](http://ubuntuforums.org/showthread.php?p=2558967#post2558967)

I gave up on the "ati" driver and decided to use the proprietary drivers. I tried using packages, binary Catalyst files from ATI, and even Envy.
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

When I first used the ATI drivers I got a white screen. I fixed this by disabling "composite." But every time I installed and ran fglrxinfo I received:
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)
```

Saw someone with a similar problem here:
[http://ubuntuforums.org/showthread.php?t=475699](http://ubuntuforums.org/showthread.php?t=475699)

I have created the symbolic link as per the solution found here:
[http://www.thinkwiki.org/wiki/Problems_with_fglrx#Perpetual_Mesa_GLX_Indirect_on_Debian](http://www.thinkwiki.org/wiki/Problems_with_fglrx#Perpetual_Mesa_GLX_Indirect_on_Debian)
but still nothing.

When I run glxgears I receive about 300fps.

Is there anything I am missing?  Any help would be greatly appreciated. I have spent many hours on this without hope. All I want are some wiggly windows... is that so much to ask for?

Here is my latest xorg.conf (Although I have modified it countless times):
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "dbe" # Double-Buffering Extension
	Load  "extmod"
	Load  "type1"
	Load  "freetype"
	Load  "glx" # 3D layer
	Load  "dri" # direct rendering
	Load  "vbe"
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
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
```

---

