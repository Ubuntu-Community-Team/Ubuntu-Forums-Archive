---
title: "ATI, Xlib:  extension &quot;XFree86-DRI&quot; missing on display &quot;:0.0&quot;."
date: 2011-01-11
forum: Multimedia Software
---

### Post by lvm on 2011-01-11
VLC media player 1.1.4 The Luggage (revision exported)
[skipped]
libva: libva version 0.31.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns -1

and hardware acceleration dosn't work. Now I'm not the first to come across this problem and I tried all the stuff which is recommended in this situation - explicitly loading dri, disabling composite, updating and reinstalling drivers (currently version 8.801) - no effect. Any fresh ideas?

ATI HD 4290, ubuntu 10.10

Xorg.0.log follows, the last line is interesting (actual resolution is 1920*1080)
```

[    10.961] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    10.961] X Protocol Version 11, Revision 0
[    10.961] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    10.961] Current Operating System: Linux htpc 2.6.35-24-generic-pae #42-Ubuntu SMP Thu Dec 2 03:21:31 UTC 2010 i686
[    10.961] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.35-24-generic-pae root=UUID=f7dcc9e2-5750-4b69-9133-62e0c940ea66 ro quiet splash
[    10.961] Build Date: 16 September 2010  05:39:22PM
[    10.961] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    10.961] Current version of pixman: 0.18.4
[    10.961] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    10.961] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    10.961] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 11 19:27:14 2011
[    10.961] (==) Using config file: "/etc/X11/xorg.conf"
[    10.961] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    10.961] (==) ServerLayout "aticonfig Layout"
[    10.961] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    10.961] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    10.961] (**) |   |-->Device "aticonfig-Device[0]-0"
[    10.961] (==) Automatically adding devices
[    10.961] (==) Automatically enabling devices
[    10.961] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    10.961] 	Entry deleted from font path.
[    10.961] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    10.961] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    10.961] (**) Extension "Composite" is disabled
[    10.961] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    10.961] (II) Loader magic: 0x81f8e00
[    10.961] (II) Module ABI versions:
[    10.961] 	X.Org ANSI C Emulation: 0.4
[    10.961] 	X.Org Video Driver: 8.0
[    10.961] 	X.Org XInput driver : 11.0
[    10.961] 	X.Org Server Extension : 4.0
[    10.962] (--) PCI:*(0:1:5:0) 1002:9714:1462:7642 rev 0, Mem @ 0xd0000000/268435456, 0xfe8f0000/65536, 0xfe700000/1048576, I/O @ 0x0000b000/256
[    10.962] (II) Open ACPI successful (/var/run/acpid.socket)
[    10.962] (II) "extmod" will be loaded by default.
[    10.962] (II) "dbe" will be loaded by default.
[    10.962] (II) "glx" will be loaded by default.
[    10.962] (II) "record" will be loaded by default.
[    10.962] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    10.962] (II) "dri2" will be loaded by default.
[    10.962] (II) LoadModule: "dri"
[    10.973] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    10.973] (II) Module dri: vendor="X.Org Foundation"
[    10.973] 	compiled for 1.9.0, module version = 1.0.0
[    10.973] 	ABI class: X.Org Server Extension, version 4.0
[    10.973] (II) Loading extension XFree86-DRI
[    10.973] (II) LoadModule: "extmod"
[    10.974] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    10.974] (II) Module extmod: vendor="X.Org Foundation"
[    10.974] 	compiled for 1.9.0, module version = 1.0.0
[    10.974] 	Module class: X.Org Server Extension
[    10.974] 	ABI class: X.Org Server Extension, version 4.0
[    10.974] (II) Loading extension MIT-SCREEN-SAVER
[    10.974] (II) Loading extension XFree86-VidModeExtension
[    10.974] (II) Loading extension XFree86-DGA
[    10.974] (II) Loading extension DPMS
[    10.974] (II) Loading extension XVideo
[    10.974] (II) Loading extension XVideo-MotionCompensation
[    10.974] (II) Loading extension X-Resource
[    10.974] (II) LoadModule: "dbe"
[    10.974] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    10.974] (II) Module dbe: vendor="X.Org Foundation"
[    10.974] 	compiled for 1.9.0, module version = 1.0.0
[    10.974] 	Module class: X.Org Server Extension
[    10.974] 	ABI class: X.Org Server Extension, version 4.0
[    10.974] (II) Loading extension DOUBLE-BUFFER
[    10.974] (II) LoadModule: "glx"
[    10.974] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[    10.974] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    10.974] 	compiled for 7.6.0, module version = 1.0.0
[    10.974] (II) Loading extension GLX
[    10.974] (II) LoadModule: "record"
[    10.974] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    10.974] (II) Module record: vendor="X.Org Foundation"
[    10.974] 	compiled for 1.9.0, module version = 1.13.0
[    10.974] 	Module class: X.Org Server Extension
[    10.974] 	ABI class: X.Org Server Extension, version 4.0
[    10.974] (II) Loading extension RECORD
[    10.974] (II) LoadModule: "dri2"
[    10.975] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    10.975] (II) Module dri2: vendor="X.Org Foundation"
[    10.975] 	compiled for 1.9.0, module version = 1.2.0
[    10.975] 	ABI class: X.Org Server Extension, version 4.0
[    10.975] (II) Loading extension DRI2
[    10.975] (II) LoadModule: "fglrx"
[    10.975] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    10.987] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    10.987] 	compiled for 1.4.99.906, module version = 8.80.5
[    10.987] 	Module class: X.Org Video Driver
[    10.987] (II) Loading sub module "fglrxdrm"
[    10.987] (II) LoadModule: "fglrxdrm"
[    10.987] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    10.988] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    10.988] 	compiled for 1.4.99.906, module version = 8.80.5
[    10.988] (II) ATI Proprietary Linux Driver Version Identifier:8.80.5
[    10.988] (II) ATI Proprietary Linux Driver Release Identifier: 8.801                                
[    10.988] (II) ATI Proprietary Linux Driver Build Date: Nov 25 2010 21:35:47
[    10.988] (++) using VT number 7

[    10.988] (WW) Falling back to old probe method for fglrx
[    10.993] (II) Loading PCS database from /etc/ati/amdpcsdb
[    10.993] (--) Chipset Supported AMD Graphics Processor (0x9714) found
[    10.993] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[    10.993] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[    10.993] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[    10.993] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[    10.993] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[    10.993] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[    10.993] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[    10.993] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[    10.993] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[    10.993] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
[    10.993] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:0) found
[    10.993] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:0) found
[    10.993] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:2) found
[    10.993] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:5:1) found
[    10.993] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    10.993] (II) AMD Video driver is signed
[    10.993] (II) fglrx(0): pEnt->device->identifier=0x86566a8
[    10.993] (II) fglrx(0): === [xdl_x760_atiddxPreInit] === begin
[    10.993] (II) Loading sub module "vgahw"
[    10.993] (II) LoadModule: "vgahw"
[    10.994] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    10.994] (II) Module vgahw: vendor="X.Org Foundation"
[    10.994] 	compiled for 1.9.0, module version = 0.1.0
[    10.994] 	ABI class: X.Org Video Driver, version 8.0
[    10.994] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    10.994] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    10.994] (==) fglrx(0): Default visual is TrueColor
[    10.994] (**) fglrx(0): Option "DPMS" "true"
[    10.994] (==) fglrx(0): RGB weight 888
[    10.994] (II) fglrx(0): Using 8 bits per RGB 
[    10.994] (==) fglrx(0): Buffer Tiling is ON
[    10.994] (II) Loading sub module "fglrxdrm"
[    10.994] (II) LoadModule: "fglrxdrm"
[    10.994] (II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    10.995] ukiDynamicMajor: found major device number 250
[    10.995] ukiDynamicMajor: found major device number 250
[    10.995] ukiOpenByBusid: Searching for BusID PCI:1:5:0
[    10.995] ukiOpenDevice: node name is /dev/ati/card0
[    10.995] ukiOpenDevice: open result is 11, (OK)
[    10.995] ukiOpenByBusid: ukiOpenMinor returns 11
[    10.995] ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
[    10.995] (==) fglrx(0): NoAccel = NO
[    10.995] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    10.995] (--) fglrx(0): Chipset: "ATI Radeon HD 4290" (Chipset = 0x9714)
[    10.995] (--) fglrx(0): (PciSubVendor = 0x1462, PciSubDevice = 0x7642)
[    10.995] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    10.995] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    10.995] (--) fglrx(0): MMIO registers at 0xfe8f0000
[    10.995] (--) fglrx(0): I/O port at 0x0000b000
[    10.995] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    10.996] (II) fglrx(0): AC Adapter is used
[    11.001] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    11.042] (II) Loading sub module "vbe"
[    11.042] (II) LoadModule: "vbe"
[    11.042] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    11.042] (II) Module vbe: vendor="X.Org Foundation"
[    11.042] 	compiled for 1.9.0, module version = 1.1.0
[    11.043] 	ABI class: X.Org Video Driver, version 8.0
[    11.043] (II) fglrx(0): VESA BIOS detected
[    11.043] (II) fglrx(0): VESA VBE Version 3.0
[    11.043] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    11.043] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    11.043] (II) fglrx(0): VESA VBE OEM Software Rev: 10.94
[    11.043] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    11.043] (II) fglrx(0): VESA VBE OEM Product: RS880
[    11.043] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    11.049] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    11.049] (II) fglrx(0): UMA/SP interleave mode is enabled in the BIOS
[    11.049] (--) fglrx(0): Video RAM: 638976 kByte, Type: DDR3
[    11.049] (II) fglrx(0): PCIE card detected
[    11.049] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    11.049] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    11.051] (II) fglrx(0): Using adapter: 1:5.0.
[    11.056] (II) fglrx(0): [FB] MC range(MCFBBase = 0xc0000000, MCFBSize = 0x27000000)
[    11.212] (II) fglrx(0): Interrupt handler installed at IRQ 18.
[    11.213] (II) fglrx(0): RandR 1.2 support is enabled!
[    11.213] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    11.213] (==) fglrx(0): Center Mode is disabled 
[    11.213] (II) Loading sub module "fb"
[    11.213] (II) LoadModule: "fb"
[    11.213] (II) Loading /usr/lib/xorg/modules/libfb.so
[    11.213] (II) Module fb: vendor="X.Org Foundation"
[    11.213] 	compiled for 1.9.0, module version = 1.0.0
[    11.213] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    11.213] (II) Loading sub module "ddc"
[    11.213] (II) LoadModule: "ddc"
[    11.213] (II) Module "ddc" already built-in
[    12.048] (II) fglrx(0): Finished Initialize PPLIB!
[    12.049] (II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
[    12.049] (II) fglrx(0): Output CRT1 has no monitor section
[    12.049] (II) Loading sub module "ddc"
[    12.049] (II) LoadModule: "ddc"
[    12.049] (II) Module "ddc" already built-in
[    12.049] (II) fglrx(0): Connected Display0: DFP1
[    12.049] (II) Quirked EDID physical size to 0x0 cm
[    12.049] (II) fglrx(0): Display0 EDID data ---------------------------
[    12.049] (II) fglrx(0): Manufacturer: SAM  Model: 509  Serial#: 1
[    12.049] (II) fglrx(0): Year: 2008  Week: 48
[    12.049] (II) fglrx(0): EDID Version: 1.3
[    12.049] (II) fglrx(0): Digital Display Input
[    12.049] (II) fglrx(0): Indeterminate output size
[    12.049] (II) fglrx(0): Gamma: 2.20
[    12.049] (II) fglrx(0): No DPMS capabilities specified
[    12.049] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    12.049] (II) fglrx(0): First detailed timing is preferred mode
[    12.049] (II) fglrx(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[    12.049] (II) fglrx(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
[    12.049] (II) fglrx(0): Supported established timings:
[    12.049] (II) fglrx(0): 720x400@70Hz
[    12.049] (II) fglrx(0): 640x480@60Hz
[    12.049] (II) fglrx(0): 640x480@67Hz
[    12.049] (II) fglrx(0): 640x480@72Hz
[    12.049] (II) fglrx(0): 640x480@75Hz
[    12.050] (II) fglrx(0): 800x600@60Hz
[    12.050] (II) fglrx(0): 800x600@72Hz
[    12.050] (II) fglrx(0): 800x600@75Hz
[    12.050] (II) fglrx(0): 832x624@75Hz
[    12.050] (II) fglrx(0): 1024x768@60Hz
[    12.050] (II) fglrx(0): 1024x768@70Hz
[    12.050] (II) fglrx(0): 1024x768@75Hz
[    12.050] (II) fglrx(0): 1280x1024@75Hz
[    12.050] (II) fglrx(0): 1152x864@75Hz
[    12.050] (II) fglrx(0): Manufacturer's mask: 0
[    12.050] (II) fglrx(0): Supported standard timings:
[    12.050] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    12.050] (II) fglrx(0): #1: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    12.050] (II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    12.050] (II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    12.050] (II) fglrx(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    12.050] (II) fglrx(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    12.050] (II) fglrx(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    12.050] (II) fglrx(0): Supported detailed timing:
[    12.050] (II) fglrx(0): clock: 148.5 MHz   Image Size:  160 x 90 mm
[    12.050] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    12.050] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    12.050] (II) fglrx(0): Supported detailed timing:
[    12.050] (II) fglrx(0): clock: 85.5 MHz   Image Size:  160 x 90 mm
[    12.050] (II) fglrx(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
[    12.050] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
[    12.050] (II) fglrx(0): Ranges: V min: 24 V max: 75 Hz, H min: 26 H max: 81 kHz, PixClock max 235 MHz
[    12.050] (II) fglrx(0): Monitor name: SAMSUNG
[    12.050] (II) fglrx(0): Supported detailed timing:
[    12.050] (II) fglrx(0): clock: 74.2 MHz   Image Size:  160 x 90 mm
[    12.050] (II) fglrx(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    12.050] (II) fglrx(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    12.050] (II) fglrx(0): Supported detailed timing:
[    12.050] (II) fglrx(0): clock: 74.2 MHz   Image Size:  160 x 90 mm
[    12.050] (II) fglrx(0): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
[    12.050] (II) fglrx(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    12.050] (II) fglrx(0): Supported detailed timing:
[    12.050] (II) fglrx(0): clock: 74.2 MHz   Image Size:  160 x 90 mm
[    12.050] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    12.050] (II) fglrx(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    12.050] (II) fglrx(0): Supported detailed timing:
[    12.050] (II) fglrx(0): clock: 74.2 MHz   Image Size:  160 x 90 mm
[    12.050] (II) fglrx(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[    12.050] (II) fglrx(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    12.050] (II) fglrx(0): Number of EDID sections to follow: 1
[    12.050] (II) fglrx(0): EDID (in hex):
[    12.050] (II) fglrx(0): 	00ffffffffffff004c2d090501000000
[    12.050] (II) fglrx(0): 	30120103801009780aee91a3544c9926
[    12.050] (II) fglrx(0): 	0f5054bdef80714f8100814081809500
[    12.050] (II) fglrx(0): 	950fb3000101023a801871382d40582c
[    12.050] (II) fglrx(0): 	4500a05a0000001e662150b051001b30
[    12.050] (II) fglrx(0): 	40703600a05a0000001e000000fd0018
[    12.050] (II) fglrx(0): 	4b1a5117000a202020202020000000fc
[    12.050] (II) fglrx(0): 	0053414d53554e470a2020202020016f
[    12.050] (II) fglrx(0): End of Display0 EDID data --------------------
[    12.070] (II) Quirked EDID physical size to 0x0 cm
[    12.070] (II) fglrx(0): EDID for output DFP1
[    12.070] (II) fglrx(0): Manufacturer: SAM  Model: 509  Serial#: 1
[    12.070] (II) fglrx(0): Year: 2008  Week: 48
[    12.070] (II) fglrx(0): EDID Version: 1.3
[    12.070] (II) fglrx(0): Digital Display Input
[    12.070] (II) fglrx(0): Indeterminate output size
[    12.070] (II) fglrx(0): Gamma: 2.20
[    12.070] (II) fglrx(0): No DPMS capabilities specified
[    12.070] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    12.070] (II) fglrx(0): First detailed timing is preferred mode
[    12.070] (II) fglrx(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[    12.070] (II) fglrx(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
[    12.070] (II) fglrx(0): Supported established timings:
[    12.070] (II) fglrx(0): 720x400@70Hz
[    12.070] (II) fglrx(0): 640x480@60Hz
[    12.070] (II) fglrx(0): 640x480@67Hz
[    12.070] (II) fglrx(0): 640x480@72Hz
[    12.070] (II) fglrx(0): 640x480@75Hz
[    12.070] (II) fglrx(0): 800x600@60Hz
[    12.070] (II) fglrx(0): 800x600@72Hz
[    12.070] (II) fglrx(0): 800x600@75Hz
[    12.070] (II) fglrx(0): 832x624@75Hz
[    12.070] (II) fglrx(0): 1024x768@60Hz
[    12.070] (II) fglrx(0): 1024x768@70Hz
[    12.070] (II) fglrx(0): 1024x768@75Hz
[    12.070] (II) fglrx(0): 1280x1024@75Hz
[    12.070] (II) fglrx(0): 1152x864@75Hz
[    12.070] (II) fglrx(0): Manufacturer's mask: 0
[    12.070] (II) fglrx(0): Supported standard timings:
[    12.070] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    12.070] (II) fglrx(0): #1: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    12.070] (II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    12.070] (II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    12.070] (II) fglrx(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    12.070] (II) fglrx(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    12.070] (II) fglrx(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    12.070] (II) fglrx(0): Supported detailed timing:
[    12.070] (II) fglrx(0): clock: 148.5 MHz   Image Size:  160 x 90 mm
[    12.070] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    12.070] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    12.070] (II) fglrx(0): Supported detailed timing:
[    12.070] (II) fglrx(0): clock: 85.5 MHz   Image Size:  160 x 90 mm
[    12.070] (II) fglrx(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
[    12.070] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
[    12.070] (II) fglrx(0): Ranges: V min: 24 V max: 75 Hz, H min: 26 H max: 81 kHz, PixClock max 235 MHz
[    12.070] (II) fglrx(0): Monitor name: SAMSUNG
[    12.070] (II) fglrx(0): Number of EDID sections to follow: 1
[    12.070] (II) fglrx(0): EDID (in hex):
[    12.070] (II) fglrx(0): 	7465642064657461696c65642074696d
[    12.070] (II) fglrx(0): 	696e673a0a00003a0a0069616c233a20
[    12.070] (II) fglrx(0): 	25750a00290000000000000078283029
[    12.070] (II) fglrx(0): 	3a20454449442028696e20686578293a
[    12.070] (II) fglrx(0): 	0a00a05a0000001e662150b041000000
[    12.070] (II) fglrx(0): 	00000000782830293a204e756d626572
[    12.070] (II) fglrx(0): 	206f6620454449442073656374696f6e
[    12.070] (II) fglrx(0): 	7320746f20666f6c6c6f773a2025690a
[    12.070] (II) fglrx(0): EDID vendor "SAM", prod id 1289
[    12.070] (II) fglrx(0): Using EDID range info for horizontal sync
[    12.070] (II) fglrx(0): Using EDID range info for vertical refresh
[    12.070] (II) fglrx(0): Printing DDC gathered Modelines:
[    12.070] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    12.070] (II) fglrx(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[    12.070] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    12.070] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    12.070] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    12.070] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    12.070] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    12.070] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    12.070] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    12.070] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    12.070] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    12.070] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    12.070] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    12.070] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    12.070] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    12.070] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    12.070] (II) fglrx(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[    12.070] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    12.070] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    12.070] (II) fglrx(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    12.070] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    12.070] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    12.070] (II) fglrx(0): Printing probed modes for output DFP1
[    12.070] (II) fglrx(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz)
[    12.070] (II) fglrx(0): Modeline "1776x1000"x60.0  147.05  1776 1880 2072 2368  1000 1001 1004 1035 +hsync -vsync (62.1 kHz)
[    12.070] (II) fglrx(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 -hsync -vsync (56.2 kHz)
[    12.070] (II) fglrx(0): Modeline "1920x1080"x30.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace -hsync -vsync (33.8 kHz)
[    12.070] (II) fglrx(0): Modeline "1920x1080"x25.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace -hsync -vsync (28.1 kHz)
[    12.070] (II) fglrx(0): Modeline "1920x1080"x24.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 -hsync -vsync (27.0 kHz)
[    12.070] (II) fglrx(0): Modeline "1776x1000"x30.0   67.92  1776 1824 2000 2224  1000 1001 1004 1018 +hsync -vsync (30.5 kHz)
[    12.070] (II) fglrx(0): Modeline "1776x1000"x25.0   55.21  1776 1800 1976 2176  1000 1001 1004 1015 +hsync -vsync (25.4 kHz)
[    12.071] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync (65.3 kHz)
[    12.071] (II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync -vsync (65.3 kHz)
[    12.071] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 -hsync -vsync (80.0 kHz)
[    12.071] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 -hsync -vsync (64.0 kHz)
[    12.071] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync (55.9 kHz)
[    12.071] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 -hsync -vsync (60.0 kHz)
[    12.071] (II) fglrx(0): Modeline "1366x768"x60.0   85.76  1366 1438 1582 1800  768 769 772 795 +hsync -vsync (47.6 kHz)
[    12.071] (II) fglrx(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 -hsync -vsync (47.7 kHz)
[    12.071] (II) fglrx(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 +hsync -vsync (49.7 kHz)
[    12.071] (II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 -hsync -vsync (67.5 kHz)
[    12.071] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync -vsync (53.7 kHz)
[    12.071] (II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
[    12.071] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 -hsync -vsync (45.0 kHz)
[    12.071] (II) fglrx(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 -hsync -vsync (37.5 kHz)
[    12.071] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[    12.071] (II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
[    12.071] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
[    12.071] (II) fglrx(0): Modeline "1152x648"x60.0   59.90  1152 1200 1320 1488  648 649 652 671 +hsync -vsync (40.3 kHz)
[    12.071] (II) fglrx(0): Modeline "1152x648"x50.0   48.55  1152 1184 1304 1456  648 649 652 667 +hsync -vsync (33.3 kHz)
[    12.071] (II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 -hsync -vsync (48.1 kHz)
[    12.071] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 -hsync -vsync (46.9 kHz)
[    12.071] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 -hsync -vsync (37.9 kHz)
[    12.071] (II) fglrx(0): Modeline "800x600"x50.0   31.14  800 824 904 1008  600 601 604 618 +hsync -vsync (30.9 kHz)
[    12.071] (II) fglrx(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 +hsync +vsync (31.2 kHz)
[    12.071] (II) fglrx(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 +hsync +vsync (31.5 kHz)
[    12.071] (II) fglrx(0): Modeline "720x480"x50.0   21.78  720 728 800 880  480 481 484 495 +hsync -vsync (24.8 kHz)
[    12.071] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
[    12.071] (II) fglrx(0): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 +hsync +vsync (37.9 kHz)
[    12.071] (II) fglrx(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
[    12.071] (II) fglrx(0): Modeline "640x480"x50.0   19.40  640 648 712 784  480 481 484 495 +hsync -vsync (24.7 kHz)
[    12.071] (II) fglrx(0): EDID for output CRT1
[    12.071] (II) fglrx(0): Output DFP1 connected
[    12.071] (II) fglrx(0): Output CRT1 disconnected
[    12.071] (II) fglrx(0): Using exact sizes for initial modes
[    12.071] (II) fglrx(0): Output DFP1 using initial mode 1920x1080
[    12.071] (II) fglrx(0): DPI set to (96, 96)
[    12.071] (II) fglrx(0): Adapter ATI Radeon HD 4290 has 2 configurable heads and 1 displays connected.
[    12.071] (==) fglrx(0):  PseudoColor visuals disabled
[    12.071] (II) Loading sub module "ramdac"
[    12.071] (II) LoadModule: "ramdac"
[    12.071] (II) Module "ramdac" already built-in
[    12.071] (==) fglrx(0): NoDRI = NO
[    12.071] (==) fglrx(0): Capabilities: 0x00000000
[    12.071] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    12.071] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    12.071] (==) fglrx(0): UseFastTLS=0
[    12.071] (==) fglrx(0): BlockSignalsOnLock=1
[    12.071] (--) Depth 24 pixmap format is 32 bpp
[    12.071] (II) Loading extension ATIFGLRXDRI
[    12.071] (II) fglrx(0): doing swlDriScreenInit
[    12.071] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    12.071] ukiDynamicMajor: found major device number 250
[    12.071] ukiDynamicMajor: found major device number 250
[    12.071] ukiDynamicMajor: found major device number 250
[    12.071] ukiOpenByBusid: Searching for BusID PCI:1:5:0
[    12.071] ukiOpenDevice: node name is /dev/ati/card0
[    12.071] ukiOpenDevice: open result is 16, (OK)
[    12.071] ukiOpenByBusid: ukiOpenMinor returns 16
[    12.071] ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
[    12.071] (II) fglrx(0): [uki] DRM interface version 1.0
[    12.071] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:5:0"
[    12.071] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    12.071] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0xb73f8000
[    12.071] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    12.071] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    12.071] (II) fglrx(0): swlDriScreenInit done
[    12.071] (II) fglrx(0): Kernel Module Version Information:
[    12.071] (II) fglrx(0):     Name: fglrx
[    12.071] (II) fglrx(0):     Version: 8.80.5
[    12.071] (II) fglrx(0):     Date: Nov 25 2010
[    12.071] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    12.071] (II) fglrx(0): Kernel Module version matches driver.
[    12.071] (II) fglrx(0): Kernel Module Build Time Information:
[    12.071] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.35-24-generic-pae
[    12.071] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    12.071] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    12.071] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    12.071] (II) fglrx(0): [uki] register handle = 0x00004000
[    12.080] (II) fglrx(0): DRI initialization successfull
[    12.080] (II) fglrx(0): FBADPhys: 0xe5fed000 FBMappedSize: 0x0100e000
[    12.080] (II) fglrx(0): Reserved 0x04000000 bytes of sideport memory for power saving
[    12.080] (==) fglrx(0): Backing store disabled
[    12.080] (II) Loading extension FGLRXEXTENSION
[    12.080] (**) fglrx(0): DPMS enabled
[    12.080] (II) fglrx(0): Initialized in-driver Xinerama extension
[    12.080] (**) fglrx(0): Textured Video is enabled.
[    12.080] (II) LoadModule: "glesx"
[    12.081] (II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
[    12.081] (II) Module glesx: vendor="X.Org Foundation"
[    12.081] 	compiled for 1.4.99.906, module version = 1.0.0
[    12.081] (II) Loading extension GLESX
[    12.081] (II) fglrx(0): GLESX enableFlags = 528
[    12.081] (II) fglrx(0): GLESX is enabled
[    12.081] (II) fglrx(0): Acceleration enabled
[    12.081] (II) LoadModule: "amdxmm"
[    12.081] (II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
[    12.081] (II) Module amdxmm: vendor="X.Org Foundation"
[    12.081] 	compiled for 1.8.99.905, module version = 1.0.0
[    12.082] (II) Loading extension AMDXVOPL
[    12.082] (II) Loading extension AMDXVBA
[    12.082] (II) fglrx(0): UVD feature is enabled
[    12.083] (II) fglrx(0): Composite extension is not loaded
[    12.083] (WW) fglrx(0): Option "VendorName" is not used
[    12.083] (WW) fglrx(0): Option "ModelName" is not used
[    12.083] (II) fglrx(0): X context handle = 0x1
[    12.083] (II) fglrx(0): [DRI] installation complete
[    12.083] (==) fglrx(0): Silken mouse enabled
[    12.084] (==) fglrx(0): Using HW cursor of display infrastructure!
[    12.084] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    12.137] (--) RandR disabled
[    12.137] (II) Initializing built-in extension Generic Event Extension
[    12.137] (II) Initializing built-in extension SHAPE
[    12.137] (II) Initializing built-in extension MIT-SHM
[    12.137] (II) Initializing built-in extension XInputExtension
[    12.137] (II) Initializing built-in extension XTEST
[    12.137] (II) Initializing built-in extension BIG-REQUESTS
[    12.137] (II) Initializing built-in extension SYNC
[    12.137] (II) Initializing built-in extension XKEYBOARD
[    12.137] (II) Initializing built-in extension XC-MISC
[    12.137] (II) Initializing built-in extension SECURITY
[    12.137] (II) Initializing built-in extension XINERAMA
[    12.137] (II) Initializing built-in extension XFIXES
[    12.137] (II) Initializing built-in extension RENDER
[    12.137] (II) Initializing built-in extension RANDR
[    12.137] (II) Initializing built-in extension COMPOSITE
[    12.137] (II) Initializing built-in extension DAMAGE
[    12.137] (II) Initializing built-in extension GESTURE
[    12.139] ukiDynamicMajor: found major device number 250
[    12.139] ukiDynamicMajor: found major device number 250
[    12.139] ukiOpenByBusid: Searching for BusID PCI:1:5:0
[    12.139] ukiOpenDevice: node name is /dev/ati/card0
[    12.139] ukiOpenDevice: open result is 17, (OK)
[    12.139] ukiOpenByBusid: ukiOpenMinor returns 17
[    12.139] ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
[    12.189] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    12.199] (II) fglrx(0): Enable the clock gating!
[    12.199] (II) fglrx(0): Setting screen physical size to 507 x 285

```

---

### Post by Baboontu on 2011-03-15
You're not the only one. Can somebody help?

---

### Post by Yellow Pasque on 2011-03-16
You need a special version of libva, and then rebuild vlc against it. All of that is done for you with this PPA: [https://launchpad.net/~dtl131/+archive/catalysthacks](https://launchpad.net/~dtl131/+archive/catalysthacks)

Don't forget to install xvba-video from here as well: [http://www.splitted-desktop.com/~gbeauchesne/xvba-video/](http://www.splitted-desktop.com/~gbeauchesne/xvba-video/)

---

