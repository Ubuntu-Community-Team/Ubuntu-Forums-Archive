---
title: "lspci reports wrong video ram size"
date: 2010-06-11
forum: Multimedia Software
---

### Post by rlarrowe on 2010-06-11
Hello,

   I am running ubuntu 10.04 with the fglrx driver installed with apt-get.  I have an ATI Radeon HD AGP with 512MB of video ram.  My bios window size is 64MB.  The Xorg.0.log file shows that 512MB is recognized.  I also tried checking the /proc/mtrr file and it shows two values one I believe is my ram size which looks to be correct at 1.5GB the other is 512MB which I think is my video ram size, but when I do an lspci -v the video ram size shows 256MB.  I am trying to run Doom 3 and it only allows me to use 256MB of memory.

Thank you,

Ryan

Sorry they aren't attachments I couldn't get it to work.


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux Merlin 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=b72f83f8-a868-4098-9d87-2a082f698167 ro quiet splash
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun 11 21:47:04 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
    Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 1002:9598:1002:9598 ATI Technologies Inc Mobility Radeon HD 3600 Series rev 0, Mem @ 0xe0000000/268435456, 0xdf000000/65536, I/O @ 0x0000d800/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
    compiled for 7.5.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.7.1, module version = 8.72.11
    Module class: X.Org Video Driver
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.7.1, module version = 8.72.11
(II) ATI Proprietary Linux Driver Version Identifier:8.72.11
(II) ATI Proprietary Linux Driver Release Identifier: 8.723.1                              
(II) ATI Proprietary Linux Driver Build Date: Apr  8 2010 21:40:29
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for fglrx
(II) Loading PCS database from /etc/ati/amdpcsdb
(--) Assigning device section with no busID to primary device
(--) Chipset Supported AMD Graphics Processor (0x9598) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) fglrx(0): pEnt->device->identifier=0x8341b80
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) fglrx(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB 
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 11, (OK)
ukiOpenByBusid: ukiOpenMinor returns 11
ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
(--) fglrx(0): Chipset: "ATI Radeon HD 3600 Series" (Chipset = 0x9598)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x9598)
(==) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
(--) fglrx(0): MMIO registers at 0xdf000000
(--) fglrx(0): I/O port at 0x0000d800
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): AC Adapter is used
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 10.88
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV635
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(--) fglrx(0): Video RAM: 524288 kByte, Type: DDR2
(II) fglrx(0): AGP card detected
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) fglrx(0): Using adapter: 1:0.0.
(II) fglrx(0): [FB] MC range(MCFBBase = 0xd0000000, MCFBSize = 0x20000000)
(II) fglrx(0): [pci] find AGP GART
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board.(cmd=0x1f000314)
(II) fglrx(0): [agp] graphics chipset has AGP v2.0
(II) fglrx(0): Interrupt handler installed at IRQ 11.
(II) fglrx(0): RandR 1.2 support is enabled!
(II) fglrx(0): RandR 1.2 rotation support is enabled!
(==) fglrx(0): Center Mode is disabled 
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): Finished Initialize PPLIB!
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): Connected Display0: DFP on secondary TMDS [tmds2i]
(II) fglrx(0): Display0 EDID data ---------------------------
(II) fglrx(0): Manufacturer: HSD  Model: 15c6  Serial#: 2490
(II) fglrx(0): Year: 2009  Week: 14
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): DFP 1.x compatible TMDS
(II) fglrx(0): Max Image Size [cm]: horiz.: 38  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.641 redY: 0.337   greenX: 0.304 greenY: 0.620
(II) fglrx(0): blueX: 0.141 blueY: 0.073   whiteX: 0.313 whiteY: 0.326
(II) fglrx(0): Supported established timings:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x864@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported standard timings:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Serial No: 914GR3JY02490
(II) fglrx(0): Ranges: V min: 50 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: HX191D
(II) fglrx(0): EDID (in hex):
(II) fglrx(0):     00ffffffffffff002264c615ba090000
(II) fglrx(0):     0e13010381261e782a1f36a4564d9e24
(II) fglrx(0):     125053bfef808180714f814001010101
(II) fglrx(0):     010101010101302a009851002a403070
(II) fglrx(0):     1300782d1100001e000000ff00393134
(II) fglrx(0):     4752334a593032343930000000fd0032
(II) fglrx(0):     4c1e530e000a202020202020000000fc
(II) fglrx(0):     004858313931440a2020202020200041
(II) fglrx(0): End of Display0 EDID data --------------------
(II) fglrx(0): Output DFP1 has no monitor section
(II) fglrx(0): Output DFP2 has no monitor section
(II) fglrx(0): Output CRT1 has no monitor section
(II) fglrx(0): Output CRT2 has no monitor section
(II) fglrx(0): Output TV has no monitor section
(II) fglrx(0): Output COMPONENT_VIDEO has no monitor section
(II) fglrx(0): Output DFP1 disconnected
(II) fglrx(0): Output DFP2 connected
(II) fglrx(0): Output CRT1 disconnected
(II) fglrx(0): Output CRT2 disconnected
(II) fglrx(0): Output TV disconnected
(II) fglrx(0): Output COMPONENT_VIDEO disconnected
(II) fglrx(0): Using exact sizes for initial modes
(II) fglrx(0): Output DFP2 using initial mode 1280x1024
(II) fglrx(0): DPI set to (96, 96)
(II) fglrx(0): Adapter ATI Radeon HD 3600 Series has 2 configurable heads and 1 displays connected.
(==) fglrx(0): QBS disabled
(==) fglrx(0):  PseudoColor visuals disabled
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): NoDRI = NO
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing swlDriScreenInit
(II) fglrx(0): swlDriScreenInit for fglrx driver
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 17, (OK)
ukiOpenByBusid: ukiOpenMinor returns 17
ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
(II) fglrx(0): [uki] DRM interface version 1.0
(II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [uki] mapped SAREA 0x2000 to 0xb7677000
(II) fglrx(0): [uki] framebuffer handle = 0x3000
(II) fglrx(0): [uki] added 1 reserved context for kernel
(II) fglrx(0): swlDriScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.72.11
(II) fglrx(0):     Date: Apr  8 2010
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.32-22-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [uki] register handle = 0x00004000
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xd0000000 FBMappedSize: 0x01004000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,3280)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1280) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 2000
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(==) fglrx(0): DPMS enabled
(II) fglrx(0): Initialized in-driver Xinerama extension
(**) fglrx(0): Textured Video is enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
(II) Module glesx: vendor="X.Org Foundation"
    compiled for 1.7.1, module version = 1.0.0
(II) Loading extension GLESX
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.1
    ABI class: X.Org Video Driver, version 6.0
(II) fglrx(0): GLESX enableFlags = 94
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    Solid Horizontal and Vertical Lines
    Driver provided ScreenToScreenBitBlt replacement
    Driver provided FillSolidRects replacement
(II) fglrx(0): GLESX is enabled
(II) LoadModule: "amdxmm"
(II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
    compiled for 1.7.1, module version = 1.0.0
(II) Loading extension AMDXVOPL
(II) fglrx(0): UVD2 feature is available
(II) fglrx(0): Enable composite support successfully
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using HW cursor of display infrastructure!
(II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
(II) fglrx(0): Cannot get TV Format. Set all TV geometry value to zero!
(II) fglrx(0): Cannot set TV horizontal size.
(II) fglrx(0): Cannot get TV Format for trying to adjust horizontal position after horizontal size changed. 
(II) fglrx(0): Cannot set TV horizontal position.
(II) fglrx(0): Cannot set TV vertical position.
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
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 18, (OK)
ukiOpenByBusid: ukiOpenMinor returns 18
ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) fglrx(0): Enable the clock gating!
(II) fglrx(0): Setting screen physical size to 338 x 270
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
(**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found 12 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Configuring as mouse
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(II) Logitech USB Receiver: initialized for relative axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HID 0a5c:4502 (/dev/input/event7)
(**) HID 0a5c:4502: Applying InputClass "evdev keyboard catchall"
(**) HID 0a5c:4502: always reports core events
(**) HID 0a5c:4502: Device: "/dev/input/event7"
(II) HID 0a5c:4502: Found keys
(II) HID 0a5c:4502: Configuring as keyboard
(II) XINPUT: Adding extended input device "HID 0a5c:4502" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HID 0a5c:4503 (/dev/input/event8)
(**) HID 0a5c:4503: Applying InputClass "evdev pointer catchall"
(**) HID 0a5c:4503: always reports core events
(**) HID 0a5c:4503: Device: "/dev/input/event8"
(II) HID 0a5c:4503: Found 3 mouse buttons
(II) HID 0a5c:4503: Found relative axes
(II) HID 0a5c:4503: Found x and y relative axes
(II) HID 0a5c:4503: Configuring as mouse
(**) HID 0a5c:4503: YAxisMapping: buttons 4 and 5
(**) HID 0a5c:4503: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "HID 0a5c:4503" (type: MOUSE)
(II) HID 0a5c:4503: initialized for relative axes.
(II) config/udev: Adding input device HID 0a5c:4503 (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech WingMan Cordless Gamepad (/dev/input/event9)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech WingMan Cordless Gamepad (/dev/input/js2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech Logitech Dual Action (/dev/input/event6)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech Logitech Dual Action (/dev/input/js1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech Inc. WingMan Extreme Digital 3D (/dev/input/event5)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech Inc. WingMan Extreme Digital 3D (/dev/input/js0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
(II) fglrx(0): Hot-plug event occurs on device: 1:0:0 
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) fglrx(0): Cannot get updated TV attributes.

reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back
reg01: base=0x040000000 ( 1024MB), size=  512MB, count=1: write-back

00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8043
    Flags: bus master, fast devsel, latency 0
    Memory at f8000000 (32-bit, prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
    Flags: bus master, 66MHz, fast devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: df000000-dfefffff
    Prefetchable memory behind bridge: dff00000-f7ffffff
    Kernel modules: shpchp

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
    I/O behind bridge: 0000a000-0000bfff
    Memory behind bridge: dd000000-deffffff
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02) (prog-if 80 [Master])
    Subsystem: ASUSTeK Computer Inc. Device 8043
    Flags: bus master, medium devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at 9800 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8043
    Flags: bus master, medium devsel, latency 0, IRQ 9
    I/O ports at 9400 [size=32]
    Kernel driver in use: uhci_hcd

00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8043
    Flags: medium devsel, IRQ 10
    I/O ports at e800 [size=16]
    Kernel modules: i2c-i801

00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8043
    Flags: bus master, medium devsel, latency 0, IRQ 9
    I/O ports at 9000 [size=32]
    Kernel driver in use: uhci_hcd

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3600 Series
    Subsystem: ATI Technologies Inc Mobility Radeon HD 3600 Series
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at d800 [size=256]
    Memory at df000000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at dffe0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

02:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
    Subsystem: Creative Labs Device 8061
    Flags: bus master, medium devsel, latency 32, IRQ 11
    I/O ports at b800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: EMU10K1_Audigy
    Kernel modules: snd-emu10k1

02:07.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
    Subsystem: Creative Labs Device 0020
    Flags: bus master, medium devsel, latency 32
    I/O ports at b400 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: Emu10k1_gameport
    Kernel modules: emu10k1-gp

02:09.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01) (prog-if 02)
    Subsystem: 3Com Corp, Modem Division Device 00a2
    Flags: medium devsel, IRQ 10
    I/O ports at b000 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: serial

02:0a.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
    Subsystem: D-Link System Inc Device 1301
    Flags: bus master, medium devsel, latency 32, IRQ 11
    I/O ports at a800 [size=256]
    Memory at de800000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: 8139too

02:0b.0 USB Controller: NEC Corporation USB (rev 43) (prog-if 10)
    Subsystem: NEC Corporation USB
    Flags: bus master, medium devsel, latency 32, IRQ 9
    Memory at de000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

02:0b.1 USB Controller: NEC Corporation USB (rev 43) (prog-if 10)
    Subsystem: NEC Corporation USB
    Flags: bus master, medium devsel, latency 32, IRQ 11
    Memory at dd800000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

02:0b.2 USB Controller: NEC Corporation USB 2.0 (rev 04) (prog-if 20)
    Subsystem: NEC Corporation USB 2.0
    Flags: bus master, medium devsel, latency 32, IRQ 10
    Memory at dd000000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

---

### Post by wilee-nilee on 2010-06-11
If you could edit that list in code tags your more likely to get some sort of answer.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by CylnZ on 2010-06-12
I get the same sort of thing, i have an Nvidia 8800M GTS with 512 RAM

```
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 8800M GTS] (rev a2)
    Subsystem: Gateway 2000 Device 0690
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at cc000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at 2000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb
```

Apparently lspci thinks i have 256 RAM.

---

