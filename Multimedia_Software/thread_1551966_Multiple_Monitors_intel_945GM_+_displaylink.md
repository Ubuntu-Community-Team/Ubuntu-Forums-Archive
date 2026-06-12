---
title: "Multiple Monitors intel 945GM + displaylink"
date: 2010-08-13
forum: Multimedia Software
---

### Post by inittab on 2010-08-13
Hello, I have a laptop in a docking station with an intel 945gm graphics chipset, off of the dock i have 2 20" lcds, one on vga, one on dvi.
I also have a usb vga adapter connected IOGEAR OU86USG4100545 with another 20" lcd which uses the display link driver. My problem is trying to get X to span all 3 monitors. Ubuntu's graphical monitor setup refuses to see all 3 monitors so I have tried to hancraft a xorg.conf file.

The closest I've gotten to making this work is the 2 monitors on the intel chipset will clone each other and the iogear will show another screen.

Here is /usr/lib/X11/xorg.conf.d/10-display.conf

```

#################################################

Section "Files"
ModulePath      "/usr/lib/xorg/modules"
ModulePath      "/usr/local/lib/xorg/modules"
ModulePath    "/usr/local/lib/xorg/modules/drivers"
EndSection

# xorg.conf (X.Org X Window System server configuration file)


############################ Devices ############################
Section "Device"
Identifier      "iogear"
driver          "displaylink"
Option  "fbdev" "/dev/fb1"
Option "IOGEAR GUC2015V" "middle"
EndSection

Section "Device"
Identifier      "intel"
Driver        "intel"
#Option  "fbdev" "/dev/fb0"
Option	"monitor-VGA1" "leftie"
Option	"monitor-LVDS1" "laptop"
Option	"monitor-DVI1" "rightie"
EndSection

######################### Monitors ##################################

####Laptop Screen####
Section "Monitor"
Identifier	"laptop"
Option	"Ignore" "true"
EndSection

####Left Screen####
Section "Monitor"
Identifier      "leftie"
Option "LeftOf" "middle"
EndSection

###Middle Screen####
Section "Monitor"
Identifier      "middle"
EndSection

####Right Screen####
Section "Monitor"
Identifier	"rightie"
Option "RightOf" "middle"
EndSection


##################### Screens ################################

####Leftie####
Section "Screen"
Identifier      "leftie"
Monitor         "leftie"
Device          "intel"
DefaultDepth    16
SubSection "Display"
Depth   16
Modes   "1680×1050"
EndSubSection
EndSection

####Middle####
Section "Screen"
Identifier      "middle"
Device          "iogear"
Monitor         "middle"
DefaultDepth    16
SubSection "Display"
Depth   16
Modes   "1280x1024"
EndSubSection
EndSection

####Rightie####
Section "Screen"
Identifier	"rightie"
Monitor		"rightie"
Device		"intel"
DefaultDepth	16
SubSection "Display"
Depth	16
Modes	"1680x1050"
EndSubSection
EndSection

###################Server layout##############################

Section "ServerLayout"
Identifier      "Server Layout"
Screen 0 "middle" 0 0
Screen 1 "leftie"
Screen 2 "rightie"
#Virtual		"4640x1050"
Option          "Xinerama" "On"
Option		"Clone"	"Off"
EndSection




```

This results in the following Xorg.0.log



```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux rknapp-laptop.local 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=5f2fcbab-f0dc-465a-9581-4f9388cb1fd8 ro quiet splash
Build Date: 16 June 2010  09:31:32AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug 13 01:15:54 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Server Layout"
(**) |-->Screen "middle" (0)
(**) |   |-->Monitor "middle"
(**) |   |-->Device "iogear"
(**) |-->Screen "leftie" (1)
(**) |   |-->Monitor "leftie"
(**) |   |-->Device "intel"
(**) |-->Screen "rightie" (2)
(**) |   |-->Monitor "rightie"
(**) |   |-->Device "intel"
(**) Option "Xinerama" "On"
(==) Automatically adding devices
(==) Automatically enabling devices
(**) Xinerama: enabled
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(**) ModulePath set to "/usr/lib/xorg/modules,/usr/local/lib/xorg/modules,/usr/local/lib/xorg/modules/drivers"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:0:2:0) 8086:27a2:1028:01c2 Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xeff00000/524288, 0xd0000000/268435456, 0xefec0000/262144, I/O @ 0x0000eff8/8
(--) PCI: (0:0:2:1) 8086:27a6:1028:01c2 Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xeff80000/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "displaylink"
(II) Loading /usr/lib/xorg/modules/drivers/displaylink_drv.so
(II) Module displaylink: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.1
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.9.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) DL: driver for : displaylink
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for displaylink
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(II) DL(0): using /dev/fb1
(II) DL(0): Manufacturer: DEL  Model: 4043  Serial#: 1096307029
(II) DL(0): Year: 2008  Week: 27
(II) DL(0): EDID Version: 1.3
(II) DL(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) DL(0): Sync:  Separate
(II) DL(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) DL(0): Gamma: 2.20
(II) DL(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) DL(0): Default color space is primary color space
(II) DL(0): First detailed timing is preferred mode
(II) DL(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) DL(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) DL(0): Supported established timings:
(II) DL(0): 720x400@70Hz
(II) DL(0): 640x480@60Hz
(II) DL(0): 640x480@75Hz
(II) DL(0): 800x600@60Hz
(II) DL(0): 800x600@75Hz
(II) DL(0): 1024x768@60Hz
(II) DL(0): 1024x768@75Hz
(II) DL(0): 1280x1024@75Hz
(II) DL(0): 1152x864@75Hz
(II) DL(0): Manufacturer's mask: 0
(II) DL(0): Supported standard timings:
(II) DL(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) DL(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) DL(0): #2: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) DL(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) DL(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) DL(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) DL(0): Supported detailed timing:
(II) DL(0): clock: 146.2 MHz   Image Size:  433 x 271 mm
(II) DL(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) DL(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) DL(0): Serial No: M743D871AXQU
(II) DL(0): Monitor name: DELL E2009W
(II) DL(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 160 MHz
(II) DL(0): EDID (in hex):
(II) DL(0): 	00ffffffffffff0010ac434055515841
(II) DL(0): 	1b120103682b1b78eeee95a3544c9926
(II) DL(0): 	0f5054a54b80714f8180b300950081c0
(II) DL(0): 	81000101010121399030621a274068b0
(II) DL(0): 	3600b10f1100001c000000ff004d3734
(II) DL(0): 	3344383731415851550a000000fc0044
(II) DL(0): 	454c4c204532303039570a20000000fd
(II) DL(0): 	00384b1e5310000a20202020202000e4
(**) DL(0): Depth 16, (--) framebuffer bpp 16
(==) DL(0): RGB weight 565
(==) DL(0): Default visual is TrueColor
(==) DL(0): Using gamma correction (1.0, 1.0, 1.0)
(II) DL(0): hardware: IOGEAR GUC2015V (video memory: 2560kB)
(**) DL(0): Option "fbdev" "/dev/fb1"
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) DL(0): Output IOGEAR GUC2015V using monitor section middle
(II) DL(0): EDID for output IOGEAR GUC2015V
(II) DL(0): Manufacturer: DEL  Model: 4043  Serial#: 1096307029
(II) DL(0): Year: 2008  Week: 27
(II) DL(0): EDID Version: 1.3
(II) DL(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) DL(0): Sync:  Separate
(II) DL(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) DL(0): Gamma: 2.20
(II) DL(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) DL(0): Default color space is primary color space
(II) DL(0): First detailed timing is preferred mode
(II) DL(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) DL(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) DL(0): Supported established timings:
(II) DL(0): 720x400@70Hz
(II) DL(0): 640x480@60Hz
(II) DL(0): 640x480@75Hz
(II) DL(0): 800x600@60Hz
(II) DL(0): 800x600@75Hz
(II) DL(0): 1024x768@60Hz
(II) DL(0): 1024x768@75Hz
(II) DL(0): 1280x1024@75Hz
(II) DL(0): 1152x864@75Hz
(II) DL(0): Manufacturer's mask: 0
(II) DL(0): Supported standard timings:
(II) DL(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) DL(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) DL(0): #2: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) DL(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) DL(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) DL(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) DL(0): Supported detailed timing:
(II) DL(0): clock: 146.2 MHz   Image Size:  433 x 271 mm
(II) DL(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) DL(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) DL(0): Serial No: M743D871AXQU
(II) DL(0): Monitor name: DELL E2009W
(II) DL(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 160 MHz
(II) DL(0): EDID (in hex):
(II) DL(0): 	00ffffffffffff0010ac434055515841
(II) DL(0): 	1b120103682b1b78eeee95a3544c9926
(II) DL(0): 	0f5054a54b80714f8180b300950081c0
(II) DL(0): 	81000101010121399030621a274068b0
(II) DL(0): 	3600b10f1100001c000000ff004d3734
(II) DL(0): 	3344383731415851550a000000fc0044
(II) DL(0): 	454c4c204532303039570a20000000fd
(II) DL(0): 	00384b1e5310000a20202020202000e4
(II) DL(0): EDID vendor "DEL", prod id 16451
(II) DL(0): Using EDID range info for horizontal sync
(II) DL(0): Using EDID range info for vertical refresh
(II) DL(0): Printing DDC gathered Modelines:
(II) DL(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) DL(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) DL(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) DL(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) DL(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) DL(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) DL(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) DL(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) DL(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) DL(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) DL(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) DL(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) DL(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) DL(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) DL(0): EDID vendor "DEL", prod id 16451
(II) DL(0): EDID for output IOGEAR GUC2015V
(II) DL(0): Manufacturer: DEL  Model: 4043  Serial#: 1096307029
(II) DL(0): Year: 2008  Week: 27
(II) DL(0): EDID Version: 1.3
(II) DL(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) DL(0): Sync:  Separate
(II) DL(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) DL(0): Gamma: 2.20
(II) DL(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) DL(0): Default color space is primary color space
(II) DL(0): First detailed timing is preferred mode
(II) DL(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) DL(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) DL(0): Supported established timings:
(II) DL(0): 720x400@70Hz
(II) DL(0): 640x480@60Hz
(II) DL(0): 640x480@75Hz
(II) DL(0): 800x600@60Hz
(II) DL(0): 800x600@75Hz
(II) DL(0): 1024x768@60Hz
(II) DL(0): 1024x768@75Hz
(II) DL(0): 1280x1024@75Hz
(II) DL(0): 1152x864@75Hz
(II) DL(0): Manufacturer's mask: 0
(II) DL(0): Supported standard timings:
(II) DL(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) DL(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) DL(0): #2: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) DL(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) DL(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) DL(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) DL(0): Supported detailed timing:
(II) DL(0): clock: 146.2 MHz   Image Size:  433 x 271 mm
(II) DL(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) DL(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) DL(0): Serial No: M743D871AXQU
(II) DL(0): Monitor name: DELL E2009W
(II) DL(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 160 MHz
(II) DL(0): EDID (in hex):
(II) DL(0): 	00ffffffffffff0010ac434055515841
(II) DL(0): 	1b120103682b1b78eeee95a3544c9926
(II) DL(0): 	0f5054a54b80714f8180b300950081c0
(II) DL(0): 	81000101010121399030621a274068b0
(II) DL(0): 	3600b10f1100001c000000ff004d3734
(II) DL(0): 	3344383731415851550a000000fc0044
(II) DL(0): 	454c4c204532303039570a20000000fd
(II) DL(0): 	00384b1e5310000a20202020202000e4
(II) DL(0): EDID vendor "DEL", prod id 16451
(II) DL(0): Using hsync ranges from config file
(II) DL(0): Using vrefresh ranges from config file
(II) DL(0): Printing DDC gathered Modelines:
(II) DL(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) DL(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) DL(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) DL(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) DL(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) DL(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) DL(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) DL(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) DL(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) DL(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) DL(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) DL(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) DL(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) DL(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) DL(0): EDID vendor "DEL", prod id 16451
(II) DL(0): Not using mode "1680x1050" (height too large for virtual size)
(II) DL(0): Not using mode "1440x900" (width too large for virtual size)
(II) DL(0): Printing probed modes for output IOGEAR GUC2015V
(II) DL(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) DL(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) DL(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) DL(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) DL(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) DL(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) DL(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) DL(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) DL(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) DL(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) DL(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) DL(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) DL(0): Output IOGEAR GUC2015V connected
(II) DL(0): Using user preference for initial modes
(II) DL(0): Output IOGEAR GUC2015V using initial mode 1280x1024
(II) DL(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(--) DL(0): Virtual size is 1280x1024 (pitch 0)
(**) DL(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) DL(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) DL(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) DL(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) DL(0):  Driver mode "1280x800": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 59.8 Hz
(II) DL(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(**) DL(0):  Driver mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) DL(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) DL(0):  Driver mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) DL(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(**) DL(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) DL(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) DL(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) DL(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) DL(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) DL(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) DL(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
(II) DL(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) DL(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) DL(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) DL(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
(II) DL(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) DL(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
(II) DL(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) DL(0): Display dimensions: (430, 270) mm
(**) DL(0): DPI set to (75, 96)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 13, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 13, (OK)
drmOpenByBusid: drmOpenMinor returns 13
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(**) intel(1): Depth 16, (--) framebuffer bpp 16
(==) intel(1): RGB weight 565
(==) intel(1): Default visual is TrueColor
(II) intel(1): Integrated Graphics Chipset: Intel(R) 945GM
(--) intel(1): Chipset: "945GM"
(II) intel(1): Output VGA1 using monitor section leftie
(**) intel(1): Option "LeftOf" "middle"
(II) intel(1): Output LVDS1 using monitor section laptop
(**) intel(1): Option "Ignore" "true"
(II) intel(1): Output DVI1 using monitor section rightie
(**) intel(1): Option "RightOf" "middle"
(II) intel(1): Output TV1 has no monitor section
(II) intel(1): EDID for output VGA1
(II) intel(1): Manufacturer: DEL  Model: 4043  Serial#: 1096239189
(II) intel(1): Year: 2008  Week: 27
(II) intel(1): EDID Version: 1.3
(II) intel(1): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(1): Sync:  Separate
(II) intel(1): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) intel(1): Gamma: 2.20
(II) intel(1): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) intel(1): Default color space is primary color space
(II) intel(1): First detailed timing is preferred mode
(II) intel(1): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(1): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) intel(1): Supported established timings:
(II) intel(1): 720x400@70Hz
(II) intel(1): 640x480@60Hz
(II) intel(1): 640x480@75Hz
(II) intel(1): 800x600@60Hz
(II) intel(1): 800x600@75Hz
(II) intel(1): 1024x768@60Hz
(II) intel(1): 1024x768@75Hz
(II) intel(1): 1280x1024@75Hz
(II) intel(1): 1152x864@75Hz
(II) intel(1): Manufacturer's mask: 0
(II) intel(1): Supported standard timings:
(II) intel(1): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(1): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(1): #2: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(1): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(1): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) intel(1): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(1): Supported detailed timing:
(II) intel(1): clock: 146.2 MHz   Image Size:  433 x 271 mm
(II) intel(1): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) intel(1): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) intel(1): Serial No: M743D871AWHU
(II) intel(1): Monitor name: DELL E2009W
(II) intel(1): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 160 MHz
(II) intel(1): EDID (in hex):
(II) intel(1): 	00ffffffffffff0010ac434055485741
(II) intel(1): 	1b120103682b1b78eeee95a3544c9926
(II) intel(1): 	0f5054a54b80714f8180b300950081c0
(II) intel(1): 	81000101010121399030621a274068b0
(II) intel(1): 	3600b10f1100001c000000ff004d3734
(II) intel(1): 	3344383731415748550a000000fc0044
(II) intel(1): 	454c4c204532303039570a20000000fd
(II) intel(1): 	00384b1e5310000a20202020202000f8
(II) intel(1): EDID vendor "DEL", prod id 16451
(II) intel(1): Using EDID range info for horizontal sync
(II) intel(1): Using EDID range info for vertical refresh
(II) intel(1): Printing DDC gathered Modelines:
(II) intel(1): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(1): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(1): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(1): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(1): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(1): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(1): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(1): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(1): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(1): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(1): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(1): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(1): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) intel(1): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(1): Printing probed modes for output VGA1
(II) intel(1): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(1): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(1): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(1): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(1): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz)
(II) intel(1): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(1): Modeline "1280x720"x60.0   74.44  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.7 kHz)
(II) intel(1): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(1): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(1): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(1): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(1): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(1): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(1): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(1): EDID for output DVI1
(II) intel(1): Manufacturer: DEL  Model: 4044  Serial#: 1096234069
(II) intel(1): Year: 2008  Week: 27
(II) intel(1): EDID Version: 1.3
(II) intel(1): Digital Display Input
(II) intel(1): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) intel(1): Gamma: 2.20
(II) intel(1): DPMS capabilities: StandBy Suspend Off
(II) intel(1): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(1): Default color space is primary color space
(II) intel(1): First detailed timing is preferred mode
(II) intel(1): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(1): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) intel(1): Supported established timings:
(II) intel(1): 720x400@70Hz
(II) intel(1): 640x480@60Hz
(II) intel(1): 640x480@75Hz
(II) intel(1): 800x600@60Hz
(II) intel(1): 800x600@75Hz
(II) intel(1): 1024x768@60Hz
(II) intel(1): 1024x768@75Hz
(II) intel(1): 1280x1024@75Hz
(II) intel(1): 1152x864@75Hz
(II) intel(1): Manufacturer's mask: 0
(II) intel(1): Supported standard timings:
(II) intel(1): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(1): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(1): #2: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(1): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(1): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) intel(1): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(1): Supported detailed timing:
(II) intel(1): clock: 146.2 MHz   Image Size:  433 x 271 mm
(II) intel(1): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) intel(1): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) intel(1): Serial No: M743D871AW4U
(II) intel(1): Monitor name: DELL E2009W
(II) intel(1): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 160 MHz
(II) intel(1): EDID (in hex):
(II) intel(1): 	00ffffffffffff0010ac444055345741
(II) intel(1): 	1b120103802b1b78eeee95a3544c9926
(II) intel(1): 	0f5054a54b80714f8180b300950081c0
(II) intel(1): 	81000101010121399030621a274068b0
(II) intel(1): 	3600b10f1100001c000000ff004d3734
(II) intel(1): 	3344383731415734550a000000fc0044
(II) intel(1): 	454c4c204532303039570a20000000fd
(II) intel(1): 	00384b1e5310000a2020202020200007
(II) intel(1): Printing probed modes for output DVI1
(II) intel(1): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(1): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(1): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(1): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(1): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz)
(II) intel(1): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(1): Modeline "1280x720"x60.0   74.44  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.7 kHz)
(II) intel(1): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(1): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(1): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(1): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(1): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(1): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(1): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(1): EDID for output TV1
(II) intel(1): Output VGA1 connected
(II) intel(1): Output DVI1 connected
(II) intel(1): Output TV1 disconnected
(II) intel(1): Using user preference for initial modes
(II) intel(1): Output VGA1 using initial mode 1680x1050
(II) intel(1): Output DVI1 using initial mode 1680x1050
(EE) intel(1): Cannot position output VGA1 relative to unknown output middle
(EE) intel(1): Cannot position output DVI1 relative to unknown output middle
(II) intel(1): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(==) intel(1): video overlay key set to 0x83e
(**) intel(1): Display dimensions: (430, 270) mm
(**) intel(1): DPI set to (99, 98)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/lib/xorg/modules/libfb.so
(==) DL(0): Backing store disabled
(==) DL(0): DPMS enabled
(II) DL(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) intel(1): [DRI2] Setup complete
(**) intel(1): Kernel mode setting active, disabling FBC.
(**) intel(1): Framebuffer compression disabled
(**) intel(1): Tiling enabled
(**) intel(1): SwapBuffers wait enabled
(==) intel(1): VideoRam: 262144 KB
(II) intel(1): Attempting memory allocation with tiled buffers.
(II) intel(1): Tiled allocation successful.
(II) UXA(1): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(1): Backing store disabled
(==) intel(1): Silken mouse enabled
(II) intel(1): Initializing HW Cursor
(II) intel(1): No memory allocations
(II) intel(1): RandR 1.2 enabled, ignore the following RandR disabled message.
(==) intel(1): DPMS enabled
(==) intel(1): Intel XvMC decoder disabled
(II) intel(1): Set up textured video
(II) intel(1): Set up overlay video
(II) intel(1): direct rendering: DRI2 Enabled
(WW) intel(1): Option "LeftOf" is not used
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 1
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event5)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Video Bus (/dev/input/event6)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event6"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Lid Switch (/dev/input/event0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event2)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HDA Intel Mic at Ext Left Jack (/dev/input/event14)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel HP Out at Ext Left Jack (/dev/input/event15)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event8)
(**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Dell Dell USB Keyboard: always reports core events
(**) Dell Dell USB Keyboard: Device: "/dev/input/event8"
(II) Dell Dell USB Keyboard: Found keys
(II) Dell Dell USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event9)
(**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Dell Dell USB Keyboard: always reports core events
(**) Dell Dell USB Keyboard: Device: "/dev/input/event9"
(II) Dell Dell USB Keyboard: Found absolute axes
(II) Dell Dell USB Keyboard: Found keys
(II) Dell Dell USB Keyboard: Configuring as mouse
(II) Dell Dell USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) Dell Dell USB Keyboard: initialized for absolute axes.
(II) config/udev: Adding input device Dell Dell USB Optical Mouse (/dev/input/event10)
(**) Dell Dell USB Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) Dell Dell USB Optical Mouse: always reports core events
(**) Dell Dell USB Optical Mouse: Device: "/dev/input/event10"
(II) Dell Dell USB Optical Mouse: Found 3 mouse buttons
(II) Dell Dell USB Optical Mouse: Found scroll wheel(s)
(II) Dell Dell USB Optical Mouse: Found relative axes
(II) Dell Dell USB Optical Mouse: Found x and y relative axes
(II) Dell Dell USB Optical Mouse: Configuring as mouse
(**) Dell Dell USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Dell Dell USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Dell Dell USB Optical Mouse" (type: MOUSE)
(II) Dell Dell USB Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device Dell Dell USB Optical Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech Logitech USB Headset (/dev/input/event7)
(**) Logitech Logitech USB Headset: Applying InputClass "evdev keyboard catchall"
(**) Logitech Logitech USB Headset: always reports core events
(**) Logitech Logitech USB Headset: Device: "/dev/input/event7"
(II) Logitech Logitech USB Headset: Found keys
(II) Logitech Logitech USB Headset: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech Logitech USB Headset" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device DualPoint Stick (/dev/input/event12)
(**) DualPoint Stick: Applying InputClass "evdev pointer catchall"
(**) DualPoint Stick: always reports core events
(**) DualPoint Stick: Device: "/dev/input/event12"
(II) DualPoint Stick: Found 3 mouse buttons
(II) DualPoint Stick: Found relative axes
(II) DualPoint Stick: Found x and y relative axes
(II) DualPoint Stick: Configuring as mouse
(**) DualPoint Stick: YAxisMapping: buttons 4 and 5
(**) DualPoint Stick: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "DualPoint Stick" (type: MOUSE)
(II) DualPoint Stick: initialized for relative axes.
(II) config/udev: Adding input device DualPoint Stick (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/event13)
(**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "evdev pointer catchall"
(**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "evdev touchpad catchall"
(**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event13"
(II) AlpsPS/2 ALPS DualPoint TouchPad: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS DualPoint TouchPad: y-axis range 0 - 767
(II) AlpsPS/2 ALPS DualPoint TouchPad: pressure range 0 - 127
(II) AlpsPS/2 ALPS DualPoint TouchPad: finger width range 0 - 0
(II) AlpsPS/2 ALPS DualPoint TouchPad: buttons: left right middle
(--) AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
(**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS DualPoint TouchPad" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration profile 0
(**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration factor: 2.000
(**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration threshold: 4
(--) AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
(II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/mouse3)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event11)
(**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
(**) Dell WMI hotkeys: always reports core events
(**) Dell WMI hotkeys: Device: "/dev/input/event11"
(II) Dell WMI hotkeys: Found keys
(II) Dell WMI hotkeys: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)

note the two EE lines.

(EE) intel(1): Cannot position output VGA1 relative to unknown output middle
(EE) intel(1): Cannot position output DVI1 relative to unknown output middle

yet earlier in the log its perfectly aware of the output middle

(**) |-->Screen "middle" (0)
(**) |   |-->Monitor "middle"
(II) DL(0): Output IOGEAR GUC2015V using monitor section middle

```
This clones all 3 screens with the mouse starting on the middle screen (not visible on the other 2 screens) if i move the mouse over to the left or to the right it will then get stuck on the 2 intel screens and not be able to make it back to the displaylink screen (everything else is cloned except the mouse). Note the Normal Gnome menu is nowhere to be found.


I have also tried the following config:


```

#################################################

Section "Files"
ModulePath      "/usr/lib/xorg/modules"
ModulePath      "/usr/local/lib/xorg/modules"
ModulePath    "/usr/local/lib/xorg/modules/drivers"
EndSection

# xorg.conf (X.Org X Window System server configuration file)


############################ Devices ############################
Section "Device"
Identifier      "iogear"
driver          "displaylink"
Option  "fbdev" "/dev/fb1"
Option "IOGEAR GUC2015V" "middle"
EndSection

Section "Device"
Identifier      "intel"
Driver        "intel"
#Option  "fbdev" "/dev/fb0"
Option	"monitor-VGA1" "leftie"
Option	"monitor-LVDS1" "laptop"
Option	"monitor-DVI1" "rightie"
EndSection

######################### Monitors ##################################

####Laptop Screen####
Section "Monitor"
Identifier	"laptop"
Option	"Ignore" "true"
EndSection

####Left Screen####
Section "Monitor"
Identifier      "leftie"
#Option "LeftOf" "middle"
EndSection

###Middle Screen####
Section "Monitor"
Identifier      "middle"
EndSection

####Right Screen####
Section "Monitor"
Identifier	"rightie"
#Option "RightOf" "middle"
EndSection


##################### Screens ################################

####Leftie####
Section "Screen"
Identifier      "leftie"
Monitor         "leftie"
Device          "intel"
DefaultDepth    16
SubSection "Display"
Depth   16
Modes   "1680×1050"
EndSubSection
EndSection

####Middle####
Section "Screen"
Identifier      "middle"
Device          "iogear"
Monitor         "middle"
DefaultDepth    16
SubSection "Display"
Depth   16
Modes   "1280x1024"
EndSubSection
EndSection

####Rightie####
Section "Screen"
Identifier	"rightie"
Monitor		"rightie"
Device		"intel"
DefaultDepth	16
SubSection "Display"
Depth	16
Modes	"1680x1050"
EndSubSection
EndSection

###################Server layout##############################

Section "ServerLayout"
Identifier      "Server Layout"
Screen 0 "middle" 0 0
Screen 1 "leftie" LeftOf "middle"
Screen 2 "rightie" RightOf "middle"
#Virtual		"4640x1050"
Option          "Xinerama" "On"
Option		"Clone"	"Off"
EndSection

```

This results in the following Xorg.0.log

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux rknapp-laptop.local 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=5f2fcbab-f0dc-465a-9581-4f9388cb1fd8 ro quiet splash
Build Date: 16 June 2010  09:31:32AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug 13 01:19:17 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Server Layout"
(**) |-->Screen "middle" (0)
(**) |   |-->Monitor "middle"
(**) |   |-->Device "iogear"
(**) |-->Screen "leftie" (1)
(**) |   |-->Monitor "leftie"
(**) |   |-->Device "intel"
(**) |-->Screen "rightie" (2)
(**) |   |-->Monitor "rightie"
(**) |   |-->Device "intel"
(**) Option "Xinerama" "On"
(==) Automatically adding devices
(==) Automatically enabling devices
(**) Xinerama: enabled
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(**) ModulePath set to "/usr/lib/xorg/modules,/usr/local/lib/xorg/modules,/usr/local/lib/xorg/modules/drivers"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:0:2:0) 8086:27a2:1028:01c2 Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xeff00000/524288, 0xd0000000/268435456, 0xefec0000/262144, I/O @ 0x0000eff8/8
(--) PCI: (0:0:2:1) 8086:27a6:1028:01c2 Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xeff80000/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "displaylink"
(II) Loading /usr/lib/xorg/modules/drivers/displaylink_drv.so
(II) Module displaylink: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.1
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.9.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) DL: driver for : displaylink
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for displaylink
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(II) DL(0): using /dev/fb1
(II) DL(0): Manufacturer: DEL  Model: 4043  Serial#: 1096307029
(II) DL(0): Year: 2008  Week: 27
(II) DL(0): EDID Version: 1.3
(II) DL(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) DL(0): Sync:  Separate
(II) DL(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) DL(0): Gamma: 2.20
(II) DL(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) DL(0): Default color space is primary color space
(II) DL(0): First detailed timing is preferred mode
(II) DL(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) DL(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) DL(0): Supported established timings:
(II) DL(0): 720x400@70Hz
(II) DL(0): 640x480@60Hz
(II) DL(0): 640x480@75Hz
(II) DL(0): 800x600@60Hz
(II) DL(0): 800x600@75Hz
(II) DL(0): 1024x768@60Hz
(II) DL(0): 1024x768@75Hz
(II) DL(0): 1280x1024@75Hz
(II) DL(0): 1152x864@75Hz
(II) DL(0): Manufacturer's mask: 0
(II) DL(0): Supported standard timings:
(II) DL(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) DL(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) DL(0): #2: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) DL(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) DL(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) DL(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) DL(0): Supported detailed timing:
(II) DL(0): clock: 146.2 MHz   Image Size:  433 x 271 mm
(II) DL(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) DL(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) DL(0): Serial No: M743D871AXQU
(II) DL(0): Monitor name: DELL E2009W
(II) DL(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 160 MHz
(II) DL(0): EDID (in hex):
(II) DL(0): 	00ffffffffffff0010ac434055515841
(II) DL(0): 	1b120103682b1b78eeee95a3544c9926
(II) DL(0): 	0f5054a54b80714f8180b300950081c0
(II) DL(0): 	81000101010121399030621a274068b0
(II) DL(0): 	3600b10f1100001c000000ff004d3734
(II) DL(0): 	3344383731415851550a000000fc0044
(II) DL(0): 	454c4c204532303039570a20000000fd
(II) DL(0): 	00384b1e5310000a20202020202000e4
(**) DL(0): Depth 16, (--) framebuffer bpp 16
(==) DL(0): RGB weight 565
(==) DL(0): Default visual is TrueColor
(==) DL(0): Using gamma correction (1.0, 1.0, 1.0)
(II) DL(0): hardware: IOGEAR GUC2015V (video memory: 2560kB)
(**) DL(0): Option "fbdev" "/dev/fb1"
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) DL(0): Output IOGEAR GUC2015V using monitor section middle
(II) DL(0): EDID for output IOGEAR GUC2015V
(II) DL(0): Manufacturer: DEL  Model: 4043  Serial#: 1096307029
(II) DL(0): Year: 2008  Week: 27
(II) DL(0): EDID Version: 1.3
(II) DL(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) DL(0): Sync:  Separate
(II) DL(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) DL(0): Gamma: 2.20
(II) DL(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) DL(0): Default color space is primary color space
(II) DL(0): First detailed timing is preferred mode
(II) DL(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) DL(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) DL(0): Supported established timings:
(II) DL(0): 720x400@70Hz
(II) DL(0): 640x480@60Hz
(II) DL(0): 640x480@75Hz
(II) DL(0): 800x600@60Hz
(II) DL(0): 800x600@75Hz
(II) DL(0): 1024x768@60Hz
(II) DL(0): 1024x768@75Hz
(II) DL(0): 1280x1024@75Hz
(II) DL(0): 1152x864@75Hz
(II) DL(0): Manufacturer's mask: 0
(II) DL(0): Supported standard timings:
(II) DL(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) DL(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) DL(0): #2: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) DL(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) DL(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) DL(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) DL(0): Supported detailed timing:
(II) DL(0): clock: 146.2 MHz   Image Size:  433 x 271 mm
(II) DL(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) DL(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) DL(0): Serial No: M743D871AXQU
(II) DL(0): Monitor name: DELL E2009W
(II) DL(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 160 MHz
(II) DL(0): EDID (in hex):
(II) DL(0): 	00ffffffffffff0010ac434055515841
(II) DL(0): 	1b120103682b1b78eeee95a3544c9926
(II) DL(0): 	0f5054a54b80714f8180b300950081c0
(II) DL(0): 	81000101010121399030621a274068b0
(II) DL(0): 	3600b10f1100001c000000ff004d3734
(II) DL(0): 	3344383731415851550a000000fc0044
(II) DL(0): 	454c4c204532303039570a20000000fd
(II) DL(0): 	00384b1e5310000a20202020202000e4
(II) DL(0): EDID vendor "DEL", prod id 16451
(II) DL(0): Using EDID range info for horizontal sync
(II) DL(0): Using EDID range info for vertical refresh
(II) DL(0): Printing DDC gathered Modelines:
(II) DL(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) DL(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) DL(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) DL(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) DL(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) DL(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) DL(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) DL(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) DL(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) DL(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) DL(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) DL(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) DL(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) DL(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) DL(0): EDID vendor "DEL", prod id 16451
(II) DL(0): EDID for output IOGEAR GUC2015V
(II) DL(0): Manufacturer: DEL  Model: 4043  Serial#: 1096307029
(II) DL(0): Year: 2008  Week: 27
(II) DL(0): EDID Version: 1.3
(II) DL(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) DL(0): Sync:  Separate
(II) DL(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) DL(0): Gamma: 2.20
(II) DL(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) DL(0): Default color space is primary color space
(II) DL(0): First detailed timing is preferred mode
(II) DL(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) DL(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) DL(0): Supported established timings:
(II) DL(0): 720x400@70Hz
(II) DL(0): 640x480@60Hz
(II) DL(0): 640x480@75Hz
(II) DL(0): 800x600@60Hz
(II) DL(0): 800x600@75Hz
(II) DL(0): 1024x768@60Hz
(II) DL(0): 1024x768@75Hz
(II) DL(0): 1280x1024@75Hz
(II) DL(0): 1152x864@75Hz
(II) DL(0): Manufacturer's mask: 0
(II) DL(0): Supported standard timings:
(II) DL(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) DL(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) DL(0): #2: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) DL(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) DL(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) DL(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) DL(0): Supported detailed timing:
(II) DL(0): clock: 146.2 MHz   Image Size:  433 x 271 mm
(II) DL(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) DL(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) DL(0): Serial No: M743D871AXQU
(II) DL(0): Monitor name: DELL E2009W
(II) DL(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 160 MHz
(II) DL(0): EDID (in hex):
(II) DL(0): 	00ffffffffffff0010ac434055515841
(II) DL(0): 	1b120103682b1b78eeee95a3544c9926
(II) DL(0): 	0f5054a54b80714f8180b300950081c0
(II) DL(0): 	81000101010121399030621a274068b0
(II) DL(0): 	3600b10f1100001c000000ff004d3734
(II) DL(0): 	3344383731415851550a000000fc0044
(II) DL(0): 	454c4c204532303039570a20000000fd
(II) DL(0): 	00384b1e5310000a20202020202000e4
(II) DL(0): EDID vendor "DEL", prod id 16451
(II) DL(0): Using hsync ranges from config file
(II) DL(0): Using vrefresh ranges from config file
(II) DL(0): Printing DDC gathered Modelines:
(II) DL(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) DL(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) DL(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) DL(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) DL(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) DL(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) DL(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) DL(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) DL(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) DL(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) DL(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) DL(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) DL(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) DL(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) DL(0): EDID vendor "DEL", prod id 16451
(II) DL(0): Not using mode "1680x1050" (height too large for virtual size)
(II) DL(0): Not using mode "1440x900" (width too large for virtual size)
(II) DL(0): Printing probed modes for output IOGEAR GUC2015V
(II) DL(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) DL(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) DL(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) DL(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) DL(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) DL(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) DL(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) DL(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) DL(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) DL(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) DL(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) DL(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) DL(0): Output IOGEAR GUC2015V connected
(II) DL(0): Using user preference for initial modes
(II) DL(0): Output IOGEAR GUC2015V using initial mode 1280x1024
(II) DL(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(--) DL(0): Virtual size is 1280x1024 (pitch 0)
(**) DL(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) DL(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) DL(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) DL(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) DL(0):  Driver mode "1280x800": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 59.8 Hz
(II) DL(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(**) DL(0):  Driver mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) DL(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) DL(0):  Driver mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) DL(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(**) DL(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) DL(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) DL(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) DL(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) DL(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) DL(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) DL(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
(II) DL(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) DL(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) DL(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) DL(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
(II) DL(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) DL(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
(II) DL(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) DL(0): Display dimensions: (430, 270) mm
(**) DL(0): DPI set to (75, 96)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 13, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 13, (OK)
drmOpenByBusid: drmOpenMinor returns 13
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(**) intel(1): Depth 16, (--) framebuffer bpp 16
(==) intel(1): RGB weight 565
(==) intel(1): Default visual is TrueColor
(II) intel(1): Integrated Graphics Chipset: Intel(R) 945GM
(--) intel(1): Chipset: "945GM"
(II) intel(1): Output VGA1 using monitor section leftie
(II) intel(1): Output LVDS1 using monitor section laptop
(**) intel(1): Option "Ignore" "true"
(II) intel(1): Output DVI1 using monitor section rightie
(II) intel(1): Output TV1 has no monitor section
(II) intel(1): EDID for output VGA1
(II) intel(1): Manufacturer: DEL  Model: 4043  Serial#: 1096239189
(II) intel(1): Year: 2008  Week: 27
(II) intel(1): EDID Version: 1.3
(II) intel(1): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(1): Sync:  Separate
(II) intel(1): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) intel(1): Gamma: 2.20
(II) intel(1): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) intel(1): Default color space is primary color space
(II) intel(1): First detailed timing is preferred mode
(II) intel(1): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(1): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) intel(1): Supported established timings:
(II) intel(1): 720x400@70Hz
(II) intel(1): 640x480@60Hz
(II) intel(1): 640x480@75Hz
(II) intel(1): 800x600@60Hz
(II) intel(1): 800x600@75Hz
(II) intel(1): 1024x768@60Hz
(II) intel(1): 1024x768@75Hz
(II) intel(1): 1280x1024@75Hz
(II) intel(1): 1152x864@75Hz
(II) intel(1): Manufacturer's mask: 0
(II) intel(1): Supported standard timings:
(II) intel(1): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(1): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(1): #2: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(1): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(1): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) intel(1): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(1): Supported detailed timing:
(II) intel(1): clock: 146.2 MHz   Image Size:  433 x 271 mm
(II) intel(1): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) intel(1): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) intel(1): Serial No: M743D871AWHU
(II) intel(1): Monitor name: DELL E2009W
(II) intel(1): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 160 MHz
(II) intel(1): EDID (in hex):
(II) intel(1): 	00ffffffffffff0010ac434055485741
(II) intel(1): 	1b120103682b1b78eeee95a3544c9926
(II) intel(1): 	0f5054a54b80714f8180b300950081c0
(II) intel(1): 	81000101010121399030621a274068b0
(II) intel(1): 	3600b10f1100001c000000ff004d3734
(II) intel(1): 	3344383731415748550a000000fc0044
(II) intel(1): 	454c4c204532303039570a20000000fd
(II) intel(1): 	00384b1e5310000a20202020202000f8
(II) intel(1): EDID vendor "DEL", prod id 16451
(II) intel(1): Using EDID range info for horizontal sync
(II) intel(1): Using EDID range info for vertical refresh
(II) intel(1): Printing DDC gathered Modelines:
(II) intel(1): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(1): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(1): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(1): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(1): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(1): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(1): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(1): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(1): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(1): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(1): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(1): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(1): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) intel(1): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(1): Printing probed modes for output VGA1
(II) intel(1): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(1): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(1): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(1): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(1): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz)
(II) intel(1): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(1): Modeline "1280x720"x60.0   74.44  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.7 kHz)
(II) intel(1): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(1): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(1): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(1): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(1): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(1): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(1): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(1): EDID for output DVI1
(II) intel(1): Manufacturer: DEL  Model: 4044  Serial#: 1096234069
(II) intel(1): Year: 2008  Week: 27
(II) intel(1): EDID Version: 1.3
(II) intel(1): Digital Display Input
(II) intel(1): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) intel(1): Gamma: 2.20
(II) intel(1): DPMS capabilities: StandBy Suspend Off
(II) intel(1): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(1): Default color space is primary color space
(II) intel(1): First detailed timing is preferred mode
(II) intel(1): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(1): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) intel(1): Supported established timings:
(II) intel(1): 720x400@70Hz
(II) intel(1): 640x480@60Hz
(II) intel(1): 640x480@75Hz
(II) intel(1): 800x600@60Hz
(II) intel(1): 800x600@75Hz
(II) intel(1): 1024x768@60Hz
(II) intel(1): 1024x768@75Hz
(II) intel(1): 1280x1024@75Hz
(II) intel(1): 1152x864@75Hz
(II) intel(1): Manufacturer's mask: 0
(II) intel(1): Supported standard timings:
(II) intel(1): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(1): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(1): #2: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(1): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(1): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) intel(1): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(1): Supported detailed timing:
(II) intel(1): clock: 146.2 MHz   Image Size:  433 x 271 mm
(II) intel(1): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) intel(1): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) intel(1): Serial No: M743D871AW4U
(II) intel(1): Monitor name: DELL E2009W
(II) intel(1): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 160 MHz
(II) intel(1): EDID (in hex):
(II) intel(1): 	00ffffffffffff0010ac444055345741
(II) intel(1): 	1b120103802b1b78eeee95a3544c9926
(II) intel(1): 	0f5054a54b80714f8180b300950081c0
(II) intel(1): 	81000101010121399030621a274068b0
(II) intel(1): 	3600b10f1100001c000000ff004d3734
(II) intel(1): 	3344383731415734550a000000fc0044
(II) intel(1): 	454c4c204532303039570a20000000fd
(II) intel(1): 	00384b1e5310000a2020202020200007
(II) intel(1): Printing probed modes for output DVI1
(II) intel(1): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(1): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(1): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(1): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(1): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz)
(II) intel(1): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(1): Modeline "1280x720"x60.0   74.44  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.7 kHz)
(II) intel(1): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(1): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(1): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(1): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(1): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(1): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(1): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(1): EDID for output TV1
(II) intel(1): Output VGA1 connected
(II) intel(1): Output DVI1 connected
(II) intel(1): Output TV1 disconnected
(II) intel(1): Using exact sizes for initial modes
(II) intel(1): Output VGA1 using initial mode 1680x1050
(II) intel(1): Output DVI1 using initial mode 1680x1050
(II) intel(1): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(==) intel(1): video overlay key set to 0x83e
(**) intel(1): Display dimensions: (430, 270) mm
(**) intel(1): DPI set to (99, 98)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/lib/xorg/modules/libfb.so
(==) DL(0): Backing store disabled
(==) DL(0): DPMS enabled
(II) DL(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) intel(1): [DRI2] Setup complete
(**) intel(1): Kernel mode setting active, disabling FBC.
(**) intel(1): Framebuffer compression disabled
(**) intel(1): Tiling enabled
(**) intel(1): SwapBuffers wait enabled
(==) intel(1): VideoRam: 262144 KB
(II) intel(1): Attempting memory allocation with tiled buffers.
(II) intel(1): Tiled allocation successful.
(II) UXA(1): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(1): Backing store disabled
(==) intel(1): Silken mouse enabled
(II) intel(1): Initializing HW Cursor
(II) intel(1): No memory allocations
(II) intel(1): RandR 1.2 enabled, ignore the following RandR disabled message.
(==) intel(1): DPMS enabled
(==) intel(1): Intel XvMC decoder disabled
(II) intel(1): Set up textured video
(II) intel(1): Set up overlay video
(II) intel(1): direct rendering: DRI2 Enabled
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 1
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event5)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Video Bus (/dev/input/event6)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event6"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Lid Switch (/dev/input/event0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event2)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HDA Intel Mic at Ext Left Jack (/dev/input/event14)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel HP Out at Ext Left Jack (/dev/input/event15)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event8)
(**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Dell Dell USB Keyboard: always reports core events
(**) Dell Dell USB Keyboard: Device: "/dev/input/event8"
(II) Dell Dell USB Keyboard: Found keys
(II) Dell Dell USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event9)
(**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Dell Dell USB Keyboard: always reports core events
(**) Dell Dell USB Keyboard: Device: "/dev/input/event9"
(II) Dell Dell USB Keyboard: Found absolute axes
(II) Dell Dell USB Keyboard: Found keys
(II) Dell Dell USB Keyboard: Configuring as mouse
(II) Dell Dell USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) Dell Dell USB Keyboard: initialized for absolute axes.
(II) config/udev: Adding input device Dell Dell USB Optical Mouse (/dev/input/event10)
(**) Dell Dell USB Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) Dell Dell USB Optical Mouse: always reports core events
(**) Dell Dell USB Optical Mouse: Device: "/dev/input/event10"
(II) Dell Dell USB Optical Mouse: Found 3 mouse buttons
(II) Dell Dell USB Optical Mouse: Found scroll wheel(s)
(II) Dell Dell USB Optical Mouse: Found relative axes
(II) Dell Dell USB Optical Mouse: Found x and y relative axes
(II) Dell Dell USB Optical Mouse: Configuring as mouse
(**) Dell Dell USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Dell Dell USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Dell Dell USB Optical Mouse" (type: MOUSE)
(II) Dell Dell USB Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device Dell Dell USB Optical Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech Logitech USB Headset (/dev/input/event7)
(**) Logitech Logitech USB Headset: Applying InputClass "evdev keyboard catchall"
(**) Logitech Logitech USB Headset: always reports core events
(**) Logitech Logitech USB Headset: Device: "/dev/input/event7"
(II) Logitech Logitech USB Headset: Found keys
(II) Logitech Logitech USB Headset: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech Logitech USB Headset" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device DualPoint Stick (/dev/input/event12)
(**) DualPoint Stick: Applying InputClass "evdev pointer catchall"
(**) DualPoint Stick: always reports core events
(**) DualPoint Stick: Device: "/dev/input/event12"
(II) DualPoint Stick: Found 3 mouse buttons
(II) DualPoint Stick: Found relative axes
(II) DualPoint Stick: Found x and y relative axes
(II) DualPoint Stick: Configuring as mouse
(**) DualPoint Stick: YAxisMapping: buttons 4 and 5
(**) DualPoint Stick: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "DualPoint Stick" (type: MOUSE)
(II) DualPoint Stick: initialized for relative axes.
(II) config/udev: Adding input device DualPoint Stick (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/event13)
(**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "evdev pointer catchall"
(**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "evdev touchpad catchall"
(**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event13"
(II) AlpsPS/2 ALPS DualPoint TouchPad: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS DualPoint TouchPad: y-axis range 0 - 767
(II) AlpsPS/2 ALPS DualPoint TouchPad: pressure range 0 - 127
(II) AlpsPS/2 ALPS DualPoint TouchPad: finger width range 0 - 0
(II) AlpsPS/2 ALPS DualPoint TouchPad: buttons: left right middle
(--) AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
(**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS DualPoint TouchPad" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration profile 0
(**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration factor: 2.000
(**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration threshold: 4
(--) AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
(II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/mouse3)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event11)
(**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
(**) Dell WMI hotkeys: always reports core events
(**) Dell WMI hotkeys: Device: "/dev/input/event11"
(II) Dell WMI hotkeys: Found keys
(II) Dell WMI hotkeys: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)

```
With this setup the two intel displays clone each other and the displaylink is its own screen. and there are no errors listed in the log file.


Any ideas to fix this are greatly appreciated as I dearly miss having my middle screen working correctly.

Thank you.

---

### Post by inittab on 2010-08-17
nobody have any ideas? or a suggestion of a better place to ask?

Thanks.

---

### Post by overdrank on 2010-08-17
Moved to Multimedia & Video. :)

---

### Post by balblua on 2010-10-01
OP, I figured out a basic solution for triple head DisplayLink with intel driver (Core i5). Sorry for the messiness.

Notes:

- DisplayLink Must be screen 0 and reference IntelScreen
- Intel screen needs to have virtual display size jacked up large enough to span both displays

Caveats
- Configuration does not support hotplug.
- Configuration still needs some kind of Xinerama hack to make maximize work correctly.
- Couldn't figure out how to put DisplayLink display between Intel displays. Best I could get was 3 properly laid out heads with broken mouse pointer.

HTH.

============

```
Section "ServerLayout"
	Identifier "Server Layout"
	Screen 0 "DisplayLinkScreen" RightOf "IntelScreen"
	Screen 1 "IntelScreen" 0 0
	Option	 "Xinerama" "on" 
	Option "clone" "off"
EndSection

################################################# 

Section "Files"
	ModulePath "/usr/local/lib/xorg/modules/drivers"
	ModulePath "/usr/lib/xorg/modules"
	ModulePath "/usr/lib/xorg/modules/drivers"
	ModulePath "/usr/local/lib"
EndSection

############### DisplayLink Stuff ############### 

Section "Device"
	Identifier "DisplayLinkDevice"
	driver "displaylink"
	Option "fbdev" "/dev/fb0"
EndSection


Section "Screen"
	Identifier "DisplayLinkScreen"
	Device "DisplayLinkDevice"
	Monitor "DisplayLinkMonitor"
	SubSection "Display"
		Depth 16
		Modes "1280x1024"
	EndSubSection
EndSection


############### Default Video Device ############### 
Section "Device"
	Identifier "IntelDevice"
	Driver "Intel"

        Option          "monitor-VGA1" "vga"
        Option          "monitor-LVDS1" "lcd"
EndSection

Section "Monitor"
	Identifier "lcd"
	option "position" "0 0"
EndSection

Section "Monitor"
	Identifier "DisplayLinkMonitor"
	Option "PreferredMode"  "1280x1024"
EndSection

Section "Monitor"
	Identifier "vga"
	Option "PreferredMode"  "1280x1024"
	Option "rightOf" "lcd"

	#option "position" "2560 0"
	#Option "below" "lcd"
	#option "position" "0 800"
EndSection

Section "Screen"
	Identifier "IntelScreen"
	Monitor "lcd"
	Device "IntelDevice"
	DefaultDepth 16
	SubSection "Display"
		Depth 16
		Modes "1280x800" "1280x1024"
		Virtual 2560 1024
		#Virtual 3840 1024
	EndSubSection
EndSection
```

---

