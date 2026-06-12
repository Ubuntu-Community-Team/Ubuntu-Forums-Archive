---
title: "Problem w/ Openchrome &amp; VN800 graphics"
date: 2006-12-02
forum: Multimedia &amp; Video
---

### Post by Sith_cz on 2006-12-02
Hi all.
I'm Gentoo user, but I have installed nice Kubuntu on my friends notebook so I'm requesting help here :).

NB configuration:
some UMAX stuff, chipset VN(M)800, Xorg 7.1, Openchrome drivers.

I compiled and installed Openchrome drivers without any problems ([https://help.ubuntu.com/community/UserDocumentation)](https://help.ubuntu.com/community/UserDocumentation)). But problem is when I want to start Xorg and KDM manager -> screen goes black. Otherwise KDM is normally loading even if display is black. Sounds are playing etc.


Here is IMO fully clear shortened :) Xorg log:
```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux pap-laptop 2.6.17-10-generic #2 SMP Fri Oct 13 
...........
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "via"
(II) Loading /usr/lib/xorg/modules/drivers/via_drv.so
(II) Module via: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) VIA: driver for VIA chipsets: CLE266, KM400/KN400, K8M800,
	PM800/PM880/CN400, VM800
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset VM800 found
(!!) VIA Technologies does not support or endorse this driver in any way.
(!!) For support, please refer to http://www.openchrome.org/ or
(!!) your X vendor.
(!!) (development build, at svn revision 236)
(II) resource ranges after xf86ClaimFixedResources() call:
...........
(II) Setting vga for screen 0.
(II) VIA(0): VIAPreInit
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) VIA(0): VIAGetRec
(**) VIA(0): Depth 24, (--) framebuffer bpp 32
(==) VIA(0): RGB weight 888
(==) VIA(0): Default visual is TrueColor
(**) VIA(0): Option "ActiveDevice" "LCD"
(II) VIA(0): Starting to parse config file options...
(==) VIA(0): ShadowFB is disabled.
(==) VIA(0): Acceleration is enabled.
(==) VIA(0): Using XAA acceleration architecture.
(==) VIA(0): Hardware two-color cursors.
	Software full color cursors.
(**) VIA(0): VideoRAM 0kB
(==) VIA(0): GPU virtual command queue will be enabled.
(==) VIA(0): DRI IRQ will be enabled if DRI is enabled.
(==) VIA(0): AGP DMA will be disabled if DRI is enabled.
(==) VIA(0): PCI DMA will be used for XV image transfer if DRI is enabled.
(==) VIA(0): Will not enable VBE modes.
(==) VIA(0): VBE VGA register save & restore will not be used
	if VBE modes are enabled.
(==) VIA(0): Xv Bandwidth check is enabled.
(==) VIA(0): Will not impose a limit on video-ram set aside for DRI.
(==) VIA(0): Will try to allocate 32768kB of AGP memory.
(==) VIA(0): Digital output bus width is 12 bits.
(==) VIA(0): DVI Center is disabled.
(==) VIA(0): Panel size is not selected from config file.
(==) VIA(0): Panel will not be forced.
(==) VIA(0): TV dotCrawl is disabled.
(==) VIA(0): TV deflicker is set to 0.
(==) VIA(0): No default TV type is set.
(==) VIA(0): No default TV output signal type is set.
(--) VIA(0): Chipset: "VM800"
(II) VIA(0): VIAMapMMIO
(--) VIA(0): mapping MMIO @ 0xf4000000 with size 0x9000
(--) VIA(0): mapping BitBlt MMIO @ 0xf4200000 with size 0x10000
(II) VIA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) VIA(0): Will not print VGA Registers.
(==) VIA(0): Will not scan I2C buses.
(==) VIA(0): Chipset Rev.: 0
(EE) VIA(0): Unknown Card-Ids (1558| 662); please report to openchrome-users@openchrome.org
(II) VIA(0): ...Finished parsing config file options.
(II) VIA(0): Detected MemClk 4
(II) VIA(0): ViaGetMemoryBandwidth
(II) VIA(0): Detected TV Standard: PAL.
(==) VIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) VIA(0): videoram =  65536k
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules/libi2c.so
(II) VIA(0): ViaI2CInit
(II) VIA(0): ViaI2CBus1Init
(II) VIA(0): I2C bus "I2C bus 1" initialized.
(II) VIA(0): ViaI2cBus2Init
(II) VIA(0): I2C bus "I2C bus 2" initialized.
(II) VIA(0): ViaI2CBus3Init
(II) VIA(0): I2C bus "I2C bus 3" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) VIA(0): I2C device "I2C bus 1:ddc2" registered at address 0xA0.
(II) VIA(0): I2C device "I2C bus 1:ddc2" removed.
(II) VIA(0): Manufacturer: BNQ  Model: 76c2  Serial#: 8269
(II) VIA(0): Year: 2005  Week: 47
(II) VIA(0): EDID Version: 1.3
(II) VIA(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) VIA(0): Sync:  Separate  Composite
(II) VIA(0): Max H-Image Size [cm]: horiz.: 43  vert.: 27
(II) VIA(0): Gamma: 2.20
(II) VIA(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) VIA(0): Default color space is primary color space
(II) VIA(0): First detailed timing is preferred mode
(II) VIA(0): redX: 0.640 redY: 0.332   greenX: 0.288 greenY: 0.601
(II) VIA(0): blueX: 0.146 blueY: 0.065   whiteX: 0.313 whiteY: 0.329
(II) VIA(0): Supported VESA Video Modes:
(II) VIA(0): 720x400@70Hz
(II) VIA(0): 640x480@60Hz
(II) VIA(0): 640x480@75Hz
(II) VIA(0): 800x600@60Hz
(II) VIA(0): 800x600@75Hz
(II) VIA(0): 832x624@75Hz
(II) VIA(0): 1024x768@60Hz
(II) VIA(0): 1024x768@70Hz
(II) VIA(0): 1024x768@75Hz
(II) VIA(0): 1280x1024@75Hz
(II) VIA(0): 1152x870@75Hz
(II) VIA(0): Manufacturer's mask: 0
(II) VIA(0): Supported Future Video Modes:
(II) VIA(0): #0: hsize: 800  vsize 600  refresh: 75  vid: 20293
(II) VIA(0): #1: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) VIA(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) VIA(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) VIA(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) VIA(0): #5: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) VIA(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) VIA(0): Supported additional Video Mode:
(II) VIA(0): clock: 146.2 MHz   Image Size:  433 x 271 mm
(II) VIA(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) VIA(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) VIA(0): Supported additional Video Mode:
(II) VIA(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
(II) VIA(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
(II) VIA(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
(II) VIA(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 84 kHz, PixClock max 170 MHz
(II) VIA(0): Monitor name: BenQ FP202W
(II) VIA(0): ViaOutputsDetect
(II) VIA(0): VIATVDetect
(II) VIA(0): ViaOutputsSelect
(II) VIA(0): ViaOutputsSelect: X Configuration: 0x02
(II) VIA(0): ViaOutputsSelect: BIOS Initialised register: 0x07
(WW) VIA(0): Unable to activate panel: no panel is present.
(II) VIA(0): ViaOutputsSelect: CRT.
(II) VIA(0): ViaModesAttach
(II) VIA(0): Generic Monitor: Using default hsync range of 30.00-84.00 kHz
(II) VIA(0): Generic Monitor: Using default vrefresh range of 56.00-76.00 Hz
(II) VIA(0): Clock range:  20.00 to 230.00 MHz
(II) VIA(0): ViaValidMode: Validating 640x350 (31500)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "640x350" (vrefresh out of range)
(II) VIA(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 640x400 (31500)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "640x400" (vrefresh out of range)
(II) VIA(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 720x400 (35500)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "720x400" (vrefresh out of range)
(II) VIA(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 640x480 (25200)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 640x480 (31500)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 640x480 (31500)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 640x480 (36000)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 800x600 (36000)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 800x600 (40000)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 800x600 (50000)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 800x600 (49500)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 800x600 (56300)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1024x768 (44900)
(II) VIA(0): Not using default mode "1024x768" (interlace mode not supported)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1024x768 (65000)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1024x768 (75000)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1024x768 (78800)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1024x768 (94500)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1152x864 (108000)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1280x960 (108000)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1280x960 (148500)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "1280x960" (hsync out of range)
(II) VIA(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1280x1024 (108000)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1280x1024 (135000)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1280x1024 (157500)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1600x1200 (162000)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1600x1200 (175500)
(II) VIA(0): ViaModePrimaryVGAValid
(WW) (1600x1200,Generic Monitor) mode clock 175.5MHz exceeds DDC maximum 170MHz
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1600x1200 (189000)
(II) VIA(0): ViaModePrimaryVGAValid
(WW) (1600x1200,Generic Monitor) mode clock 189MHz exceeds DDC maximum 170MHz
(II) VIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1600x1200 (202500)
(II) VIA(0): ViaModePrimaryVGAValid
(WW) (1600x1200,Generic Monitor) mode clock 202.5MHz exceeds DDC maximum 170MHz
(II) VIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1600x1200 (229500)
(II) VIA(0): ViaModePrimaryVGAValid
(WW) (1600x1200,Generic Monitor) mode clock 229.5MHz exceeds DDC maximum 170MHz
(II) VIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1792x1344 (204800)
(II) VIA(0): ViaModePrimaryVGAValid
(WW) (1792x1344,Generic Monitor) mode clock 204.8MHz exceeds DDC maximum 170MHz
(II) VIA(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1856x1392 (218300)
(II) VIA(0): ViaModePrimaryVGAValid
(WW) (1856x1392,Generic Monitor) mode clock 218.3MHz exceeds DDC maximum 170MHz
(II) VIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) VIA(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 832x624 (57284)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1280x768 (80140)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1280x800 (83460)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1152x768 (64995)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "1152x768" (vrefresh out of range)
(II) VIA(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1152x864 (121500)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1400x1050 (122000)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1400x1050 (151000)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1400x1050 (155800)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): CrtcHSyncEnd out of range.
(II) VIA(0): Not using default mode "1400x1050" (horizontal sync too wide)
(II) VIA(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1400x1050 (184000)
(II) VIA(0): ViaModePrimaryVGAValid
(WW) (1400x1050,Generic Monitor) mode clock 184MHz exceeds DDC maximum 170MHz
(II) VIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) VIA(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1440x900 (108840)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): CrtcHSyncEnd out of range.
(II) VIA(0): Not using default mode "1440x900" (horizontal sync too wide)
(II) VIA(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1600x1024 (106910)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1680x1050 (147140)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1920x1200 (193160)
(II) VIA(0): ViaModePrimaryVGAValid
(WW) (1920x1200,Generic Monitor) mode clock 193.16MHz exceeds DDC maximum 170MHz
(II) VIA(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1920x1200 (230000)
(II) VIA(0): ViaModePrimaryVGAValid
(WW) (1920x1200,Generic Monitor) mode clock 230MHz exceeds DDC maximum 170MHz
(II) VIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) VIA(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1280x800 (83460)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): ViaValidMode: Validating 800x600 (49500)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): ViaValidMode: Validating 640x480 (31500)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) VIA(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) VIA(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) VIA(0): Not using default mode "1280x960" (height too large for virtual size)
(II) VIA(0): Not using default mode "1152x864" (height too large for virtual size)
(II) VIA(0): ViaValidMode: Validating 1280x768 (80140)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): ViaValidMode: Validating 1024x768 (78800)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): ViaValidMode: Validating 1024x768 (75000)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): ViaValidMode: Validating 1024x768 (65000)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): ViaValidMode: Validating 832x624 (57284)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): ViaValidMode: Validating 800x600 (50000)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): ViaValidMode: Validating 800x600 (40000)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): ViaValidMode: Validating 800x600 (36000)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): ViaValidMode: Validating 640x480 (31500)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): ViaValidMode: Validating 640x480 (25200)
(II) VIA(0): ViaModePrimaryVGAValid
(--) VIA(0): Virtual size is 1280x800 (pitch 1280)
(**) VIA(0): *Default mode "1280x800": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 60.0 Hz
(II) VIA(0): Modeline "1280x800"   83.46  1280 1344 1480 1680  800 801 804 828
(**) VIA(0): *Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) VIA(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) VIA(0): *Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) VIA(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) VIA(0):  Default mode "1280x768": 80.1 MHz (scaled from 0.0 MHz), 47.7 kHz, 60.0 Hz
(II) VIA(0): Modeline "1280x768"   80.14  1280 1344 1480 1680  768 769 772 795
(**) VIA(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.1 Hz
(II) VIA(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) VIA(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz
(II) VIA(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) VIA(0):  Default mode "1024x768": 65.0 MHz (scaled from -0.0 MHz), 48.4 kHz, 60.0 Hz
(II) VIA(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) VIA(0):  Default mode "832x624": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.6 Hz
(II) VIA(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) VIA(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz
(II) VIA(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) VIA(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
(II) VIA(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) VIA(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
(II) VIA(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) VIA(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.8 Hz
(II) VIA(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) VIA(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) VIA(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(--) VIA(0): Display dimensions: (430, 270) mm
(--) VIA(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) VIA(0): VIAUnmapMem
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
.......
(II) VIA(0): VIAScreenInit
(II) VIA(0): VIAMapFB
(--) VIA(0): mapping framebuffer @ 0xf0000000 with size 0x4000000
(==) VIA(0): Write-combining range (0xf0000000,0x4000000)
(--) VIA(0): Frame buffer start: 0xb3a8d000, free start: 0x3e8000 end: 0x4000000
(II) VIA(0): VIAMapMMIO
(--) VIA(0): mapping MMIO @ 0xf4000000 with size 0x9000
(--) VIA(0): mapping BitBlt MMIO @ 0xf4200000 with size 0x10000
(II) VIA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) VIA(0): VIASave
(II) VIA(0): Primary
(II) VIA(0): TVSave...
(II) VIA(0): VIAWriteMode
(II) VIA(0): ViaModePrimary
(II) VIA(0): ViaModePrimaryVGA
(II) VIA(0): ViaModePrimaryVGA: Setting up 1280x800
(II) VIA(0): CrtcHTotal: 0x690
(II) VIA(0): CrtcHDisplay: 0x500
(II) VIA(0): CrtcHBlankStart: 0x500
(II) VIA(0): CrtcHBlankEnd: 0x690
(II) VIA(0): CrtcHSyncStart: 0x540
(II) VIA(0): CrtcHSyncEnd: 0x5C8
(II) VIA(0): CrtcVTotal: 0x33C
(II) VIA(0): CrtcVDisplay: 0x320
(II) VIA(0): CrtcVSyncStart: 0x321
(II) VIA(0): CrtcVSyncEnd: 0x324
(II) VIA(0): CrtcVBlankStart: 0x320
(II) VIA(0): CrtcVBlankEnd: 0x33C
(II) VIA(0): Offset: 0x280
(II) VIA(0): Fetch Count: 0x280
(II) VIA(0): ViaTVPower: Off.
(II) VIA(0): ViaSetPrimaryFIFO
(II) VIA(0): ViaSetPrimaryDotclock to 0x448801
(II) VIA(0): ViaSetUseExternalClock
(II) VIA(0): 3D Engine has been initialized.
(II) VIA(0): VIAAdjustFrame
(II) VIA(0): VIAAdjustFrame
(II) VIA(0): - Blanked
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) VIA(0): [drm] loaded kernel module for "via" driver
(II) VIA(0): [drm] DRM interface version 1.3
(II) VIA(0): [drm] created "via" driver at busid "PCI:1:0:0"
(II) VIA(0): [drm] added 8192 byte SAREA at 0xdcc53000
(II) VIA(0): [drm] mapped SAREA 0xdcc53000 to 0xb3a8b000
(II) VIA(0): [drm] framebuffer handle = 0xf0000000
(II) VIA(0): [drm] added 1 reserved context for kernel
(II) VIA(0): [dri] visual configs initialized.
(II) VIA(0): [drm] register handle = 0xf4000000
(II) VIA(0): [drm] framebuffer handle = 0xf0000000
(II) VIA(0): [drm] mmio Registers = 0xf4000000
(II) VIA(0): [dri] mmio mapped.
(II) VIA(0): - Visuals set up
(II) VIA(0): VIAInternalScreenInit
(II) VIA(0): - B & W
(II) VIA(0): Using 2400 lines for offscreen memory.
(II) VIA(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	8x8 color pattern filled rectangles
	Solid Lines
	Dashed Lines
	Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		17 256x256 slots
		5 512x512 slots
		32 8x8 color pattern slots
(==) VIA(0): Backing store disabled
(II) VIA(0): - Backing store set up
(II) VIA(0): - SW cursor set up
(II) VIA(0): VIAHWCursorInit
(II) VIA(0): - Def Color map set up
(II) VIA(0): VIALoadPalette
(II) VIA(0): - Palette loaded
(II) VIA(0): - DPMS set up
(II) VIA(0): - Color maps etc. set up
(II) VIA(0): [drm] Detected AGP vendor 0x1106, device 0x314
(II) VIA(0): [drm] Found AGP v3 compatible device. Trying AGP 8X mode.
(II) VIA(0): [drm] Trying to enable AGP fast writes.
(II) VIA(0): [drm] drmAgpEnabled succeeded
(II) VIA(0): [drm] agpAddr = 0xe0000000
(II) VIA(0): [drm] agpBase = (nil)
(II) VIA(0): [drm] agpAddr = 0xe0000000
(II) VIA(0): [drm] agpSize = 0x02000000
(II) VIA(0): [drm] agp physical addr = 0x00000000
(II) VIA(0): [dri] use agp.
(II) VIA(0): [drm] Using 50448352 bytes for DRM memory heap.
(II) VIA(0): [dri] frame buffer initialized.
(II) VIA(0): X context handle = 0x1
(II) VIA(0): [drm] installed DRM signal handler
(II) VIA(0): [DRI] installation complete
(II) VIA(0): [dri] kernel data initialized.
(II) VIA(0): [drm] Irq handler installed, using IRQ 177.
(II) VIA(0): direct rendering enabled
(II) VIA(0): [Xv] Using PCI DMA for Xv image transfer.
Fulfilled via DRI at 16389120
(II) VIA(0): Benchmarking video copy. Less is better.
(--) VIA(0): Timed   libc YUV420 copy... 8832012. Throughput: 107.2 MiB/s.
(--) VIA(0): Timed kernel YUV420 copy... 8823276. Throughput: 107.3 MiB/s.
(--) VIA(0): Timed    SSE YUV420 copy... 8814684. Throughput: 107.4 MiB/s.
(--) VIA(0): Timed    MMX YUV420 copy... 8775084. Throughput: 107.9 MiB/s.
(--) VIA(0): Ditch 3DNow! YUV420 copy... Not supported by CPU.
(--) VIA(0): Timed   MMX2 YUV420 copy... 8824500. Throughput: 107.3 MiB/s.
Freed 16389120 (pool 2)
(--) VIA(0): Using MMX YUV42X copy for video.
(II) VIA(0): [XvMC] Registering viaXvMC.
(II) VIA(0): [XvMC] Initialized XvMC extension.
(II) VIA(0): - Done
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
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
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(WW) AIGLX: 3D driver claims to not support visual 0x22
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
(II) AIGLX: Loaded and initialized /usr/lib/dri/unichrome_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
error opening security policy file /usr/lib/xserver/SecurityPolicy
..........
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) VIA(0): VIALeaveVT
(II) VIA(0): ViaCursorStore
(II) VIA(0): VIARestore
(II) VIA(0): ViaDisablePrimaryFIFO

```

xorg.conf
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	ModulePath "/usr/lib/xorg/modules/drivers"
	ModulePath "/usr/local/lib/xorg/modules/drivers"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"glx"
	Load	"extmod"
	Load	"freetype"
	Load	"dri"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"cz"
	Option		"XkbOptions"	"lv3:ralt_switch"
	Option		"XkbVariant"	"qwerty"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"via"
	Option	"ActiveDevice"	"LCD"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x800" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "800x600" "640x480"
		ViewPort	0 0
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0777
EndSection

```

Vesa drivers sucks. Need 3D acc. :(
Thanks in advance..

---

### Post by Sith_cz on 2006-12-05
Nobody knows where may be problem?

---

### Post by Amodef on 2007-01-10
Same problem for me, with gdm instead of kdm...

---

### Post by Sith_cz on 2007-01-11
Yep. Unfortunately I haven't resolved problem too.. Maybe this chipset is just unusable for Linux. These crappy chipsets are just for surfing in IE under Windows..

---

### Post by Amodef on 2007-01-11
Do you have the 2D acceleration ? Or do you have, as me, the scroll that is jerked ?

Perhaps that we should post on the openchrome mailing-list...

---

### Post by Sith_cz on 2007-01-12
2D acc? I think this stuff is computed by CPU, because scrolling is yerked (never heard this before :o) ) - as you say.. 
Anyway unfortunately I don't have notebook there. So I can't make any tests..

---

### Post by Amodef on 2007-01-22
Yup !

Same problem for me : as it's my girlfriend's laptop, I can't keep it all the time ^^ .

For now, I have downgraded her laptop to Dapper (the Vesa driver are not so buggy there, and scrolling is faster/smoother).

However, since an upgrade last week, her Wifi card isn't working anymore (the system is freezing after 2secs to 5minutes, no CTRL+ALT+F1 is possible -_-).

I've asked her to download OpenSuse to see if it works or not (at least the Wifi) until Feisty is there (I was unable to install the Feisty Herd 2 by any way, as the boot up crashed).

If it doesn't work on OpenSuse (the video drivers I mean), I'll invite you in my future discussion on the Openchrome mailing-list :) .

---

### Post by 3x3cut0r on 2007-01-29
Hi, I've got similar problem with my Umax VisionBook 2500 with its VN800 chipset. I tried to install OpenChrome drivers, but right after start of kdm, it freezes.
I've got also problems with installing a lot of distributions...OpenSuse 10.2, Kubuntu Edgy & Feisty....I now run on Kubuntu Dapper, because I can't upgrade to Edgy or Feisty, it always freezes :(

---

