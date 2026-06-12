---
title: "sys driver on ubuntu 8.10"
date: 2008-12-24
forum: Multimedia Software
---

### Post by slavix on 2008-12-24
hello,
I am having problems getting sys driver to work on ubuntu 8.10
I ran dpkg-reconfigure xserver-xorg and now get errors starting graphics.
problem seems to be here
(II) SIS(0): Not using driver mode "1680x1050" (mode clock too high)

here is my log
```

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
(WW) SIS: No matching Device section for instance (BusID PCI:0@0:1:1) found
(WW) SIS: No matching Device section for instance (BusID PCI:0@0:1:2) found
(WW) SIS: No matching Device section for instance (BusID PCI:0@0:1:3) found
(WW) SIS: No matching Device section for instance (BusID PCI:0@0:1:4) found
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
(II) SIS(0): *** See http://www.winischhofer.at/linuxsisvga.shtml
(II) SIS(0): *** for documentation and updates.
(--) SIS(0): sisfb not found
(--) SIS(0): Relocated I/O registers at 0xC000
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
		http://www.winischhofer.at/linuxsispart1.shtml#sisctrl
(==) SIS(0): DRI enabled
(II) SIS(0): Checking OS for SSE support is not supported in this version of X.org
(II) SIS(0): If your OS supports SSE, set the option "UseSSE" to "on".
(--) SIS(0): Shared Memory Area is on DIMM0
(--) SIS(0): DRAM type: SDR SDRAM
(--) SIS(0): Memory clock: 133.634 MHz
(--) SIS(0): (Adapter assumes MCLK being 133 Mhz)
(--) SIS(0): DRAM bus width: 64 bit
(--) SIS(0): Linear framebuffer at 0xD0000000
(--) SIS(0): MMIO registers at 0xDD000000 (size 64K)
(--) SIS(0): VideoRAM: 8192 KB
(II) SIS(0): Using 4096K of framebuffer memory at offset 0K
(--) SIS(0): Hardware supports two video overlays
(==) SIS(0): Using gamma correction (1.0, 1.0, 1.0)
(II) SIS(0): Gamma correction is enabled
(--) SIS(0): Memory bandwidth at 32 bpp is 267.268 MHz
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
(II) SIS(0): VESA VBE Total Mem: 8192 kB
(II) SIS(0): VESA VBE OEM: SiS
(II) SIS(0): VESA VBE OEM Software Rev: 1.0
(II) SIS(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
(II) SIS(0): VESA VBE OEM Product: 630
(II) SIS(0): VESA VBE OEM Product Rev: 1.07.54
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) SIS(0): VESA VBE DDC supported
(II) SIS(0): VESA VBE DDC Level 2
(II) SIS(0): VESA VBE DDC transfer in appr. 1 sec.
(II) SIS(0): VESA VBE DDC read successfully
(--) SIS(0): VBE CRT1 DDC monitor info:
(II) SIS(0): Manufacturer: SAM  Model: 37b  Serial#: 1095840306
(II) SIS(0): Year: 2008  Week: 8
(II) SIS(0): EDID Version: 1.3
(II) SIS(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) SIS(0): Sync:  Separate  Composite  SyncOnGreen
(II) SIS(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) SIS(0): Gamma: 2.20
(II) SIS(0): DPMS capabilities: Off; RGB/Color Display
(II) SIS(0): First detailed timing is preferred mode
(II) SIS(0): redX: 0.649 redY: 0.335   greenX: 0.283 greenY: 0.605
(II) SIS(0): blueX: 0.151 blueY: 0.073   whiteX: 0.312 whiteY: 0.329
(II) SIS(0): Supported VESA Video Modes:
(II) SIS(0): 720x400@70Hz
(II) SIS(0): 640x480@60Hz
(II) SIS(0): 640x480@67Hz
(II) SIS(0): 640x480@72Hz
(II) SIS(0): 640x480@75Hz
(II) SIS(0): 800x600@56Hz
(II) SIS(0): 800x600@60Hz
(II) SIS(0): 800x600@72Hz
(II) SIS(0): 800x600@75Hz
(II) SIS(0): 832x624@75Hz
(II) SIS(0): 1024x768@60Hz
(II) SIS(0): 1024x768@70Hz
(II) SIS(0): 1024x768@75Hz
(II) SIS(0): 1280x1024@75Hz
(II) SIS(0): 1152x870@75Hz
(II) SIS(0): Manufacturer's mask: 0
(II) SIS(0): Supported Future Video Modes:
(II) SIS(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) SIS(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) SIS(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) SIS(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) SIS(0): Supported additional Video Mode:
(II) SIS(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
(II) SIS(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) SIS(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) SIS(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) SIS(0): Monitor name: SyncMaster
(II) SIS(0): Serial No: HVLQ211648
(II) SIS(0): EDID (in hex):
(II) SIS(0): 	00ffffffffffff004c2d7b0332325141
(II) SIS(0): 	081201030e2f1e782a78f1a655489b26
(II) SIS(0): 	125054bfef80b30081808140714f0101
(II) SIS(0): 	0101010101017c2e90a0601a1e403020
(II) SIS(0): 	3600da281100001a000000fd00384b1e
(II) SIS(0): 	510e000a202020202020000000fc0053
(II) SIS(0): 	796e634d61737465720a2020000000ff
(II) SIS(0): 	0048564c513231313634380a2020003b
(II) SIS(0): EDID vendor "SAM", prod id 891
(II) SIS(0): Using EDID range info for horizontal sync
(II) SIS(0): Using EDID range info for vertical refresh
(II) SIS(0): Printing DDC gathered Modelines:
(II) SIS(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) SIS(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) SIS(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) SIS(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) SIS(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) SIS(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) SIS(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) SIS(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) SIS(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) SIS(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) SIS(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) SIS(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) SIS(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) SIS(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) SIS(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) SIS(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) SIS(0): Modeline "1680x1050"x60.0  147.14  1680 1784 1968 2256  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) SIS(0): Modeline "1280x1024"x60.0  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
(II) SIS(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) SIS(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(--) SIS(0): End of VBE CRT1 DDC monitor info
(==) SIS(0): Min pixel clock is 10 MHz
(--) SIS(0): Max pixel clock is 185 MHz
(II) SIS(0): Replaced default mode list with built-in modes
(II) SIS(0): "Unknown reason" in the following list means that the mode
(II) SIS(0): is not supported on the chipset/bridge/current output device.
(II) SIS(0): Configured Monitor: Using hsync range of 30.00-81.00 kHz
(II) SIS(0): Configured Monitor: Using vrefresh range of 56.00-75.00 Hz
(II) SIS(0): Configured Monitor: Using maximum pixel clock of 140.00 MHz
(II) SIS(0): Estimated virtual size for aspect ratio 1.5667 is 1680x1050
(II) SIS(0): Clock range:  10.00 to 185.45 MHz
(II) SIS(0): Not using driver mode "1680x1050" (mode clock too high)
(II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
(II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
(II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) SIS(0): Not using default mode "1280x1024" (hsync out of range)
(II) SIS(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) SIS(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) SIS(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) SIS(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) SIS(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) SIS(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) SIS(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) SIS(0): Not using default mode "1280x960" (hsync out of range)
(II) SIS(0): Not using default mode "800x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x576" (vrefresh out of range)
(II) SIS(0): Not using default mode "1280x720" (hsync out of range)
(II) SIS(0): Not using default mode "1152x864" (vrefresh out of range)
(II) SIS(0): Not using default mode "848x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "856x480" (vrefresh out of range)
(EE) SIS(0): **************************************************
(EE) SIS(0):                       ERROR:
(EE) SIS(0): Virtual screen too big for memory; 6890K needed, 4096K available
(EE) SIS(0):                   END OF MESSAGE
(EE) SIS(0): **************************************************
(II) UnloadModule: "sis"
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules//libint10.so
(II) UnloadModule: "vbe"
(II) Unloading /usr/lib/xorg/modules//libvbe.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

---

### Post by albinootje on 2008-12-24
> **slavix said:**
> 
(EE) SIS(0): Virtual screen too big for memory; 6890K needed, 4096K available

Looks like you have an ancient 4 Mb SiS video card.

Years ago I would use a Knoppix Live cdrom to get the X config from Knoppix in those cases where I could not manage to get a reasonable desktop resolution.
Knoppix used to be pretty good at producing a good X config file.

And you might also want to try the "vesa" driver, and see how that goes.

---

### Post by slavix on 2008-12-24
Thanks. I tried vesa, but it does not support my monitor recommended resolution 1680x 1050 and the screen and I can only see part of the screen in 1280x1024. Is upgrading the video card the only way to go?

---

