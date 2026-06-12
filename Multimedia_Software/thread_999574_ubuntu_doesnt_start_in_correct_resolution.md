---
title: "ubuntu doesnt start in correct resolution"
date: 2008-12-02
forum: Multimedia Software
---

### Post by awais_rauf on 2008-12-02
I have been using ubuntu since quite a while now. I have been facing a problem that whenever the any desktop enviornment starts it (most of the times) starts with 800x600 resolution although i have specified 1024x768 and 60hz. I try to change the resolution via gnome applet but it doesnt show other display modes. When this happens i logout and login back and it reverts to the correct resolution.

Here is the Xorg log file


```
 X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux RAUFS-DESKTOP 2.6.27-7-generic #1 SMP Thu Oct 30 04:18:38 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec  2 09:12:03 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
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

(--) PCI:*(0@1:0:0) Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter rev 33, Mem @ 0xf0000000/0, 0xe6000000/0, I/O @ 0x0000a800/0
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
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
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
(II) Matched sis from file name sis.ids
(==) Matched sis for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "sis"

(II) Loading /usr/lib/xorg/modules/drivers//sis_drv.so
(II) Module sis: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 0.10.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
	SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
	SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
	SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX],
	SIS340
(II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
	Volari V3XT/V5/V8/Duo (XG40)
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for sis
(WW) SIS: No matching Device section for instance (BusID PCI:0@0:0:0) found
(WW) SIS: No matching Device section for instance (BusID PCI:0@0:0:1) found
(WW) SIS: No matching Device section for instance (BusID PCI:0@0:1:0) found
(WW) SIS: No matching Device section for instance (BusID PCI:0@0:1:2) found
(WW) SIS: No matching Device section for instance (BusID PCI:0@0:1:3) found
(WW) SIS: No matching Device section for instance (BusID PCI:0@0:2:0) found
(--) Assigning device section with no busID to primary device
(--) Chipset SIS630/730 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) SIS(0): SiS driver (2005/09/20-1, compiled for X.org 1.5.0.0)
(II) SIS(0): Copyright (C) 2001-2005 Thomas Winischhofer <thomas@winischhofer.net> and others
(II) SIS(0): *** See [http://www.winischhofer.at/linuxsisvga.shtml](http://www.winischhofer.at/linuxsisvga.shtml)
(II) SIS(0): *** for documentation and updates.
(--) SIS(0): sisfb not found
(--) SIS(0): Relocated I/O registers at 0xA800
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) SIS(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) SIS(0): Depth 24, (==) framebuffer bpp 32
(==) SIS(0): RGB weight 888
(==) SIS(0): Default visual is TrueColor
(WW) SIS(0): Could not find/read video BIOS
(==) SIS(0): Using XAA acceleration architecture
(==) SIS(0): Using HW cursor
(==) SIS(0): Color HW cursor is disabled
(==) SIS(0): TurboQueue enabled
(==) SIS(0): Hotkey display switching is disabled
(II) SIS(0): WARNING: Using the Hotkey might freeze your machine, regardless
(II) SIS(0):          whether enabled or disabled. This is no driver bug.
(==) SIS(0): SiSCtrl utility interface is disabled
(II) SIS(0): For information on SiSCtrl, see
		[http://www.winischhofer.at/linuxsispart1.shtml#sisctrl](http://www.winischhofer.at/linuxsispart1.shtml#sisctrl)
(==) SIS(0): DRI enabled
(II) SIS(0): Checking OS for SSE support is not supported in this version of X.org
(II) SIS(0): If your OS supports SSE, set the option "UseSSE" to "on".
(--) SIS(0): Shared Memory Area is on DIMM0
(--) SIS(0): DRAM type: SDR SDRAM
(--) SIS(0): Memory clock: 100.226 MHz
(--) SIS(0): (Adapter assumes MCLK being 100 Mhz)
(--) SIS(0): DRAM bus width: 64 bit
(--) SIS(0): Linear framebuffer at 0xF0000000
(--) SIS(0): MMIO registers at 0xE6000000 (size 64K)
(--) SIS(0): VideoRAM: 16384 KB
(II) SIS(0): Using 8192K of framebuffer memory at offset 0K
(--) SIS(0): Hardware supports two video overlays
(==) SIS(0): Using gamma correction (1.0, 1.0, 1.0)
(II) SIS(0): Gamma correction is enabled
(--) SIS(0): Memory bandwidth at 32 bpp is 200.452 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(--) SIS(0): CRT1 DDC probing failed
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) SIS(0): initializing int10
(II) SIS(0): Primary V_BIOS segment is: 0xc000
(II) SIS(0): VESA BIOS detected
(II) SIS(0): VESA VBE Version 3.0
(II) SIS(0): VESA VBE Total Mem: 16384 kB
(II) SIS(0): VESA VBE OEM: SiS
(II) SIS(0): VESA VBE OEM Software Rev: 1.0
(II) SIS(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
(II) SIS(0): VESA VBE OEM Product: 630
(II) SIS(0): VESA VBE OEM Product Rev: 2.08.50
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) SIS(0): VESA VBE DDC supported
(II) SIS(0): VESA VBE DDC Level none
(II) SIS(0): VESA VBE DDC transfer in appr. 0 sec.
(II) SIS(0): VESA VBE DDC read failed
(==) SIS(0): Min pixel clock is 10 MHz
(--) SIS(0): Max pixel clock is 139 MHz
(II) SIS(0): Replaced entire mode list with built-in modes
(II) SIS(0): "Unknown reason" in the following list means that the mode
(II) SIS(0): is not supported on the chipset/bridge/current output device.
(II) SIS(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) SIS(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
[b]
(WW) SIS(0): Unable to estimate virtual size
(II) SIS(0): Clock range:  10.00 to 139.09 MHz
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x400" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "320x200" (vrefresh out of range)
(II) SIS(0): Not using default mode "512x384" (hsync out of range)
(II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1280x960" (hsync out of range)
(II) SIS(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1024x600" (hsync out of range)
(II) SIS(0): Not using default mode "1152x768" (hsync out of range)
(II) SIS(0): Not using default mode "800x480" (hsync out of range)
(II) SIS(0): Not using default mode "800x480" (hsync out of range)
(II) SIS(0): Not using default mode "1024x576" (hsync out of range)
(II) SIS(0): Not using default mode "1024x576" (hsync out of range)
(II) SIS(0): Not using default mode "1024x576" (hsync out of range)
(II) SIS(0): Not using default mode "1280x720" (hsync out of range)
(II) SIS(0): Not using default mode "1280x720" (hsync out of range)
(II) SIS(0): Not using default mode "1280x720" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1152x864" (hsync out of range)
(II) SIS(0): Not using default mode "1152x864" (hsync out of range)
(II) SIS(0): Not using default mode "1152x864" (hsync out of range)
(II) SIS(0): Not using default mode "848x480" (hsync out of range)
(II) SIS(0): Not using default mode "848x480" (hsync out of range)
(II) SIS(0): Not using default mode "856x480" (hsync out of range)
(II) SIS(0): Not using default mode "1360x768" (hsync out of range)
(II) SIS(0): Not using default mode "1280x768" (hsync out of range)
(II) SIS(0): Not using default mode "1360x1024" (hsync out of range) [\b]
(--) SIS(0): Virtual size is 856x600 (pitch 856)
(**) SIS(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) SIS(0): Modeline "800x600"x60.3   39.97  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) SIS(0): *Default mode "800x600": 36.1 MHz, 35.2 kHz, 56.3 Hz
(II) SIS(0): Modeline "800x600"x56.3   36.06  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) SIS(0): *Default mode "768x576": 35.0 MHz, 35.9 kHz, 60.1 Hz
(II) SIS(0): Modeline "768x576"x60.1   35.00  768 792 872 976  576 578 581 597 +hsync +vsync (35.9 kHz)
(**) SIS(0): *Default mode "720x576": 32.7 MHz, 35.9 kHz, 60.1 Hz
(II) SIS(0): Modeline "720x576"x60.1   32.73  720 744 816 912  576 578 581 597 +hsync +vsync (35.9 kHz)
(**) SIS(0): *Default mode "856x480": 33.9 MHz, 31.7 kHz, 59.8 Hz
(II) SIS(0): Modeline "856x480"x59.8   33.94  856 872 1000 1072  480 492 495 529 -hsync -vsync (31.7 kHz)
(**) SIS(0): *Default mode "800x480": 39.8 MHz, 37.7 kHz, 60.0 Hz
(II) SIS(0): Modeline "800x480"x60.0   39.77  800 840 968 1056  480 552 556 628 +hsync +vsync (37.7 kHz)
(**) SIS(0): *Default mode "720x480": 28.3 MHz, 31.6 kHz, 61.0 Hz
(II) SIS(0): Modeline "720x480"x61.0   28.28  720 728 840 896  480 490 492 517 -hsync -vsync (31.6 kHz)
(**) SIS(0): *Default mode "640x480": 25.1 MHz, 31.3 kHz, 59.7 Hz
(II) SIS(0): Modeline "640x480"x59.7   25.06  640 656 752 800  480 490 492 525 -hsync -vsync (31.3 kHz)
(**) SIS(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) SIS(0): Modeline "400x300"x60.3   19.98  400 416 480 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) SIS(0): *Default mode "320x240": 12.5 MHz, 31.3 kHz, 60.7 Hz (D)
(II) SIS(0): Modeline "320x240"x60.7   12.53  320 328 376 400  240 245 246 258 doublescan -hsync -vsync (31.3 kHz)
(==) SIS(0): DPI set to (96, 96)
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
(II) SIS(0): 2D acceleration enabled
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) SIS(0): initializing int10
(II) SIS(0): Primary V_BIOS segment is: 0xc000
(II) SIS(0): VESA BIOS detected
(II) SIS(0): VESA VBE Version 3.0
(II) SIS(0): VESA VBE Total Mem: 16384 kB
(II) SIS(0): VESA VBE OEM: SiS
(II) SIS(0): VESA VBE OEM Software Rev: 1.0
(II) SIS(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
(II) SIS(0): VESA VBE OEM Product: 630
(II) SIS(0): VESA VBE OEM Product Rev: 2.08.50
(II) SIS(0): Setting standard mode 0x63
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] loaded kernel module for "sis" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) SIS(0): [drm] Using the DRM lock SAREA also for drawables.
(II) SIS(0): [drm] framebuffer handle = 0xf0000000
(II) SIS(0): [drm] added 1 reserved context for kernel
(II) SIS(0): X context handle = 0x1
(II) SIS(0): [drm] installed DRM signal handler
(II) SIS(0): [dri] Video RAM memory heap: 0x800000 to 0xf7f000 (7676KB)
(II) SIS(0): [drm] MMIO registers mapped to 0xe6000000
(II) SIS(0): [drm] AGP enabled
(II) SIS(0): [drm] Allocated 8MB AGP memory
(II) SIS(0): [drm] Bound 8MB AGP memory
(II) SIS(0): [drm] No valid IRQ number for device 1:0:0 (code -22)
(II) SIS(0): [dri] Visual configs initialized
(II) SIS(0): Framebuffer from (0,0) to (855,2447)
(II) SIS(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Dashed Lines
	Setting up tile and stipple cache:
		32 128x128 slots
		13 256x256 slots
(--) SIS(0): CPU frequency 1002.27Mhz
(II) SIS(0): Benchmarking system RAM to video RAM memory transfer methods:
(--) SIS(0): 	Checked libc memcpy()... 	99.7 MiB/s
(--) SIS(0): 	Checked built-in-1 memcpy()... 	107.2 MiB/s
(--) SIS(0): 	Checked built-in-2 memcpy()... 	57.4 MiB/s
(--) SIS(0): 	Checked MMX memcpy()... 	108.7 MiB/s
(--) SIS(0): 	Checked MMX2 memcpy()... 	107.6 MiB/s
(--) SIS(0): Using MMX method for aligned data transfers to video RAM
(--) SIS(0): Using MMX method for unaligned data transfers to video RAM
(==) SIS(0): Backing store disabled
(==) SIS(0): Silken mouse enabled
(II) SIS(0): DPMS enabled
(II) SIS(0): Using SiS300/315/330/340 series HW Xv
(II) SIS(0): [DRI] installation complete
(II) SIS(0): Direct rendering enabled
(WW) SIS(0): Option "UseFBDev" is not used
(II) SIS(0): Initialized SISCTRL extension version 0.1
(II) SIS(0): Registered screen 0 with SISCTRL extension version 0.1
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: Loaded and initialized /usr/lib/dri/sis_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
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
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device HID 04b3:310b
(**) HID 04b3:310b: always reports core events
(**) HID 04b3:310b: Device: "/dev/input/event2"
(II) HID 04b3:310b: Found x and y relative axes
(II) HID 04b3:310b: Found 3 mouse buttons
(II) HID 04b3:310b: Configuring as mouse
(II) XINPUT: Adding extended input device "HID 04b3:310b" (type: MOUSE)
(**) HID 04b3:310b: YAxisMapping: buttons 4 and 5
(**) HID 04b3:310b: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
AUDIT: Tue Dec  2 09:12:11 2008: 4915 X: client 4 rejected from local host ( uid=0 gid=0 pid=5140 )
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux RAUFS-DESKTOP 2.6.27-7-generic #1 SMP Thu Oct 30 04:18:38 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec  2 09:12:03 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
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

(--) PCI:*(0@1:0:0) Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter rev 33, Mem @ 0xf0000000/0, 0xe6000000/0, I/O @ 0x0000a800/0
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
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
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
(II) Matched sis from file name sis.ids
(==) Matched sis for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "sis"

(II) Loading /usr/lib/xorg/modules/drivers//sis_drv.so
(II) Module sis: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 0.10.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
	SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
	SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
	SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX],
	SIS340
(II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
	Volari V3XT/V5/V8/Duo (XG40)
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for sis
(WW) SIS: No matching Device section for instance (BusID PCI:0@0:0:0) found
(WW) SIS: No matching Device section for instance (BusID PCI:0@0:0:1) found
(WW) SIS: No matching Device section for instance (BusID PCI:0@0:1:0) found
(WW) SIS: No matching Device section for instance (BusID PCI:0@0:1:2) found
(WW) SIS: No matching Device section for instance (BusID PCI:0@0:1:3) found
(WW) SIS: No matching Device section for instance (BusID PCI:0@0:2:0) found
(--) Assigning device section with no busID to primary device
(--) Chipset SIS630/730 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) SIS(0): SiS driver (2005/09/20-1, compiled for X.org 1.5.0.0)
(II) SIS(0): Copyright (C) 2001-2005 Thomas Winischhofer <thomas@winischhofer.net> and others
(II) SIS(0): *** See [http://www.winischhofer.at/linuxsisvga.shtml](http://www.winischhofer.at/linuxsisvga.shtml)
(II) SIS(0): *** for documentation and updates.
(--) SIS(0): sisfb not found
(--) SIS(0): Relocated I/O registers at 0xA800
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) SIS(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) SIS(0): Depth 24, (==) framebuffer bpp 32
(==) SIS(0): RGB weight 888
(==) SIS(0): Default visual is TrueColor
(WW) SIS(0): Could not find/read video BIOS
(==) SIS(0): Using XAA acceleration architecture
(==) SIS(0): Using HW cursor
(==) SIS(0): Color HW cursor is disabled
(==) SIS(0): TurboQueue enabled
(==) SIS(0): Hotkey display switching is disabled
(II) SIS(0): WARNING: Using the Hotkey might freeze your machine, regardless
(II) SIS(0):          whether enabled or disabled. This is no driver bug.
(==) SIS(0): SiSCtrl utility interface is disabled
(II) SIS(0): For information on SiSCtrl, see
		[http://www.winischhofer.at/linuxsispart1.shtml#sisctrl](http://www.winischhofer.at/linuxsispart1.shtml#sisctrl)
(==) SIS(0): DRI enabled
(II) SIS(0): Checking OS for SSE support is not supported in this version of X.org
(II) SIS(0): If your OS supports SSE, set the option "UseSSE" to "on".
(--) SIS(0): Shared Memory Area is on DIMM0
(--) SIS(0): DRAM type: SDR SDRAM
(--) SIS(0): Memory clock: 100.226 MHz
(--) SIS(0): (Adapter assumes MCLK being 100 Mhz)
(--) SIS(0): DRAM bus width: 64 bit
(--) SIS(0): Linear framebuffer at 0xF0000000
(--) SIS(0): MMIO registers at 0xE6000000 (size 64K)
(--) SIS(0): VideoRAM: 16384 KB
(II) SIS(0): Using 8192K of framebuffer memory at offset 0K
(--) SIS(0): Hardware supports two video overlays
(==) SIS(0): Using gamma correction (1.0, 1.0, 1.0)
(II) SIS(0): Gamma correction is enabled
(--) SIS(0): Memory bandwidth at 32 bpp is 200.452 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(--) SIS(0): CRT1 DDC probing failed
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) SIS(0): initializing int10
(II) SIS(0): Primary V_BIOS segment is: 0xc000
(II) SIS(0): VESA BIOS detected
(II) SIS(0): VESA VBE Version 3.0
(II) SIS(0): VESA VBE Total Mem: 16384 kB
(II) SIS(0): VESA VBE OEM: SiS
(II) SIS(0): VESA VBE OEM Software Rev: 1.0
(II) SIS(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
(II) SIS(0): VESA VBE OEM Product: 630
(II) SIS(0): VESA VBE OEM Product Rev: 2.08.50
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) SIS(0): VESA VBE DDC supported
(II) SIS(0): VESA VBE DDC Level none
(II) SIS(0): VESA VBE DDC transfer in appr. 0 sec.
(II) SIS(0): VESA VBE DDC read failed
(==) SIS(0): Min pixel clock is 10 MHz
(--) SIS(0): Max pixel clock is 139 MHz
(II) SIS(0): Replaced entire mode list with built-in modes
(II) SIS(0): "Unknown reason" in the following list means that the mode
(II) SIS(0): is not supported on the chipset/bridge/current output device.
(II) SIS(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) SIS(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
[B](WW) SIS(0): Unable to estimate virtual size
(II) SIS(0): Clock range:  10.00 to 139.09 MHz
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x400" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "320x200" (vrefresh out of range)
(II) SIS(0): Not using default mode "512x384" (hsync out of range)
(II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1280x960" (hsync out of range)
(II) SIS(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1024x600" (hsync out of range)
(II) SIS(0): Not using default mode "1152x768" (hsync out of range)
(II) SIS(0): Not using default mode "800x480" (hsync out of range)
(II) SIS(0): Not using default mode "800x480" (hsync out of range)
(II) SIS(0): Not using default mode "1024x576" (hsync out of range)
(II) SIS(0): Not using default mode "1024x576" (hsync out of range)
(II) SIS(0): Not using default mode "1024x576" (hsync out of range)
(II) SIS(0): Not using default mode "1280x720" (hsync out of range)
(II) SIS(0): Not using default mode "1280x720" (hsync out of range)
(II) SIS(0): Not using default mode "1280x720" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1152x864" (hsync out of range)
(II) SIS(0): Not using default mode "1152x864" (hsync out of range)
(II) SIS(0): Not using default mode "1152x864" (hsync out of range)
(II) SIS(0): Not using default mode "848x480" (hsync out of range)
(II) SIS(0): Not using default mode "848x480" (hsync out of range)
(II) SIS(0): Not using default mode "856x480" (hsync out of range)
(II) SIS(0): Not using default mode "1360x768" (hsync out of range)
(II) SIS(0): Not using default mode "1280x768" (hsync out of range)
(II) SIS(0): Not using default mode "1360x1024" (hsync out of range)[/B]
(--) SIS(0): Virtual size is 856x600 (pitch 856)
(**) SIS(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) SIS(0): Modeline "800x600"x60.3   39.97  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) SIS(0): *Default mode "800x600": 36.1 MHz, 35.2 kHz, 56.3 Hz
(II) SIS(0): Modeline "800x600"x56.3   36.06  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) SIS(0): *Default mode "768x576": 35.0 MHz, 35.9 kHz, 60.1 Hz
(II) SIS(0): Modeline "768x576"x60.1   35.00  768 792 872 976  576 578 581 597 +hsync +vsync (35.9 kHz)
(**) SIS(0): *Default mode "720x576": 32.7 MHz, 35.9 kHz, 60.1 Hz
(II) SIS(0): Modeline "720x576"x60.1   32.73  720 744 816 912  576 578 581 597 +hsync +vsync (35.9 kHz)
(**) SIS(0): *Default mode "856x480": 33.9 MHz, 31.7 kHz, 59.8 Hz
(II) SIS(0): Modeline "856x480"x59.8   33.94  856 872 1000 1072  480 492 495 529 -hsync -vsync (31.7 kHz)
(**) SIS(0): *Default mode "800x480": 39.8 MHz, 37.7 kHz, 60.0 Hz
(II) SIS(0): Modeline "800x480"x60.0   39.77  800 840 968 1056  480 552 556 628 +hsync +vsync (37.7 kHz)
(**) SIS(0): *Default mode "720x480": 28.3 MHz, 31.6 kHz, 61.0 Hz
(II) SIS(0): Modeline "720x480"x61.0   28.28  720 728 840 896  480 490 492 517 -hsync -vsync (31.6 kHz)
(**) SIS(0): *Default mode "640x480": 25.1 MHz, 31.3 kHz, 59.7 Hz
(II) SIS(0): Modeline "640x480"x59.7   25.06  640 656 752 800  480 490 492 525 -hsync -vsync (31.3 kHz)
(**) SIS(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) SIS(0): Modeline "400x300"x60.3   19.98  400 416 480 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) SIS(0): *Default mode "320x240": 12.5 MHz, 31.3 kHz, 60.7 Hz (D)
(II) SIS(0): Modeline "320x240"x60.7   12.53  320 328 376 400  240 245 246 258 doublescan -hsync -vsync (31.3 kHz)
(==) SIS(0): DPI set to (96, 96)
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
(II) SIS(0): 2D acceleration enabled
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) SIS(0): initializing int10
(II) SIS(0): Primary V_BIOS segment is: 0xc000
(II) SIS(0): VESA BIOS detected
(II) SIS(0): VESA VBE Version 3.0
(II) SIS(0): VESA VBE Total Mem: 16384 kB
(II) SIS(0): VESA VBE OEM: SiS
(II) SIS(0): VESA VBE OEM Software Rev: 1.0
(II) SIS(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
(II) SIS(0): VESA VBE OEM Product: 630
(II) SIS(0): VESA VBE OEM Product Rev: 2.08.50
(II) SIS(0): Setting standard mode 0x63
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] loaded kernel module for "sis" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) SIS(0): [drm] Using the DRM lock SAREA also for drawables.
(II) SIS(0): [drm] framebuffer handle = 0xf0000000
(II) SIS(0): [drm] added 1 reserved context for kernel
(II) SIS(0): X context handle = 0x1
(II) SIS(0): [drm] installed DRM signal handler
(II) SIS(0): [dri] Video RAM memory heap: 0x800000 to 0xf7f000 (7676KB)
(II) SIS(0): [drm] MMIO registers mapped to 0xe6000000
(II) SIS(0): [drm] AGP enabled
(II) SIS(0): [drm] Allocated 8MB AGP memory
(II) SIS(0): [drm] Bound 8MB AGP memory
(II) SIS(0): [drm] No valid IRQ number for device 1:0:0 (code -22)
(II) SIS(0): [dri] Visual configs initialized
(II) SIS(0): Framebuffer from (0,0) to (855,2447)
(II) SIS(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Dashed Lines
	Setting up tile and stipple cache:
		32 128x128 slots
		13 256x256 slots
(--) SIS(0): CPU frequency 1002.27Mhz
(II) SIS(0): Benchmarking system RAM to video RAM memory transfer methods:
(--) SIS(0): 	Checked libc memcpy()... 	99.7 MiB/s
(--) SIS(0): 	Checked built-in-1 memcpy()... 	107.2 MiB/s
(--) SIS(0): 	Checked built-in-2 memcpy()... 	57.4 MiB/s
(--) SIS(0): 	Checked MMX memcpy()... 	108.7 MiB/s
(--) SIS(0): 	Checked MMX2 memcpy()... 	107.6 MiB/s
(--) SIS(0): Using MMX method for aligned data transfers to video RAM
(--) SIS(0): Using MMX method for unaligned data transfers to video RAM
(==) SIS(0): Backing store disabled
(==) SIS(0): Silken mouse enabled
(II) SIS(0): DPMS enabled
(II) SIS(0): Using SiS300/315/330/340 series HW Xv
(II) SIS(0): [DRI] installation complete
(II) SIS(0): Direct rendering enabled
(WW) SIS(0): Option "UseFBDev" is not used
(II) SIS(0): Initialized SISCTRL extension version 0.1
(II) SIS(0): Registered screen 0 with SISCTRL extension version 0.1
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: Loaded and initialized /usr/lib/dri/sis_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
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
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device HID 04b3:310b
(**) HID 04b3:310b: always reports core events
(**) HID 04b3:310b: Device: "/dev/input/event2"
(II) HID 04b3:310b: Found x and y relative axes
(II) HID 04b3:310b: Found 3 mouse buttons
(II) HID 04b3:310b: Configuring as mouse
(II) XINPUT: Adding extended input device "HID 04b3:310b" (type: MOUSE)
(**) HID 04b3:310b: YAxisMapping: buttons 4 and 5
(**) HID 04b3:310b: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
AUDIT: Tue Dec  2 09:12:11 2008: 4915 X: client 4 rejected from local host ( uid=0 gid=0 pid=5140 )
```






Problem section i think is 
(WW) SIS(0): Unable to estimate virtual size
(II) SIS(0): Clock range:  10.00 to 139.09 MHz
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x400" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "320x200" (vrefresh out of range)
(II) SIS(0): Not using default mode "512x384" (hsync out of range)
(II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1280x960" (hsync out of range)
(II) SIS(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1024x600" (hsync out of range)
(II) SIS(0): Not using default mode "1152x768" (hsync out of range)
(II) SIS(0): Not using default mode "800x480" (hsync out of range)
(II) SIS(0): Not using default mode "800x480" (hsync out of range)
(II) SIS(0): Not using default mode "1024x576" (hsync out of range)
(II) SIS(0): Not using default mode "1024x576" (hsync out of range)
(II) SIS(0): Not using default mode "1024x576" (hsync out of range)
(II) SIS(0): Not using default mode "1280x720" (hsync out of range)
(II) SIS(0): Not using default mode "1280x720" (hsync out of range)
(II) SIS(0): Not using default mode "1280x720" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1152x864" (hsync out of range)
(II) SIS(0): Not using default mode "1152x864" (hsync out of range)
(II) SIS(0): Not using default mode "1152x864" (hsync out of range)
(II) SIS(0): Not using default mode "848x480" (hsync out of range)
(II) SIS(0): Not using default mode "848x480" (hsync out of range)
(II) SIS(0): Not using default mode "856x480" (hsync out of range)
(II) SIS(0): Not using default mode "1360x768" (hsync out of range)
(II) SIS(0): Not using default mode "1280x768" (hsync out of range)
(II) SIS(0): Not using default mode "1360x1024" (hsync out of range)

---

### Post by prshah on 2008-12-02
> **awais_rauf said:**
> Problem section i think is 
(WW) SIS(0): Unable to estimate virtual size


Try manually setting a virtual and desktop size in your /etc/X11/xorg.conf file. (Note: the xorg.conf file will soon be deprecated (not used) in some future version, but by then there will possibly be other tools to manage this situation. This workaround may work for now).

Backup / Edit your xorg.conf file; Open a terminal (Applications-Accessories-Terminal)  and give the following commands```
sudo cp -p /etc/X11/xorg.conf ~
gksudo gedit /etc/X11/xorg.conf
``` Look for a section _similar_ to that below and add the lines in red.:

[color=blue]```

Section "Screen"
    Identifier "screen1"
    Device "device1"
    Monitor "monitor1"
    
    Subsection "Display"
[color=red]        Modes   "1024x768@60"
        Virtual 1024 768[/color]
    EndSubsection

EndSection

```[/color]

Then save and quit, and either (a) reboot or (b) logout and restart X server with Ctrl+Alt+Backspace.

If you run into problems, get to a virtual terminal (Ctrl+Alt+F1..F4) and restore your original xorg.conf with these commands```
sudo rm /etc/X11/xorg.conf
sudo mv ~/xorg.conf /etc/X11/xorg.conf
```

Post back with your results.

---

