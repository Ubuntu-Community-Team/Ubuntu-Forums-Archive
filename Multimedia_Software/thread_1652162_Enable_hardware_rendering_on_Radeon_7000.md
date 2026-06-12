---
title: "Enable hardware rendering on Radeon 7000"
date: 2010-12-24
forum: Multimedia Software
---

### Post by hammad1337 on 2010-12-24
Hi community,
So here is my problem:
In short, I am having trouble enabling hardware rendering on my Radeon 7000. As a result, games run slow, and Compiz refuses to run.
ATI Radeon 7000, uses the open-source driver that already comes installed (Mesa, I think it is called)

Here are outputs of different commands I think you might find useful. Let me know if you want anything else.
```

$ lspci |grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

```
```

$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa X11
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_fragment_program,

```
```

$ cat /var/log/Xorg.0.log | grep DRI
[    37.846] (II) Loading extension XFree86-DRI
[    37.846] (II) Loading extension DRI2
[    37.875] (**) RADEON(0): Option "DRI" "on"
[    38.111] (EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
[    39.261] (II) AIGLX: Screen 0 is not DRI2 capable
[    39.261] (II) AIGLX: Screen 0 is not DRI capable
[    39.270] (II) GLX: Initialized DRISWRAST GL provider for screen 0

```
```

$ cat /etc/X11/xorg.conf 
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dbe"
	Load  "dri"
	Load  "dri2"
	Load  "extmod"
	Load  "glx"
	Load  "record"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	#DisplaySize	  340   270	# mm
	Identifier   "Monitor0"
	VendorName   "DEL"
	ModelName    "DELL 1702FP"
	HorizSync    30.0 - 80.0
	VertRefresh  56.0 - 76.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "Radeon RV100 QY [Radeon 7000/VE]"
	BusID       "PCI:1:0:0"
	Option 	    "NoAccel"		"false"
	Option	    "ColorTiling"	"true"
	Option	    "EnablePageFlip"	"true"
	Option	    "RenderAccel"	"true"
	Option	    "AccelMethod"	"XAA"
	Option 	    "XAANoOffscreenPixmaps" "true"
	Option	    "DRI"		    "on"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option "Composite" 	"Enable"
	Option "RENDER" 	"Enable"
EndSection

```
```

$ compiz-check 

Gathering information about your system...

 Distribution:          Linux Mint 10
http://www.linuxmint.com/rel_julia.php
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```
```

$ compiz --replace &
[1] 3175
compiz (core) - Fatal: Software rendering detected.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory

```
```

$ lsmod |grep radeon
radeon                825934  0 
ttm                    56633  1 radeon
drm_kms_helper         30200  1 radeon
drm                   168054  3 radeon,ttm,drm_kms_helper
i2c_algo_bit            5168  1 radeon

```
I have been googling, looking around in forums, but to no effect. :(
Any ideas what I might be missing?

---

### Post by hammad1337 on 2010-12-25
bump

---

### Post by hammad1337 on 2010-12-26
re-bump

---

### Post by Yellow Pasque on 2010-12-27
Can you post entire /var/log/Xorg.0.log? Also, maybe you can find something related in dmesg.

---

### Post by hammad1337 on 2010-12-27
My Xorg.0.log: [http://pastebin.com/g8vTuUjR](http://pastebin.com/g8vTuUjR)

Could you specify what items to look for in dmesg?

Thanks for the reply.

---

### Post by Yellow Pasque on 2010-12-27
What version of Ubuntu are you running? What kernel are you running?
```
uname -a
```

---

### Post by hammad1337 on 2010-12-27
```

$ uname -a
Linux 1337-mash33n 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux

```
I am using Linux Mint 10 (It is equivalent to Ubuntu 10.10).

---

### Post by _zifban on 2011-04-11
I have a similar, maybe related problem with Radeon 7000. One of the (K)ubuntu upgrades removed XVideo support, which was there before.  'xvinfo' doesn't find any adapters.  Now fullscreen video (in mplayer) is done with software scaling (x11) and it is too slow. OpenGL scaling and video output is possible, but it has problems keeping the video and audio synced. I have searched the forums and many have had the same problem but there has been no solutions, other than downgrading way back.

---

### Post by _zifban on 2011-04-12
I was successful at enabling xvideo by disabling KMS with
```
echo options radeon modeset=0 > /etc/modprobe.d/radeon.conf
```.
Compiz also works.

---

