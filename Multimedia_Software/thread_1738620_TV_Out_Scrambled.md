---
title: "TV Out Scrambled"
date: 2011-04-25
forum: Multimedia Software
---

### Post by adam.webb on 2011-04-25
Hi All,

I'm setting up a 'MediaPC' in my living room, using an old IBM machine with an ATI LTPro PCI graphics card. 

All was going well, I had a normal monitor plugged into the Graphics Card as well as the TV screen. The TV screen would be scrambled when I booted up (lots of, mainly stationary, horizontal blue and black lines), but this was easily fixed by switching to the PC screen and back to the TV screen (using sudo atitvout c then sudo atitvout t), however I am now at the stage where I don't want to use the external monitor any more, and when I try and do the "atitvout c" to 'refresh' the screen, it detects that no monitor is plugged in and says no, so I am stuck with the scrambled TV screen.

Does anyone have any suggestions as to what might fix this? I've played around with various settings, and been fiddling with xorg.conf, which is attached, along with Xorg.0.log from the /var/log/ folder.

Anyone got any suggestions for me?

Here are the files: 

xorg.conf:
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
	Load  "extmod"
	Load  "record"
	Load  "dbe"
	Load  "glx"
	Load  "dri"
	Load  "dri2"
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
	#DisplaySize	  300   230	# mm
	Identifier   "Monitor0"
	VendorName   "MEA"
	ModelName    "DV155B"
	HorizSync    21.0 - 63.0
	VertRefresh  21.0 - 75.0
	Option	    "DPMS"
	# 640x400 @ 60.00 Hz (GTF) hsync: 24.90 kHz; pclk: 19.52 MHz
	Modeline "640x400_60.00"  19.52  640 648 712 784  400 401 404 415  -HSync +Vsync


EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "probe_sparse"       	# [<bool>]
        #Option     "accel"              	# [<bool>]
        #Option     "crt_display"        	# [<bool>]
        #Option     "composite_sync"     	# [<bool>]
        #Option     "hw_cursor"          	# [<bool>]
        #Option     "force_pci_mode"     	# [<bool>]
        #Option     "dma_mode"           	# <str>
        #Option     "agp_mode"           	# <i>
        #Option     "agp_size"           	# <i>
        #Option     "local_textures"     	# [<bool>]
        #Option     "buffer_size"        	# <i>
        #Option     "tv_out"             	# [<bool>]
        Option     "tv_standard" "VIDEO"       	# <str>
	Option     "tv_format" "PAL-B"
        #Option     "mmio_cache"         	# [<bool>]
        #Option     "test_mmio_cache"    	# [<bool>]
        #Option     "panel_display"      	# [<bool>]
        #Option     "reference_clock"    	# <freq>
        #Option     "shadow_fb"          	# [<bool>]
        #Option     "sw_cursor"          	# [<bool>]
        #Option     "AccelMethod"        	# <str>
        #Option     "RenderAccel"        	# [<bool>]
	Option "OverlayOnCRTC2"	 "on" 
	Option "DesktopSetup" "Clone"
	Identifier  "Card0"
	Driver      "mach64"
	BusID       "PCI:3:10:0"
	#tv_out	    "true"
	Option "TexturedVideo" "off"
	Option "OpenGLOverlay" "on"	
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card1"
	Driver      "intel"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Viewport   0 0
		Depth     1
		Modes	"640x400"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
		Modes	"640x400"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
		Modes	"640x400"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
		Modes	"640x400"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
		Modes	"640x400"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes	"640x400"
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

```
And the Log File:
```
[    22.750] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    22.750] X Protocol Version 11, Revision 0
[    22.750] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    22.750] Current Operating System: Linux tau 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686
[    22.750] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=46ebebb4-b142-41ba-bb16-99f04d29b11e ro quiet splash
[    22.750] Build Date: 09 January 2011  12:14:58PM
[    22.750] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    22.767] Current version of pixman: 0.18.4
[    22.767] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    22.767] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.767] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 25 14:49:15 2011
[    22.810] (==) Using config file: "/etc/X11/xorg.conf"
[    22.810] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.916] (==) ServerLayout "X.org Configured"
[    22.916] (**) |-->Screen "Screen0" (0)
[    22.916] (**) |   |-->Monitor "Monitor0"
[    22.916] (**) |   |-->Device "Card0"
[    22.916] (**) |-->Screen "Screen1" (1)
[    22.916] (**) |   |-->Monitor "Monitor1"
[    22.916] (**) |   |-->Device "Card1"
[    22.916] (**) |-->Input Device "Mouse0"
[    22.916] (**) |-->Input Device "Keyboard0"
[    22.916] (==) Automatically adding devices
[    22.916] (==) Automatically enabling devices
[    23.005] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    23.005] 	Entry deleted from font path.
[    23.267] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    23.267] 	Entry deleted from font path.
[    23.268] (**) FontPath set to:
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
[    23.268] (**) ModulePath set to "/usr/lib/xorg/modules"
[    23.268] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    23.268] (WW) Disabling Mouse0
[    23.268] (WW) Disabling Keyboard0
[    23.268] (II) Loader magic: 0x81f9b00
[    23.268] (II) Module ABI versions:
[    23.268] 	X.Org ANSI C Emulation: 0.4
[    23.268] 	X.Org Video Driver: 8.0
[    23.268] 	X.Org XInput driver : 11.0
[    23.268] 	X.Org Server Extension : 4.0
[    23.269] (--) PCI: (0:0:2:0) 8086:2572:1014:0287 rev 2, Mem @ 0xf0000000/134217728, 0xe8080000/524288, I/O @ 0x00001890/8
[    23.269] (--) PCI:*(0:3:10:0) 1002:4c49:1002:0040 rev 220, Mem @ 0xe9000000/16777216, 0xe8120000/4096, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
[    23.269] (II) Open ACPI successful (/var/run/acpid.socket)
[    23.269] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[    23.269] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[    23.269] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    23.269] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[    23.269] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    23.269] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[    23.269] (II) LoadModule: "extmod"
[    23.349] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    23.371] (II) Module extmod: vendor="X.Org Foundation"
[    23.371] 	compiled for 1.9.0, module version = 1.0.0
[    23.371] 	Module class: X.Org Server Extension
[    23.371] 	ABI class: X.Org Server Extension, version 4.0
[    23.371] (II) Loading extension MIT-SCREEN-SAVER
[    23.371] (II) Loading extension XFree86-VidModeExtension
[    23.371] (II) Loading extension XFree86-DGA
[    23.371] (II) Loading extension DPMS
[    23.371] (II) Loading extension XVideo
[    23.371] (II) Loading extension XVideo-MotionCompensation
[    23.372] (II) Loading extension X-Resource
[    23.372] (II) LoadModule: "record"
[    23.372] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    23.381] (II) Module record: vendor="X.Org Foundation"
[    23.381] 	compiled for 1.9.0, module version = 1.13.0
[    23.381] 	Module class: X.Org Server Extension
[    23.381] 	ABI class: X.Org Server Extension, version 4.0
[    23.381] (II) Loading extension RECORD
[    23.381] (II) LoadModule: "dbe"
[    23.381] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    23.382] (II) Module dbe: vendor="X.Org Foundation"
[    23.382] 	compiled for 1.9.0, module version = 1.0.0
[    23.382] 	Module class: X.Org Server Extension
[    23.382] 	ABI class: X.Org Server Extension, version 4.0
[    23.382] (II) Loading extension DOUBLE-BUFFER
[    23.382] (II) LoadModule: "glx"
[    23.382] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    23.432] (II) Module glx: vendor="X.Org Foundation"
[    23.432] 	compiled for 1.9.0, module version = 1.0.0
[    23.432] 	ABI class: X.Org Server Extension, version 4.0
[    23.438] (==) AIGLX enabled
[    23.438] (II) Loading extension GLX
[    23.438] (II) LoadModule: "dri"
[    23.438] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    23.474] (II) Module dri: vendor="X.Org Foundation"
[    23.474] 	compiled for 1.9.0, module version = 1.0.0
[    23.474] 	ABI class: X.Org Server Extension, version 4.0
[    23.474] (II) Loading extension XFree86-DRI
[    23.474] (II) LoadModule: "dri2"
[    23.474] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    23.475] (II) Module dri2: vendor="X.Org Foundation"
[    23.475] 	compiled for 1.9.0, module version = 1.2.0
[    23.475] 	ABI class: X.Org Server Extension, version 4.0
[    23.475] (II) Loading extension DRI2
[    23.475] (II) LoadModule: "mach64"
[    23.492] (II) Loading /usr/lib/xorg/modules/drivers/mach64_drv.so
[    23.499] (II) Module mach64: vendor="X.Org Foundation"
[    23.499] 	compiled for 1.8.99.905, module version = 6.8.2
[    23.499] 	Module class: X.Org Video Driver
[    23.499] 	ABI class: X.Org Video Driver, version 8.0
[    23.499] (II) LoadModule: "intel"
[    23.500] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    23.535] (II) Module intel: vendor="X.Org Foundation"
[    23.536] 	compiled for 1.9.0, module version = 2.12.0
[    23.536] 	Module class: X.Org Video Driver
[    23.536] 	ABI class: X.Org Video Driver, version 8.0
[    23.536] (II) MACH64: Driver for ATI Mach64 chipsets
[    23.536] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    23.536] (++) using VT number 7

[    23.538] (**) MACH64(0): Depth 24, (--) framebuffer bpp 32
[    23.538] (**) MACH64(0): Option "tv_standard" "VIDEO"
[    23.538] (==) MACH64(0): Using XAA acceleration architecture
[    23.538] (II) MACH64: Mach64 in slot 3:10:0 detected.
[    23.538] (II) Loading sub module "int10"
[    23.538] (II) LoadModule: "int10"
[    23.538] (II) Loading /usr/lib/xorg/modules/libint10.so
[    23.848] (II) Module int10: vendor="X.Org Foundation"
[    23.848] 	compiled for 1.9.0, module version = 1.0.0
[    23.848] 	ABI class: X.Org Video Driver, version 8.0
[    23.876] (II) MACH64(0): Primary V_BIOS segment is: 0xc000
[    23.876] (II) Loading sub module "ddc"
[    23.876] (II) LoadModule: "ddc"
[    23.876] (II) Module "ddc" already built-in
[    23.876] (II) Loading sub module "vbe"
[    23.876] (II) LoadModule: "vbe"
[    23.876] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    23.930] (II) Module vbe: vendor="X.Org Foundation"
[    23.930] 	compiled for 1.9.0, module version = 1.1.0
[    23.930] 	ABI class: X.Org Video Driver, version 8.0
[    23.930] (II) MACH64(0): VESA BIOS detected
[    23.930] (II) MACH64(0): VESA VBE Version 2.0
[    23.930] (II) MACH64(0): VESA VBE Total Mem: 8128 kB
[    23.930] (II) MACH64(0): VESA VBE OEM: ATI MACH64
[    23.930] (II) MACH64(0): VESA VBE OEM Software Rev: 1.0
[    23.930] (II) MACH64(0): VESA VBE OEM Vendor: ATI Technologies Inc.
[    23.930] (II) MACH64(0): VESA VBE OEM Product: MACH64LP
[    23.930] (II) MACH64(0): VESA VBE OEM Product Rev: 01.00
[    23.937] (II) MACH64(0): VESA VBE DDC supported
[    23.937] (II) MACH64(0): VESA VBE DDC Level 2
[    23.937] (II) MACH64(0): VESA VBE DDC transfer in appr. 2 sec.
[    23.939] (II) MACH64(0): VESA VBE DDC read failed
[    23.941] (--) MACH64(0): Panel model (C) 1988-98, ATI Technol.
[    23.941] (II) MACH64(0): BIOS Data:  BIOSSize=0x10000, ROMTable=0x010C.
[    23.941] (II) MACH64(0): BIOS Data:  ClockTable=0x0908, FrequencyTable=0x0000.
[    23.941] (II) MACH64(0): BIOS Data:  LCDTable=0x0184.
[    23.941] (II) MACH64(0): BIOS Data:  VideoTable=0x0000, HardwareTable=0x0156.
[    23.941] (II) MACH64(0): BIOS Data:  I2CType=0x03, Tuner=0x00, Decoder=0x00, Audio=0x0F.
[    23.941] (--) MACH64(0): ATI 3D Rage LT Pro graphics controller detected.
[    23.941] (--) MACH64(0): Chip type 4C49 "LI", version 4, foundry UMC, class 0, revision 0x03.
[    23.941] (--) MACH64(0): PCI bus interface detected;  block I/O base is 0x2000.
[    23.941] (--) MACH64(0): ATI Mach64 adapter detected.
[    23.941] (!!) MACH64(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
[    23.941] (--) MACH64(0): Internal RAMDAC (subtype 1) detected.
[    23.941] (==) MACH64(0): RGB weight 888
[    23.941] (==) MACH64(0): Default visual is TrueColor
[    23.941] (==) MACH64(0): Using gamma correction (1.0, 1.0, 1.0)
[    23.941] (II) MACH64(0): Using Mach64 accelerator CRTC.
[    23.941] (**) MACH64(0): Using CRT interface and disabling digital flat panel.
[    23.942] (II) MACH64(0): Storing hardware cursor image at 0xE97FFC00.
[    23.942] (II) MACH64(0): Using 8 MB linear aperture at 0xE9000000.
[    23.942] (!!) MACH64(0): Virtual resolutions will be limited to 8191 kB
 due to linear aperture size and/or placement of hardware cursor image area.
[    23.942] (II) MACH64(0): Using Block 0 MMIO aperture at 0xE8120400.
[    23.942] (II) MACH64(0): Using Block 1 MMIO aperture at 0xE8120000.
[    23.944] (II) MACH64(0): MMIO write caching enabled.
[    23.944] (--) MACH64(0): 8192 kB of SDRAM (1:1) detected (using 8191 kB).
[    23.944] (WW) MACH64(0): Cannot shadow an accelerated frame buffer.
[    23.944] (II) MACH64(0): Engine XCLK 100.023 MHz;  Refresh rate code 7.
[    23.944] (--) MACH64(0): Internal programmable clock generator detected.
[    23.944] (--) MACH64(0): Reference clock 29.500 MHz.
[    23.944] (II) MACH64(0): Monitor0: Using hsync range of 21.00-63.00 kHz
[    23.944] (II) MACH64(0): Monitor0: Using vrefresh range of 21.00-75.00 Hz
[    23.944] (II) MACH64(0): Maximum clock: 200.00 MHz
[    23.944] (II) MACH64(0): Not using default mode "640x350" (vrefresh out of range)
[    23.944] (II) MACH64(0): Not using default mode "320x175" (vrefresh out of range)
[    23.944] (II) MACH64(0): Not using default mode "640x400" (vrefresh out of range)
[    23.944] (II) MACH64(0): Not using default mode "320x200" (vrefresh out of range)
[    23.944] (II) MACH64(0): Not using default mode "720x400" (vrefresh out of range)
[    23.944] (II) MACH64(0): Not using default mode "360x200" (vrefresh out of range)
[    23.944] (II) MACH64(0): Not using default mode "640x480" (vrefresh out of range)
[    23.944] (II) MACH64(0): Not using default mode "320x240" (vrefresh out of range)
[    23.944] (II) MACH64(0): Not using default mode "800x600" (vrefresh out of range)
[    23.944] (II) MACH64(0): Not using default mode "400x300" (vrefresh out of range)
[    23.944] (II) MACH64(0): Not using default mode "1024x768i" (vrefresh out of range)
[    23.944] (II) MACH64(0): Not using default mode "512x384i" (vrefresh out of range)
[    23.944] (II) MACH64(0): Not using default mode "1024x768" (hsync out of range)
[    23.944] (II) MACH64(0): Not using default mode "512x384" (hsync out of range)
[    23.944] (II) MACH64(0): Not using default mode "1152x864" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "576x432" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1280x960" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "640x480" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1280x1024" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "640x512" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1280x1024" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "640x512" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1280x1024" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "640x512" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1600x1200" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "800x600" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1600x1200" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "800x600" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1600x1200" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "800x600" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
[    23.945] (II) MACH64(0): Not using default mode "800x600" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
[    23.945] (II) MACH64(0): Not using default mode "800x600" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1792x1344" (insufficient memory for mode)
[    23.945] (II) MACH64(0): Not using default mode "896x672" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1792x1344" (insufficient memory for mode)
[    23.945] (II) MACH64(0): Not using default mode "896x672" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1856x1392" (insufficient memory for mode)
[    23.945] (II) MACH64(0): Not using default mode "928x696" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1856x1392" (insufficient memory for mode)
[    23.945] (II) MACH64(0): Not using default mode "928x696" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    23.945] (II) MACH64(0): Not using default mode "960x720" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    23.945] (II) MACH64(0): Not using default mode "960x720" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1152x864" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "576x432" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1152x864" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "576x432" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1152x864" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "576x432" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1152x864" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "576x432" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    23.945] (II) MACH64(0): Not using default mode "1400x1050" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "700x525" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1400x1050" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "700x525" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1400x1050" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "700x525" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1400x1050" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "700x525" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1680x1050" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "840x525" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1680x1050" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "840x525" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1680x1050" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "840x525" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1680x1050" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "840x525" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
[    23.945] (II) MACH64(0): Not using default mode "840x525" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1920x1080" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "960x540" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1920x1200" (insufficient memory for mode)
[    23.945] (II) MACH64(0): Not using default mode "960x600" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    23.945] (II) MACH64(0): Not using default mode "960x720" (hsync out of range)
[    23.945] (II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    23.945] (II) MACH64(0): Not using default mode "1024x768" (hsync out of range)
[    23.946] (II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    23.946] (II) MACH64(0): Not using default mode "1024x768" (hsync out of range)
[    23.946] (II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    23.946] (II) MACH64(0): Not using default mode "1024x768" (hsync out of range)
[    23.946] (II) MACH64(0): Not using mode "640x400" (no mode of this name)
[    23.946] (II) MACH64(0): Not using default mode "1280x960" (height too large for virtual size)
[    23.946] (--) MACH64(0): Virtual size is 1440x900 (pitch 1440)
[    23.946] (**) MACH64(0):  Default mode "1440x900": 106.5 MHz, 55.9 kHz, 59.9 Hz
[    23.946] (II) MACH64(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    23.946] (**) MACH64(0):  Default mode "1360x768": 84.8 MHz, 47.7 kHz, 59.8 Hz
[    23.946] (II) MACH64(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    23.946] (**) MACH64(0):  Default mode "1152x864": 96.8 MHz, 63.0 kHz, 70.0 Hz
[    23.946] (II) MACH64(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
[    23.946] (**) MACH64(0):  Default mode "1152x864": 81.6 MHz, 53.7 kHz, 60.0 Hz
[    23.946] (II) MACH64(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    23.946] (**) MACH64(0):  Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
[    23.946] (II) MACH64(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    23.946] (**) MACH64(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
[    23.946] (II) MACH64(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    23.946] (**) MACH64(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[    23.946] (II) MACH64(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    23.946] (**) MACH64(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
[    23.946] (II) MACH64(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    23.946] (**) MACH64(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
[    23.946] (II) MACH64(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    23.946] (**) MACH64(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
[    23.946] (II) MACH64(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    23.946] (**) MACH64(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[    23.946] (II) MACH64(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    23.946] (**) MACH64(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
[    23.946] (II) MACH64(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    23.946] (**) MACH64(0):  Default mode "720x450": 53.2 MHz, 55.9 kHz, 59.9 Hz (D)
[    23.946] (II) MACH64(0): Modeline "720x450"x59.9   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz)
[    23.946] (**) MACH64(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
[    23.946] (II) MACH64(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    23.946] (**) MACH64(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
[    23.946] (II) MACH64(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    23.946] (**) MACH64(0):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
[    23.946] (II) MACH64(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
[    23.946] (**) MACH64(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[    23.946] (II) MACH64(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    23.946] (**) MACH64(0):  Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
[    23.946] (II) MACH64(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
[    23.946] (**) MACH64(0):  Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
[    23.946] (II) MACH64(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
[    23.947] (**) MACH64(0):  Mode "640x400_60.00": 19.5 MHz, 24.9 kHz, 60.0 Hz
[    23.947] (II) MACH64(0): Modeline "640x400_60.00"x60.0   19.52  640 648 712 784  400 401 404 415 -hsync +vsync (24.9 kHz)
[    23.947] (**) MACH64(0):  Default mode "576x432": 48.4 MHz, 63.0 kHz, 70.0 Hz (D)
[    23.947] (II) MACH64(0): Modeline "576x432"x70.0   48.38  576 612 672 768  432 432 434 450 doublescan -hsync +vsync (63.0 kHz)
[    23.947] (**) MACH64(0):  Default mode "576x432": 40.8 MHz, 53.7 kHz, 60.1 Hz (D)
[    23.947] (II) MACH64(0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz)
[    23.947] (**) MACH64(0):  Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
[    23.947] (II) MACH64(0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz)
[    23.947] (**) MACH64(0):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
[    23.947] (II) MACH64(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
[    23.947] (**) MACH64(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
[    23.947] (II) MACH64(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
[    23.947] (**) MACH64(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
[    23.947] (II) MACH64(0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz)
[    23.947] (**) MACH64(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
[    23.947] (II) MACH64(0): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync (46.9 kHz)
[    23.947] (**) MACH64(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
[    23.947] (II) MACH64(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz)
[    23.947] (**) MACH64(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
[    23.947] (II) MACH64(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
[    23.947] (**) MACH64(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
[    23.947] (II) MACH64(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
[    23.947] (**) MACH64(0):  Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
[    23.947] (II) MACH64(0): Modeline "320x240"x75.0   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync (37.5 kHz)
[    23.947] (**) MACH64(0):  Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
[    23.947] (II) MACH64(0): Modeline "320x240"x72.8   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync (37.9 kHz)
[    23.947] (**) MACH64(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
[    23.947] (II) MACH64(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
[    23.947] (==) MACH64(0): DPI set to (96, 96)
[    23.947] (II) Loading sub module "fb"
[    23.947] (II) LoadModule: "fb"
[    23.947] (II) Loading /usr/lib/xorg/modules/libfb.so
[    23.979] (II) Module fb: vendor="X.Org Foundation"
[    23.979] 	compiled for 1.9.0, module version = 1.0.0
[    23.979] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    23.979] (II) Loading sub module "ramdac"
[    23.979] (II) LoadModule: "ramdac"
[    23.979] (II) Module "ramdac" already built-in
[    23.979] (II) Loading sub module "xaa"
[    23.979] (II) LoadModule: "xaa"
[    23.979] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    24.034] (II) Module xaa: vendor="X.Org Foundation"
[    24.034] 	compiled for 1.9.0, module version = 1.2.1
[    24.034] 	ABI class: X.Org Video Driver, version 8.0
[    24.034] (II) Loading sub module "i2c"
[    24.034] (II) LoadModule: "i2c"
[    24.034] (II) Module "i2c" already built-in
[    24.034] (II) MACH64(0): I2C bus "Mach64" initialized.
[    25.297] (EE) intel(1): No kernel modesetting driver detected.
[    25.297] (II) UnloadModule: "intel"
[    25.297] (--) Depth 24 pixmap format is 32 bpp
[    25.375] (WW) MACH64(0): DRI static buffer allocation failed -- need at least 12656 kB video memory
[    25.490] (II) MACH64(0): Largest offscreen areas (with overlaps):
[    25.490] (II) MACH64(0): 	1440 x 556 rectangle at 0,900
[    25.490] (II) MACH64(0): 	256 x 557 rectangle at 0,900
[    25.490] (II) MACH64(0): Using XFree86 Acceleration Architecture (XAA)
[    25.490] 	Screen to screen bit blits
[    25.490] 	Solid filled rectangles
[    25.490] 	8x8 mono pattern filled rectangles
[    25.490] 	Indirect CPU to Screen color expansion
[    25.490] 	Solid Lines
[    25.490] 	Setting up tile and stipple cache:
[    25.490] 		24 128x128 slots
[    25.490] 		5 256x256 slots
[    25.490] (==) MACH64(0): Backing store disabled
[    25.527] (==) MACH64(0): Silken mouse enabled
[    25.529] (**) MACH64(0): DPMS enabled
[    25.529] (WW) MACH64(0): Option "tv_format" is not used
[    25.529] (WW) MACH64(0): Option "OverlayOnCRTC2" is not used
[    25.529] (WW) MACH64(0): Option "DesktopSetup" is not used
[    25.529] (WW) MACH64(0): Option "TexturedVideo" is not used
[    25.529] (WW) MACH64(0): Option "OpenGLOverlay" is not used
[    25.529] (II) MACH64(0): Direct rendering disabled
[    25.529] (==) RandR enabled
[    25.529] (II) Initializing built-in extension Generic Event Extension
[    25.529] (II) Initializing built-in extension SHAPE
[    25.529] (II) Initializing built-in extension MIT-SHM
[    25.529] (II) Initializing built-in extension XInputExtension
[    25.529] (II) Initializing built-in extension XTEST
[    25.529] (II) Initializing built-in extension BIG-REQUESTS
[    25.529] (II) Initializing built-in extension SYNC
[    25.529] (II) Initializing built-in extension XKEYBOARD
[    25.529] (II) Initializing built-in extension XC-MISC
[    25.529] (II) Initializing built-in extension SECURITY
[    25.529] (II) Initializing built-in extension XINERAMA
[    25.529] (II) Initializing built-in extension XFIXES
[    25.529] (II) Initializing built-in extension RENDER
[    25.529] (II) Initializing built-in extension RANDR
[    25.529] (II) Initializing built-in extension COMPOSITE
[    25.529] (II) Initializing built-in extension DAMAGE
[    25.529] (II) Initializing built-in extension GESTURE
[    25.583] (II) AIGLX: Screen 0 is not DRI2 capable
[    25.583] (II) AIGLX: Screen 0 is not DRI capable
[    26.023] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[    26.023] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    27.221] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    27.281] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    27.282] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.282] (II) LoadModule: "evdev"
[    27.384] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.529] (II) Module evdev: vendor="X.Org Foundation"
[    27.529] 	compiled for 1.9.0, module version = 2.3.2
[    27.529] 	Module class: X.Org XInput Driver
[    27.529] 	ABI class: X.Org XInput driver, version 11.0
[    27.529] (**) Power Button: always reports core events
[    27.529] (**) Power Button: Device: "/dev/input/event1"
[    27.529] (II) Power Button: Found keys
[    27.529] (II) Power Button: Configuring as keyboard
[    27.529] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    27.529] (**) Option "xkb_rules" "evdev"
[    27.529] (**) Option "xkb_model" "pc105"
[    27.529] (**) Option "xkb_layout" "us"
[    27.529] (**) Option "xkb_options" "lv3:ralt_switch"
[    27.533] (II) XKB: reuse xkmfile /var/lib/xkb/server-0C76CA335E924C2441A31FBFED02D59A89874CA6.xkm
[    27.563] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    27.563] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.563] (**) Power Button: always reports core events
[    27.563] (**) Power Button: Device: "/dev/input/event0"
[    27.563] (II) Power Button: Found keys
[    27.563] (II) Power Button: Configuring as keyboard
[    27.563] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    27.563] (**) Option "xkb_rules" "evdev"
[    27.563] (**) Option "xkb_model" "pc105"
[    27.563] (**) Option "xkb_layout" "us"
[    27.563] (**) Option "xkb_options" "lv3:ralt_switch"
[    27.566] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event2)
[    27.566] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    27.566] (**) USB Optical Mouse: always reports core events
[    27.566] (**) USB Optical Mouse: Device: "/dev/input/event2"
[    27.566] (II) USB Optical Mouse: Found 3 mouse buttons
[    27.566] (II) USB Optical Mouse: Found scroll wheel(s)
[    27.566] (II) USB Optical Mouse: Found relative axes
[    27.566] (II) USB Optical Mouse: Found x and y relative axes
[    27.566] (II) USB Optical Mouse: Configuring as mouse
[    27.566] (**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    27.566] (**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    27.566] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
[    27.566] (II) USB Optical Mouse: initialized for relative axes.
[    27.567] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    27.567] (II) No input driver/identifier specified (ignoring)
[    27.568] (II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event3)
[    27.568] (**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    27.568] (**) Dell Dell USB Keyboard: always reports core events
[    27.568] (**) Dell Dell USB Keyboard: Device: "/dev/input/event3"
[    27.568] (II) Dell Dell USB Keyboard: Found keys
[    27.568] (II) Dell Dell USB Keyboard: Configuring as keyboard
[    27.568] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
[    27.568] (**) Option "xkb_rules" "evdev"
[    27.568] (**) Option "xkb_model" "pc105"
[    27.568] (**) Option "xkb_layout" "us"
[    27.568] (**) Option "xkb_options" "lv3:ralt_switch"
[    27.570] (II) config/udev: Adding input device IR-receiver inside an USB DVB receiver (/dev/input/event4)
[    27.571] (**) IR-receiver inside an USB DVB receiver: Applying InputClass "evdev keyboard catchall"
[    27.571] (**) IR-receiver inside an USB DVB receiver: always reports core events
[    27.571] (**) IR-receiver inside an USB DVB receiver: Device: "/dev/input/event4"
[    27.571] (II) IR-receiver inside an USB DVB receiver: Found keys
[    27.571] (II) IR-receiver inside an USB DVB receiver: Configuring as keyboard
[    27.571] (II) XINPUT: Adding extended input device "IR-receiver inside an USB DVB receiver" (type: KEYBOARD)
[    27.571] (**) Option "xkb_rules" "evdev"
[    27.571] (**) Option "xkb_model" "pc105"
[    27.571] (**) Option "xkb_layout" "us"
[    27.571] (**) Option "xkb_options" "lv3:ralt_switch"
```
Cheers

Adam

---

### Post by poodoopealeoaph on 2011-04-25
not sure if this may do the trick but you could try to do your little switcheroo to get the tv to show up and then go to the additional drivers section under system>administration and see if there is a driver you need for your tv specifically. Maybe it is loading the driver as a plug and play but when you have it there from the beginning it may not be loading the driver. Another thing you can try is to go to system>preferences>monitors and see if there is a driver you can see/use in there.

---

### Post by adam.webb on 2011-04-26
Thanks for the reply. No luck with drivers in either of those places. Does anyone have any other suggestions?

Adam

---

### Post by adam.webb on 2011-05-15
I've now realised that it is a change in resolution which seems to trigger this problem. Does this give anyone any idea what the problem could be?

Cheers

Adam

---

