---
title: "ATI/fglrx - assistance would be appreciated"
date: 2006-09-26
forum: Multimedia &amp; Video
---

### Post by infol on 2006-09-26
Hello everyone!

Now I've been searching these forums (and others) for a working howto to install fglrx, but to no avail :confused: ](*,)  

Hopefully, some kind soul might look over my configurations below and maybe point me in the right direction... :-D 

(I also want to point out that I had fglrx working on this machine before - a dell inspiron with mob.radeon 9700, 128mb - so my problems are not hardware-related.. 
However, I'm pretty sure my previous fglrx was an earlier version than the current build (8.29.6), probably 8.28.8 (which I have also tried to install after purging 8.29.6). 
The kernel was also different; I now have 2.6.15-27-686, and the previous kernel was probably 2.6.15-26-386.

Anyway, as far as i've been able to figure out myself (not being totally n00b), there are _at least_ 2 issues that needs to be resolved (maybe fixing one will solve the other - wishful thinking...).

**1)** is that fglrx seems to be rendering on "the wrong display"..
Reasoning: 
```
fglrxinfo
``` 
gives me 
```
Error: unable to open display :0
```

whereas
```
fglrxinfo -display :1
``` 
gives me
```
infol@infol-laptop:~$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.6011 (8.28.8)
```

Thus, how do I force fglrx to render on display 1? (Yes, I do specify BusID as"PCI:1:0:0" in xorg.conf, as you will see further down)

**2)** is that DRI fails to initialize (maybe should be no 1?)
Doing a 
```
cat /var/log/Xorg.0.log|grep fglrx|less
```
gives me
```
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```
but what interests me is the line above this message, i.e.
```
(II) fglrx(0): Composite extension enabled, disabling direct rendering
```
At first, I had commented out the part about composite extensions in xorg.conf, but even if I actively disable extensions
```
Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
```
i get the same message from Xorg.0.log...........

Any ideas so far??

For reference, you will find xorg.conf, /etc/modules, and the outputs from Xorg.0.log below.

xorg.conf:
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Logitech MX1000" "CorePointer"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"

#	Load	"i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dbe"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "se"
EndSection

Section "InputDevice"
	Identifier  "Logitech MX1000"
	Driver      "evdev"
	Option	    "Name" "Logitech USB Receiver"
	Option	    "HWHEELRelativeAxisButtons" "7 6"
	Option	    "Device" "/dev/input/event9"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
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
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
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

Section "DRI"
	Mode         0666
EndSection

# Section "Extensions"
#	Option	    "Composite" "Enable"
# EndSection


```

/etc/modules
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
sbp2
sr_mod
agpgart
fglrx
dri


```

Xorg.0.log (with |grep fglrx - if you need the rest as well, let me know)
```

(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): pEnt->device->identifier=0x81db9d8
(II) fglrx(0): === [atiddxPreInit] === begin, [s]
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "MOBILITY RADEON 9600/9700 (M10/M11 4E50)" (Chipset = 0x4e50)
(--) fglrx(0): (PciSubVendor = 0x1028, PciSubDevice = 0x017c)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xf0000000
(--) fglrx(0): MMIO registers at 0xfcff0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 131008 kB
(II) fglrx(0): VESA VBE OEM: ATI MOBILITY RADEON 9700   
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: P11 
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Connected Display1: LCD on internal LVDS
(II) fglrx(0):  Display1: No EDID information from DDC.
(II) fglrx(0): Derived EDID from BIOS and internal tables for Display1:
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: MS_  Model: 0  Serial#: 0
(II) fglrx(0): Year: 1990  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 40  vert.: 30
(II) fglrx(0): Gamma: 1.00
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; Non RGB Multicolor Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.000 redY: 0.000   greenX: 0.000 greenY: 0.000
(II) fglrx(0): blueX: 0.000 blueY: 0.000   whiteX: 0.000 whiteY: 0.000
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 60  vid: 16453
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 60  vid: 16497
(II) fglrx(0): #4: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 119.2 MHz   Image Size:  0 x 0 mm
(II) fglrx(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) fglrx(0): v_active: 1050  v_sync: 1052  v_sync_end 1058 v_blanking: 1080 v_border: 0
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay version 3.  5 power states available:
(II) fglrx(0):   1. 105/182MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 108/108MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   3. 105/182MHz @ 60Hz [low voltage, enable sleep, thermal diode mode]
(II) fglrx(0):   4. 209/182MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   5. 209/182MHz @ 60Hz [low voltage, enable sleep, thermal diode mode]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 16 modes found for primary display.
(--) fglrx(0): Virtual size is 1680x1050 (pitch 0)
(**) fglrx(0): *Mode "1680x1050": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"  119.25  1680 1728 1760 1840  1050 1052 1058 1080
(**) fglrx(0): *Mode "1280x1024": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  119.25  1280 1528 1560 1840  1024 1039 1045 1080
(**) fglrx(0): *Mode "1280x800": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"  119.25  1280 1528 1560 1840  800 927 933 1080
(**) fglrx(0): *Mode "1280x768": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"  119.25  1280 1528 1560 1840  768 911 917 1080
(**) fglrx(0): *Mode "1024x768": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"  119.25  1024 1400 1432 1840  768 911 917 1080
(**) fglrx(0): *Mode "848x480": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"  119.25  848 1312 1344 1840  480 767 773 1080
(**) fglrx(0): *Mode "800x600": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"  119.25  800 1288 1320 1840  600 827 833 1080
(**) fglrx(0): *Mode "720x576": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"  119.25  720 1248 1280 1840  576 815 821 1080
(**) fglrx(0): *Mode "720x480": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"  119.25  720 1248 1280 1840  480 767 773 1080
(**) fglrx(0): *Mode "640x480": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"  119.25  640 1208 1240 1840  480 767 773 1080
(**) fglrx(0):  Default mode "640x400": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"  119.25  640 1208 1240 1840  400 727 733 1080
(**) fglrx(0):  Default mode "640x350": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"  119.25  640 1208 1240 1840  350 702 708 1080
(**) fglrx(0):  Default mode "512x384": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"  119.25  512 1144 1176 1840  384 719 725 1080
(**) fglrx(0):  Default mode "400x300": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"  119.25  400 1088 1120 1840  300 827 833 1080 doublescan
(**) fglrx(0):  Default mode "320x240": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"  119.25  320 1048 1080 1840  240 767 773 1080 doublescan
(**) fglrx(0):  Default mode "320x200": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"  119.25  320 1048 1080 1840  200 727 733 1080 doublescan
(++) fglrx(0): DPI set to (100, 100)
(--) fglrx(0): Virtual size is 1680x1050 (pitch 1728)
(**) fglrx(0): *Mode "1680x1050": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"  119.25  1680 1728 1760 1840  1050 1052 1058 1080
(**) fglrx(0): *Mode "1280x1024": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  119.25  1280 1528 1560 1840  1024 1039 1045 1080
(**) fglrx(0): *Mode "1280x800": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"  119.25  1280 1528 1560 1840  800 927 933 1080
(**) fglrx(0): *Mode "1280x768": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"  119.25  1280 1528 1560 1840  768 911 917 1080
(**) fglrx(0): *Mode "1024x768": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"  119.25  1024 1400 1432 1840  768 911 917 1080
(**) fglrx(0): *Mode "848x480": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"  119.25  848 1312 1344 1840  480 767 773 1080
(**) fglrx(0): *Mode "800x600": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"  119.25  800 1288 1320 1840  600 827 833 1080
(**) fglrx(0): *Mode "720x576": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"  119.25  720 1248 1280 1840  576 815 821 1080
(**) fglrx(0): *Mode "720x480": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"  119.25  720 1248 1280 1840  480 767 773 1080
(**) fglrx(0): *Mode "640x480": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"  119.25  640 1208 1240 1840  480 767 773 1080
(**) fglrx(0):  Default mode "640x400": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"  119.25  640 1208 1240 1840  400 727 733 1080
(**) fglrx(0):  Default mode "640x350": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"  119.25  640 1208 1240 1840  350 702 708 1080
(**) fglrx(0):  Default mode "512x384": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"  119.25  512 1144 1176 1840  384 719 725 1080
(**) fglrx(0):  Default mode "400x300": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"  119.25  400 1088 1120 1840  300 827 833 1080 doublescan
(**) fglrx(0):  Default mode "320x240": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"  119.25  320 1048 1080 1840  240 767 773 1080 doublescan
(**) fglrx(0):  Default mode "320x200": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"  119.25  320 1048 1080 1840  200 727 733 1080 doublescan
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) fglrx(0): UMM Bus area:     0xf08f7000 (size=0x07709000)
(II) fglrx(0): UMM area:     0xf08f7000 (size=0x07709000)
(II) fglrx(0): Composite extension enabled, disabling direct rendering
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xf0000000 FBMappedSize: 0x08000000
(II) fglrx(0): FBMM initialized for area (0,0)-(1728,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1728,1050) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1728 x 7138
(**) fglrx(0): Video overlay enabled on CRTC1

```

---

### Post by infol on 2006-09-26
Okidoki

New theory...

fglrx works fine if I run startx from the console; thus the problem should be in gdm.conf or gdm.conf-custom. I'll dig around a little more, but suggestions are appreciated

---

### Post by xbx on 2006-11-01
I had the same error message.

and I found the explanation in 
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

> 
 Disable Composite Extension

In Ubuntu Edgy the Composite extension is enabled by default, however, fglrx does not yet support Composite with DRI. In order to to disable Composite you have to edit the xorg.conf file:

sudo gedit /etc/X11/xorg.conf

and add these lines at the end of the file:
File: /etc/X11/xorg.conf

Section "Extensions"
        Option  "Composite" "0"
EndSection


now 3D works!

---

