---
title: "Compiling ATI driver for Radeon 9000 with Hardy"
date: 2008-06-17
forum: Multimedia Software
---

### Post by barney_1 on 2008-06-17
Hi Folks,

I just upgraded my htpc to Hardy and as usual, this broke the ati driver.  I have had much success compiling my own driver ever since Dapper but can't seem to get this to work this time.

I have been using the gatos tv-out patch detailed here:
[http://megahurts.dk/rune/tv_output.html](http://megahurts.dk/rune/tv_output.html)

I did everything the same as before, patching and compiling version 6.6.3.  It seemed to install just fine but when I restart X the log looks as though my compiled driver is not being used.  Can anyone give me a shove in the right direction?  Thanks!

```
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
```
```
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.28.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video RAM=65536K, accessible=65536K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 65536 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 2048x1200
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 35000, min_in_pll: 40, max_in_pll: 3000, xclk: 20000, sclk: 200.000000, mclk: 250.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=35000; xclk=20000
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-0x60, DACType-1, TMDSType-1, ConnectorType-1
(II) RADEON(0): Port1: DDCType-0x64, DACType-2, TMDSType-1, ConnectorType-2
(II) RADEON(0): Port5: DDCType-0x0, DACType-2, TMDSType-0, ConnectorType-5
(II) RADEON(0): Output VGA-0 using monitor section Generic Monitor
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): DFP table revision: 3
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: NTSC
(II) RADEON(0): TV standards supported by chip: NTSC PAL 
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- 0x60
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- 0x64
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
finished output detect: 0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
finished output detect: 1
finished output detect: 2
(EE) RADEON(0): No connected devices found!
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(EE) RADEON(0): Using VGA default
in RADEONProbeOutputModes
(II) RADEON(0): Adding Screen mode: 800x600
(II) RADEON(0): Total number of valid Screen mode(s) added: 1
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Output VGA-0 using initial mode 1280x768
after xf86InitialConfiguration
(++) RADEON(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfd600000 - 0xfd60ffff (0x10000) MX[B]
	[1] 0	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfdb00000 - 0xfdb000ff (0x100) MX[B]
	[7] -1	0	0xfdd00000 - 0xfdd03fff (0x4000) MX[B]
	[8] -1	0	0xfda00000 - 0xfda007ff (0x800) MX[B]
	[9] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[10] -1	0	0xfd500000 - 0xfd51ffff (0x20000) MX[B](B)
	[11] -1	0	0xfd600000 - 0xfd60ffff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[17] 0	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[22] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[23] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[24] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[25] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[26] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[27] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[28] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[29] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[30] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[31] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[32] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[33] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[34] -1	0	0x0000c800 - 0x0000c87f (0x80) IX[B]
	[35] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit e0000000 0 0
(==) RADEON(0): Write-combining range (0xe0000000,0x4000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable montype: 1
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x04000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xe3ffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1728,8191)
(II) RADEON(0): Reserved area from (0,1200) to (1728,1202)
(II) RADEON(0): Largest offscreen area available: 1728 x 6989
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0x1023000
(II) RADEON(0): Will use depth buffer at offset 0x180c000
(II) RADEON(0): Will use 32768 kb for textures at offset 0x1ff5000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0xe0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(==) RADEON(0): Using AGP 4x
(II) RADEON(0): [agp] Mode 0x1f000207 [AGP 0x1106/0x3188; Card 0x1002/0x4966]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xf8000000
(II) RADEON(0): [agp] Ring mapped at 0xb7958000
(II) RADEON(0): [agp] ring read ptr handle = 0xf8101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb7957000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xf8102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xb3695000
(II) RADEON(0): [agp] GART texture map handle = 0xf8302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xb31b5000
(II) RADEON(0): [drm] register handle = 0xfd600000
(II) RADEON(0): [dri] Visual configs initialized
disable montype: 1
init memmap
init common
init crtc1
init pll1
freq: 80140000
best_freq: 80140909
best_feedback_div: 653
best_ref_div: 55
best_post_div: 4
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xe3ffe000 0x1fff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 1
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 17
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xe3ffe000 is: 0xe3ffe000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xf87ff800
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xe3ffe000 0xe3ffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xf87ff800
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
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
(II) RADEON(0): Acceleration enabled
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor 0 (scanline 1202)
(II) RADEON(0): Using hardware cursor 1 (scanline 1204)
(II) RADEON(0): Largest offscreen area available: 1728 x 6984
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(WW) RADEON(0): Option "MonitorLayout" is not used
(WW) RADEON(0): Option "TVOutput" is not used
(WW) RADEON(0): Option "XV_TVO_HPOS" is not used
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/r200_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 325 x 195
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
enable montype: 1
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
```

---

### Post by barney_1 on 2008-06-18
I'm making a bit of headway.

I reinstalled the Hardy ati driver and added this to the device section of my xorg.conf:
```
     Option "TVDACLoadDetect" "TRUE"
```
Now I get video from the TV so mission accomplished there. Unfortunately, trying to play a recording in mythtv crashes mythfrontend.

Any thoughts?

**moderators** Can you move this to the mythbuntu forum for me? Thanks!

---

### Post by barney_1 on 2008-06-18
Solved:

fglrx driver was installed for some reason.  Uninstall:

```
sudo apt-get uninstall xorg-driver-fglrx
```

---

