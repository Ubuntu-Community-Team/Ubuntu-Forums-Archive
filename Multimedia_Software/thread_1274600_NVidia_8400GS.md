---
title: "NVidia 8400GS"
date: 2009-09-24
forum: Multimedia Software
---

### Post by steev182 on 2009-09-24
After having problems with the nvidia drivers on 32 bit karmic, I got frustrated and decided that if I'm going to put any more effort into it, I might as well do it on 64-bit!

Anyway, long story short.

I install the 185 driver in Hardware Drivers, it installs, restarts and gives nothing.

I then got the Xorg.0.log which has this:

```

EEX.Org X Server 1.6.3
Release Date: 2009-7-31
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux steve-desktop 2.6.31-10-generic #35-Ubuntu SMP Tue Sep 22 17:33:14 UTC 2009 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-10-generic root=UUID=74392613-493f-4d37-83fd-dd9b76de52ec ro quiet splash
Build Date: 09 September 2009  12:45:08AM
xorg-server 2:1.6.3-1ubuntu6 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 24 20:19:30 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:2:0:0) 10de:06e4:1043:8265 nVidia Corporation G98 [GeForce 8400 GS] rev 161, Mem @ 0xee000000/16777216, 0xd0000000/268435456, 0xec000000/33554432, I/O @ 0x0000dc80/128, BIOS @ 0x????????/131072
(--) PCI: (0:5:7:0) 1002:515e:1028:01df ATI Technologies Inc ES1000 rev 2, Mem @ 0xe0000000/134217728, 0xebdf0000/65536, I/O @ 0x0000cc00/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
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
	compiled for 1.6.3, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: file too short
(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched nv for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 2.1.14
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) NV: driver for NVIDIA chipsets:  RIVA 128,  RIVA TNT,  RIVA TNT2,
	 RIVA TNT2 Ultra,  Unknown TNT2,  Vanta,  RIVA TNT2 Model 64,
	 GeForce 6800 Ultra,  GeForce 6800,  GeForce 6800 LE,
	 GeForce 6800 XE,  GeForce 6800 XT,  GeForce 6800 GT,
	 GeForce 6800 GT,  GeForce 6800 GS,  GeForce 6800 XT,
	 Quadro FX 4000,  GeForce 7800 GTX,  GeForce 7800 GTX,
	 GeForce 7800 GT,  GeForce 7800 GS,  GeForce 7800 SLI,
	 GeForce Go 7800,  GeForce Go 7800 GTX,  Quadro FX 4500,
	 Aladdin TNT2,  GeForce 6800 GS,  GeForce 6800,  GeForce 6800 LE,
	 GeForce 6800 XT,  GeForce Go 6800,  GeForce Go 6800 Ultra,
	 Quadro FX Go1400,  Quadro FX 3450/4000 SDI,  Quadro FX 1400,
	 GeForce 256,  GeForce DDR,  Quadro,  GeForce2 MX/MX 400,
	 GeForce2 MX 100/200,  GeForce2 Go,  Quadro2 MXR/EX/Go,
	 GeForce 6600 GT,  GeForce 6600,  GeForce 6600 LE,  GeForce 6600 VE,
	 GeForce Go 6600,  GeForce 6610 XL,  GeForce Go 6600 TE/6200 TE,
	 GeForce 6700 XL,  GeForce Go 6600,  GeForce Go 6600 GT,
	 Quadro NVS 440,  Quadro FX 550,  Quadro FX 550,  Quadro FX 540,
	 GeForce 6200,  GeForce2 GTS,  GeForce2 Ti,  GeForce2 Ultra,
	 Quadro2 Pro,  GeForce 6500,  GeForce 6200 TurboCache(TM),
	 GeForce 6200SE TurboCache(TM),  GeForce 6200 LE,  GeForce Go 6200,
	 Quadro NVS 285,  GeForce Go 6400,  GeForce Go 6200,
	 GeForce Go 6400,  GeForce 6250,  GeForce 7100 GS,  GeForce4 MX 460,
	 GeForce4 MX 440,  GeForce4 MX 420,  GeForce4 MX 440-SE,
	 GeForce4 440 Go,  GeForce4 420 Go,  GeForce4 420 Go 32M,
	 GeForce4 460 Go,  Quadro4 550 XGL,  GeForce4 440 Go 64M,
	 Quadro NVS,  Quadro4 500 GoGL,  GeForce4 410 Go 16M,
	 GeForce4 MX 440 with AGP8X,  GeForce4 MX 440SE with AGP8X,
	 GeForce4 MX 420 with AGP8X,  GeForce4 MX 4000,  GeForce4 448 Go,
	 GeForce4 488 Go,  Quadro4 580 XGL,  Quadro4 NVS 280 SD,
	 Quadro4 380 XGL,  Quadro NVS 50 PCI,  GeForce4 448 Go,
	 GeForce 8800 GTX,  GeForce 8800 GTS,  GeForce 8800 Ultra,
	 Quadro FX 5600,  Quadro FX 4600,  GeForce2 Integrated GPU,
	 GeForce 7350 LE,  GeForce 7300 LE,  GeForce 7300 SE,
	 GeForce Go 7200,  GeForce Go 7300,  GeForce Go 7400,
	 GeForce Go 7400 GS,  Quadro NVS 110M,  Quadro NVS 120M,
	 Quadro FX 350M,  GeForce 7500 LE,  Quadro FX 350,  GeForce 7300 GS,
	 GeForce4 MX Integrated GPU,  GeForce3,  GeForce3 Ti 200,
	 GeForce3 Ti 500,  Quadro DCC,  GeForce 6800,  GeForce 6800 LE,
	 GeForce 6800 GT,  GeForce 6800 XT,  GeForce 6200,
	 GeForce 6200 A-LE,  GeForce 6150,  GeForce 6150 LE,  GeForce 6100,
	 GeForce Go 6150,  Quadro NVS 210S / NVIDIA GeForce 6150LE,
	 GeForce Go 6100,  GeForce4 Ti 4600,  GeForce4 Ti 4400,
	 GeForce4 Ti 4200,  Quadro4 900 XGL,  Quadro4 750 XGL,
	 Quadro4 700 XGL,  GeForce4 Ti 4800,  GeForce4 Ti 4200 with AGP8X,
	 GeForce4 Ti 4800 SE,  GeForce4 4200 Go,  Quadro4 980 XGL,
	 Quadro4 780 XGL,  Quadro4 700 GoGL,  GeForce 7900 GTX,
	 GeForce 7900 GT,  GeForce 7900 GS,  GeForce 7950 GX2,
	 GeForce 7950 GX2,  GeForce 7950 GT},  GeForce Go 7950 GTX,
	 GeForce Go 7900 GS,  GeForce Go 7900 GTX,  Quadro FX 2500M,
	 Quadro FX 1500M,  Quadro FX 5500,  Quadro FX 3500,  Quadro FX 1500,
	 Quadro FX 4500 X2,  GeForce FX 5800 Ultra,  GeForce FX 5800,
	 Quadro FX 2000,  Quadro FX 1000,  GeForce FX 5600 Ultra,
	 GeForce FX 5600,  GeForce FX 560T,  GeForce FX Go5600,
	 GeForce FX Go5650,  Quadro FX Go700,  GeForce FX 5200,
	 GeForce FX 5200 Ultra,  GeForce FX 5200,  GeForce FX 5200LE,
	 GeForce FX Go5200,  GeForce FX Go5250,  GeForce FX 5500,
	 GeForce FX 5100,  GeForce FX Go5200 32M/64M,  Quadro NVS 55/280 PCI,
	 Quadro FX 500/600 PCI,  GeForce FX Go53xx Series,
	 GeForce FX Go5100,  GeForce FX 5900 Ultra,  GeForce FX 5900,
	 GeForce FX 590T,  GeForce FX 5950 Ultra,  GeForce FX 5900ZT,
	 Quadro FX 3000,  Quadro FX 700,  GeForce FX 5700 Ultra,
	 GeForce FX 5700,  GeForce FX 5700LE,  GeForce FX 5700VE,
	 GeForce FX Go5700,  GeForce FX Go5700,  Quadro FX Go1000,
	 Quadro FX 1100,  GeForce 7650 GS,  GeForce 7600 GT,
	 GeForce 7600 GS,  GeForce 7300 GT,  GeForce 7600 LE,
	 GeForce 7300 GT,  GeForce Go 7700,  GeForce Go 7600,
	 GeForce Go 7600 GT},  Quadro NVS 300M,  GeForce Go 7900 SE,
	 Quadro FX 550M,  Quadro FX 560,  GeForce 6150SE,
	 GeForce 6100 nForce 405,  GeForce 6100 nForce 400,
	 GeForce 6100 nForce 420,  GeForce 8600 GTS,  GeForce 8600 GT,
	 GeForce 8600 GT,  GeForce 8600 GS,  GeForce 8400 GS,
	 GeForce 9500M GS,  GeForce 8600M GT,  GeForce 9650M GS,
	 GeForce 8700M GT,  Quadro FX 370,  Quadro NVS 320M,  Quadro FX 570M,
	 Quadro FX 1600M,  Quadro FX 570,  Quadro FX 1700,  GeForce 8400 SE,
	 GeForce 8500 GT,  GeForce 8400 GS,  GeForce 8300 GS,
	 GeForce 8400 GS,  GeForce 8600M GS,  GeForce 8400M GT,
	 GeForce 8400M GS,  GeForce 8400M G,  Quadro NVS 140M,
	 Quadro NVS 130M,  Quadro NVS 135M,  GeForce 9400 GT,
	 Quadro FX 360M,  GeForce 9300M G,  Quadro NVS 290,  GeForce GTX 295,
	 GeForce GTX 280,  GeForce GTX 260,  GeForce GTX 285,  GeForce 7050,
	 GeForce 7025,  Quadro CX,  Quadro FX 5800,  Quadro FX 4800,
	 Quadro FX 3800,  GeForce 8800 GTS 512,  GeForce 9800 GT,
	 GeForce 8800 GT,  GeForce 9800 GX2,  GeForce 9800 GT,
	 GeForce 8800 GS,  GeForce 9800M GTX,  GeForce 8800M GTS,
	 GeForce 9800M GT,  GeForce 8800M GTX,  GeForce 8800 GS,
	 GeForce 9600 GSO,  GeForce 8800 GT,  GeForce 9800 GTX,
	 GeForce 9800 GTX+,  GeForce 9800 GT,  GeForce GTS 250,
	 GeForce 9800M GTX,  Quadro FX 3700,  Quadro FX 3600M,
	 Quadro FX 3700M,  GeForce 9600 GT,  GeForce 9600 GS,
	 GeForce 9600 GSO 512,  GeForce GT 130,  GeForce GT 140,
	 GeForce 9800M GTS,  GeForce 9700M GTS,  GeForce 9800M GS,
	 GeForce 9800M GTS,  Quadro FX 1800,  Quadro FX 2700M,
	 GeForce 9500 GT,  GeForce 9400 GT,  GeForce 9500 GT,
	 GeForce GT 120,  GeForce 9600M GT,  GeForce 9600M GS,
	 GeForce 9600M GT,  GeForce 9700M GT,  GeForce 9500M G,
	 GeForce 9650M GT,  GeForce 9500 GT,  Quadro FX 380,  Quadro FX 580,
	 Quadro FX 770M,  GeForce 9300 GE,  GeForce 9300 GS,
	 GeForce 8400 GS,  GeForce 9300M GS,  GeForce G100,
	 GeForce 9200M GS,  GeForce 9300M GS,  Quadro NVS 150M,
	 Quadro NVS 160M,  Quadro NVS 420,  Quadro FX 370 LP,
	 Quadro NVS 450,  Quadro NVS 295
(II) Primary Device is: PCI 02@00:00:0
(--) NV: Found NVIDIA  GeForce 8400 GS at 02@00:00:0
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
	compiled for 1.6.3, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Console is VGA mode 0x3
(II) NV(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(==) NV(0): Using hardware cursor
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): MMIO registers mapped at 0x7f0eab09a000
(--) NV(0): Total video RAM: 256.0 MB
(--) NV(0):       BAR1 size: 256.0 MB
(--) NV(0):   Mapped memory: 255.0 MB
(II) NV(0): Linear framebuffer mapped at 0x7f0e9b19a000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(--) NV(0): Connector map:
(--) NV(0):   Bus 0 -> DAC1
(--) NV(0):   Bus 0 -> SOR0
(--) NV(0):   Bus 1 -> DAC2
(--) NV(0): Load detection: 295
(II) NV(0): I2C bus "I2C0" initialized.
(II) NV(0): Output VGA1 has no monitor section
(II) NV(0): Output DVI0 has no monitor section
(II) NV(0): I2C bus "I2C1" initialized.
(II) NV(0): Output VGA2 has no monitor section
(II) NV(0): Probing for EDID on I2C bus 0...
(II) NV(0): I2C device "I2C0:E-EDID segment register" registered at address 0x60.
(II) NV(0): I2C device "I2C0:ddc2" registered at address 0xA0.
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: HIT  Model: 6dff  Serial#: 16843009
(II) NV(0): Year: 2007  Week: 20
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) NV(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #3: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Monitor name: N220W DVI
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 150 MHz
(II) NV(0): Serial No: 0WDP0B7502119
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff002134ff6d01010101
(II) NV(0): 	14110103802f1e78ead515a455499a27
(II) NV(0): 	145054adcf008180b3009500950f0101
(II) NV(0): 	01010101010121399030621a274068b0
(II) NV(0): 	3600da281100001c000000fc004e3232
(II) NV(0): 	3057204456490a202020000000fd0038
(II) NV(0): 	4c1f500f000a202020202020000000ff
(II) NV(0): 	003057445030423735303231313900f9
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): EDID for output DVI0
(II) NV(0): Manufacturer: HIT  Model: 6dff  Serial#: 16843009
(II) NV(0): Year: 2007  Week: 20
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) NV(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #3: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Monitor name: N220W DVI
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 150 MHz
(II) NV(0): Serial No: 0WDP0B7502119
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff002134ff6d01010101
(II) NV(0): 	14110103802f1e78ead515a455499a27
(II) NV(0): 	145054adcf008180b3009500950f0101
(II) NV(0): 	01010101010121399030621a274068b0
(II) NV(0): 	3600da281100001c000000fc004e3232
(II) NV(0): 	3057204456490a202020000000fd0038
(II) NV(0): 	4c1f500f000a202020202020000000ff
(II) NV(0): 	003057445030423735303231313900f9
(II) NV(0): EDID for output VGA1
(II) NV(0): EDID vendor "HIT", prod id 28159
(II) NV(0): Printing probed modes for output DVI0
(II) NV(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NV(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) NV(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NV(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Probing for EDID on I2C bus 1...
(II) NV(0): I2C device "I2C1:E-EDID segment register" registered at address 0x60.
(II) NV(0): I2C device "I2C1:ddc2" registered at address 0xA0.
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA2 ... nothing.
(II) NV(0): EDID for output VGA2
(II) NV(0): Output VGA1 disconnected
(II) NV(0): Output DVI0 connected
(II) NV(0): Output VGA2 disconnected
(II) NV(0): Using exact sizes for initial modes
(II) NV(0): Output DVI0 using initial mode 1680x1050
(--) NV(0): Virtual size is 1680x1680 (pitch 1792)
(**) NV(0):  Driver mode "1680x1050": 146.2 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) NV(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(**) NV(0):  Driver mode "1680x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 59.9 Hz
(II) NV(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(**) NV(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) NV(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) NV(0):  Driver mode "1440x900": 136.8 MHz (scaled from 0.0 MHz), 70.6 kHz, 75.0 Hz
(II) NV(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(**) NV(0):  Driver mode "1440x900": 88.8 MHz (scaled from 0.0 MHz), 55.5 kHz, 59.9 Hz
(II) NV(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(**) NV(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) NV(0):  Driver mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) NV(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NV(0):  Driver mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) NV(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) NV(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NV(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) NV(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
(II) NV(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(==) NV(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
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
(--) NV(0): 212.51 MB available for offscreen pixmaps
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
(II) NV(0): RandR 1.2 enabled, ignore the following RandR disabled message.
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
(II) NV(0): Setting screen physical size to 474 x 296
(II) config/hal: Adding input device Mitsumi Electric Apple Extended USB Keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
(**) Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event5"
(II) Mitsumi Electric Apple Extended USB Keyboard: Found keys
(II) Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(**) Option "xkb_variant" "mac"
(II) config/hal: Adding input device Mitsumi Electric Apple Extended USB Keyboard
(**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
(**) Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event4"
(II) Mitsumi Electric Apple Extended USB Keyboard: Found keys
(II) Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(**) Option "xkb_variant" "mac"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(**) Option "xkb_variant" "mac"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(**) Option "xkb_variant" "mac"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Dell Premium USB Optical Mouse
(**) Dell Premium USB Optical Mouse: always reports core events
(**) Dell Premium USB Optical Mouse: Device: "/dev/input/event3"
(II) Dell Premium USB Optical Mouse: Found 14 mouse buttons
(II) Dell Premium USB Optical Mouse: Found x and y relative axes
(II) Dell Premium USB Optical Mouse: Found scroll wheel(s)
(II) Dell Premium USB Optical Mouse: Configuring as mouse
(**) Dell Premium USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Dell Premium USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Dell Premium USB Optical Mouse" (type: MOUSE)
(**) Dell Premium USB Optical Mouse: (accel) keeping acceleration scheme 1
(**) Dell Premium USB Optical Mouse: (accel) filter chain progression: 2.00
(**) Dell Premium USB Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Dell Premium USB Optical Mouse: (accel) set acceleration profile 0
(II) Dell Premium USB Optical Mouse: initialized for relative axes.
(II) NV(0): Probing for EDID on I2C bus 0...
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: HIT  Model: 6dff  Serial#: 16843009
(II) NV(0): Year: 2007  Week: 20
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) NV(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #3: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Monitor name: N220W DVI
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 150 MHz
(II) NV(0): Serial No: 0WDP0B7502119
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff002134ff6d01010101
(II) NV(0): 	14110103802f1e78ead515a455499a27
(II) NV(0): 	145054adcf008180b3009500950f0101
(II) NV(0): 	01010101010121399030621a274068b0
(II) NV(0): 	3600da281100001c000000fc004e3232
(II) NV(0): 	3057204456490a202020000000fd0038
(II) NV(0): 	4c1f500f000a202020202020000000ff
(II) NV(0): 	003057445030423735303231313900f9
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): EDID for output DVI0
(II) NV(0): Manufacturer: HIT  Model: 6dff  Serial#: 16843009
(II) NV(0): Year: 2007  Week: 20
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) NV(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #3: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Monitor name: N220W DVI
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 150 MHz
(II) NV(0): Serial No: 0WDP0B7502119
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff002134ff6d01010101
(II) NV(0): 	14110103802f1e78ead515a455499a27
(II) NV(0): 	145054adcf008180b3009500950f0101
(II) NV(0): 	01010101010121399030621a274068b0
(II) NV(0): 	3600da281100001c000000fc004e3232
(II) NV(0): 	3057204456490a202020000000fd0038
(II) NV(0): 	4c1f500f000a202020202020000000ff
(II) NV(0): 	003057445030423735303231313900f9
(II) NV(0): EDID vendor "HIT", prod id 28159
(II) NV(0): Using EDID range info for horizontal sync
(II) NV(0): Using EDID range info for vertical refresh
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NV(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NV(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) NV(0): EDID for output VGA1
(II) NV(0): EDID vendor "HIT", prod id 28159
(II) NV(0): Printing probed modes for output DVI0
(II) NV(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NV(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) NV(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NV(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Probing for EDID on I2C bus 1...
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA2 ... nothing.
(II) NV(0): EDID for output VGA2
(II) NV(0): Probing for EDID on I2C bus 0...
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: HIT  Model: 6dff  Serial#: 16843009
(II) NV(0): Year: 2007  Week: 20
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) NV(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #3: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Monitor name: N220W DVI
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 150 MHz
(II) NV(0): Serial No: 0WDP0B7502119
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff002134ff6d01010101
(II) NV(0): 	14110103802f1e78ead515a455499a27
(II) NV(0): 	145054adcf008180b3009500950f0101
(II) NV(0): 	01010101010121399030621a274068b0
(II) NV(0): 	3600da281100001c000000fc004e3232
(II) NV(0): 	3057204456490a202020000000fd0038
(II) NV(0): 	4c1f500f000a202020202020000000ff
(II) NV(0): 	003057445030423735303231313900f9
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): EDID for output DVI0
(II) NV(0): Manufacturer: HIT  Model: 6dff  Serial#: 16843009
(II) NV(0): Year: 2007  Week: 20
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) NV(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #3: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Monitor name: N220W DVI
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 150 MHz
(II) NV(0): Serial No: 0WDP0B7502119
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff002134ff6d01010101
(II) NV(0): 	14110103802f1e78ead515a455499a27
(II) NV(0): 	145054adcf008180b3009500950f0101
(II) NV(0): 	01010101010121399030621a274068b0
(II) NV(0): 	3600da281100001c000000fc004e3232
(II) NV(0): 	3057204456490a202020000000fd0038
(II) NV(0): 	4c1f500f000a202020202020000000ff
(II) NV(0): 	003057445030423735303231313900f9
(II) NV(0): EDID vendor "HIT", prod id 28159
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NV(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NV(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) NV(0): EDID for output VGA1
(II) NV(0): EDID vendor "HIT", prod id 28159
(II) NV(0): Printing probed modes for output DVI0
(II) NV(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NV(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) NV(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NV(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Probing for EDID on I2C bus 1...
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA2 ... nothing.
(II) NV(0): EDID for output VGA2
(II) NV(0): Probing for EDID on I2C bus 0...
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: HIT  Model: 6dff  Serial#: 16843009
(II) NV(0): Year: 2007  Week: 20
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) NV(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #3: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Monitor name: N220W DVI
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 150 MHz
(II) NV(0): Serial No: 0WDP0B7502119
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff002134ff6d01010101
(II) NV(0): 	14110103802f1e78ead515a455499a27
(II) NV(0): 	145054adcf008180b3009500950f0101
(II) NV(0): 	01010101010121399030621a274068b0
(II) NV(0): 	3600da281100001c000000fc004e3232
(II) NV(0): 	3057204456490a202020000000fd0038
(II) NV(0): 	4c1f500f000a202020202020000000ff
(II) NV(0): 	003057445030423735303231313900f9
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): EDID for output DVI0
(II) NV(0): Manufacturer: HIT  Model: 6dff  Serial#: 16843009
(II) NV(0): Year: 2007  Week: 20
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) NV(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #3: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Monitor name: N220W DVI
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 150 MHz
(II) NV(0): Serial No: 0WDP0B7502119
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff002134ff6d01010101
(II) NV(0): 	14110103802f1e78ead515a455499a27
(II) NV(0): 	145054adcf008180b3009500950f0101
(II) NV(0): 	01010101010121399030621a274068b0
(II) NV(0): 	3600da281100001c000000fc004e3232
(II) NV(0): 	3057204456490a202020000000fd0038
(II) NV(0): 	4c1f500f000a202020202020000000ff
(II) NV(0): 	003057445030423735303231313900f9
(II) NV(0): EDID vendor "HIT", prod id 28159
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NV(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NV(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) NV(0): EDID for output VGA1
(II) NV(0): EDID vendor "HIT", prod id 28159
(II) NV(0): Printing probed modes for output DVI0
(II) NV(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NV(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) NV(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NV(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Probing for EDID on I2C bus 1...
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA2 ... nothing.
(II) NV(0): EDID for output VGA2
(II) NV(0): Probing for EDID on I2C bus 0...
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: HIT  Model: 6dff  Serial#: 16843009
(II) NV(0): Year: 2007  Week: 20
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) NV(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #3: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Monitor name: N220W DVI
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 150 MHz
(II) NV(0): Serial No: 0WDP0B7502119
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff002134ff6d01010101
(II) NV(0): 	14110103802f1e78ead515a455499a27
(II) NV(0): 	145054adcf008180b3009500950f0101
(II) NV(0): 	01010101010121399030621a274068b0
(II) NV(0): 	3600da281100001c000000fc004e3232
(II) NV(0): 	3057204456490a202020000000fd0038
(II) NV(0): 	4c1f500f000a202020202020000000ff
(II) NV(0): 	003057445030423735303231313900f9
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): EDID for output DVI0
(II) NV(0): Manufacturer: HIT  Model: 6dff  Serial#: 16843009
(II) NV(0): Year: 2007  Week: 20
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) NV(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #3: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Monitor name: N220W DVI
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 150 MHz
(II) NV(0): Serial No: 0WDP0B7502119
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff002134ff6d01010101
(II) NV(0): 	14110103802f1e78ead515a455499a27
(II) NV(0): 	145054adcf008180b3009500950f0101
(II) NV(0): 	01010101010121399030621a274068b0
(II) NV(0): 	3600da281100001c000000fc004e3232
(II) NV(0): 	3057204456490a202020000000fd0038
(II) NV(0): 	4c1f500f000a202020202020000000ff
(II) NV(0): 	003057445030423735303231313900f9
(II) NV(0): EDID vendor "HIT", prod id 28159
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NV(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NV(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) NV(0): EDID for output VGA1
(II) NV(0): EDID vendor "HIT", prod id 28159
(II) NV(0): Printing probed modes for output DVI0
(II) NV(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NV(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) NV(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NV(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Probing for EDID on I2C bus 1...
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA2 ... nothing.
(II) NV(0): EDID for output VGA2
(II) NV(0): Probing for EDID on I2C bus 0...
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: HIT  Model: 6dff  Serial#: 16843009
(II) NV(0): Year: 2007  Week: 20
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) NV(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #3: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Monitor name: N220W DVI
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 150 MHz
(II) NV(0): Serial No: 0WDP0B7502119
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff002134ff6d01010101
(II) NV(0): 	14110103802f1e78ead515a455499a27
(II) NV(0): 	145054adcf008180b3009500950f0101
(II) NV(0): 	01010101010121399030621a274068b0
(II) NV(0): 	3600da281100001c000000fc004e3232
(II) NV(0): 	3057204456490a202020000000fd0038
(II) NV(0): 	4c1f500f000a202020202020000000ff
(II) NV(0): 	003057445030423735303231313900f9
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): EDID for output DVI0
(II) NV(0): Manufacturer: HIT  Model: 6dff  Serial#: 16843009
(II) NV(0): Year: 2007  Week: 20
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) NV(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #3: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Monitor name: N220W DVI
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 150 MHz
(II) NV(0): Serial No: 0WDP0B7502119
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff002134ff6d01010101
(II) NV(0): 	14110103802f1e78ead515a455499a27
(II) NV(0): 	145054adcf008180b3009500950f0101
(II) NV(0): 	01010101010121399030621a274068b0
(II) NV(0): 	3600da281100001c000000fc004e3232
(II) NV(0): 	3057204456490a202020000000fd0038
(II) NV(0): 	4c1f500f000a202020202020000000ff
(II) NV(0): 	003057445030423735303231313900f9
(II) NV(0): EDID vendor "HIT", prod id 28159
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NV(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NV(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) NV(0): EDID for output VGA1
(II) NV(0): EDID vendor "HIT", prod id 28159
(II) NV(0): Printing probed modes for output DVI0
(II) NV(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NV(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) NV(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NV(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Probing for EDID on I2C bus 1...
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA2 ... nothing.
(II) NV(0): EDID for output VGA2
(II) NV(0): Probing for EDID on I2C bus 0...
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: HIT  Model: 6dff  Serial#: 16843009
(II) NV(0): Year: 2007  Week: 20
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) NV(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #3: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Monitor name: N220W DVI
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 150 MHz
(II) NV(0): Serial No: 0WDP0B7502119
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff002134ff6d01010101
(II) NV(0): 	14110103802f1e78ead515a455499a27
(II) NV(0): 	145054adcf008180b3009500950f0101
(II) NV(0): 	01010101010121399030621a274068b0
(II) NV(0): 	3600da281100001c000000fc004e3232
(II) NV(0): 	3057204456490a202020000000fd0038
(II) NV(0): 	4c1f500f000a202020202020000000ff
(II) NV(0): 	003057445030423735303231313900f9
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): EDID for output DVI0
(II) NV(0): Manufacturer: HIT  Model: 6dff  Serial#: 16843009
(II) NV(0): Year: 2007  Week: 20
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) NV(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #3: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Monitor name: N220W DVI
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 150 MHz
(II) NV(0): Serial No: 0WDP0B7502119
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff002134ff6d01010101
(II) NV(0): 	14110103802f1e78ead515a455499a27
(II) NV(0): 	145054adcf008180b3009500950f0101
(II) NV(0): 	01010101010121399030621a274068b0
(II) NV(0): 	3600da281100001c000000fc004e3232
(II) NV(0): 	3057204456490a202020000000fd0038
(II) NV(0): 	4c1f500f000a202020202020000000ff
(II) NV(0): 	003057445030423735303231313900f9
(II) NV(0): EDID vendor "HIT", prod id 28159
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NV(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NV(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) NV(0): EDID for output VGA1
(II) NV(0): EDID vendor "HIT", prod id 28159
(II) NV(0): Printing probed modes for output DVI0
(II) NV(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NV(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) NV(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NV(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Probing for EDID on I2C bus 1...
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA2 ... nothing.
(II) NV(0): EDID for output VGA2
(II) NV(0): Probing for EDID on I2C bus 0...
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: HIT  Model: 6dff  Serial#: 16843009
(II) NV(0): Year: 2007  Week: 20
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) NV(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #3: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Monitor name: N220W DVI
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 150 MHz
(II) NV(0): Serial No: 0WDP0B7502119
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff002134ff6d01010101
(II) NV(0): 	14110103802f1e78ead515a455499a27
(II) NV(0): 	145054adcf008180b3009500950f0101
(II) NV(0): 	01010101010121399030621a274068b0
(II) NV(0): 	3600da281100001c000000fc004e3232
(II) NV(0): 	3057204456490a202020000000fd0038
(II) NV(0): 	4c1f500f000a202020202020000000ff
(II) NV(0): 	003057445030423735303231313900f9
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): EDID for output DVI0
(II) NV(0): Manufacturer: HIT  Model: 6dff  Serial#: 16843009
(II) NV(0): Year: 2007  Week: 20
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) NV(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #3: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Monitor name: N220W DVI
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 150 MHz
(II) NV(0): Serial No: 0WDP0B7502119
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff002134ff6d01010101
(II) NV(0): 	14110103802f1e78ead515a455499a27
(II) NV(0): 	145054adcf008180b3009500950f0101
(II) NV(0): 	01010101010121399030621a274068b0
(II) NV(0): 	3600da281100001c000000fc004e3232
(II) NV(0): 	3057204456490a202020000000fd0038
(II) NV(0): 	4c1f500f000a202020202020000000ff
(II) NV(0): 	003057445030423735303231313900f9
(II) NV(0): EDID vendor "HIT", prod id 28159
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NV(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NV(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) NV(0): EDID for output VGA1
(II) NV(0): EDID vendor "HIT", prod id 28159
(II) NV(0): Printing probed modes for output DVI0
(II) NV(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NV(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) NV(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NV(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Probing for EDID on I2C bus 1...
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA2 ... nothing.
(II) NV(0): EDID for output VGA2
(II) NV(0): Probing for EDID on I2C bus 0...
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: HIT  Model: 6dff  Serial#: 16843009
(II) NV(0): Year: 2007  Week: 20
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) NV(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #3: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Monitor name: N220W DVI
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 150 MHz
(II) NV(0): Serial No: 0WDP0B7502119
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff002134ff6d01010101
(II) NV(0): 	14110103802f1e78ead515a455499a27
(II) NV(0): 	145054adcf008180b3009500950f0101
(II) NV(0): 	01010101010121399030621a274068b0
(II) NV(0): 	3600da281100001c000000fc004e3232
(II) NV(0): 	3057204456490a202020000000fd0038
(II) NV(0): 	4c1f500f000a202020202020000000ff
(II) NV(0): 	003057445030423735303231313900f9
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): EDID for output DVI0
(II) NV(0): Manufacturer: HIT  Model: 6dff  Serial#: 16843009
(II) NV(0): Year: 2007  Week: 20
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) NV(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #3: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Monitor name: N220W DVI
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 150 MHz
(II) NV(0): Serial No: 0WDP0B7502119
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff002134ff6d01010101
(II) NV(0): 	14110103802f1e78ead515a455499a27
(II) NV(0): 	145054adcf008180b3009500950f0101
(II) NV(0): 	01010101010121399030621a274068b0
(II) NV(0): 	3600da281100001c000000fc004e3232
(II) NV(0): 	3057204456490a202020000000fd0038
(II) NV(0): 	4c1f500f000a202020202020000000ff
(II) NV(0): 	003057445030423735303231313900f9
(II) NV(0): EDID vendor "HIT", prod id 28159
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NV(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NV(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) NV(0): EDID for output VGA1
(II) NV(0): EDID vendor "HIT", prod id 28159
(II) NV(0): Printing probed modes for output DVI0
(II) NV(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NV(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) NV(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NV(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Probing for EDID on I2C bus 1...
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA2 ... nothing.
(II) NV(0): EDID for output VGA2
(II) config/hal: Adding input device PWC snapshot button
(**) PWC snapshot button: always reports core events
(**) PWC snapshot button: Device: "/dev/input/event6"
(II) PWC snapshot button: Found keys
(II) PWC snapshot button: Configuring as keyboard
(II) XINPUT: Adding extended input device "PWC snapshot button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(**) Option "xkb_variant" "mac"
(II) Mitsumi Electric Apple Extended USB Keyboard: Close
(II) UnloadModule: "evdev"
(II) Mitsumi Electric Apple Extended USB Keyboard: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) Dell Premium USB Optical Mouse: Close
(II) UnloadModule: "evdev"
(II) PWC snapshot button: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log
```

The things of note in this error is:
```
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: file too short
(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)
```

What could be the way to fix this? I really want to fix this problem...

---

### Post by steev182 on 2009-09-24
I also had this show up in my kern.log:

```
Sep 24 22:33:27 steve-desktop kernel: [    6.591629] nvidia: module license 'NVIDIA' taints kernel.
Sep 24 22:33:27 steve-desktop kernel: [    6.591633] Disabling lock debugging due to kernel taint
Sep 24 22:33:27 steve-desktop kernel: [    6.605626] EXT4-fs: mballoc enabled
Sep 24 22:33:27 steve-desktop kernel: [    6.605641] EXT4-fs (sdb1): mounted filesystem with ordered data mode
Sep 24 22:33:27 steve-desktop kernel: [    6.847417] EDAC MC0: Giving out device to 'i3000_edac' 'i3000': DEV 0000:00:00.0
Sep 24 22:33:27 steve-desktop kernel: [    6.847440] EDAC PCI0: Giving out device to module 'i3000_edac' controller 'EDAC PCI controller': DEV '0000:00:00.0' (POLLED)
Sep 24 22:33:27 steve-desktop kernel: [    6.847631] nvidia 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Sep 24 22:33:27 steve-desktop kernel: [    6.847639] nvidia 0000:02:00.0: setting latency timer to 64
Sep 24 22:33:27 steve-desktop kernel: [    6.847797] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
```

---

### Post by steev182 on 2009-09-25
I managed to fix this.

It appears that the onboard radeon was starting and trying to take precedence over the nvidia.

adding

```
blacklist radeon
```

to /etc/modprobe.d/blacklist.conf fixed it nicely :D

---

