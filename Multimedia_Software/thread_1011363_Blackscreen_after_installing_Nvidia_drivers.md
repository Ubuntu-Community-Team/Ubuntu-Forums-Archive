---
title: "Blackscreen after installing Nvidia drivers"
date: 2008-12-14
forum: Multimedia Software
---

### Post by Flaffen on 2008-12-14
Hi, I'm using Ubuntu 8.10, and when I install the latest Nvidia drivers from the driver update thing and reboot, the loading bar shows, then the screen goes black. Anyone know how to avoid this black screen, and get the drivers working?
I'm currently on a fresh install of Ubuntu and havent installed any updates yet. I've read a bit about this issue, but I'm very new to Ubuntu, so most of its just hebrew to me. My Nvidia card is: Geforce4 Ti 4200 with AGP8X.

---

### Post by 67GTA on 2008-12-14
Which version of the drivers did you install? I think your card needs the 96 version. There are 173, 177, 96, etc.

---

### Post by Flaffen on 2008-12-15
The Update Manager installs nvidia-96-modaliases.

Edit: I've read a bit about this and there are loads of ppl getting black screen from installing their nvidia drivers.
But so far the solutions I've read so far are disabling the drivers so they can get back into X. I want my drivers working
so I can try playing games on Ubuntu. Without them, the WoW-intro movie even lags like crap.

---

### Post by 67GTA on 2008-12-15
Just a hunch, do you have a TV tuner card? Run ```
lsmod | grep cx18
``` and post any output. The new cx18 module in 2.6.27 causes problems with the nvidia module, but you should at least get the bulletproofx dialog and be able to run 800x600 res.

---

### Post by Flaffen on 2008-12-15
Sorry, I actually made a mistake, It was not the nvidia-96-modaliases that gave me blacscreen, it was the restricted nvidia accellerated graphics drivers that gave me blackscreen, tried it again now :P
But after reading all the stuff on the other forums, I now ran recovery mode and did xfix. But the accellerated graphics driver is now disabled again it seems.

Edit: Btw, I'm supposed to do: lsmod | grep cx18 in terminal right?
(I'm a noob with linux)

---

### Post by Flaffen on 2008-12-16
I think i have a TV-out on it if thats what you mean. Now I've tried to use envy, but same thing happens there. The Ubuntu loading screen completes, then I get black screen (like no input) then another shade of black (like in dos), then that repeats and it stays at the last one. Keep having to use xfix to disable the accelerated graphics driver. On the hardware drivers it says a different version of this driver is in use. Can anyone help?

---

### Post by 67GTA on 2008-12-16
Edit: Btw, I'm supposed to do: lsmod | grep cx18 in terminal right?
(I'm a noob with linux)[/quote]

Yes, run that command in a terminal and see if you get any output.

---

### Post by Flaffen on 2008-12-16
Nothing happened, just got a new line where i enter the commands.

---

### Post by 67GTA on 2008-12-16
That means you don't have the cx18 module loaded. Post a copy of your /var/log/Xorg.0.log file.

---

### Post by Flaffen on 2008-12-16
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux flaffarium 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec 16 07:50:32 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x] rev 161, Mem @ 0xde000000/0, 0xd0000000/0, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  96.43.09  Mon Oct 27 14:37:08 PST 2008
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched nv from file name nv.ids
(==) Matched nv for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "nv"

(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 2.1.10
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
	GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
	GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
	GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
	GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
	Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
	Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
	GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, GeForce 8800 GTS,
	GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600, GeForce 8600 GTS,
	GeForce 8600 GT, GeForce 8600 GT, GeForce 8400 GS, GeForce 9500M GS,
	GeForce 8600M GT, GeForce 9650M GS, GeForce 8700M GT, Quadro FX 370,
	Quadro NVS 320M, Quadro FX 570M, Quadro FX 1600M, Quadro FX 570,
	Quadro FX 1700, GeForce 8400 SE, GeForce 8500 GT, GeForce 8400 GS,
	GeForce 8300 GS, GeForce 8400 GS, GeForce 8600M GS, GeForce 8400M GT,
	GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, Quadro NVS 130M,
	Quadro NVS 135M, Quadro FX 360M, GeForce 9300M G, Quadro NVS 290,
	GeForce GTX 280, GeForce GTX 260, GeForce 8800 GTS 512,
	GeForce 8800 GT, GeForce 9800 GX2, GeForce 8800 GS,
	GeForce 8800M GTS, GeForce 8800M GTX, GeForce 8800 GS,
	GeForce 9600 GSO, GeForce 8800 GT, GeForce 9800 GTX, Quadro FX 3700,
	Quadro FX 3600M, GeForce 9600 GT, GeForce 9600M GT, GeForce 9600M GS,
	GeForce 9600M GT, GeForce 9500M G, GeForce 8400 GS, GeForce 9300M GS,
	GeForce 9200M GS, GeForce 9300M GS
(II) Primary Device is: PCI 01@00:00:0
(--) NV: Found NVIDIA GeForce4 Ti 4200 with AGP8X at 01@00:00:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce4 Ti 4200 with AGP8X"
(II) NV(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) NV(0): Depth 24, (==) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xD0000000
(--) NV(0): MMIO registers at 0xDE000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...found one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: ACR  Model: ad80  Serial#: 0
(II) NV(0): Year: 2006  Week: 41
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NV(0): Sync:  Separate
(II) NV(0): Max Image Size [cm]: horiz.: 41  vert.: 26
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): First detailed timing not preferred mode in violation of standard!(II) NV(0): redX: 0.650 redY: 0.345   greenX: 0.287 greenY: 0.600
(II) NV(0): blueX: 0.140 blueY: 0.068   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@67Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): 1152x870@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 1400  vsize 1050  refresh: 75  vid: 20368
(II) NV(0): #1: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) NV(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #4: hsize: 1280  vsize 800  refresh: 75  vid: 3969
(II) NV(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) NV(0): #6: hsize: 1152  vsize 921  refresh: 76  vid: 36977
(II) NV(0): #7: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 89.0 MHz   Image Size:  410 x 257 mm
(II) NV(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1600 h_border: 0
(II) NV(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 926 v_border: 0
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 84 kHz, PixClock max 140 MHz
(II) NV(0): Serial No: 641059E14010
(II) NV(0): Monitor name: AL1916W
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff00047280ad00000000
(II) NV(0): 	2910010308291a78e89ae5a658499923
(II) NV(0): 	115054bfef80904f950f81808140810f
(II) NV(0): 	81007190714fc422a0a050841a303020
(II) NV(0): 	36009a011100001e000000fd00384c1f
(II) NV(0): 	540e000a202020202020000000ff0036
(II) NV(0): 	34313035394531343031300a000000fc
(II) NV(0): 	00414c31393136570a202020202000c7
(--) NV(0): CRTC 0 appears to have a CRT attached
(II) NV(0): Using CRT on CRTC 0
(II) NV(0): EDID vendor "ACR", prod id 44416
(II) NV(0): Using EDID range info for horizontal sync
(II) NV(0): Using EDID range info for vertical refresh
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1440x900"x0.0   89.00  1440 1488 1520 1600  900 903 909 926 +hsync +vsync (55.6 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) NV(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NV(0): Modeline "1400x1050"x75.0  155.85  1400 1496 1648 1896  1050 1051 1054 1096 -hsync +vsync (82.2 kHz)
(II) NV(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) NV(0): Modeline "1280x1024"x60.0  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
(II) NV(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) NV(0): Modeline "1280x800"x75.0  107.21  1280 1360 1496 1712  800 801 804 835 -hsync +vsync (62.6 kHz)
(II) NV(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 -hsync +vsync (49.7 kHz)
(II) NV(0): Modeline "1152x921"x76.0  113.47  1152 1224 1352 1552  921 922 925 962 -hsync +vsync (73.1 kHz)
(II) NV(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(--) NV(0): VideoRAM: 131072 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Configured Monitor: Using hsync range of 31.00-84.00 kHz
(II) NV(0): Configured Monitor: Using vrefresh range of 56.00-76.00 Hz
(II) NV(0): Configured Monitor: Using maximum pixel clock of 140.00 MHz
(II) NV(0): Estimated virtual size for aspect ratio 1.5769 is 1440x900
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (vrefresh out of range)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (vrefresh out of range)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (vrefresh out of range)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (vrefresh out of range)
(II) NV(0): Not using default mode "1280x960" (height too large for virtual size)
(II) NV(0): Not using default mode "1280x960" (height too large for virtual size)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) NV(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) NV(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NV(0): Not using default mode "576x432" (vrefresh out of range)
(II) NV(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NV(0): Not using default mode "576x432" (vrefresh out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) NV(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) NV(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) NV(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) NV(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) NV(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using driver mode "1280x1024" (height too large for virtual size)
(II) NV(0): Not using driver mode "1400x1050" (height too large for virtual size)
(II) NV(0): Not using driver mode "1280x1024" (height too large for virtual size)
(II) NV(0): Not using driver mode "1280x960" (height too large for virtual size)
(II) NV(0): Not using driver mode "1152x921" (height too large for virtual size)
(--) NV(0): Virtual size is 1440x900 (pitch 1440)
(**) NV(0): *Driver mode "1440x900": 136.5 MHz, 70.5 kHz, 75.0 Hz
(II) NV(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(**) NV(0): *Driver mode "1440x900": 89.0 MHz, 55.6 kHz, 60.1 Hz
(II) NV(0): Modeline "1440x900"x60.1   89.00  1440 1488 1520 1600  900 903 909 926 +hsync +vsync (55.6 kHz)
(**) NV(0): *Default mode "1440x900": 106.5 MHz, 55.9 kHz, 59.9 Hz
(II) NV(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(**) NV(0): *Default mode "1360x768": 84.8 MHz, 47.7 kHz, 59.8 Hz
(II) NV(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(**) NV(0): *Driver mode "1280x800": 107.2 MHz, 62.6 kHz, 75.0 Hz
(II) NV(0): Modeline "1280x800"x75.0  107.21  1280 1360 1496 1712  800 801 804 835 -hsync +vsync (62.6 kHz)
(**) NV(0): *Driver mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 -hsync +vsync (49.7 kHz)
(**) NV(0): *Driver mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) NV(0): *Driver mode "1152x864": 105.0 MHz, 67.7 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(**) NV(0): *Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) NV(0): *Default mode "1152x864": 105.0 MHz, 67.6 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(**) NV(0): *Default mode "1152x864": 96.8 MHz, 63.0 kHz, 70.0 Hz
(II) NV(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(**) NV(0): *Default mode "1152x864": 81.6 MHz, 53.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(**) NV(0): *Driver mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) NV(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(**) NV(0): *Driver mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) NV(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NV(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) NV(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) NV(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NV(0): *Default mode "896x672": 102.4 MHz, 83.7 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "896x672"x60.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz)
(**) NV(0): *Driver mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) NV(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) NV(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) NV(0): *Driver mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) NV(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0): *Driver mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) NV(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) NV(0): *Default mode "800x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
(II) NV(0): Modeline "800x600"x65.0   87.75  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (81.2 kHz)
(**) NV(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "800x600"x60.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz)
(**) NV(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "840x525": 93.5 MHz, 82.3 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "840x525"x75.0   93.50  840 900 988 1136  525 526 529 549 doublescan -hsync +vsync (82.3 kHz)
(**) NV(0): *Default mode "840x525": 87.0 MHz, 76.6 kHz, 69.9 Hz (D)
(II) NV(0): Modeline "840x525"x69.9   87.00  840 900 988 1136  525 526 529 548 doublescan -hsync +vsync (76.6 kHz)
(**) NV(0): *Default mode "840x525": 73.1 MHz, 65.3 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "840x525"x60.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz)
(**) NV(0): *Default mode "700x525": 77.9 MHz, 81.5 kHz, 74.8 Hz (D)
(II) NV(0): Modeline "700x525"x74.8   77.90  700 732 892 956  525 526 532 545 doublescan +hsync +vsync (81.5 kHz)
(**) NV(0): *Default mode "700x525": 72.5 MHz, 76.5 kHz, 70.1 Hz (D)
(II) NV(0): Modeline "700x525"x70.1   72.53  700 748 824 948  525 525 527 546 doublescan -hsync +vsync (76.5 kHz)
(**) NV(0): *Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "700x525"x60.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz)
(**) NV(0): *Default mode "640x512": 67.5 MHz, 80.0 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "640x512"x75.0   67.50  640 648 720 844  512 512 514 533 doublescan +hsync +vsync (80.0 kHz)
(**) NV(0): *Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x512"x60.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz)
(**) NV(0): *Default mode "720x450": 53.2 MHz, 55.9 kHz, 59.9 Hz (D)
(II) NV(0): Modeline "720x450"x59.9   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz)
(**) NV(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NV(0): *Driver mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(**) NV(0): *Driver mode "640x480": 30.2 MHz, 35.0 kHz, 66.7 Hz
(II) NV(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(**) NV(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NV(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) NV(0): *Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
(**) NV(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) NV(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) NV(0): *Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
(**) NV(0): *Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
(II) NV(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
(**) NV(0): *Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "576x432"x75.0   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync (67.5 kHz)
(**) NV(0): *Default mode "576x432": 52.5 MHz, 67.6 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "576x432"x75.0   52.49  576 612 676 776  432 432 434 451 doublescan -hsync +vsync (67.6 kHz)
(**) NV(0): *Default mode "576x432": 48.4 MHz, 63.0 kHz, 70.0 Hz (D)
(II) NV(0): Modeline "576x432"x70.0   48.38  576 612 672 768  432 432 434 450 doublescan -hsync +vsync (63.0 kHz)
(**) NV(0): *Default mode "576x432": 40.8 MHz, 53.7 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz)
(**) NV(0): *Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz)
(**) NV(0): *Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) NV(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
(**) NV(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
(**) NV(0): *Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) NV(0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz)
(**) NV(0): *Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) NV(0): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync (46.9 kHz)
(**) NV(0): *Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) NV(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz)
(**) NV(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "320x240"x75.0   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync (37.5 kHz)
(**) NV(0): *Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) NV(0): Modeline "320x240"x72.8   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync (37.9 kHz)
(**) NV(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(**) NV(0): Display dimensions: (410, 260) mm
(**) NV(0): DPI set to (89, 87)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(II) NV(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device ImPS/2 Logitech Wheel Mouse
(**) ImPS/2 Logitech Wheel Mouse: always reports core events
(**) ImPS/2 Logitech Wheel Mouse: Device: "/dev/input/event5"
(II) ImPS/2 Logitech Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Logitech Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Logitech Wheel Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "ImPS/2 Logitech Wheel Mouse" (type: MOUSE)
(**) ImPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "no"
(**) AT Translated Set 2 keyboard: xkb_layout: "no"
AUDIT: Tue Dec 16 07:50:37 2008: 5092 X: client 4 rejected from local host ( uid=0 gid=0 pid=5260 )
AUDIT: Tue Dec 16 07:50:42 2008: 5092 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5319 )
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1
AUDIT: Tue Dec 16 07:50:42 2008: 5092 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5320 )
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1
AUDIT: Tue Dec 16 07:50:42 2008: 5092 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5321 )
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1


There you have it, really long :P

---

### Post by 67GTA on 2008-12-16
Nvidia has recently dropped support for some of it's older cards. It looks like you have been hit with this. It is mentioned here under "Upgrading": [http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

---

### Post by Flaffen on 2008-12-16
So that means i'm just screwed right? Nothing can be done?

---

### Post by 67GTA on 2008-12-16
The older card drivers are not compatible with the newer xorg in 8.10. Unless Nvidia decides to put out new drivers(not likely), then you will have to use the nv driver without 3D support. The only other option is to go back to Hardy.

---

### Post by Flaffen on 2008-12-16
So I can install an older version of Ubuntu and it should work?
(Would that be: Ubuntu 8.04.1 desktop?, and is it possible to downgrade it or do I have to remove the entire thing and install again?)

---

### Post by 67GTA on 2008-12-16
Yes. Hardy is the latest LTS(long term support) release. It is supported for three years with security updates. Intrepid(8.10), and every other 6 month release in between are only supported for 18 months. My advice would be to install Hardy. It will be officially supported until the next LTS release.

---

### Post by 67GTA on 2008-12-16
You would have to install it again. Another friendly tip is to make a /home partition separate from the main partition. That way you will keep all of your tweaks and personal settings each time you install another version.

---

### Post by Flaffen on 2008-12-16
Ok. Well thanx for all the help you provided. Without it I would still be stuck in the same place having no idea what to do :P So you have saved me a LOT of time, and I'm VERY grateful for that.
So thanx :D

---

### Post by 67GTA on 2008-12-16
Check out this link: [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) It helped me a lot when I first started using Linux. There is a section about how to move your existing /home to a separate partition(in it's current state) before reinstalling. If you shrink your current Ubuntu partition, and then create a new one to move your /home folder to, you might be able to save yourself some headache.

---

### Post by Flaffen on 2008-12-20
Ok, i'm back again, just installed ubuntu 8.04 LTS. Thing is that i run into same problem again with the drivers. Upon enabling the accellerated graphics drivers i just get the black screen. Then i have to run xfix so it diables it. Does this mean i need a new graphics card? That is supported by Nvidia? (this means i need a new comuter altogether)

---

### Post by RJARRRPCGP on 2008-12-21
Try this:

```
sudo apt-get install linux-headers-generic dkms nvidia-glx-legacy && sudo nvidia-xconfig
```

Then reboot.

---

### Post by Flaffen on 2008-12-21
I tried that command, and it replaced my nvidia-glx file with nvidia-glx-legacy, but at the end it says: "sudo: nvidia-xconfig: command not found". I was guessing this was cuz i diddent have xconfig so I tried to install it via synaptic package manager, problem is that it removes the nvidia-glx-legacy when i install nvidia-xconfig. I've tried several drivers and nothing seems to work. When i run opengl on programs it drops to 2 fps, even in 2d games like The Mana World. And whenever i try to install the Nvidia Accellerated Graphics driver, it removes whatever driver i have and installs the nvidia-glx thing.
Got any other ideas?

---

### Post by RJARRRPCGP on 2008-12-21
Try this:

```
sudo apt-get install linux-headers-generic dkms nvidia-glx-96
```

---

### Post by Flaffen on 2008-12-21
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
E: Couldn't find package nvidia-glx-96

Thats what it said.

---

### Post by RJARRRPCGP on 2008-12-21
> **Flaffen said:**
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
E: Couldn't find package nvidia-glx-96

Thats what it said.

Try this:

```
sudo apt-get install linux-headers-generic dkms nvidia-glx-legacy
```

---

### Post by Flaffen on 2008-12-21
Sorry guys, but i think i've wasted your time. I now believe its the graphics card itself thats faulty. The reason is that i reinstalled windows and i noticed small glitches there. Now since there are problems on both OS'es its most likely its the card itself. Really sorry that i wasted your time. But thanx for the help, i've at least leared a bit about ubuntu during this debugging process, and i've decided i'm gonna stick to linux.
Now i just need a new grapics card.

---

### Post by thinkinhurtz on 2008-12-23
I also am running the geForce 9600 GT and after 8 months of trying I am still having the same problem with Every Driver i have tried. I dont think installing windows again will help though because I have also tried that and noticed small glitches with this card. Currently I'm stuck after installing a fresh 8.10 with no nvidia drivers loaded. After installing drivers several times it leaves me hanging before the gdm loading screen with "Checking Battery State" errors. Also I have tried with EnvyNG. tried editing xorg. Any help would be great at this point....

---

### Post by bannik on 2009-01-16
I have the exact same problem

i use an nvidia geforce 5600 and after installing the nvidia driver i reboot and after the stupid loading screen it goes into a blank screen and  i cant do anything apart from recovery mode and xfix

then it doesnt read the driver as activated

xorg doesnt chage etc

i did try Envy and it kinda worked but instead of a black screen it gets me to an error page (low graphic interface) where it gives me 3 options one being activate default mode and the other say use ubuntu in low resolution but that fails and i have too reboot again.


any ideas? i dont think its a hardware fault - this only happend recently like 2-3 days ago

i havea fresh install of intrepid same problem, same with hardy.

i personally thinks that the drivers arent correctly transfering into the xorg file (what ever the file is)..but i dont know so if anyone has same problem and any advice please do tell ....

---

