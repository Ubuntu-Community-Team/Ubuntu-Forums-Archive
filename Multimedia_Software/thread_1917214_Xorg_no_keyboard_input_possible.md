---
title: "Xorg no keyboard input possible"
date: 2012-01-29
forum: Multimedia Software
---

### Post by anXieTyPB on 2012-01-29
Good evening!

Today i installed XORG and ATI propretiary drivers on my HTPC and i tried to run XServer using startx.

It works all fine but the fact that i cannot input anything into the xserver-terminal.

It simply does not react. All i see is 

> xbmc@ubuntuPC:~$

while the background is completele black.

Here is my xserver-logfile:

```
[   696.563] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[   696.563] X Protocol Version 11, Revision 0
[   696.563] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[   696.569] Current Operating System: Linux ubuntuPC 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 15:59:53 UTC 2012 i686
[   696.574] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-15-generic root=UUID=0a56e977-6a5b-4199-9a6b-d70a5bf8b852 ro splash quiet vt.handoff=7
[   696.578] Build Date: 19 October 2011  05:09:41AM
[   696.581] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[   696.583] Current version of pixman: 0.22.2
[   696.586] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   696.592] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   696.601] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan 29 21:25:33 2012
[   696.604] (==) Using config file: "/etc/X11/xorg.conf"
[   696.607] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   696.611] (==) ServerLayout "aticonfig Layout"
[   696.611] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[   696.611] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[   696.611] (**) |   |-->Device "aticonfig-Device[0]-0"
[   696.612] (==) Automatically adding devices
[   696.612] (==) Automatically enabling devices
[   696.612] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   696.612] 	Entry deleted from font path.
[   696.612] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   696.612] 	Entry deleted from font path.
[   696.612] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   696.612] 	Entry deleted from font path.
[   696.612] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   696.612] 	Entry deleted from font path.
[   696.612] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   696.612] 	Entry deleted from font path.
[   696.612] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   696.612] 	Entry deleted from font path.
[   696.612] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[   696.612] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   696.612] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   696.612] (II) Loader magic: 0x823ada0
[   696.612] (II) Module ABI versions:
[   696.612] 	X.Org ANSI C Emulation: 0.4
[   696.612] 	X.Org Video Driver: 10.0
[   696.612] 	X.Org XInput driver : 12.3
[   696.612] 	X.Org Server Extension : 5.0
[   696.614] (--) PCI:*(0:0:1:0) 1002:9802:1849:9802 rev 0, Mem @ 0xc0000000/268435456, 0xfeb00000/262144, I/O @ 0x0000f000/256
[   696.614] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[   696.614] (II) "extmod" will be loaded by default.
[   696.614] (II) "dbe" will be loaded by default.
[   696.614] (II) "glx" will be loaded by default.
[   696.614] (II) "record" will be loaded by default.
[   696.614] (II) "dri" will be loaded by default.
[   696.614] (II) "dri2" will be loaded by default.
[   696.614] (II) LoadModule: "extmod"
[   696.615] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   696.615] (II) Module extmod: vendor="X.Org Foundation"
[   696.615] 	compiled for 1.10.4, module version = 1.0.0
[   696.615] 	Module class: X.Org Server Extension
[   696.615] 	ABI class: X.Org Server Extension, version 5.0
[   696.615] (II) Loading extension MIT-SCREEN-SAVER
[   696.615] (II) Loading extension XFree86-VidModeExtension
[   696.615] (II) Loading extension XFree86-DGA
[   696.615] (II) Loading extension DPMS
[   696.615] (II) Loading extension XVideo
[   696.616] (II) Loading extension XVideo-MotionCompensation
[   696.616] (II) Loading extension X-Resource
[   696.616] (II) LoadModule: "dbe"
[   696.616] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   696.616] (II) Module dbe: vendor="X.Org Foundation"
[   696.616] 	compiled for 1.10.4, module version = 1.0.0
[   696.617] 	Module class: X.Org Server Extension
[   696.617] 	ABI class: X.Org Server Extension, version 5.0
[   696.617] (II) Loading extension DOUBLE-BUFFER
[   696.617] (II) LoadModule: "glx"
[   696.617] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[   696.617] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[   696.617] 	compiled for 6.9.0, module version = 1.0.0
[   696.618] (II) Loading extension GLX
[   696.618] (II) LoadModule: "record"
[   696.618] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   696.619] (II) Module record: vendor="X.Org Foundation"
[   696.619] 	compiled for 1.10.4, module version = 1.13.0
[   696.619] 	Module class: X.Org Server Extension
[   696.619] 	ABI class: X.Org Server Extension, version 5.0
[   696.619] (II) Loading extension RECORD
[   696.619] (II) LoadModule: "dri"
[   696.620] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   696.620] (II) Module dri: vendor="X.Org Foundation"
[   696.620] 	compiled for 1.10.4, module version = 1.0.0
[   696.620] 	ABI class: X.Org Server Extension, version 5.0
[   696.620] (II) Loading extension XFree86-DRI
[   696.620] (II) LoadModule: "dri2"
[   696.621] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   696.621] (II) Module dri2: vendor="X.Org Foundation"
[   696.621] 	compiled for 1.10.4, module version = 1.2.0
[   696.621] 	ABI class: X.Org Server Extension, version 5.0
[   696.621] (II) Loading extension DRI2
[   696.621] (II) LoadModule: "fglrx"
[   696.621] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[   696.658] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[   696.658] 	compiled for 1.4.99.906, module version = 8.93.4
[   696.658] 	Module class: X.Org Video Driver
[   696.659] (II) Loading sub module "fglrxdrm"
[   696.659] (II) LoadModule: "fglrxdrm"
[   696.659] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[   696.660] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[   696.660] 	compiled for 1.4.99.906, module version = 8.93.4
[   696.660] (II) ATI Proprietary Linux Driver Version Identifier:8.93.4
[   696.660] (II) ATI Proprietary Linux Driver Release Identifier: 8.93                                 
[   696.660] (II) ATI Proprietary Linux Driver Build Date: Dec  5 2011 21:06:49
[   696.660] (--) using VT number 7

[   696.670] (WW) Falling back to old probe method for fglrx
[   696.693] (II) Loading PCS database from /etc/ati/amdpcsdb
[   696.696] (--) Chipset Supported AMD Graphics Processor (0x9802) found
[   696.696] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:1:1) found
[   696.697] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[   696.697] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[   696.697] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[   696.697] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[   696.697] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[   696.697] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[   696.697] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
[   696.697] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[   696.697] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[   696.697] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[   696.697] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
[   696.697] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:0) found
[   696.697] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:1) found
[   696.697] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:0) found
[   696.697] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:2) found
[   696.699] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[   696.699] (II) AMD Video driver is signed
[   696.699] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[   696.699] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[   696.699] (II) fglrx(0): pEnt->device->identifier=0x8fd4ef0
[   696.699] (II) fglrx(0): === [xdl_xs110_atiddxPreInit] === begin
[   696.699] (II) Loading sub module "vgahw"
[   696.699] (II) LoadModule: "vgahw"
[   696.700] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[   696.700] (II) Module vgahw: vendor="X.Org Foundation"
[   696.700] 	compiled for 1.10.4, module version = 0.1.0
[   696.700] 	ABI class: X.Org Video Driver, version 10.0
[   696.700] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[   696.700] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[   696.700] (==) fglrx(0): Default visual is TrueColor
[   696.700] (**) fglrx(0): Option "UseFastTLS" "1"
[   696.700] (**) fglrx(0): Option "DPMS" "true"
[   696.701] (==) fglrx(0): RGB weight 888
[   696.701] (II) fglrx(0): Using 8 bits per RGB 
[   696.701] (==) fglrx(0): Buffer Tiling is ON
[   696.701] (II) Loading sub module "fglrxdrm"
[   696.701] (II) LoadModule: "fglrxdrm"
[   696.701] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[   696.701] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[   696.701] 	compiled for 1.4.99.906, module version = 8.93.4
[   696.705] ukiDynamicMajor: found major device number 250
[   696.705] ukiDynamicMajor: found major device number 250
[   696.705] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[   696.705] ukiOpenDevice: node name is /dev/ati/card0
[   696.705] ukiOpenDevice: open result is 9, (OK)
[   696.705] ukiOpenByBusid: ukiOpenMinor returns 9
[   696.705] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[   696.706] (==) fglrx(0): NoAccel = NO
[   696.706] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[   696.706] (--) fglrx(0): Chipset: "AMD Radeon HD 6310 Graphics" (Chipset = 0x9802)
[   696.706] (--) fglrx(0): (PciSubVendor = 0x1849, PciSubDevice = 0x9802)
[   696.706] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[   696.706] (--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
[   696.706] (--) fglrx(0): MMIO registers at 0xfeb00000
[   696.706] (--) fglrx(0): I/O port at 0x0000f000
[   696.706] (==) fglrx(0): ROM-BIOS at 0x000c0000
[   696.753] (II) fglrx(0): AC Adapter is used
[   696.807] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[   696.807] (II) Loading sub module "vbe"
[   696.807] (II) LoadModule: "vbe"
[   696.808] (II) Loading /usr/lib/xorg/modules/libvbe.so
[   696.808] (II) Module vbe: vendor="X.Org Foundation"
[   696.808] 	compiled for 1.10.4, module version = 1.1.0
[   696.808] 	ABI class: X.Org Video Driver, version 10.0
[   696.809] (II) fglrx(0): VESA BIOS detected
[   696.809] (II) fglrx(0): VESA VBE Version 3.0
[   696.809] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[   696.809] (II) fglrx(0): VESA VBE OEM: AMD ATOMBIOS
[   696.809] (II) fglrx(0): VESA VBE OEM Software Rev: 12.36
[   696.809] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[   696.809] (II) fglrx(0): VESA VBE OEM Product: WRESTLER
[   696.809] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[   696.824] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[   696.824] (--) fglrx(0): Video RAM: 393216 kByte, Type: DDR3
[   696.824] (II) fglrx(0): PCIE card detected
[   696.824] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[   696.824] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[   696.832] (II) fglrx(0): Using adapter: 0:1.0.
[   698.064] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x18000000)
[   698.188] (II) fglrx(0): Interrupt handler installed at IRQ 42.
[   698.188] (II) fglrx(0): RandR 1.2 support is enabled!
[   698.188] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[   698.189] (==) fglrx(0): Center Mode is disabled 
[   698.189] (II) Loading sub module "fb"
[   698.189] (II) LoadModule: "fb"
[   698.189] (II) Loading /usr/lib/xorg/modules/libfb.so
[   698.189] (II) Module fb: vendor="X.Org Foundation"
[   698.189] 	compiled for 1.10.4, module version = 1.0.0
[   698.189] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   698.190] (II) Loading sub module "ddc"
[   698.190] (II) LoadModule: "ddc"
[   698.190] (II) Module "ddc" already built-in
[   698.406] (II) fglrx(0): Finished Initialize PPLIB!
[   698.407] (II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
[   698.407] (II) fglrx(0): Output DFP2 has no monitor section
[   698.407] (II) fglrx(0): Output CRT1 has no monitor section
[   698.407] (II) Loading sub module "ddc"
[   698.407] (II) LoadModule: "ddc"
[   698.407] (II) Module "ddc" already built-in
[   698.407] (II) fglrx(0): Connected Display0: DFP1
[   698.407] (II) fglrx(0): Display0 EDID data ---------------------------
[   698.407] (II) fglrx(0): Manufacturer: SAM  Model: 7ad  Serial#: 0
[   698.407] (II) fglrx(0): Year: 2010  Week: 48
[   698.407] (II) fglrx(0): EDID Version: 1.3
[   698.407] (II) fglrx(0): Digital Display Input
[   698.407] (II) fglrx(0): Max Image Size [cm]: horiz.: 53  vert.: 30
[   698.407] (II) fglrx(0): Gamma: 2.20
[   698.407] (II) fglrx(0): No DPMS capabilities specified
[   698.407] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   698.407] (II) fglrx(0): First detailed timing is preferred mode
[   698.407] (II) fglrx(0): redX: 0.631 redY: 0.351   greenX: 0.334 greenY: 0.615
[   698.408] (II) fglrx(0): blueX: 0.157 blueY: 0.051   whiteX: 0.312 whiteY: 0.329
[   698.408] (II) fglrx(0): Supported established timings:
[   698.408] (II) fglrx(0): 720x400@70Hz
[   698.408] (II) fglrx(0): 640x480@60Hz
[   698.408] (II) fglrx(0): 640x480@67Hz
[   698.408] (II) fglrx(0): 640x480@72Hz
[   698.408] (II) fglrx(0): 640x480@75Hz
[   698.408] (II) fglrx(0): 800x600@56Hz
[   698.408] (II) fglrx(0): 800x600@60Hz
[   698.408] (II) fglrx(0): 800x600@72Hz
[   698.408] (II) fglrx(0): 800x600@75Hz
[   698.408] (II) fglrx(0): 832x624@75Hz
[   698.408] (II) fglrx(0): 1024x768@60Hz
[   698.408] (II) fglrx(0): 1024x768@70Hz
[   698.408] (II) fglrx(0): 1024x768@75Hz
[   698.408] (II) fglrx(0): 1280x1024@75Hz
[   698.408] (II) fglrx(0): 1152x864@75Hz
[   698.408] (II) fglrx(0): Manufacturer's mask: 0
[   698.408] (II) fglrx(0): Supported standard timings:
[   698.408] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   698.408] (II) fglrx(0): #1: hsize: 1280  vsize 800  refresh: 60  vid: 129
[   698.408] (II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[   698.408] (II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   698.408] (II) fglrx(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[   698.408] (II) fglrx(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[   698.408] (II) fglrx(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[   698.408] (II) fglrx(0): Supported detailed timing:
[   698.408] (II) fglrx(0): clock: 148.5 MHz   Image Size:  531 x 299 mm
[   698.408] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[   698.408] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[   698.408] (II) fglrx(0): Supported detailed timing:
[   698.408] (II) fglrx(0): clock: 85.5 MHz   Image Size:  531 x 299 mm
[   698.408] (II) fglrx(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
[   698.408] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
[   698.408] (II) fglrx(0): Ranges: V min: 24 V max: 75 Hz, H min: 26 H max: 81 kHz, PixClock max 235 MHz
[   698.408] (II) fglrx(0): Monitor name: SMT24A350
[   698.408] (II) fglrx(0): Supported detailed timing:
[   698.408] (II) fglrx(0): clock: 74.2 MHz   Image Size:  160 x 90 mm
[   698.408] (II) fglrx(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[   698.408] (II) fglrx(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[   698.408] (II) fglrx(0): Supported detailed timing:
[   698.408] (II) fglrx(0): clock: 74.2 MHz   Image Size:  160 x 90 mm
[   698.408] (II) fglrx(0): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
[   698.408] (II) fglrx(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[   698.409] (II) fglrx(0): Supported detailed timing:
[   698.409] (II) fglrx(0): clock: 74.2 MHz   Image Size:  160 x 90 mm
[   698.409] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[   698.409] (II) fglrx(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[   698.409] (II) fglrx(0): Supported detailed timing:
[   698.409] (II) fglrx(0): clock: 74.2 MHz   Image Size:  160 x 90 mm
[   698.409] (II) fglrx(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[   698.409] (II) fglrx(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[   698.409] (II) fglrx(0): Number of EDID sections to follow: 1
[   698.409] (II) fglrx(0): EDID (in hex):
[   698.409] (II) fglrx(0): 	00ffffffffffff004c2dad0700000000
[   698.409] (II) fglrx(0): 	3014010380351e780aba41a159559d28
[   698.409] (II) fglrx(0): 	0d5054bfef80714f8100814081809500
[   698.409] (II) fglrx(0): 	950fb3000101023a801871382d40582c
[   698.409] (II) fglrx(0): 	4500132b2100001e662150b051001b30
[   698.409] (II) fglrx(0): 	40703600132b2100001e000000fd0018
[   698.409] (II) fglrx(0): 	4b1a5117000a202020202020000000fc
[   698.409] (II) fglrx(0): 	00534d543234413335300a2020200161
[   698.409] (II) fglrx(0): End of Display0 EDID data --------------------
[   698.414] (II) fglrx(0): EDID for output DFP1
[   698.414] (II) fglrx(0): Manufacturer: SAM  Model: 7ad  Serial#: 0
[   698.414] (II) fglrx(0): Year: 2010  Week: 48
[   698.414] (II) fglrx(0): EDID Version: 1.3
[   698.414] (II) fglrx(0): Digital Display Input
[   698.414] (II) fglrx(0): Max Image Size [cm]: horiz.: 53  vert.: 30
[   698.414] (II) fglrx(0): Gamma: 2.20
[   698.414] (II) fglrx(0): No DPMS capabilities specified
[   698.414] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   698.414] (II) fglrx(0): First detailed timing is preferred mode
[   698.414] (II) fglrx(0): redX: 0.631 redY: 0.351   greenX: 0.334 greenY: 0.615
[   698.414] (II) fglrx(0): blueX: 0.157 blueY: 0.051   whiteX: 0.312 whiteY: 0.329
[   698.414] (II) fglrx(0): Supported established timings:
[   698.414] (II) fglrx(0): 720x400@70Hz
[   698.415] (II) fglrx(0): 640x480@60Hz
[   698.415] (II) fglrx(0): 640x480@67Hz
[   698.415] (II) fglrx(0): 640x480@72Hz
[   698.415] (II) fglrx(0): 640x480@75Hz
[   698.415] (II) fglrx(0): 800x600@56Hz
[   698.415] (II) fglrx(0): 800x600@60Hz
[   698.415] (II) fglrx(0): 800x600@72Hz
[   698.415] (II) fglrx(0): 800x600@75Hz
[   698.415] (II) fglrx(0): 832x624@75Hz
[   698.415] (II) fglrx(0): 1024x768@60Hz
[   698.415] (II) fglrx(0): 1024x768@70Hz
[   698.415] (II) fglrx(0): 1024x768@75Hz
[   698.415] (II) fglrx(0): 1280x1024@75Hz
[   698.415] (II) fglrx(0): 1152x864@75Hz
[   698.415] (II) fglrx(0): Manufacturer's mask: 0
[   698.415] (II) fglrx(0): Supported standard timings:
[   698.415] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   698.415] (II) fglrx(0): #1: hsize: 1280  vsize 800  refresh: 60  vid: 129
[   698.415] (II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[   698.415] (II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   698.415] (II) fglrx(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[   698.415] (II) fglrx(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[   698.415] (II) fglrx(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[   698.415] (II) fglrx(0): Supported detailed timing:
[   698.415] (II) fglrx(0): clock: 148.5 MHz   Image Size:  531 x 299 mm
[   698.415] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[   698.415] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[   698.415] (II) fglrx(0): Supported detailed timing:
[   698.415] (II) fglrx(0): clock: 85.5 MHz   Image Size:  531 x 299 mm
[   698.415] (II) fglrx(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
[   698.415] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
[   698.415] (II) fglrx(0): Ranges: V min: 24 V max: 75 Hz, H min: 26 H max: 81 kHz, PixClock max 235 MHz
[   698.415] (II) fglrx(0): Monitor name: SMT24A350
[   698.415] (II) fglrx(0): Supported detailed timing:
[   698.415] (II) fglrx(0): clock: 74.2 MHz   Image Size:  160 x 90 mm
[   698.415] (II) fglrx(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[   698.415] (II) fglrx(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[   698.415] (II) fglrx(0): Supported detailed timing:
[   698.415] (II) fglrx(0): clock: 74.2 MHz   Image Size:  160 x 90 mm
[   698.415] (II) fglrx(0): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
[   698.415] (II) fglrx(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[   698.415] (II) fglrx(0): Supported detailed timing:
[   698.415] (II) fglrx(0): clock: 74.2 MHz   Image Size:  160 x 90 mm
[   698.415] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[   698.415] (II) fglrx(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[   698.415] (II) fglrx(0): Supported detailed timing:
[   698.416] (II) fglrx(0): clock: 74.2 MHz   Image Size:  160 x 90 mm
[   698.416] (II) fglrx(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[   698.416] (II) fglrx(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[   698.416] (II) fglrx(0): Number of EDID sections to follow: 1
[   698.416] (II) fglrx(0): EDID (in hex):
[   698.416] (II) fglrx(0): 	00ffffffffffff004c2dad0700000000
[   698.416] (II) fglrx(0): 	3014010380351e780aba41a159559d28
[   698.416] (II) fglrx(0): 	0d5054bfef80714f8100814081809500
[   698.416] (II) fglrx(0): 	950fb3000101023a801871382d40582c
[   698.416] (II) fglrx(0): 	4500132b2100001e662150b051001b30
[   698.416] (II) fglrx(0): 	40703600132b2100001e000000fd0018
[   698.416] (II) fglrx(0): 	4b1a5117000a202020202020000000fc
[   698.416] (II) fglrx(0): 	00534d543234413335300a2020200161
[   698.416] (II) fglrx(0): EDID vendor "SAM", prod id 1965
[   698.416] (II) fglrx(0): Using EDID range info for horizontal sync
[   698.416] (II) fglrx(0): Using EDID range info for vertical refresh
[   698.416] (II) fglrx(0): Printing DDC gathered Modelines:
[   698.416] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[   698.416] (II) fglrx(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[   698.416] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[   698.416] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[   698.416] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[   698.416] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[   698.416] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   698.416] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   698.416] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   698.416] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   698.416] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   698.416] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   698.416] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   698.416] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   698.416] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   698.417] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   698.417] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   698.417] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   698.417] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   698.417] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   698.417] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   698.417] (II) fglrx(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[   698.417] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   698.417] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   698.417] (II) fglrx(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[   698.417] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   698.417] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   698.417] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[   698.417] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[   698.417] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[   698.417] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[   698.417] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[   698.417] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.8 kHz)
[   698.417] (II) fglrx(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz)
[   698.417] (II) fglrx(0): Printing probed modes for output DFP1
[   698.418] (II) fglrx(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[   698.418] (II) fglrx(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[   698.418] (II) fglrx(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz)
[   698.418] (II) fglrx(0): Modeline "1920x1080"x60.0   74.25  1920 2008 2052 2200  1080 1085 1095 1125 interlace +hsync +vsync (33.8 kHz)
[   698.418] (II) fglrx(0): Modeline "1920x1080"x50.0   74.25  1920 2448 2492 2640  1080 1085 1095 1125 interlace +hsync +vsync (28.1 kHz)
[   698.418] (II) fglrx(0): Modeline "1920x1080"x30.0   74.25  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.8 kHz)
[   698.418] (II) fglrx(0): Modeline "1920x1080"x25.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[   698.418] (II) fglrx(0): Modeline "1920x1080"x24.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[   698.418] (II) fglrx(0): Modeline "1920x1080"x59.9   74.18  1920 2008 2052 2200  1080 1085 1095 1125 interlace +hsync +vsync (33.7 kHz)
[   698.418] (II) fglrx(0): Modeline "1920x1080"x30.0   74.18  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.7 kHz)
[   698.418] (II) fglrx(0): Modeline "1920x1080"x24.0   74.18  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[   698.418] (II) fglrx(0): Modeline "1776x1000"x50.0  148.50  1776 2304 2348 2640  1000 1004 1009 1125 +hsync +vsync (56.2 kHz)
[   698.418] (II) fglrx(0): Modeline "1776x1000"x59.9  148.35  1776 1864 1908 2200  1000 1004 1009 1125 +hsync +vsync (67.4 kHz)
[   698.418] (II) fglrx(0): Modeline "1776x1000"x50.0   74.25  1776 2304 2348 2640  1000 1005 1015 1125 interlace +hsync +vsync (28.1 kHz)
[   698.418] (II) fglrx(0): Modeline "1776x1000"x25.0   74.25  1776 2304 2348 2640  1000 1004 1009 1125 +hsync +vsync (28.1 kHz)
[   698.418] (II) fglrx(0): Modeline "1776x1000"x24.0   74.25  1776 2414 2458 2750  1000 1004 1009 1125 +hsync +vsync (27.0 kHz)
[   698.418] (II) fglrx(0): Modeline "1776x1000"x59.9   74.18  1776 1864 1908 2200  1000 1005 1015 1125 interlace +hsync +vsync (33.7 kHz)
[   698.418] (II) fglrx(0): Modeline "1776x1000"x30.0   74.18  1776 1864 1908 2200  1000 1004 1009 1125 +hsync +vsync (33.7 kHz)
[   698.418] (II) fglrx(0): Modeline "1680x1050"x50.0  148.50  1680 2448 2492 2640  1050 1084 1089 1125 +hsync +vsync (56.2 kHz)
[   698.418] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[   698.418] (II) fglrx(0): Modeline "1680x1050"x25.0   74.25  1680 2448 2492 2640  1050 1084 1089 1125 +hsync +vsync (28.1 kHz)
[   698.418] (II) fglrx(0): Modeline "1680x1050"x30.0   74.18  1680 2008 2052 2200  1050 1084 1089 1125 +hsync +vsync (33.7 kHz)
[   698.418] (II) fglrx(0): Modeline "1680x1050"x24.0   74.18  1680 2558 2602 2750  1050 1084 1089 1125 +hsync +vsync (27.0 kHz)
[   698.418] (II) fglrx(0): Modeline "1400x1050"x50.0  148.50  1400 2448 2492 2640  1050 1084 1089 1125 +hsync +vsync (56.2 kHz)
[   698.418] (II) fglrx(0): Modeline "1400x1050"x60.0  146.25  1400 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[   698.418] (II) fglrx(0): Modeline "1400x1050"x25.0   74.25  1400 2448 2492 2640  1050 1084 1089 1125 +hsync +vsync (28.1 kHz)
[   698.418] (II) fglrx(0): Modeline "1400x1050"x30.0   74.18  1400 2008 2052 2200  1050 1084 1089 1125 +hsync +vsync (33.7 kHz)
[   698.418] (II) fglrx(0): Modeline "1400x1050"x24.0   74.18  1400 2558 2602 2750  1050 1084 1089 1125 +hsync +vsync (27.0 kHz)
[   698.418] (II) fglrx(0): Modeline "1600x900"x50.0  148.50  1600 2448 2492 2640  900 1084 1089 1125 +hsync +vsync (56.2 kHz)
[   698.418] (II) fglrx(0): Modeline "1600x900"x60.0  146.25  1600 1784 1960 2240  900 1053 1059 1089 -hsync +vsync (65.3 kHz)
[   698.418] (II) fglrx(0): Modeline "1600x900"x25.0   74.25  1600 2448 2492 2640  900 1084 1089 1125 +hsync +vsync (28.1 kHz)
[   698.418] (II) fglrx(0): Modeline "1600x900"x30.0   74.18  1600 2008 2052 2200  900 1084 1089 1125 +hsync +vsync (33.7 kHz)
[   698.418] (II) fglrx(0): Modeline "1600x900"x24.0   74.18  1600 2558 2602 2750  900 1084 1089 1125 +hsync +vsync (27.0 kHz)
[   698.418] (II) fglrx(0): Modeline "1280x1024"x50.0  148.50  1280 2448 2492 2640  1024 1084 1089 1125 +hsync +vsync (56.2 kHz)
[   698.419] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   698.419] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   698.419] (II) fglrx(0): Modeline "1280x1024"x25.0   74.25  1280 2448 2492 2640  1024 1084 1089 1125 +hsync +vsync (28.1 kHz)
[   698.419] (II) fglrx(0): Modeline "1280x1024"x30.0   74.18  1280 2008 2052 2200  1024 1084 1089 1125 +hsync +vsync (33.7 kHz)
[   698.419] (II) fglrx(0): Modeline "1280x1024"x24.0   74.18  1280 2558 2602 2750  1024 1084 1089 1125 +hsync +vsync (27.0 kHz)
[   698.419] (II) fglrx(0): Modeline "1440x900"x50.0  148.50  1440 2448 2492 2640  900 1084 1089 1125 +hsync +vsync (56.2 kHz)
[   698.419] (II) fglrx(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   698.419] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   698.419] (II) fglrx(0): Modeline "1440x900"x25.0   74.25  1440 2448 2492 2640  900 1084 1089 1125 +hsync +vsync (28.1 kHz)
[   698.419] (II) fglrx(0): Modeline "1440x900"x30.0   74.18  1440 2008 2052 2200  900 1084 1089 1125 +hsync +vsync (33.7 kHz)
[   698.419] (II) fglrx(0): Modeline "1440x900"x24.0   74.18  1440 2558 2602 2750  900 1084 1089 1125 +hsync +vsync (27.0 kHz)
[   698.419] (II) fglrx(0): Modeline "1280x960"x50.0  148.50  1280 2448 2492 2640  960 1084 1089 1125 +hsync +vsync (56.2 kHz)
[   698.419] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   698.419] (II) fglrx(0): Modeline "1280x960"x25.0   74.25  1280 2448 2492 2640  960 1084 1089 1125 +hsync +vsync (28.1 kHz)
[   698.419] (II) fglrx(0): Modeline "1280x960"x30.0   74.18  1280 2008 2052 2200  960 1084 1089 1125 +hsync +vsync (33.7 kHz)
[   698.419] (II) fglrx(0): Modeline "1280x960"x24.0   74.18  1280 2558 2602 2750  960 1084 1089 1125 +hsync +vsync (27.0 kHz)
[   698.419] (II) fglrx(0): Modeline "1360x768"x50.0  148.50  1360 2448 2492 2640  768 1084 1089 1125 +hsync +vsync (56.2 kHz)
[   698.419] (II) fglrx(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[   698.419] (II) fglrx(0): Modeline "1360x768"x25.0   74.25  1360 2448 2492 2640  768 1084 1089 1125 +hsync +vsync (28.1 kHz)
[   698.419] (II) fglrx(0): Modeline "1360x768"x30.0   74.18  1360 2008 2052 2200  768 1084 1089 1125 +hsync +vsync (33.7 kHz)
[   698.419] (II) fglrx(0): Modeline "1360x768"x24.0   74.18  1360 2558 2602 2750  768 1084 1089 1125 +hsync +vsync (27.0 kHz)
[   698.419] (II) fglrx(0): Modeline "1280x800"x50.0  148.50  1280 2448 2492 2640  800 1084 1089 1125 +hsync +vsync (56.2 kHz)
[   698.419] (II) fglrx(0): Modeline "1280x800"x60.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[   698.419] (II) fglrx(0): Modeline "1280x800"x25.0   74.25  1280 2448 2492 2640  800 1084 1089 1125 +hsync +vsync (28.1 kHz)
[   698.419] (II) fglrx(0): Modeline "1280x800"x30.0   74.18  1280 2008 2052 2200  800 1084 1089 1125 +hsync +vsync (33.7 kHz)
[   698.419] (II) fglrx(0): Modeline "1280x800"x24.0   74.18  1280 2558 2602 2750  800 1084 1089 1125 +hsync +vsync (27.0 kHz)
[   698.419] (II) fglrx(0): Modeline "1152x864"x50.0  148.50  1152 2448 2492 2640  864 1084 1089 1125 +hsync +vsync (56.2 kHz)
[   698.419] (II) fglrx(0): Modeline "1152x864"x59.9  148.35  1152 2008 2052 2200  864 1084 1089 1125 +hsync +vsync (67.4 kHz)
[   698.419] (II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   698.419] (II) fglrx(0): Modeline "1152x864"x25.0   74.25  1152 2448 2492 2640  864 1084 1089 1125 +hsync +vsync (28.1 kHz)
[   698.419] (II) fglrx(0): Modeline "1152x864"x30.0   74.18  1152 2008 2052 2200  864 1084 1089 1125 +hsync +vsync (33.7 kHz)
[   698.419] (II) fglrx(0): Modeline "1152x864"x24.0   74.18  1152 2558 2602 2750  864 1084 1089 1125 +hsync +vsync (27.0 kHz)
[   698.419] (II) fglrx(0): Modeline "1280x768"x50.0  148.50  1280 2448 2492 2640  768 1084 1089 1125 +hsync +vsync (56.2 kHz)
[   698.419] (II) fglrx(0): Modeline "1280x768"x60.0   83.50  1280 1352 1480 1680  768 803 809 831 -hsync +vsync (49.7 kHz)
[   698.420] (II) fglrx(0): Modeline "1280x768"x25.0   74.25  1280 2448 2492 2640  768 1084 1089 1125 +hsync +vsync (28.1 kHz)
[   698.420] (II) fglrx(0): Modeline "1280x768"x30.0   74.18  1280 2008 2052 2200  768 1084 1089 1125 +hsync +vsync (33.7 kHz)
[   698.420] (II) fglrx(0): Modeline "1280x768"x24.0   74.18  1280 2558 2602 2750  768 1084 1089 1125 +hsync +vsync (27.0 kHz)
[   698.420] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[   698.420] (II) fglrx(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[   698.420] (II) fglrx(0): Modeline "1280x720"x25.0   74.25  1280 2448 2492 2640  720 1084 1089 1125 +hsync +vsync (28.1 kHz)
[   698.420] (II) fglrx(0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[   698.420] (II) fglrx(0): Modeline "1280x720"x30.0   74.18  1280 2008 2052 2200  720 1084 1089 1125 +hsync +vsync (33.7 kHz)
[   698.420] (II) fglrx(0): Modeline "1280x720"x24.0   74.18  1280 2558 2602 2750  720 1084 1089 1125 +hsync +vsync (27.0 kHz)
[   698.420] (II) fglrx(0): Modeline "1024x768"x50.0  148.50  1024 2448 2492 2640  768 1084 1089 1125 +hsync +vsync (56.2 kHz)
[   698.420] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   698.420] (II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   698.420] (II) fglrx(0): Modeline "1024x768"x25.0   74.25  1024 2448 2492 2640  768 1084 1089 1125 +hsync +vsync (28.1 kHz)
[   698.420] (II) fglrx(0): Modeline "1024x768"x30.0   74.18  1024 2008 2052 2200  768 1084 1089 1125 +hsync +vsync (33.7 kHz)
[   698.420] (II) fglrx(0): Modeline "1024x768"x24.0   74.18  1024 2558 2602 2750  768 1084 1089 1125 +hsync +vsync (27.0 kHz)
[   698.420] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   698.420] (II) fglrx(0): Modeline "1152x648"x50.0   74.25  1152 1592 1632 1980  648 653 658 750 +hsync +vsync (37.5 kHz)
[   698.420] (II) fglrx(0): Modeline "1152x648"x59.9   74.18  1152 1262 1302 1650  648 653 658 750 +hsync +vsync (45.0 kHz)
[   698.420] (II) fglrx(0): Modeline "1024x600"x50.0  148.50  1024 2448 2492 2640  600 1084 1089 1125 +hsync +vsync (56.2 kHz)
[   698.420] (II) fglrx(0): Modeline "1024x600"x75.0   78.75  1024 1040 1136 1312  600 769 772 800 +hsync +vsync (60.0 kHz)
[   698.420] (II) fglrx(0): Modeline "1024x600"x70.0   75.00  1024 1048 1184 1328  600 771 777 806 -hsync -vsync (56.5 kHz)
[   698.420] (II) fglrx(0): Modeline "1024x600"x25.0   74.25  1024 2448 2492 2640  600 1084 1089 1125 +hsync +vsync (28.1 kHz)
[   698.420] (II) fglrx(0): Modeline "1024x600"x30.0   74.18  1024 2008 2052 2200  600 1084 1089 1125 +hsync +vsync (33.7 kHz)
[   698.420] (II) fglrx(0): Modeline "1024x600"x24.0   74.18  1024 2558 2602 2750  600 1084 1089 1125 +hsync +vsync (27.0 kHz)
[   698.420] (II) fglrx(0): Modeline "1024x600"x60.0   65.00  1024 1048 1184 1344  600 771 777 806 -hsync -vsync (48.4 kHz)
[   698.420] (II) fglrx(0): Modeline "800x600"x50.0  148.50  800 2448 2492 2640  600 1084 1089 1125 +hsync +vsync (56.2 kHz)
[   698.420] (II) fglrx(0): Modeline "800x600"x25.0   74.25  800 2448 2492 2640  600 1084 1089 1125 +hsync +vsync (28.1 kHz)
[   698.420] (II) fglrx(0): Modeline "800x600"x30.0   74.18  800 2008 2052 2200  600 1084 1089 1125 +hsync +vsync (33.7 kHz)
[   698.420] (II) fglrx(0): Modeline "800x600"x24.0   74.18  800 2558 2602 2750  600 1084 1089 1125 +hsync +vsync (27.0 kHz)
[   698.420] (II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   698.420] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   698.420] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   698.420] (II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   698.420] (II) fglrx(0): Modeline "800x480"x50.0  148.50  800 2448 2492 2640  480 1084 1089 1125 +hsync +vsync (56.2 kHz)
[   698.421] (II) fglrx(0): Modeline "800x480"x25.0   74.25  800 2448 2492 2640  480 1084 1089 1125 +hsync +vsync (28.1 kHz)
[   698.421] (II) fglrx(0): Modeline "800x480"x30.0   74.18  800 2008 2052 2200  480 1084 1089 1125 +hsync +vsync (33.7 kHz)
[   698.421] (II) fglrx(0): Modeline "800x480"x24.0   74.18  800 2558 2602 2750  480 1084 1089 1125 +hsync +vsync (27.0 kHz)
[   698.421] (II) fglrx(0): Modeline "800x480"x72.0   50.00  800 856 976 1040  480 637 643 666 +hsync +vsync (48.1 kHz)
[   698.421] (II) fglrx(0): Modeline "800x480"x75.0   49.50  800 816 896 1056  480 601 604 625 +hsync +vsync (46.9 kHz)
[   698.421] (II) fglrx(0): Modeline "800x480"x60.0   40.00  800 840 968 1056  480 601 605 628 +hsync +vsync (37.9 kHz)
[   698.421] (II) fglrx(0): Modeline "800x480"x56.0   36.00  800 824 896 1024  480 601 603 625 +hsync +vsync (35.2 kHz)
[   698.421] (II) fglrx(0): Modeline "720x480"x50.0  148.50  720 2448 2492 2640  480 1084 1089 1125 +hsync +vsync (56.2 kHz)
[   698.421] (II) fglrx(0): Modeline "720x480"x25.0   74.25  720 2448 2492 2640  480 1084 1089 1125 +hsync +vsync (28.1 kHz)
[   698.421] (II) fglrx(0): Modeline "720x480"x30.0   74.18  720 2008 2052 2200  480 1084 1089 1125 +hsync +vsync (33.7 kHz)
[   698.421] (II) fglrx(0): Modeline "720x480"x24.0   74.18  720 2558 2602 2750  480 1084 1089 1125 +hsync +vsync (27.0 kHz)
[   698.421] (II) fglrx(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[   698.421] (II) fglrx(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[   698.421] (II) fglrx(0): Modeline "640x480"x50.0  148.50  640 2448 2492 2640  480 1084 1089 1125 +hsync +vsync (56.2 kHz)
[   698.421] (II) fglrx(0): Modeline "640x480"x25.0   74.25  640 2448 2492 2640  480 1084 1089 1125 +hsync +vsync (28.1 kHz)
[   698.421] (II) fglrx(0): Modeline "640x480"x30.0   74.18  640 2008 2052 2200  480 1084 1089 1125 +hsync +vsync (33.7 kHz)
[   698.421] (II) fglrx(0): Modeline "640x480"x24.0   74.18  640 2558 2602 2750  480 1084 1089 1125 +hsync +vsync (27.0 kHz)
[   698.421] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   698.421] (II) fglrx(0): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 -hsync -vsync (37.9 kHz)
[   698.421] (II) fglrx(0): Modeline "640x480"x67.0   27.28  640 664 728 816  480 481 484 499 -hsync +vsync (33.4 kHz)
[   698.421] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   698.421] (II) fglrx(0): EDID for output DFP2
[   698.421] (II) fglrx(0): EDID for output CRT1
[   698.421] (II) fglrx(0): Output DFP1 connected
[   698.421] (II) fglrx(0): Output DFP2 disconnected
[   698.421] (II) fglrx(0): Output CRT1 disconnected
[   698.421] (II) fglrx(0): Using exact sizes for initial modes
[   698.421] (II) fglrx(0): Output DFP1 using initial mode 1920x1080
[   698.421] (II) fglrx(0): Display dimensions: (530, 300) mm
[   698.421] (II) fglrx(0): DPI set to (92, 92)
[   698.422] (II) fglrx(0): Adapter AMD Radeon HD 6310 Graphics has 2 configurable heads and 1 displays connected.
[   698.422] (==) fglrx(0):  PseudoColor visuals disabled
[   698.422] (II) Loading sub module "ramdac"
[   698.422] (II) LoadModule: "ramdac"
[   698.422] (II) Module "ramdac" already built-in
[   698.422] (==) fglrx(0): NoDRI = NO
[   698.422] (==) fglrx(0): Capabilities: 0x00000000
[   698.422] (==) fglrx(0): CapabilitiesEx: 0x00000000
[   698.422] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[   698.422] (**) fglrx(0): UseFastTLS=0
[   698.422] (==) fglrx(0): BlockSignalsOnLock=1
[   698.422] (--) Depth 24 pixmap format is 32 bpp
[   698.423] (II) Loading extension ATIFGLRXDRI
[   698.423] (II) fglrx(0): doing swlDriScreenInit
[   698.423] (II) fglrx(0): swlDriScreenInit for fglrx driver
[   698.423] ukiDynamicMajor: found major device number 250
[   698.423] ukiDynamicMajor: found major device number 250
[   698.423] ukiDynamicMajor: found major device number 250
[   698.423] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[   698.423] ukiOpenDevice: node name is /dev/ati/card0
[   698.423] ukiOpenDevice: open result is 12, (OK)
[   698.423] ukiOpenByBusid: ukiOpenMinor returns 12
[   698.423] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[   698.423] (II) fglrx(0): [uki] DRM interface version 1.0
[   698.423] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:0:1:0"
[   698.423] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2b000
[   698.423] (II) fglrx(0): [uki] mapped SAREA 0x2b000 to 0xb7695000
[   698.423] (II) fglrx(0): [uki] framebuffer handle = 0x2c000
[   698.424] (II) fglrx(0): [uki] added 1 reserved context for kernel
[   698.424] (II) fglrx(0): swlDriScreenInit done
[   698.424] (II) fglrx(0): Kernel Module Version Information:
[   698.424] (II) fglrx(0):     Name: fglrx
[   698.424] (II) fglrx(0):     Version: 8.93.4
[   698.424] (II) fglrx(0):     Date: Dec  5 2011
[   698.424] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[   698.424] (II) fglrx(0): Kernel Module version matches driver.
[   698.424] (II) fglrx(0): Kernel Module Build Time Information:
[   698.424] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.0.0-15-generic
[   698.424] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[   698.424] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[   698.424] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[   698.424] (II) fglrx(0): [uki] register handle = 0x0002d000
[   698.449] (II) fglrx(0): DRI initialization successfull
[   698.449] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x0102c000
[   698.449] (==) fglrx(0): Backing store disabled
[   698.449] (II) Loading extension FGLRXEXTENSION
[   698.449] (**) fglrx(0): DPMS enabled
[   698.450] (II) fglrx(0): Initialized in-driver Xinerama extension
[   698.450] (**) fglrx(0): Textured Video is enabled.
[   698.450] (II) LoadModule: "glesx"
[   698.450] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/glesx.so
[   698.452] (II) Module glesx: vendor="X.Org Foundation"
[   698.452] 	compiled for 1.4.99.906, module version = 1.0.0
[   698.452] (II) Loading extension GLESX
[   698.452] (II) fglrx(0): GLESX enableFlags = 592
[   698.452] (II) fglrx(0): GLESX is enabled
[   698.452] (II) LoadModule: "amdxmm"
[   698.452] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/amdxmm.so
[   698.453] (II) Module amdxmm: vendor="X.Org Foundation"
[   698.453] 	compiled for 1.4.99.906, module version = 2.0.0
[   698.465] (II) Loading extension AMDXVOPL
[   698.465] (II) Loading extension AMDXVBA
[   698.465] [-     XMM_GLX] [I ]glesxXvInit Configureable RGBOutputColorRange
[   698.467] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[   698.473] (II) fglrx(0): Enable composite support successfully
[   698.473] (WW) fglrx(0): Option "VendorName" is not used
[   698.473] (WW) fglrx(0): Option "ModelName" is not used
[   698.473] (II) fglrx(0): X context handle = 0x1
[   698.473] (II) fglrx(0): [DRI] installation complete
[   698.473] (==) fglrx(0): Silken mouse enabled
[   698.473] (==) fglrx(0): Using HW cursor of display infrastructure!
[   698.474] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[   698.584] (II) fglrx(0): Framebuffer compression enabled: mcAddr=0xf01370000 width=0x800 height=0x258
[   698.584] (--) RandR disabled
[   698.584] (II) Initializing built-in extension Generic Event Extension
[   698.584] (II) Initializing built-in extension SHAPE
[   698.584] (II) Initializing built-in extension MIT-SHM
[   698.584] (II) Initializing built-in extension XInputExtension
[   698.584] (II) Initializing built-in extension XTEST
[   698.584] (II) Initializing built-in extension BIG-REQUESTS
[   698.584] (II) Initializing built-in extension SYNC
[   698.584] (II) Initializing built-in extension XKEYBOARD
[   698.584] (II) Initializing built-in extension XC-MISC
[   698.584] (II) Initializing built-in extension SECURITY
[   698.584] (II) Initializing built-in extension XINERAMA
[   698.584] (II) Initializing built-in extension XFIXES
[   698.584] (II) Initializing built-in extension RENDER
[   698.584] (II) Initializing built-in extension RANDR
[   698.584] (II) Initializing built-in extension COMPOSITE
[   698.584] (II) Initializing built-in extension DAMAGE
[   698.584] (II) Initializing built-in extension GESTURE
[   698.590] ukiDynamicMajor: found major device number 250
[   698.590] ukiDynamicMajor: found major device number 250
[   698.590] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[   698.590] ukiOpenDevice: node name is /dev/ati/card0
[   698.590] ukiOpenDevice: open result is 13, (OK)
[   698.590] ukiOpenByBusid: ukiOpenMinor returns 13
[   698.590] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[   698.810] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[   698.849] (II) fglrx(0): Enable the clock gating!
[   698.849] (II) fglrx(0): Setting screen physical size to 507 x 285
[   698.868] (II) XKB: reuse xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   698.884] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   698.884] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   698.884] (II) LoadModule: "evdev"
[   698.885] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   698.885] (II) Module evdev: vendor="X.Org Foundation"
[   698.885] 	compiled for 1.10.2, module version = 2.6.0
[   698.885] 	Module class: X.Org XInput Driver
[   698.885] 	ABI class: X.Org XInput driver, version 12.3
[   698.885] (II) Using input driver 'evdev' for 'Power Button'
[   698.885] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   698.886] (**) Power Button: always reports core events
[   698.886] (**) Power Button: Device: "/dev/input/event1"
[   698.886] (--) Power Button: Found keys
[   698.886] (II) Power Button: Configuring as keyboard
[   698.886] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   698.886] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   698.886] (**) Option "xkb_rules" "evdev"
[   698.886] (**) Option "xkb_model" "pc105"
[   698.886] (**) Option "xkb_layout" "de"
[   698.891] (II) XKB: reuse xkmfile /tmp/server-808BBA3D4C227BDB44C370226C34E44C5D69A4A9.xkm
[   698.896] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   698.896] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   698.896] (II) Using input driver 'evdev' for 'Power Button'
[   698.896] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   698.896] (**) Power Button: always reports core events
[   698.896] (**) Power Button: Device: "/dev/input/event0"
[   698.896] (--) Power Button: Found keys
[   698.896] (II) Power Button: Configuring as keyboard
[   698.896] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   698.896] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   698.896] (**) Option "xkb_rules" "evdev"
[   698.896] (**) Option "xkb_model" "pc105"
[   698.896] (**) Option "xkb_layout" "de"
[   698.899] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event4)
[   698.899] (II) No input driver/identifier specified (ignoring)
[   698.906] (II) config/udev: Adding input device Logitech HID compliant keyboard (/dev/input/event6)
[   698.906] (**) Logitech HID compliant keyboard: Applying InputClass "evdev keyboard catchall"
[   698.906] (II) Using input driver 'evdev' for 'Logitech HID compliant keyboard'
[   698.906] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   698.906] (**) Logitech HID compliant keyboard: always reports core events
[   698.906] (**) Logitech HID compliant keyboard: Device: "/dev/input/event6"
[   698.906] (--) Logitech HID compliant keyboard: Found keys
[   698.906] (II) Logitech HID compliant keyboard: Configuring as keyboard
[   698.906] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5:1.0/input/input6/event6"
[   698.906] (II) XINPUT: Adding extended input device "Logitech HID compliant keyboard" (type: KEYBOARD)
[   698.906] (**) Option "xkb_rules" "evdev"
[   698.906] (**) Option "xkb_model" "pc105"
[   698.906] (**) Option "xkb_layout" "de"
[   698.908] (II) config/udev: Adding input device Logitech HID compliant keyboard (/dev/input/event7)
[   698.908] (**) Logitech HID compliant keyboard: Applying InputClass "evdev keyboard catchall"
[   698.908] (II) Using input driver 'evdev' for 'Logitech HID compliant keyboard'
[   698.908] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   698.908] (**) Logitech HID compliant keyboard: always reports core events
[   698.909] (**) Logitech HID compliant keyboard: Device: "/dev/input/event7"
[   698.909] (--) Logitech HID compliant keyboard: Found 20 mouse buttons
[   698.909] (--) Logitech HID compliant keyboard: Found keys
[   698.909] (II) Logitech HID compliant keyboard: Configuring as mouse
[   698.909] (II) Logitech HID compliant keyboard: Configuring as keyboard
[   698.909] (**) Logitech HID compliant keyboard: YAxisMapping: buttons 4 and 5
[   698.909] (**) Logitech HID compliant keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   698.909] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5:1.1/input/input7/event7"
[   698.909] (II) XINPUT: Adding extended input device "Logitech HID compliant keyboard" (type: KEYBOARD)
[   698.909] (**) Option "xkb_rules" "evdev"
[   698.909] (**) Option "xkb_model" "pc105"
[   698.909] (**) Option "xkb_layout" "de"
[   698.912] (II) config/udev: Adding input device HDA ATI SB Headphone (/dev/input/event5)
[   698.912] (II) No input driver/identifier specified (ignoring)
[   698.965] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments

```

---

