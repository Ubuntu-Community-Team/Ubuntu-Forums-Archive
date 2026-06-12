---
title: "ATI Mobility Radeon HD 2400 XT Drivers?"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by Forlornity on 2007-10-31
Hi there,
I got myself a new laptop the other day with Vista (ugh) installed.
Naturally I immediately downloaded Ubuntu Gutsy and installed it, when it came to installing the drivers for my GPU however, I ran into problems:
After trying a number of methods of installing I eventually stumbled upon [this one]("http://ubuntuforums.org/showthread.php?t=575843") and found that it came closest to working. Not quite there though, it's actually made my graphics worse than before (using the Vesa driver) apart from now displaying resolutions above 1024*768, when browsing the internet, for example, it stops to render when I scroll (displaying the all too familiar lines). 
So my direct rendering is disabled :( 
I followed the aforementioned guide to the word on a fresh install of Ubuntu Gutsy with a ATI Mobility Radeon HD 2400 XT, in my xorg logs (in /var/log/Xorg.0.log) it says
```
(II) ATI Proprietary Linux Driver Version Identifier:8.42.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.423.2                  
(II) ATI Proprietary Linux Driver Build Date: Oct 19 2007 16:13:26
(--) Assigning device section with no busID to primary device
(--) Chipset Supported AMD Graphics Processor (0x94C8) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf0503000 - 0xf05037ff (0x800) MX[B]
	[5] -1	0	0xf0502000 - 0xf0502fff (0x1000) MX[B]
	[6] -1	0	0xf0501000 - 0xf0501fff (0x1000) MX[B]
	[7] -1	0	0xf0503800 - 0xf05038ff (0x100) MX[B]
	[8] -1	0	0xf0400000 - 0xf0403fff (0x4000) MX[B]
	[9] -1	0	0xf0300000 - 0xf0303fff (0x4000) MX[B]
	[10] -1	0	0xf0600000 - 0xf0603fff (0x4000) MX[B]
	[11] -1	0	0xf0609400 - 0xf06094ff (0x100) MX[B]
	[12] -1	0	0xf0608000 - 0xf0608fff (0x1000) MX[B]
	[13] -1	0	0xf0607000 - 0xf0607fff (0x1000) MX[B]
	[14] -1	0	0xf0606000 - 0xf0606fff (0x1000) MX[B]
	[15] -1	0	0xf0605000 - 0xf0605fff (0x1000) MX[B]
	[16] -1	0	0xf0604000 - 0xf0604fff (0x1000) MX[B]
	[17] -1	0	0xf0609000 - 0xf06093ff (0x400) MX[B]
	[18] -1	0	0xf0200000 - 0xf020ffff (0x10000) MX[B](B)
	[19] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[23] -1	0	0x00008420 - 0x0000842f (0x10) IX[B]
	[24] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[26] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[29] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[30] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[31] -1	0	0x00008438 - 0x0000843f (0x8) IX[B]
	[32] -1	0	0x00008434 - 0x00008437 (0x4) IX[B]
	[33] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[34] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x8209490
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf0503000 - 0xf05037ff (0x800) MX[B]
	[5] -1	0	0xf0502000 - 0xf0502fff (0x1000) MX[B]
	[6] -1	0	0xf0501000 - 0xf0501fff (0x1000) MX[B]
	[7] -1	0	0xf0503800 - 0xf05038ff (0x100) MX[B]
	[8] -1	0	0xf0400000 - 0xf0403fff (0x4000) MX[B]
	[9] -1	0	0xf0300000 - 0xf0303fff (0x4000) MX[B]
	[10] -1	0	0xf0600000 - 0xf0603fff (0x4000) MX[B]
	[11] -1	0	0xf0609400 - 0xf06094ff (0x100) MX[B]
	[12] -1	0	0xf0608000 - 0xf0608fff (0x1000) MX[B]
	[13] -1	0	0xf0607000 - 0xf0607fff (0x1000) MX[B]
	[14] -1	0	0xf0606000 - 0xf0606fff (0x1000) MX[B]
	[15] -1	0	0xf0605000 - 0xf0605fff (0x1000) MX[B]
	[16] -1	0	0xf0604000 - 0xf0604fff (0x1000) MX[B]
	[17] -1	0	0xf0609000 - 0xf06093ff (0x400) MX[B]
	[18] -1	0	0xf0200000 - 0xf020ffff (0x10000) MX[B](B)
	[19] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[26] -1	0	0x00008420 - 0x0000842f (0x10) IX[B]
	[27] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[32] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[33] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[34] -1	0	0x00008438 - 0x0000843f (0x8) IX[B]
	[35] -1	0	0x00008434 - 0x00008437 (0x4) IX[B]
	[36] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[37] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "on"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "TexturedVideo" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Mobility Radeon HD 2400 XT" (Chipset = 0x94c8)
(--) fglrx(0): (PciSubVendor = 0x1025, PciSubDevice = 0x0124)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xf0200000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 10.60
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: M74
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(WW) fglrx(0): Failed to open DRM connection
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SEC  Model: 4945  Serial#: 0
(II) fglrx(0): Year: 2007  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) fglrx(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) fglrx(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(II) fglrx(0):  SAMSUNG
(II) fglrx(0):  LTN154XA-L01
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff004ca3454900000000
(II) fglrx(0): 	00110103802115780a87f594574f8c27
(II) fglrx(0): 	27505400000001010101010101010101
(II) fglrx(0): 	010101010101ee1a0080502010301030
(II) fglrx(0): 	13004bcf100000190000000f00000000
(II) fglrx(0): 	00000000002387026401000000fe0053
(II) fglrx(0): 	414d53554e470a2020202020000000fe
(II) fglrx(0): 	004c544e31353458412d4c30310a0041
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 9 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x800 (pitch 0)
(**) fglrx(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   68.94  1280 1296 1344 1408  800 801 804 816 +hsync +vsync
(**) fglrx(0): *Mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   68.94  1024 1296 1344 1408  768 801 804 816 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   68.94  800 1296 1344 1408  600 801 804 816 +hsync +vsync
(**) fglrx(0): *Mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   68.94  640 1296 1344 1408  480 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   68.94  640 1296 1344 1408  400 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   68.94  512 1296 1344 1408  384 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"   68.94  400 1296 1344 1408  300 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "320x240": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"   68.94  320 1296 1344 1408  240 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "320x200": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"   68.94  320 1296 1344 1408  200 801 804 816 +hsync +vsync
(--) fglrx(0): Display dimensions: (330, 210) mm
(--) fglrx(0): DPI set to (98, 96)
(--) fglrx(0): Virtual size is 1280x800 (pitch 1280)
(**) fglrx(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   68.94  1280 1296 1344 1408  800 801 804 816 +hsync +vsync
(**) fglrx(0): *Mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   68.94  1024 1296 1344 1408  768 801 804 816 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   68.94  800 1296 1344 1408  600 801 804 816 +hsync +vsync
(**) fglrx(0): *Mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   68.94  640 1296 1344 1408  480 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   68.94  640 1296 1344 1408  400 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   68.94  512 1296 1344 1408  384 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"   68.94  400 1296 1344 1408  300 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "320x240": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"   68.94  320 1296 1344 1408  240 801 804 816 +hsync +vsync
(**) fglrx(0):  Default mode "320x200": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"   68.94  320 1296 1344 1408  200 801 804 816 +hsync +vsync
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) fglrx(0): HPV inactive
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.42.3
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf0200000 - 0xf020ffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xf0503000 - 0xf05037ff (0x800) MX[B]
	[7] -1	0	0xf0502000 - 0xf0502fff (0x1000) MX[B]
	[8] -1	0	0xf0501000 - 0xf0501fff (0x1000) MX[B]
	[9] -1	0	0xf0503800 - 0xf05038ff (0x100) MX[B]
	[10] -1	0	0xf0400000 - 0xf0403fff (0x4000) MX[B]
	[11] -1	0	0xf0300000 - 0xf0303fff (0x4000) MX[B]
	[12] -1	0	0xf0600000 - 0xf0603fff (0x4000) MX[B]
	[13] -1	0	0xf0609400 - 0xf06094ff (0x100) MX[B]
	[14] -1	0	0xf0608000 - 0xf0608fff (0x1000) MX[B]
	[15] -1	0	0xf0607000 - 0xf0607fff (0x1000) MX[B]
	[16] -1	0	0xf0606000 - 0xf0606fff (0x1000) MX[B]
	[17] -1	0	0xf0605000 - 0xf0605fff (0x1000) MX[B]
	[18] -1	0	0xf0604000 - 0xf0604fff (0x1000) MX[B]
	[19] -1	0	0xf0609000 - 0xf06093ff (0x400) MX[B]
	[20] -1	0	0xf0200000 - 0xf020ffff (0x10000) MX[B](B)
	[21] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[22] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[23] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[24] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[25] 0	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[28] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[29] -1	0	0x00008420 - 0x0000842f (0x10) IX[B]
	[30] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[31] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[32] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[35] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[36] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[37] -1	0	0x00008438 - 0x0000843f (0x8) IX[B]
	[38] -1	0	0x00008434 - 0x00008437 (0x4) IX[B]
	[39] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[40] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[41] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[42] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x10000000
(==) fglrx(0): Write-combining range (0xd0000000,0x10000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 7391
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Textured Video not supported without DRI enabled.
(WW) fglrx(0): Video Overlay not supported on AVIVO based graphics cards. For XVideo support use Option "TexturedVideo".
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 10
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Direct rendering disabled
(II) fglrx(0): Finished Initialize PPLIB!
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
```

Hell if I know what's wrong.

Thanks in advance for your help, Forlornity

---

### Post by Forlornity on 2007-11-01
Anyone got any idea?
It seems really beyond me.

thanks, Forlornity

---

