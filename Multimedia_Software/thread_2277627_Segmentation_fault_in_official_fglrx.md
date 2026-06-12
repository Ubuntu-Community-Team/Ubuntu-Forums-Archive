---
title: "Segmentation fault in official fglrx"
date: 2015-05-10
forum: Multimedia Software
---

### Post by dc740 on 2015-05-10
I used to play just fine for hours on my AMD HD 7770. Now everytime I open anything that uses the Source engine (CS:Go, L4D2), I get a segmentation fault after a few minutes. But I can play Dota2 just fine. I tried the open source drivers, but I get an error in Dota2 after some time playing.

Before everyone asks about temperatures: I'm using a water cooling solution, the card temperature is always below 56°C, and the CPU temperature is around 42°C while playing. No over-clocking at all.

It started happening with 14.10+fglrx Omega (14.12) after some daily ubuntu update (I didn't notice at the moment). The Omega drivers were working perfectly, and then suddenly they stopped crashing (probably after some kernel upgrade). Now I'm using ubuntu 15.04 + fglrx beta release exclusive for Ubuntu (which is the only version that compiles in 15.04), and I still get the problem.

I found this in "Xorg.1.log.old":

```
[ 40658.742] 
X.Org X Server 1.16.0
Release Date: 2014-07-16
[ 40658.742] X Protocol Version 11, Revision 0
[ 40658.742] Build Operating System: Linux 3.2.0-54-generic x86_64 Ubuntu
[ 40658.742] Current Operating System: Linux dc740-System-Product-Name 3.16.0-28-generic #38-Ubuntu SMP Fri Dec 12 17:37:40 UTC 2014 x86_64
[ 40658.742] Kernel command line: BOOT_IMAGE=/vmlinuz-3.16.0-28-generic root=/dev/mapper/lubuntu--vg-root ro
[ 40658.742] Build Date: 09 December 2014  11:01:03PM
[ 40658.742] xorg-server 2:1.16.0-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
[ 40658.742] Current version of pixman: 0.32.4
[ 40658.742] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[ 40658.742] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 40658.742] (==) Log file: "/var/log/Xorg.1.log", Time: Thu Dec 25 00:48:14 2014
[ 40658.743] (==) Using config file: "/etc/X11/xorg.conf"
[ 40658.743] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 40658.743] (==) ServerLayout "aticonfig Layout"
[ 40658.743] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[ 40658.743] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[ 40658.743] (**) |   |-->Device "aticonfig-Device[0]-0"
[ 40658.743] (==) Automatically adding devices
[ 40658.743] (==) Automatically enabling devices
[ 40658.743] (==) Automatically adding GPU devices
[ 40658.743] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 40658.743] 	Entry deleted from font path.
[ 40658.743] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 40658.743] 	Entry deleted from font path.
[ 40658.743] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 40658.743] 	Entry deleted from font path.
[ 40658.743] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 40658.743] 	Entry deleted from font path.
[ 40658.743] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 40658.743] 	Entry deleted from font path.
[ 40658.743] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[ 40658.743] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[ 40658.743] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[ 40658.743] (II) Loader magic: 0x7ff13ed2ed80
[ 40658.743] (II) Module ABI versions:
[ 40658.743] 	X.Org ANSI C Emulation: 0.4
[ 40658.743] 	X.Org Video Driver: 18.0
[ 40658.743] 	X.Org XInput driver : 21.0
[ 40658.743] 	X.Org Server Extension : 8.0
[ 40658.744] (--) PCI:*(0:1:0:0) 1002:683d:1682:3230 rev 0, Mem @ 0xd0000000/268435456, 0xfeb80000/262144, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
[ 40658.744] (II) "glx" will be loaded by default.
[ 40658.744] (WW) "xmir" is not to be loaded by default. Skipping.
[ 40658.744] (II) LoadModule: "glx"
[ 40658.773] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[ 40658.773] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[ 40658.773] 	compiled for 6.9.0, module version = 1.0.0
[ 40658.774] (II) LoadModule: "fglrx"
[ 40658.774] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[ 40658.800] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[ 40658.800] 	compiled for 1.4.99.906, module version = 14.50.2
[ 40658.800] 	Module class: X.Org Video Driver
[ 40658.800] (II) Loading sub module "fglrxdrm"
[ 40658.800] (II) LoadModule: "fglrxdrm"
[ 40658.800] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[ 40658.800] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[ 40658.800] 	compiled for 1.4.99.906, module version = 14.50.2
[ 40658.800] (II) AMD Proprietary Linux Driver Version Identifier:14.50.2
[ 40658.800] (II) AMD Proprietary Linux Driver Release Identifier: 14.501.1003                          
[ 40658.800] (II) AMD Proprietary Linux Driver Build Date: Nov 20 2014 21:22:54
[ 40658.800] (++) using VT number 8

[ 40659.347] (WW) Falling back to old probe method for fglrx
[ 40659.358] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[ 40659.362] ukiDynamicMajor: found major device number 250
[ 40659.362] ukiDynamicMajor: found major device number 250
[ 40659.362] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[ 40659.362] ukiOpenDevice: node name is /dev/ati/card0
[ 40659.362] ukiOpenDevice: open result is 9, (OK)
[ 40659.362] ukiOpenByBusid: ukiOpenMinor returns 9
[ 40659.363] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[ 40659.398] (--) Chipset Supported AMD Graphics Processor (0x683D) found
[ 40659.399] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[ 40659.399] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[ 40659.399] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
[ 40659.399] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[ 40659.399] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[ 40659.399] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
[ 40659.399] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[ 40659.399] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[ 40659.399] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
[ 40659.399] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[ 40659.399] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[ 40659.399] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[ 40659.399] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
[ 40659.399] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[ 40659.399] (II) fglrx(0): pEnt->device->identifier=0x7ff13fab12f0
[ 40659.399] (II) fglrx(0): === [xdl_xs116_atiddxPreInit] === begin
[ 40659.399] (II) fglrx(0): FB driver is not enabled
[ 40659.399] (II) Loading sub module "vgahw"
[ 40659.399] (II) LoadModule: "vgahw"
[ 40659.399] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[ 40659.399] (II) Module vgahw: vendor="X.Org Foundation"
[ 40659.399] 	compiled for 1.16.0, module version = 0.1.0
[ 40659.399] 	ABI class: X.Org Video Driver, version 18.0
[ 40659.400] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[ 40659.400] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[ 40659.400] (==) fglrx(0): Default visual is TrueColor
[ 40659.400] (**) fglrx(0): Option "DPMS" "true"
[ 40659.400] (==) fglrx(0): RGB weight 888
[ 40659.400] (II) fglrx(0): Using 8 bits per RGB 
[ 40659.400] (==) fglrx(0): Buffer Tiling is ON
[ 40659.400] (II) Loading sub module "fglrxdrm"
[ 40659.400] (II) LoadModule: "fglrxdrm"
[ 40659.400] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[ 40659.400] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[ 40659.400] 	compiled for 1.4.99.906, module version = 14.50.2
[ 40659.404] ukiDynamicMajor: found major device number 250
[ 40659.404] ukiDynamicMajor: found major device number 250
[ 40659.404] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[ 40659.404] ukiOpenDevice: node name is /dev/ati/card0
[ 40659.404] ukiOpenDevice: open result is 11, (OK)
[ 40659.404] ukiOpenByBusid: ukiOpenMinor returns 11
[ 40659.404] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[ 40659.404] (**) fglrx(0): NoAccel = NO
[ 40659.404] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[ 40659.404] (--) fglrx(0): Chipset: "AMD Radeon HD 7700 Series  " (Chipset = 0x683d)
[ 40659.404] (--) fglrx(0): (PciSubVendor = 0x1682, PciSubDevice = 0x3230)
[ 40659.404] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[ 40659.404] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[ 40659.404] (--) fglrx(0): MMIO registers at 0xfeb80000
[ 40659.404] (--) fglrx(0): I/O port at 0x0000d000
[ 40659.405] (==) fglrx(0): ROM-BIOS at 0x000c0000
[ 40659.405] (II) fglrx(0): AC Adapter is used
[ 40659.411] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[ 40659.560] (II) Loading sub module "vbe"
[ 40659.560] (II) LoadModule: "vbe"
[ 40659.560] (II) Loading /usr/lib/xorg/modules/libvbe.so
[ 40659.560] (II) Module vbe: vendor="X.Org Foundation"
[ 40659.560] 	compiled for 1.16.0, module version = 1.1.0
[ 40659.560] 	ABI class: X.Org Video Driver, version 18.0
[ 40659.561] (II) fglrx(0): VESA BIOS detected
[ 40659.561] (II) fglrx(0): VESA VBE Version 3.0
[ 40659.561] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[ 40659.561] (II) fglrx(0): VESA VBE OEM: AMD ATOMBIOS
[ 40659.561] (II) fglrx(0): VESA VBE OEM Software Rev: 15.15
[ 40659.561] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2010, Advanced Micro Devices, Inc.
[ 40659.561] (II) fglrx(0): VESA VBE OEM Product: VERDE
[ 40659.561] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[ 40659.561] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[ 40659.561] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
[ 40659.561] (II) fglrx(0): PCIE card detected
[ 40659.561] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[ 40659.561] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[ 40659.561] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf400000000, MCFBSize = 0x40000000)
[ 40659.561] (II) fglrx(0): RandR 1.2 support is enabled!
[ 40659.561] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[ 40659.561] (II) Loading sub module "fb"
[ 40659.561] (II) LoadModule: "fb"
[ 40659.561] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 40659.561] (II) Module fb: vendor="X.Org Foundation"
[ 40659.561] 	compiled for 1.16.0, module version = 1.0.0
[ 40659.561] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 40659.561] (II) fglrx(0): EDID Management option: EDID Management is enabled
[ 40659.561] (II) Loading sub module "ddc"
[ 40659.561] (II) LoadModule: "ddc"
[ 40659.561] (II) Module "ddc" already built-in
[ 40659.677] (II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
[ 40659.677] (II) fglrx(0): Output DFP2 has no monitor section
[ 40659.677] (II) fglrx(0): Output DFP3 has no monitor section
[ 40659.677] (II) fglrx(0): Output DFP4 has no monitor section
[ 40659.677] (II) fglrx(0): Output DFP5 has no monitor section
[ 40659.677] (II) fglrx(0): Output DFP6 has no monitor section
[ 40659.677] (II) fglrx(0): Output DFP7 has no monitor section
[ 40659.677] (II) fglrx(0): Output CRT1 has no monitor section
[ 40659.677] (II) Loading sub module "ddc"
[ 40659.677] (II) LoadModule: "ddc"
[ 40659.677] (II) Module "ddc" already built-in
[ 40659.677] (II) fglrx(0): Connected Display0: DFP7
[ 40659.677] (II) fglrx(0): Display0 EDID data ---------------------------
[ 40659.677] (II) fglrx(0): Manufacturer: DEL  Model: a038  Serial#: 825247829
[ 40659.677] (II) fglrx(0): Year: 2009  Week: 22
[ 40659.677] (II) fglrx(0): EDID Version: 1.3
[ 40659.677] (II) fglrx(0): Digital Display Input
[ 40659.677] (II) fglrx(0): Max Image Size [cm]: horiz.: 53  vert.: 30
[ 40659.677] (II) fglrx(0): Gamma: 2.20
[ 40659.677] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[ 40659.677] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[ 40659.677] (II) fglrx(0): Default color space is primary color space
[ 40659.677] (II) fglrx(0): First detailed timing is preferred mode
[ 40659.677] (II) fglrx(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[ 40659.677] (II) fglrx(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
[ 40659.677] (II) fglrx(0): Supported established timings:
[ 40659.677] (II) fglrx(0): 720x400@70Hz
[ 40659.678] (II) fglrx(0): 640x480@60Hz
[ 40659.678] (II) fglrx(0): 640x480@75Hz
[ 40659.678] (II) fglrx(0): 800x600@60Hz
[ 40659.678] (II) fglrx(0): 800x600@75Hz
[ 40659.678] (II) fglrx(0): 1024x768@60Hz
[ 40659.678] (II) fglrx(0): 1024x768@75Hz
[ 40659.678] (II) fglrx(0): 1280x1024@75Hz
[ 40659.678] (II) fglrx(0): Manufacturer's mask: 0
[ 40659.678] (II) fglrx(0): Supported standard timings:
[ 40659.678] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[ 40659.678] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[ 40659.678] (II) fglrx(0): #2: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[ 40659.678] (II) fglrx(0): Supported detailed timing:
[ 40659.678] (II) fglrx(0): clock: 148.5 MHz   Image Size:  531 x 298 mm
[ 40659.678] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[ 40659.678] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[ 40659.678] (II) fglrx(0): Serial No: Y183D95P10HU
[ 40659.678] (II) fglrx(0): Monitor name: DELL S2409W
[ 40659.678] (II) fglrx(0): Ranges: V min: 50 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[ 40659.678] (II) fglrx(0): EDID (in hex):
[ 40659.678] (II) fglrx(0): 	00ffffffffffff0010ac38a055483031
[ 40659.678] (II) fglrx(0): 	1613010380351e78eeee91a3544c9926
[ 40659.678] (II) fglrx(0): 	0f5054a54b00714f8180d1c001010101
[ 40659.678] (II) fglrx(0): 	010101010101023a801871382d40582c
[ 40659.678] (II) fglrx(0): 	4500132a2100001e000000ff00593138
[ 40659.678] (II) fglrx(0): 	3344393550313048550a000000fc0044
[ 40659.678] (II) fglrx(0): 	454c4c205332343039570a20000000fd
[ 40659.678] (II) fglrx(0): 	00324c1e5311000a20202020202000ba
[ 40659.678] (II) fglrx(0): End of Display0 EDID data --------------------
[ 40659.678] (II) fglrx(0): Dynamic Surface Resizing Enabled
[ 40659.678] (II) fglrx(0): EDID for output DFP1
[ 40659.679] (II) fglrx(0): EDID for output DFP2
[ 40659.679] (II) fglrx(0): EDID for output DFP3
[ 40659.679] (II) fglrx(0): EDID for output DFP4
[ 40659.679] (II) fglrx(0): EDID for output DFP5
[ 40659.679] (II) fglrx(0): EDID for output DFP6
[ 40659.679] (II) fglrx(0): EDID for output DFP7
[ 40659.679] (II) fglrx(0): Manufacturer: DEL  Model: a038  Serial#: 825247829
[ 40659.679] (II) fglrx(0): Year: 2009  Week: 22
[ 40659.679] (II) fglrx(0): EDID Version: 1.3
[ 40659.679] (II) fglrx(0): Digital Display Input
[ 40659.679] (II) fglrx(0): Max Image Size [cm]: horiz.: 53  vert.: 30
[ 40659.679] (II) fglrx(0): Gamma: 2.20
[ 40659.679] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[ 40659.679] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[ 40659.679] (II) fglrx(0): Default color space is primary color space
[ 40659.679] (II) fglrx(0): First detailed timing is preferred mode
[ 40659.679] (II) fglrx(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[ 40659.679] (II) fglrx(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
[ 40659.679] (II) fglrx(0): Supported established timings:
[ 40659.679] (II) fglrx(0): 720x400@70Hz
[ 40659.679] (II) fglrx(0): 640x480@60Hz
[ 40659.679] (II) fglrx(0): 640x480@75Hz
[ 40659.679] (II) fglrx(0): 800x600@60Hz
[ 40659.679] (II) fglrx(0): 800x600@75Hz
[ 40659.679] (II) fglrx(0): 1024x768@60Hz
[ 40659.679] (II) fglrx(0): 1024x768@75Hz
[ 40659.679] (II) fglrx(0): 1280x1024@75Hz
[ 40659.679] (II) fglrx(0): Manufacturer's mask: 0
[ 40659.679] (II) fglrx(0): Supported standard timings:
[ 40659.679] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[ 40659.679] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[ 40659.679] (II) fglrx(0): #2: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[ 40659.679] (II) fglrx(0): Supported detailed timing:
[ 40659.679] (II) fglrx(0): clock: 148.5 MHz   Image Size:  531 x 298 mm
[ 40659.679] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[ 40659.679] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[ 40659.679] (II) fglrx(0): Serial No: Y183D95P10HU
[ 40659.679] (II) fglrx(0): Monitor name: DELL S2409W
[ 40659.679] (II) fglrx(0): Ranges: V min: 50 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[ 40659.679] (II) fglrx(0): EDID (in hex):
[ 40659.679] (II) fglrx(0): 	00ffffffffffff0010ac38a055483031
[ 40659.679] (II) fglrx(0): 	1613010380351e78eeee91a3544c9926
[ 40659.679] (II) fglrx(0): 	0f5054a54b00714f8180d1c001010101
[ 40659.679] (II) fglrx(0): 	010101010101023a801871382d40582c
[ 40659.679] (II) fglrx(0): 	4500132a2100001e000000ff00593138
[ 40659.679] (II) fglrx(0): 	3344393550313048550a000000fc0044
[ 40659.679] (II) fglrx(0): 	454c4c205332343039570a20000000fd
[ 40659.679] (II) fglrx(0): 	00324c1e5311000a20202020202000ba
[ 40659.679] (II) fglrx(0): Printing probed modes for output DFP7
[ 40659.679] (II) fglrx(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 40659.679] (II) fglrx(0): Modeline "1680x1050"x60.0  148.50  1680 2008 2052 2200  1050 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[ 40659.679] (II) fglrx(0): Modeline "1400x1050"x60.0  148.50  1400 2008 2052 2200  1050 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[ 40659.679] (II) fglrx(0): Modeline "1600x900"x60.0  148.50  1600 2008 2052 2200  900 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[ 40659.679] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 40659.679] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 40659.679] (II) fglrx(0): Modeline "1440x900"x60.0  148.50  1440 2008 2052 2200  900 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[ 40659.679] (II) fglrx(0): Modeline "1280x960"x75.0  135.00  1280 1296 1440 1688  960 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 40659.679] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1328 1440 1688  960 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 40659.679] (II) fglrx(0): Modeline "1152x864"x60.0  148.50  1152 2008 2052 2200  864 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[ 40659.679] (II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 40659.679] (II) fglrx(0): Modeline "1280x768"x75.0  135.00  1280 1296 1440 1688  768 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 40659.679] (II) fglrx(0): Modeline "1280x768"x60.0  108.00  1280 1328 1440 1688  768 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 40659.679] (II) fglrx(0): Modeline "1280x720"x75.0  135.00  1280 1296 1440 1688  720 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 40659.679] (II) fglrx(0): Modeline "1280x720"x60.0  108.00  1280 1328 1440 1688  720 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 40659.679] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 40659.679] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 40659.679] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 40659.679] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 40659.679] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 40659.679] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 40659.679] (II) fglrx(0): EDID for output CRT1
[ 40659.679] (II) fglrx(0): Output DFP1 disconnected
[ 40659.679] (II) fglrx(0): Output DFP2 disconnected
[ 40659.679] (II) fglrx(0): Output DFP3 disconnected
[ 40659.679] (II) fglrx(0): Output DFP4 disconnected
[ 40659.679] (II) fglrx(0): Output DFP5 disconnected
[ 40659.679] (II) fglrx(0): Output DFP6 disconnected
[ 40659.679] (II) fglrx(0): Output DFP7 connected
[ 40659.679] (II) fglrx(0): Output CRT1 disconnected
[ 40659.679] (II) fglrx(0): Using exact sizes for initial modes
[ 40659.679] (II) fglrx(0): Output DFP7 using initial mode 1920x1080
[ 40659.679] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[ 40659.679] (II) fglrx(0): DPI set to (96, 96)
[ 40659.679] (II) fglrx(0): Eyefinity capable adapter detected.
[ 40659.679] (II) fglrx(0): Adapter AMD Radeon HD 7700 Series   has 6 configurable heads and 1 displays connected.
[ 40659.679] (==) fglrx(0):  PseudoColor visuals disabled
[ 40659.679] (II) Loading sub module "ramdac"
[ 40659.679] (II) LoadModule: "ramdac"
[ 40659.679] (II) Module "ramdac" already built-in
[ 40659.679] (==) fglrx(0): NoDRI = NO
[ 40659.680] (==) fglrx(0): Capabilities: 0x00000000
[ 40659.680] (==) fglrx(0): CapabilitiesEx: 0x00000000
[ 40659.680] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[ 40659.680] (==) fglrx(0): UseFastTLS=0
[ 40659.680] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[ 40659.680] (--) Depth 24 pixmap format is 32 bpp
[ 40659.680] (II) fglrx(0): doing swlDriScreenInit
[ 40659.680] (II) fglrx(0): swlDriScreenInit for fglrx driver
[ 40659.680] ukiDynamicMajor: found major device number 250
[ 40659.680] ukiDynamicMajor: found major device number 250
[ 40659.680] ukiDynamicMajor: found major device number 250
[ 40659.680] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[ 40659.680] ukiOpenDevice: node name is /dev/ati/card0
[ 40659.680] ukiOpenDevice: open result is 12, (OK)
[ 40659.680] ukiOpenByBusid: ukiOpenMinor returns 12
[ 40659.680] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[ 40659.680] (II) fglrx(0): [uki] DRM interface version 1.0
[ 40659.680] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[ 40659.680] (II) fglrx(0): [uki] added 8192 byte SAREA at 0xb048000
[ 40659.680] (II) fglrx(0): [uki] mapped SAREA 0xb048000 to 0x7ff13e780000
[ 40659.680] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[ 40659.680] (II) fglrx(0): [uki] added 1 reserved context for kernel
[ 40659.680] (II) fglrx(0): swlDriScreenInit done
[ 40659.680] (II) fglrx(0): Kernel Module Version Information:
[ 40659.680] (II) fglrx(0):     Name: fglrx
[ 40659.680] (II) fglrx(0):     Version: 14.50.2
[ 40659.680] (II) fglrx(0):     Date: Nov 20 2014
[ 40659.680] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[ 40659.680] (II) fglrx(0): Kernel Module version matches driver.
[ 40659.680] (II) fglrx(0): Kernel Module Build Time Information:
[ 40659.680] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.16.0-28-generic
[ 40659.680] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[ 40659.680] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[ 40659.680] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[ 40659.680] (II) fglrx(0): [uki] register handle = 0x00004000
[ 40659.681] (II) fglrx(0): DRI initialization successfull
[ 40659.681] (II) fglrx(0): FBADPhys: 0xf4062c0000 FBMappedSize: 0x010e0000
[ 40659.681] (==) fglrx(0): Backing store enabled
[ 40659.681] (**) fglrx(0): DPMS enabled
[ 40659.681] (II) fglrx(0): Initialized in-driver Xinerama extension
[ 40659.681] (**) fglrx(0): Textured Video is enabled.
[ 40659.681] (II) LoadModule: "glesx"
[ 40659.681] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/glesx.so
[ 40659.683] (II) Module glesx: vendor="X.Org Foundation"
[ 40659.683] 	compiled for 1.4.99.906, module version = 1.0.0
[ 40659.683] (II) fglrx(0): GLESX enableFlags = 8784
[ 40659.683] (II) fglrx(0): GLESX is enabled
[ 40659.683] (II) LoadModule: "amdxmm"
[ 40659.683] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/amdxmm.so
[ 40659.684] (II) Module amdxmm: vendor="X.Org Foundation"
[ 40659.684] 	compiled for 1.4.99.906, module version = 2.0.0
[ 40659.702] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[ 40659.704] (II) fglrx(0): Enable composite support successfully
[ 40659.704] (WW) fglrx(0): Option "VendorName" is not used
[ 40659.704] (WW) fglrx(0): Option "ModelName" is not used
[ 40659.704] (II) fglrx(0): X context handle = 0xe
[ 40659.704] (II) fglrx(0): [DRI] installation complete
[ 40659.704] (==) fglrx(0): Silken mouse enabled
[ 40659.704] (==) fglrx(0): Using HW cursor of display infrastructure!
[ 40659.705] (II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[ 40659.854] (--) RandR disabled
[ 40659.858] (II) SELinux: Disabled on system
[ 40659.859] ukiDynamicMajor: found major device number 250
[ 40659.859] ukiDynamicMajor: found major device number 250
[ 40659.859] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[ 40659.859] ukiOpenDevice: node name is /dev/ati/card0
[ 40659.859] ukiOpenDevice: open result is 13, (OK)
[ 40659.859] ukiOpenByBusid: ukiOpenMinor returns 13
[ 40659.859] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[ 40659.859] (EE) AIGLX error: failed to open /usr/X11R6/lib64/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib64/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[ 40659.859] (EE) AIGLX error: failed to open /usr/lib64/dri/fglrx_dri.so, error[/usr/lib64/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[ 40659.859] (EE) AIGLX error: failed to open /usr/X11R6/lib/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[ 40659.861] ukiDynamicMajor: found major device number 250
[ 40659.861] ukiDynamicMajor: found major device number 250
[ 40659.861] ukiDynamicMajor: found major device number 250
[ 40659.861] ukiOpenDevice: node name is /dev/ati/card0
[ 40659.862] ukiOpenDevice: open result is 14, (OK)
[ 40659.862] ukiGetBusid returned 'PCI:1:0:0'
[ 40659.862] ukiOpenDevice: node name is /dev/ati/card1
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: Open failed
[ 40659.862] ukiOpenDevice: node name is /dev/ati/card2
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: Open failed
[ 40659.862] ukiOpenDevice: node name is /dev/ati/card3
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: Open failed
[ 40659.862] ukiOpenDevice: node name is /dev/ati/card4
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: Open failed
[ 40659.862] ukiOpenDevice: node name is /dev/ati/card5
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: Open failed
[ 40659.862] ukiOpenDevice: node name is /dev/ati/card6
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: Open failed
[ 40659.862] ukiOpenDevice: node name is /dev/ati/card7
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: Open failed
[ 40659.862] ukiOpenDevice: node name is /dev/ati/card8
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: Open failed
[ 40659.862] ukiOpenDevice: node name is /dev/ati/card9
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: Open failed
[ 40659.862] ukiOpenDevice: node name is /dev/ati/card10
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: Open failed
[ 40659.862] ukiOpenDevice: node name is /dev/ati/card11
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: Open failed
[ 40659.862] ukiOpenDevice: node name is /dev/ati/card12
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: Open failed
[ 40659.862] ukiOpenDevice: node name is /dev/ati/card13
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: Open failed
[ 40659.862] ukiOpenDevice: node name is /dev/ati/card14
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: Open failed
[ 40659.862] ukiOpenDevice: node name is /dev/ati/card15
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: open result is -1, (No such device)
[ 40659.862] ukiOpenDevice: Open failed
[ 40659.862] ukiDynamicMajor: found major device number 250
[ 40659.862] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[ 40659.862] ukiOpenDevice: node name is /dev/ati/card0
[ 40659.862] ukiOpenDevice: open result is 14, (OK)
[ 40659.862] ukiOpenByBusid: ukiOpenMinor returns 14
[ 40659.862] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[ 40659.887] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[ 40659.888] ukiDynamicMajor: found major device number 250
[ 40659.888] ukiDynamicMajor: found major device number 250
[ 40659.888] ukiDynamicMajor: found major device number 250
[ 40659.888] ukiOpenDevice: node name is /dev/ati/card0
[ 40659.888] ukiOpenDevice: open result is 15, (OK)
[ 40659.888] ukiGetBusid returned 'PCI:1:0:0'
[ 40659.888] ukiOpenDevice: node name is /dev/ati/card1
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: Open failed
[ 40659.888] ukiOpenDevice: node name is /dev/ati/card2
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: Open failed
[ 40659.888] ukiOpenDevice: node name is /dev/ati/card3
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: Open failed
[ 40659.888] ukiOpenDevice: node name is /dev/ati/card4
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: Open failed
[ 40659.888] ukiOpenDevice: node name is /dev/ati/card5
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: Open failed
[ 40659.888] ukiOpenDevice: node name is /dev/ati/card6
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: Open failed
[ 40659.888] ukiOpenDevice: node name is /dev/ati/card7
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: Open failed
[ 40659.888] ukiOpenDevice: node name is /dev/ati/card8
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: Open failed
[ 40659.888] ukiOpenDevice: node name is /dev/ati/card9
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: Open failed
[ 40659.888] ukiOpenDevice: node name is /dev/ati/card10
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: Open failed
[ 40659.888] ukiOpenDevice: node name is /dev/ati/card11
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: Open failed
[ 40659.888] ukiOpenDevice: node name is /dev/ati/card12
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: Open failed
[ 40659.888] ukiOpenDevice: node name is /dev/ati/card13
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: Open failed
[ 40659.888] ukiOpenDevice: node name is /dev/ati/card14
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.888] ukiOpenDevice: Open failed
[ 40659.888] ukiOpenDevice: node name is /dev/ati/card15
[ 40659.888] ukiOpenDevice: open result is -1, (No such device)
[ 40659.889] ukiOpenDevice: open result is -1, (No such device)
[ 40659.889] ukiOpenDevice: Open failed
[ 40659.889] ukiDynamicMajor: found major device number 250
[ 40659.889] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[ 40659.889] ukiOpenDevice: node name is /dev/ati/card0
[ 40659.889] ukiOpenDevice: open result is 15, (OK)
[ 40659.889] ukiOpenByBusid: ukiOpenMinor returns 15
[ 40659.889] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[ 40659.902] (II) fglrx(0): OverDrive5 Detected!
[ 40659.906] (II) fglrx(0): Setting screen physical size to 508 x 285
[ 40659.912] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 40659.915] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[ 40659.915] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 40659.915] (II) LoadModule: "evdev"
[ 40659.915] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 40659.915] (II) Module evdev: vendor="X.Org Foundation"
[ 40659.915] 	compiled for 1.16.0, module version = 2.9.0
[ 40659.915] 	Module class: X.Org XInput Driver
[ 40659.915] 	ABI class: X.Org XInput driver, version 21.0
[ 40659.915] (II) Using input driver 'evdev' for 'Power Button'
[ 40659.916] (**) Power Button: always reports core events
[ 40659.916] (**) evdev: Power Button: Device: "/dev/input/event1"
[ 40659.916] (--) evdev: Power Button: Vendor 0 Product 0x1
[ 40659.916] (--) evdev: Power Button: Found keys
[ 40659.916] (II) evdev: Power Button: Configuring as keyboard
[ 40659.916] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[ 40659.916] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[ 40659.916] (**) Option "xkb_rules" "evdev"
[ 40659.916] (**) Option "xkb_model" "pc105"
[ 40659.916] (**) Option "xkb_layout" "latam"
[ 40659.917] (II) XKB: reuse xkmfile /var/lib/xkb/server-D39A7DF07EFAADA1B152E688CBEB9ED49E8BFDBB.xkm
[ 40659.918] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[ 40659.918] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 40659.918] (II) Using input driver 'evdev' for 'Power Button'
[ 40659.918] (**) Power Button: always reports core events
[ 40659.918] (**) evdev: Power Button: Device: "/dev/input/event0"
[ 40659.918] (--) evdev: Power Button: Vendor 0 Product 0x1
[ 40659.918] (--) evdev: Power Button: Found keys
[ 40659.918] (II) evdev: Power Button: Configuring as keyboard
[ 40659.918] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[ 40659.918] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[ 40659.918] (**) Option "xkb_rules" "evdev"
[ 40659.918] (**) Option "xkb_model" "pc105"
[ 40659.918] (**) Option "xkb_layout" "latam"
[ 40659.918] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event4)
[ 40659.918] (II) No input driver specified, ignoring this device.
[ 40659.918] (II) This device may have been added with another device file.
[ 40659.918] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=7 (/dev/input/event5)
[ 40659.918] (II) No input driver specified, ignoring this device.
[ 40659.918] (II) This device may have been added with another device file.
[ 40659.918] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=8 (/dev/input/event6)
[ 40659.918] (II) No input driver specified, ignoring this device.
[ 40659.918] (II) This device may have been added with another device file.
[ 40659.919] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=9 (/dev/input/event7)
[ 40659.919] (II) No input driver specified, ignoring this device.
[ 40659.919] (II) This device may have been added with another device file.
[ 40659.919] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=10 (/dev/input/event8)
[ 40659.919] (II) No input driver specified, ignoring this device.
[ 40659.919] (II) This device may have been added with another device file.
[ 40659.919] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=11 (/dev/input/event9)
[ 40659.919] (II) No input driver specified, ignoring this device.
[ 40659.919] (II) This device may have been added with another device file.
[ 40659.919] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
[ 40659.919] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[ 40659.919] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[ 40659.919] (**) USB Optical Mouse: always reports core events
[ 40659.919] (**) evdev: USB Optical Mouse: Device: "/dev/input/event3"
[ 40659.919] (--) evdev: USB Optical Mouse: Vendor 0x1bcf Product 0x7
[ 40659.919] (--) evdev: USB Optical Mouse: Found 3 mouse buttons
[ 40659.919] (--) evdev: USB Optical Mouse: Found scroll wheel(s)
[ 40659.919] (--) evdev: USB Optical Mouse: Found relative axes
[ 40659.919] (--) evdev: USB Optical Mouse: Found x and y relative axes
[ 40659.919] (--) evdev: USB Optical Mouse: Found absolute axes
[ 40659.919] (II) evdev: USB Optical Mouse: Forcing absolute x/y axes to exist.
[ 40659.919] (II) evdev: USB Optical Mouse: Configuring as mouse
[ 40659.919] (II) evdev: USB Optical Mouse: Adding scrollwheel support
[ 40659.919] (**) evdev: USB Optical Mouse: YAxisMapping: buttons 4 and 5
[ 40659.919] (**) evdev: USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 40659.919] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0/0003:1BCF:0007.0001/input/input3/event3"
[ 40659.919] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 8)
[ 40659.919] (II) evdev: USB Optical Mouse: initialized for relative axes.
[ 40659.919] (WW) evdev: USB Optical Mouse: ignoring absolute axes.
[ 40659.920] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[ 40659.920] (**) USB Optical Mouse: (accel) acceleration profile 0
[ 40659.920] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[ 40659.920] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[ 40659.920] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[ 40659.920] (II) No input driver specified, ignoring this device.
[ 40659.920] (II) This device may have been added with another device file.
[ 40659.920] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event10)
[ 40659.920] (II) No input driver specified, ignoring this device.
[ 40659.920] (II) This device may have been added with another device file.
[ 40659.920] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event11)
[ 40659.920] (II) No input driver specified, ignoring this device.
[ 40659.920] (II) This device may have been added with another device file.
[ 40659.920] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event12)
[ 40659.920] (II) No input driver specified, ignoring this device.
[ 40659.920] (II) This device may have been added with another device file.
[ 40659.921] (II) config/udev: Adding input device HDA ATI SB Line Out (/dev/input/event13)
[ 40659.921] (II) No input driver specified, ignoring this device.
[ 40659.921] (II) This device may have been added with another device file.
[ 40659.921] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event14)
[ 40659.921] (II) No input driver specified, ignoring this device.
[ 40659.921] (II) This device may have been added with another device file.
[ 40659.921] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[ 40659.921] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[ 40659.921] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[ 40659.921] (**) AT Translated Set 2 keyboard: always reports core events
[ 40659.921] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[ 40659.921] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[ 40659.921] (--) evdev: AT Translated Set 2 keyboard: Found keys
[ 40659.921] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[ 40659.921] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[ 40659.921] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[ 40659.921] (**) Option "xkb_rules" "evdev"
[ 40659.921] (**) Option "xkb_model" "pc105"
[ 40659.921] (**) Option "xkb_layout" "latam"
[ 40659.926] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[ 40659.926] (WW) fglrx(0): os shared memory open failed
[ 52036.580] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 52036.580] (II) fglrx(0): Backup framebuffer data.
[ 52036.631] (II) fglrx(0): Backup complete.
[ 52036.658] (II) fglrx(0): Init Suspend Console
[ 52037.096] (II) evdev: AT Translated Set 2 keyboard: Close
[ 52037.096] (II) UnloadModule: "evdev"
[ 52037.096] (II) evdev: USB Optical Mouse: Close
[ 52037.096] (II) UnloadModule: "evdev"
[ 52037.096] (II) evdev: Power Button: Close
[ 52037.096] (II) UnloadModule: "evdev"
[ 52037.096] (II) evdev: Power Button: Close
[ 52037.096] (II) UnloadModule: "evdev"
[ 52037.097] (II) fglrx(0): Shutdown CMMQS
[ 52037.100] (II) fglrx(0): [uki] removed 1 reserved context for kernel
[ 52037.100] (II) fglrx(0): [uki] unmapping 8192 bytes of SAREA 0xb048000 at 0x7ff13e780000
[ 52037.100] (II) fglrx(0): Init Suspend Console
[ 52037.100] (EE) 
[ 52037.100] (EE) Backtrace:
[ 52037.100] (EE) 0: /usr/bin/X (xorg_backtrace+0x56) [0x7ff13eaa6e96]
[ 52037.100] (EE) 1: /usr/bin/X (0x7ff13e8f0000+0x1bb099) [0x7ff13eaab099]
[ 52037.101] (EE) 2: /lib/x86_64-linux-gnu/libc.so.6 (0x7ff13c5e8000+0x36da0) [0x7ff13c61eda0]
[ 52037.101] (EE) 3: /usr/lib/x86_64-linux-gnu/libpciaccess.so.0 (0x7ff13dbe8000+0x4f20) [0x7ff13dbecf20]
[ 52037.101] (EE) 4: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (amd_xs113_int10_x_inb+0x46) [0x7ff13a53d5e6]
[ 52037.101] (EE) 5: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (0x7ff139a48000+0xaee2c5) [0x7ff13a5362c5]
[ 52037.101] (EE) 6: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (X86EMU_exec+0xa5) [0x7ff13a529a15]
[ 52037.101] (EE) 7: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (amd_xs113_int10_xf86ExecX86int10+0x46) [0x7ff13a53e746]
[ 52037.102] (EE) 8: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (xf86ExecX86int10+0xd) [0x7ff139ed14ed]
[ 52037.102] (EE) 9: /usr/lib/xorg/modules/libvbe.so (VBESetVBEMode+0x9d) [0x7ff1393e230d]
[ 52037.102] (EE) 10: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (0x7ff139a48000+0x4bf963) [0x7ff139f07963]
[ 52037.102] (EE) 11: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (atiddxVBESetConsoleMode+0x5b) [0x7ff139f0778b]
[ 52037.102] (EE) 12: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (xdl_xs116_atiddxFreeScreen+0x76f) [0x7ff13a0dec3f]
[ 52037.102] (EE) 13: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (xdl_xs116_atiddxCloseScreen+0x321) [0x7ff13a0de231]
[ 52037.102] (EE) 14: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (0x7ff139a48000+0xb72ec6) [0x7ff13a5baec6]
[ 52037.102] (EE) 15: /usr/bin/X (0x7ff13e8f0000+0xea158) [0x7ff13e9da158]
[ 52037.103] (EE) 16: /usr/bin/X (0x7ff13e8f0000+0x135c94) [0x7ff13ea25c94]
[ 52037.103] (EE) 17: /usr/bin/X (0x7ff13e8f0000+0x1375f2) [0x7ff13ea275f2]
[ 52037.103] (EE) 18: /usr/bin/X (0x7ff13e8f0000+0x5b4e7) [0x7ff13e94b4e7]
[ 52037.103] (EE) 19: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7ff13c609ec5]
[ 52037.103] (EE) 20: /usr/bin/X (0x7ff13e8f0000+0x4576e) [0x7ff13e93576e]
[ 52037.103] (EE) 
[ 52037.103] (EE) Segmentation fault at address 0x0
[ 52037.103] (EE) 
Fatal server error:
[ 52037.103] (EE) Caught signal 11 (Segmentation fault). Server aborting
[ 52037.103] (EE) 
[ 52037.103] (EE) 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[ 52037.103] (EE) Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[ 52037.103] (EE) 
[ 52037.103] (EE) Server terminated with error (1). Closing log file.

```

Any ideas? Thanks!

---

