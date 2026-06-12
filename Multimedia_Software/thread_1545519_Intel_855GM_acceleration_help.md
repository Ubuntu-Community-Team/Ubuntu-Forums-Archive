---
title: "Intel 855GM acceleration help"
date: 2010-08-04
forum: Multimedia Software
---

### Post by Lepy on 2010-08-04
Since upgrading to lucid, I have been battling getting a laptop's intel 855GM working with acceleration for months now!

```
2.6.34-020634rc5-generic
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```

I have tried every method described here: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

At the moment, the laptop will boot giving an error message then allowing me to start in low-graphics mode. The screen is at maximum resolution (1280x800) and there appear to be no other problems.

However, the xorg log states:
```
[    26.952] 
X.Org X Server 1.8.2
Release Date: 2010-07-01
[    26.952] X Protocol Version 11, Revision 0
[    26.952] Build Operating System: Linux 2.6.24-28-xen i686 Ubuntu
[    26.952] Current Operating System: Linux mythgateway-laptop 2.6.34-020634rc5-generic #020634rc5 SMP Tue Apr 20 10:07:04 UTC 2010 i686
[    26.952] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.34-020634rc5-generic root=UUID=3162bc0f-aef5-4b6c-8a9b-a47c9413f8af ro quiet splash i915.modeset=1
[    26.952] Build Date: 08 July 2010  01:50:14AM
[    26.952] xorg-server 2:1.8.2+git20100705+server-1.8-branch.665aa7ce-0ubuntu0sarvatt2~lucid (For technical support please see http://www.ubuntu.com/support) 
[    26.952] Current version of pixman: 0.19.1
[    26.952] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    26.953] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.953] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug  3 23:33:59 2010
[    26.953] (==) Using config file: "/etc/X11/xorg.conf"
[    26.953] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    26.953] (==) ServerLayout "X.org Configured"
[    26.953] (**) |-->Screen "Screen0" (0)
[    26.953] (**) |   |-->Monitor "Monitor0"
[    26.954] (**) |   |-->Device "Card0"
[    26.954] (**) |-->Screen "Screen1" (1)
[    26.954] (**) |   |-->Monitor "Monitor1"
[    26.954] (==) No device specified for screen "Screen1".
	Using the first device section listed.
[    26.954] (**) |   |-->Device "Card0"
[    26.954] (**) |-->Input Device "Mouse0"
[    26.954] (**) |-->Input Device "Keyboard0"
[    26.954] (==) Automatically adding devices
[    26.954] (==) Automatically enabling devices
[    26.954] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    26.954] 	Entry deleted from font path.
[    26.954] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    26.954] 	Entry deleted from font path.
[    26.954] (**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    26.954] (**) ModulePath set to "/usr/lib/xorg/modules"
[    26.954] (**) Extension "Composite" is disabled
[    26.954] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    26.954] (WW) Disabling Mouse0
[    26.954] (WW) Disabling Keyboard0
[    26.954] (II) Loader magic: 0x81f4ba0
[    26.954] (II) Module ABI versions:
[    26.954] 	X.Org ANSI C Emulation: 0.4
[    26.954] 	X.Org Video Driver: 7.0
[    26.954] 	X.Org XInput driver : 9.0
[    26.954] 	X.Org Server Extension : 3.0
[    27.042] (--) PCI:*(0:0:2:0) 8086:3582:107b:0360 Intel Corporation 82852/855GM Integrated Graphics Device rev 2, Mem @ 0xe8000000/134217728, 0xe0000000/524288, I/O @ 0x00001800/8
[    27.042] (--) PCI: (0:0:2:1) 8086:3582:107b:0360 Intel Corporation 82852/855GM Integrated Graphics Device rev 2, Mem @ 0xf0000000/134217728, 0xe0080000/524288
[    27.042] (II) Open ACPI successful (/var/run/acpid.socket)
[    27.042] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[    27.042] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[    27.042] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    27.042] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[    27.042] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    27.042] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[    27.042] (II) LoadModule: "record"
[    27.069] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    27.069] (II) Module record: vendor="X.Org Foundation"
[    27.069] 	compiled for 1.8.2, module version = 1.13.0
[    27.069] 	Module class: X.Org Server Extension
[    27.069] 	ABI class: X.Org Server Extension, version 3.0
[    27.069] (II) Loading extension RECORD
[    27.069] (II) LoadModule: "extmod"
[    27.069] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    27.069] (II) Module extmod: vendor="X.Org Foundation"
[    27.069] 	compiled for 1.8.2, module version = 1.0.0
[    27.069] 	Module class: X.Org Server Extension
[    27.069] 	ABI class: X.Org Server Extension, version 3.0
[    27.069] (II) Loading extension MIT-SCREEN-SAVER
[    27.069] (II) Loading extension XFree86-VidModeExtension
[    27.069] (II) Loading extension XFree86-DGA
[    27.069] (II) Loading extension DPMS
[    27.069] (II) Loading extension XVideo
[    27.070] (II) Loading extension XVideo-MotionCompensation
[    27.070] (II) Loading extension X-Resource
[    27.070] (II) LoadModule: "dri2"
[    27.070] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    27.070] (II) Module dri2: vendor="X.Org Foundation"
[    27.070] 	compiled for 1.8.2, module version = 1.2.0
[    27.070] 	ABI class: X.Org Server Extension, version 3.0
[    27.070] (II) Loading extension DRI2
[    27.070] (II) LoadModule: "dbe"
[    27.070] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    27.070] (II) Module dbe: vendor="X.Org Foundation"
[    27.070] 	compiled for 1.8.2, module version = 1.0.0
[    27.070] 	Module class: X.Org Server Extension
[    27.070] 	ABI class: X.Org Server Extension, version 3.0
[    27.070] (II) Loading extension DOUBLE-BUFFER
[    27.070] (II) LoadModule: "glx"
[    27.070] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    27.071] (II) Module glx: vendor="X.Org Foundation"
[    27.071] 	compiled for 1.8.2, module version = 1.0.0
[    27.071] 	ABI class: X.Org Server Extension, version 3.0
[    27.071] (==) AIGLX enabled
[    27.071] (II) Loading extension GLX
[    27.071] (II) LoadModule: "dri"
[    27.071] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    27.071] (II) Module dri: vendor="X.Org Foundation"
[    27.071] 	compiled for 1.8.2, module version = 1.0.0
[    27.071] 	ABI class: X.Org Server Extension, version 3.0
[    27.071] (II) Loading extension XFree86-DRI
[    27.071] (II) LoadModule: "intel"
[    27.071] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    27.092] (II) Module intel: vendor="X.Org Foundation"
[    27.092] 	compiled for 1.7.6, module version = 2.9.1
[    27.092] 	Module class: X.Org Video Driver
[    27.092] 	ABI class: X.Org Video Driver, version 6.0
[    27.092] (EE) module ABI major version (6) doesn't match the server's version (7)
[    27.092] (II) UnloadModule: "intel"
[    27.092] (II) Unloading /usr/lib/xorg/modules/drivers/intel_drv.so
[    27.092] (EE) Failed to load module "intel" (module requirement mismatch, 0)
[    27.092] (EE) No drivers available.
[    27.092] 
Fatal server error:
[    27.092] no screens found
[    27.092] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    27.092] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    27.092] 
```

Specifically this section:
```
[    27.071] (II) Loading extension XFree86-DRI
[    27.071] (II) LoadModule: "intel"
[    27.071] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    27.092] (II) Module intel: vendor="X.Org Foundation"
[    27.092] 	compiled for 1.7.6, module version = 2.9.1
[    27.092] 	Module class: X.Org Video Driver
[    27.092] 	ABI class: X.Org Video Driver, version 6.0
[    27.092] (EE) module ABI major version (6) doesn't match the server's version (7)
[    27.092] (II) UnloadModule: "intel"
[    27.092] (II) Unloading /usr/lib/xorg/modules/drivers/intel_drv.so
[    27.092] (EE) Failed to load module "intel" (module requirement mismatch, 0)
[    27.092] (EE) No drivers available.
[    27.092] 
Fatal server error:
[    27.092] no screens found
[    27.092] 
```

It seems like the module version is too high. I got to this following the thread mentioned above, and I'm not sure how to rectify the problem. Forcing the xserver-xorg-video-intel package to one of the 5 versions from my sources does not help (probably because the lowest is 2.9.1.

I'll also attach the xorg.conf. The laptop used to have an external monitor connected to it, but it has since been repurposed:
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
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
	Load  "record"
	Load  "extmod"
	Load  "dri2"
	Load  "dbe"
	Load  "glx"
	Load  "dri"
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
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        Option     "DRI"                	"true"
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "82852/855GM Integrated Graphics Device"
	BusID       "PCI:0:2:0"
        Option          "AccelMethod"   "UXA"
        VideoRam        130560
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

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
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
	Option "Composite" "Disable"
EndSection

```

I feel like fresh installing 9.04 or 9.10 instead of dealing with 10.04 would be an acceptable route, but if I can get this fixed, I'd be happy to stay with the LTS release. Please help me in the right direction! Thanks.

---

### Post by Lepy on 2010-08-04
It seems that a ppa must have had an odd driver version. I disabled all ppas from the 'other' tab of the sources manager, then ran: sudo apt-get remove xserver-xorg && sudo apt-get update && sudo apt-get install xserver-xorg-core

Upon reboot, the Xorg log is error free and acceleration seems to be working. It looks like my attempts to fix it (by adding ppas) was not the proper direction!

---

