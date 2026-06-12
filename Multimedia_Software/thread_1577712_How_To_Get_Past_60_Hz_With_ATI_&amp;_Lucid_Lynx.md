---
title: "How To Get Past 60 Hz With ATI &amp; Lucid Lynx?"
date: 2010-09-19
forum: Multimedia Software
---

### Post by Alaksandu on 2010-09-19
Hello Forum,

I broke my xorg.conf once already and then searched for help, but to no avail so now I turn to you for help.

I've recently built a half-new computer and installed Lucid Lynx on it.

I managed to get everything else working and even got the ATI drivers installed. However, I can't get above 60 Hz on my old CRT monitor - the ATI driver controls have 60 as the highest selectable refresh rate. The preferred 1152x864 screenmode works fine otherwise.

Here are the known specifications:
Monitor horizontal refresh: 30-86 kHz
Monitor vertical refresh: 50-150 Hz
Known working display mode on earlier graphics card: 1152x864, 85 Hz.

My motherboard (with integrated graphics) is the Asus M4A88TD-V EVO/USB3 AMD 880G AM3. The GPU is Radeon HD 4250.

The ATI drivers seem to have "taken over" the xorg.conf, so I don't know where to input any values. Any suggestions on how I can get to 85 Hz are appreciated. 

Thank you in advance for any help.

---

### Post by Yellow Pasque on 2010-09-19
Posting your xorg.conf and /var/log/Xorg.0.log could be helpful.

---

### Post by Alaksandu on 2010-09-19
xorg.conf below.

I think I already tried to change the TargetRefresh to 85, but it had no effect (didn't even break anything!)
---
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1152x864"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-CRT1" "0-CRT1"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
---

---

### Post by Alaksandu on 2010-09-19
Xorg.0.conf below, if it fits within whatever post limits.

```
---

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux [Computer name redacted] 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=40a2241c-8a9b-4d02-8e56-c50229cfa11d ro quiet splash
Build Date: 21 July 2010  12:47:34PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Sep 19 13:19:04 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "amdcccle Layout"
(**) |-->Screen "amdcccle-Screen[1]-0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "amdcccle-Device[1]-0"
(==) No monitor specified for screen "amdcccle-Screen[1]-0".
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

(--) PCI:*(0:1:5:0) 1002:9715:1043:843e ATI Technologies Inc rev 0, Mem @ 0xd0000000/268435456, 0xfe8f0000/65536, 0xfe700000/1048576, I/O @ 0x0000c000/256
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
(II) Primary Device is: PCI 01@00:05:0
(WW) Falling back to old probe method for fglrx
(II) Loading PCS database from /etc/ati/amdpcsdb
(--) Chipset Supported AMD Graphics Processor (0x9715) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:5:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) fglrx(0): pEnt->device->identifier=0x960e170
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.1.0
	ABI class: X.Org Video Driver, version 6.0
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
ukiOpenByBusid: Searching for BusID PCI:1:5:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 11, (OK)
ukiOpenByBusid: ukiOpenMinor returns 11
ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
(--) fglrx(0): Chipset: "ATI Radeon HD 4250" (Chipset = 0x9715)
(--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x843e)
(==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfe8f0000
(--) fglrx(0): I/O port at 0x0000c000
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
(II) fglrx(0): VESA VBE OEM Software Rev: 10.94
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RS880
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(II) fglrx(0): UMA/SP interleave mode is enabled in the BIOS
(--) fglrx(0): Video RAM: 393216 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Using adapter: 1:5.0.
(II) fglrx(0): [FB] MC range(MCFBBase = 0xc0000000, MCFBSize = 0x18000000)
(II) fglrx(0): Interrupt handler installed at IRQ 30.
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
(II) fglrx(0): Connected Display0: CRT on primary DAC [crt1]
(II) fglrx(0):  Display0: Failed to get EDID information. 
(II) fglrx(0): Output DFP2 has no monitor section
(II) fglrx(0): Output CRT1 using monitor section 0-CRT1
(**) fglrx(0): Option "PreferredMode" "1152x864"
(**) fglrx(0): Option "Position" "0 0"
(**) fglrx(0): Option "Disable" "false"
(**) fglrx(0): Option "Rotate" "normal"
(**) fglrx(0): Option "TargetRefresh" "60"
(II) fglrx(0): Output DFP2 disconnected
(II) fglrx(0): Output CRT1 connected
(II) fglrx(0): Using user preference for initial modes
(II) fglrx(0): Output CRT1 using initial mode 1152x864
(II) fglrx(0): DPI set to (96, 96)
(II) fglrx(0): Adapter ATI Radeon HD 4250 has 2 configurable heads and 1 displays connected.
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
ukiOpenByBusid: Searching for BusID PCI:1:5:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 17, (OK)
ukiOpenByBusid: ukiOpenMinor returns 17
ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
(II) fglrx(0): [uki] DRM interface version 1.0
(II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [uki] mapped SAREA 0x2000 to 0xb76fa000
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
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.32-24-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [uki] register handle = 0x00004000
(II) fglrx(0): Display width adjusted to to 1664 due to alignment constraints
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xd6f53000 FBMappedSize: 0x010a8000
(II) fglrx(0): Reserved 0x04900000 bytes of sideport memory for power saving
(II) fglrx(0): FBMM initialized for area (0,0)-(1664,2624)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1664,1664) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1664 x 960
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
(II) fglrx(0): User Preference Output CRT1 using refresh rate 60.0 Hz.
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
ukiOpenByBusid: Searching for BusID PCI:1:5:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 18, (OK)
ukiOpenByBusid: ukiOpenMinor returns 18
ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) fglrx(0): Enable the clock gating!
(II) fglrx(0): Setting screen physical size to 304 x 228
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
(**) Option "xkb_layout" "fi"
(**) Option "xkb_variant" "classic"
(II) XKB: reuse xkmfile /var/lib/xkb/server-B810939095C0CD61AC8DAFD928C515F55FF5BF36.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "fi"
(**) Option "xkb_variant" "classic"
(II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event4)
(**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) Logitech USB-PS/2 Optical Mouse: always reports core events
(**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event4"
(II) Logitech USB-PS/2 Optical Mouse: Found 8 mouse buttons
(II) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
(II) Logitech USB-PS/2 Optical Mouse: Found relative axes
(II) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
(II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
(**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
(II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse1)
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
(**) Option "xkb_layout" "fi"
(**) Option "xkb_variant" "classic"
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
```

---

### Post by Alaksandu on 2010-09-21
It's a too hard problem, I guess. Of course, if someone happens to come up with a solution or suggestion it's still welcome...

If not, I'll just try to hack together some solution myself. The worst case scenario is that I'll have to buy a cheap GFX card with better driver support to get my screen working properly...

---

### Post by Yellow Pasque on 2010-09-21
> Option "TargetRefresh" "60"
Did you add this or did aticonfig do it?

---

### Post by Alaksandu on 2010-09-22
> **Temüjin said:**
> Did you add this or did aticonfig do it?

That was added by aticonfig. I haven't figured out any modifications that work, so it's all either the default settings or Ati's settings.

---

### Post by realzippy on 2010-09-22
Try this modified xorg.conf:

```
Section "ServerLayout"
Identifier "amdcccle Layout"
Screen 0 "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
Load "glx"
EndSection

Section "Monitor"
Identifier "0-CRT1"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
HorizSync       30.0 - 86.0             # added values for your monitor
VertRefresh     50.0 - 150.0
Option "DPMS" "true"
Option "PreferredMode" "1152x864"
#Option "TargetRefresh" "60"           # disabled
Option "Position" "0 0"
Option "Rotate" "normal"
Option "Disable" "false"
EndSection

Section "Device"
Identifier "Default Device"
Driver "fglrx"
EndSection

Section "Device"
Identifier "amdcccle-Device[1]-0"
Driver "fglrx"
Option "Monitor-CRT1" "0-CRT1"
BusID "PCI:1:5:0"
EndSection

Section "Screen"
Identifier "Default Screen"
DefaultDepth 24
EndSection

Section "Screen"
Identifier "amdcccle-Screen[1]-0"
Device "amdcccle-Device[1]-0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection
```

---

### Post by Alaksandu on 2010-09-24
[QUOTE=realzippy;9875102]Try this modified xorg.conf:

Thank you for the suggestion. Unfortunately that had no effect, there's still only 60Hz available.

I tried enabling the TargetRefresh option and feeding it various values too, but that unfortunately had no effect.

I'm at a loss with what to do next. I read the xorg.conf man page and noticed there was an option for specifying screen modes manually. That's very manual though, and I doubt I will be able to do it anytime soon.

---

### Post by realzippy on 2010-09-25
Sorry,I did not notice that there are 2 (!?) "device" and "Screen" sections in the xorg.conf.....must have been tired.Can you try this version:

```
Section "ServerLayout"
Identifier "amdcccle Layout"
Screen 0 "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
Load "glx"
EndSection

Section "Monitor"
Identifier "0-CRT1"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
HorizSync       30.0 - 86.0             # added values for your monitor
VertRefresh     50.0 - 150.0
Option "DPMS" "true"
Option "PreferredMode" "1152x864"
#Option "TargetRefresh" "60"           # disabled
Option "Position" "0 0"
Option "Rotate" "normal"
Option "Disable" "false"
EndSection

Section "Device"
Identifier "amdcccle-Device[1]-0"
Driver "fglrx"
Option "Monitor-CRT1" "0-CRT1"
BusID "PCI:1:5:0"
EndSection

Section "Screen"
Identifier "amdcccle-Screen[1]-0"
Device "amdcccle-Device[1]-0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection
```

please post the actual Xorg.log again...

---

### Post by Alaksandu on 2010-09-26
> **realzippy said:**
> Sorry,I did not notice that there are 2 (!?) "device" and "Screen" sections in the xorg.conf.....must have been tired.Can you try this version:
[...]
please post the actual Xorg.log again...

It boots, but unfortunately there is still no change.

Here's the current Xorg.0.log:
```


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux [Name] 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=40a2241c-8a9b-4d02-8e56-c50229cfa11d ro quiet splash
Build Date: 21 July 2010  12:47:34PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Sep 26 14:49:21 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "amdcccle Layout"
(**) |-->Screen "amdcccle-Screen[1]-0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "amdcccle-Device[1]-0"
(==) No monitor specified for screen "amdcccle-Screen[1]-0".
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

(--) PCI:*(0:1:5:0) 1002:9715:1043:843e ATI Technologies Inc rev 0, Mem @ 0xd0000000/268435456, 0xfe8f0000/65536, 0xfe700000/1048576, I/O @ 0x0000c000/256
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
(II) Primary Device is: PCI 01@00:05:0
(WW) Falling back to old probe method for fglrx
(II) Loading PCS database from /etc/ati/amdpcsdb
(--) Chipset Supported AMD Graphics Processor (0x9715) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:5:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) fglrx(0): pEnt->device->identifier=0x97b6f10
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.1.0
	ABI class: X.Org Video Driver, version 6.0
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
ukiOpenByBusid: Searching for BusID PCI:1:5:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 11, (OK)
ukiOpenByBusid: ukiOpenMinor returns 11
ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
(--) fglrx(0): Chipset: "ATI Radeon HD 4250" (Chipset = 0x9715)
(--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x843e)
(==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfe8f0000
(--) fglrx(0): I/O port at 0x0000c000
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
(II) fglrx(0): VESA VBE OEM Software Rev: 10.94
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RS880
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(II) fglrx(0): UMA/SP interleave mode is enabled in the BIOS
(--) fglrx(0): Video RAM: 393216 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Using adapter: 1:5.0.
(II) fglrx(0): [FB] MC range(MCFBBase = 0xc0000000, MCFBSize = 0x18000000)
(II) fglrx(0): Interrupt handler installed at IRQ 30.
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
(II) fglrx(0): Connected Display0: CRT on primary DAC [crt1]
(II) fglrx(0):  Display0: Failed to get EDID information. 
(II) fglrx(0): Output DFP2 has no monitor section
(II) fglrx(0): Output CRT1 using monitor section 0-CRT1
(**) fglrx(0): Option "PreferredMode" "1152x864"
(**) fglrx(0): Option "Position" "0 0"
(**) fglrx(0): Option "Disable" "false"
(**) fglrx(0): Option "Rotate" "normal"
(II) fglrx(0): Output DFP2 disconnected
(II) fglrx(0): Output CRT1 connected
(II) fglrx(0): Using user preference for initial modes
(II) fglrx(0): Output CRT1 using initial mode 1152x864
(II) fglrx(0): DPI set to (96, 96)
(II) fglrx(0): Adapter ATI Radeon HD 4250 has 2 configurable heads and 1 displays connected.
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
ukiOpenByBusid: Searching for BusID PCI:1:5:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 17, (OK)
ukiOpenByBusid: ukiOpenMinor returns 17
ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
(II) fglrx(0): [uki] DRM interface version 1.0
(II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [uki] mapped SAREA 0x2000 to 0xb7893000
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
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.32-24-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [uki] register handle = 0x00004000
(II) fglrx(0): Display width adjusted to to 1664 due to alignment constraints
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xd6f53000 FBMappedSize: 0x010a8000
(II) fglrx(0): Reserved 0x04900000 bytes of sideport memory for power saving
(II) fglrx(0): FBMM initialized for area (0,0)-(1664,2624)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1664,1664) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1664 x 960
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
ukiOpenByBusid: Searching for BusID PCI:1:5:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 18, (OK)
ukiOpenByBusid: ukiOpenMinor returns 18
ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) fglrx(0): Enable the clock gating!
(II) fglrx(0): Setting screen physical size to 304 x 228
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
(**) Option "xkb_layout" "fi"
(**) Option "xkb_variant" "classic"
(II) XKB: reuse xkmfile /var/lib/xkb/server-B810939095C0CD61AC8DAFD928C515F55FF5BF36.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "fi"
(**) Option "xkb_variant" "classic"
(II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event4)
(**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) Logitech USB-PS/2 Optical Mouse: always reports core events
(**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event4"
(II) Logitech USB-PS/2 Optical Mouse: Found 8 mouse buttons
(II) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
(II) Logitech USB-PS/2 Optical Mouse: Found relative axes
(II) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
(II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
(**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
(II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse1)
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
(**) Option "xkb_layout" "fi"
(**) Option "xkb_variant" "classic"
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

```

---

### Post by realzippy on 2010-09-26
Do you have this file:
/etc/ati/amdpcsdb   ??
-----------------------------
Have you ever tested if xrandr is working with specified refresh rate?

---

### Post by realzippy on 2010-09-26
...made another change to xorg.conf;specified a modeline;test it please..

```
Section "ServerLayout"
Identifier "amdcccle Layout"
Screen 0 "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
Load "glx"
EndSection

Section "Monitor"
Identifier "0-CRT1"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
HorizSync       30.0 - 86.0             # added values for your monitor
VertRefresh     50.0 - 150.0
Option "DPMS" "true"
Modeline "1152x864_75.00"  104.99  1152 1224 1352 1552  864 865 868 902  -HSync +Vsync
#Option "PreferredMode" "1152x864"
#Option "TargetRefresh" "60"           # disabled
Option "Position" "0 0"
Option "Rotate" "normal"
Option "Disable" "false"
EndSection

Section "Device"
Identifier "amdcccle-Device[1]-0"
Driver "fglrx"
Option "Monitor-CRT1" "0-CRT1"
BusID "PCI:1:5:0"
EndSection

Section "Screen"
Identifier "amdcccle-Screen[1]-0"
Device "amdcccle-Device[1]-0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
Modes    "1152x864@75"
EndSubSection
EndSection
```

---

### Post by Alaksandu on 2010-09-26
> **realzippy said:**
> Do you have this file:
/etc/ati/amdpcsdb   ??
-----------------------------
Have you ever tested if xrandr is working with specified refresh rate?



I have the amdpcsdb file, pasted it below for good measure.

Below that is the output of xrandr -q --verbose, which I'm guessing is what you're looking for (never used the program before)


```

AMDPCSDBV1
[AMDPCSROOT/SYSTEM/MCIL]
DALLinuxSupport=V1
DALRULE_POWERPLAYDISREGARDDISPLAY=V1
DALNonStandardModesBCD=R140010500000006017921344000000601800144000000060185613920000006016001200000000601280076800000060144009000000006012800960000000601680105000000060
GCORULE_FlickerWA=V1
GCORULE_LCDValidatePixelClkOnly=V1
DisableMMSnifferCode=V0
DALRULE_GetTVFakeEDID=V1
DALRULE_REGISTRYACCESS=V1
DALRULE_GETLCDFAKEEDID=V0
R6LCD_RETURNALLBIOSMODES=V1
TVEnableOverscan=V1
DALRULE_NOFORCEBOOT=V1
DALRULE_DYNAMICMODESUPPORT=V1
DALRULE_ADDNATIVEMODESTOMODETABLE=V1
DALRULE_ALLOWMONITORRANGELIMITMODESCRT=V0
GXOM5XDisableLaneSwitch=V1
Gxo50HzTimingSupport=V1
DALRULE_RESTRICTDISPLAYSBASEDONPANELRES=V0
DFP_AddHDTVPixelFormats=V3
Gxo24HzTimingSupport=V1
PXACAutoSwitch=V0
PXDCAutoSwitch=V0
UvdEnabled=V1
LoadBalancing_DEF=V0
PP_RS780DisableUVDBranchClkGating=V1
[AMDPCSROOT/SYSTEM/DDX]
OGLFMTA2R10G10B10Enable=V1
DisableLoadBalancing=V1
DisablePassiveStereo=V0
RequestMSI=STRUE
[AMDPCSROOT/SYSTEM/DDX/RECENTMODE]
EnableRestore=V1
[AMDPCSROOT/SYSTEM/LDC]
ReleaseVersion=S8.723.1-100408a-098580C-ATI
ColorPreviewDlgState=V0
HelpDisabled=V0
DP_MSG_FLAG=V0
WarningDlgDisabled=V0
LastSelectedDevice=S296:38677:4098:33854:4163|0
RebootTimeStamp=S0110/08/18 21:49:18
LastViewedPage=SWelcome
[AMDPCSROOT/SYSTEM/2ID-1002-9581-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-9583-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-9591-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-9593-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-9504-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-9506-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-9508-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-9509-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-94A3-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-9552-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-9553-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-9555-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-9480-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-9488-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-94A0-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-944A-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-94A1-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-945A-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-9491-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-68E0-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-68C1-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-68E1-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-68C0-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-68A1-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-68A0-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-94C9-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-94C8-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-95C4-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-95C2-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-94CB-0/MCIL]
DALNonStandardModesBCD1=R0800048000000060102406000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-9615-0/MCIL]
DALNonStandardModesBCD1=R1024076800000000128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9616-0/MCIL]
DALNonStandardModesBCD1=R1024076800000000128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9611-0/MCIL]
DALNonStandardModesBCD1=R1024076800000000128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9610-0/MCIL]
DALNonStandardModesBCD1=R1024076800000000128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9710-0/MCIL]
DALNonStandardModesBCD1=R10240768000000001280076800000000128009600000000013600768000000601360076800000070136607680000006013660768000000701600120000000070
DALNonStandardModesBCD2=R179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9715-0/MCIL]
DALNonStandardModesBCD1=R10240768000000001280076800000000128009600000000013600768000000601360076800000070136607680000006013660768000000701600120000000070
DALNonStandardModesBCD2=R179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9614-0/MCIL]
DALNonStandardModesBCD1=R1024076800000000128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9613-0/MCIL]
DALNonStandardModesBCD1=R08000480000000601024060000000060128006000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-9612-0/MCIL]
DALNonStandardModesBCD1=R08000480000000601024060000000060128006000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-9713-0/MCIL]
DALNonStandardModesBCD1=R08000480000000601024060000000060128006000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-9712-0/MCIL]
DALNonStandardModesBCD1=R08000480000000601024060000000060128006000000006012800768000000601400105000000060
[AMDPCSROOT/SYSTEM/2ID-1002-940F-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-940B-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-940A-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-958D-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-958C-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9511-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9403-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9400-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9589-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9587-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9588-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9586-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9598-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9596-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9507-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9505-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9515-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9501-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9519-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-94C7-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-94CC-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-94C3-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-94C4-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-94C1-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-95C5-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-95C6-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-95C9-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-95C0-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-94C6-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-95CF-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-95CE-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-95CD-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9450-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-954F-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9540-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9490-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9498-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9495-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-944E-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-94B4-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-94B3-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-94B5-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9442-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9440-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-944C-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9460-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9462-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9443-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9441-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-68F9-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-68D9-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-68D8-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-68B8-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-68BE-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-6898-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-6899-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-689C-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9452-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9557-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-949F-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-949E-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-949C-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9456-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-9444-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-6888-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-68C8-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-6889-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-68A9-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-68C9-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/2ID-1002-68F1-0/MCIL]
DALNonStandardModesBCD1=R128007680000000012800960000000001600120000000070179213440000000018001440000000001856139200000000
[AMDPCSROOT/SYSTEM/BUSID-1:5:0-0/MCIL]
DALLastConnected=V0
DALR6 CRT_MaxModeInfo=R0000000040060000B0040000000000003C000000
DAL_ACEspectReady=V0
AsicOnLowPower=V0
DALLastSelected=V1
DALLastTypes=V129
DALObjectData0=R010000000100000000000000010000000100000000000000010000000100000000000000010000000100000000000000010000000200000000000000010000000200000000000000030000000200000001000000030000000200000001000000010000000100000000000000010000000100000000000000010000000100000000000000000000000000000000000000010000000200000000000000000000000000000000000000010000000200000000000000020000000000000001000000
DALSelectObjectData0=R010000000100000000000000010000000100000000000000010000000100000000000000010000000100000000000000010000000200000000000000010000000200000000000000030000000200000001000000030000000200000001000000010000000100000000000000010000000100000000000000010000000100000000000000000000000000000000000000010000000200000000000000000000000000000000000000010000000200000000000000020000000000000001000000
DALCurrentObjectData=R010000000100000000000000000000000000000000000000
DPBBufferID=V0
DALInstallFlag=V1
DAL_CRTColorTemperatureSource00000000=R0200000064190000
DALR6 CRT=R0000000000000000000000006400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000100000000000000000000000000000000000000640000006419000000000000000000000000000000000000000000000000000000000000
DALR6 CRT1600x1200x0x60=R000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
DALR6 CRT1152x864x0x60=R000000000000000000000000000000000000000000000000010000000000000000000000000000000000000000000000
GDOADJR6 CRT=R000000000000000000000000000000000000000000000000000000000000000000000000000000000200000002000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
DALOvlYUVBrightness=R0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
DALOvlYUVContrast=R6400000064000000640000006400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
DALOvlYUVSaturation=R6400000064000000640000006400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
DALOvlYUVHue=R0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
DALOvlYUVGamma=R0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
DALOvlYUVOvlKelvin=R64190000
DALR6 CRT640x480x0x60=R000000000000000000000000000000000000000000000000010000000100000000000000000000000000000000000000
[AMDPCSROOT/SYSTEM/BUSID-1:5:0-0/DDX]
GammaCorrection0=V104960100
[AMDPCSROOT/SYSTEM/BUSID-1:5:0-0/LDC]
GammaChannelSelState=V0
[AMDPCSROOT/SYSTEM/BUSID-1:5:0-0/OpenGL]
AntiAliasSamples=V0
AAF=V0
[AMDPCSROOT/SYSTEM/LibXUtil/Display1]
Map=V1
Enable=V1

```
```

Screen 0: minimum 320 x 200, current 1152 x 864, maximum 1600 x 1600
DFP2 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x89
	Timestamp:  21747
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	SignalFormat:	TMDS
	ConnectorType:	DVI-D
CRT1 connected 1152x864+0+0 (0x8b) normal (normal left inverted right x axis y axis) 0mm x 0mm
	Identifier: 0x8a
	Timestamp:  21747
	Subpixel:   unknown
	Clones:    
	CRTC:       0
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	SignalFormat:	VGA
	ConnectorType:	VGA
  1152x864 (0x8b)   81.6MHz +HSync -VSync *current +preferred
        h: width  1152 start 1216 end 1336 total 1520 skew    0 clock   53.7KHz
        v: height  864 start  865 end  868 total  895           clock   60.0Hz
  1600x1200 (0x8c)  162.0MHz -HSync -VSync +preferred
        h: width  1600 start 1664 end 1856 total 2160 skew    0 clock   75.0KHz
        v: height 1200 start 1201 end 1204 total 1250           clock   60.0Hz
  1400x1050 (0x8d)  121.8MHz +HSync -VSync
        h: width  1400 start 1488 end 1632 total 1864 skew    0 clock   65.3KHz
        v: height 1050 start 1053 end 1057 total 1089           clock   60.0Hz
  1280x1024 (0x8e)  108.0MHz -HSync -VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1440x900 (0x8f)  106.5MHz +HSync -VSync
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock   55.9KHz
        v: height  900 start  903 end  909 total  934           clock   59.9Hz
  1280x960 (0x90)  108.0MHz -HSync -VSync
        h: width  1280 start 1376 end 1488 total 1800 skew    0 clock   60.0KHz
        v: height  960 start  961 end  964 total 1000           clock   60.0Hz
  1366x768 (0x91)   85.8MHz +HSync -VSync
        h: width  1366 start 1438 end 1582 total 1800 skew    0 clock   47.6KHz
        v: height  768 start  769 end  772 total  795           clock   59.9Hz
  1360x768 (0x92)   85.5MHz -HSync -VSync
        h: width  1360 start 1424 end 1536 total 1792 skew    0 clock   47.7KHz
        v: height  768 start  771 end  777 total  795           clock   60.0Hz
  1280x800 (0x93)   83.5MHz +HSync -VSync
        h: width  1280 start 1344 end 1480 total 1680 skew    0 clock   49.7KHz
        v: height  800 start  801 end  804 total  828           clock   60.0Hz
  1280x768 (0x94)   79.5MHz +HSync -VSync
        h: width  1280 start 1344 end 1472 total 1664 skew    0 clock   47.8KHz
        v: height  768 start  771 end  778 total  798           clock   59.9Hz
  1280x768 (0x95)   73.9MHz +HSync -VSync
        h: width  1280 start 1336 end 1472 total 1664 skew    0 clock   44.4KHz
        v: height  768 start  769 end  772 total  793           clock   56.0Hz
  1280x720 (0x96)   74.2MHz -HSync -VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock   45.0KHz
        v: height  720 start  725 end  730 total  750           clock   60.0Hz
  1280x720 (0x97)   60.5MHz +HSync -VSync
        h: width  1280 start 1328 end 1456 total 1632 skew    0 clock   37.0KHz
        v: height  720 start  721 end  724 total  741           clock   50.0Hz
  1024x768 (0x98)   65.0MHz +HSync +VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x99)   40.0MHz -HSync -VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x9a)   36.0MHz -HSync -VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  720x480 (0x9b)   26.7MHz +HSync -VSync
        h: width   720 start  736 end  808 total  896 skew    0 clock   29.8KHz
        v: height  480 start  481 end  484 total  497           clock   60.0Hz
  640x480 (0x9c)   25.2MHz +HSync +VSync
        h: width   640 start  648 end  744 total  800 skew    0 clock   31.5KHz
        v: height  480 start  482 end  484 total  525           clock   60.0Hz

```

---

### Post by realzippy on 2010-09-26
See post #13 and test the file please.

If no luck,try to delete the /etc/ati/amdpcsdb
(means rename it for backup) and reboot (or restart X).

If no luck,try to set the mode:
"1152x864_75.00"  104.99  1152 1224 1352 1552  864 865 868 902  -HSync +Vsync
with [xrandr]("http://www.x.org/archive/X11R7.5/doc/man/man1/xrandr.1.html")
Ask for help with xrandr if needed..see [also]("https://wiki.edubuntu.org/X/Config/Resolution")

Edit:
```
xrandr --newmode "1152x864_75.00" 104.99 1152 1224 1352 1552 864 865 868 902 -HSync +Vsync
xrandr --addmode CRT1 "1152x864_75.00"
xrandr --output CRT1 --mode 1152x864_75.00
#or (?)
xrandr --output CRT1 --mode 1152x864 --rate 75
```

---

### Post by Alaksandu on 2010-09-26
Sorry about the post confusion, I guess we were logged on and posting at the same time.

Your new xorg.conf with the "hard-coded" display mode gave me a 75Hz option in the Ati menu which demonstrably works, thank you!

This means I have one remaining question: is it trivial to modify the display mode to work at 85Hz? That's my old native mode and known to work on my monitor.

---

### Post by Yellow Pasque on 2010-09-26
You can generate that modeline with cvt:
```
cvt -v 1152 864 85Hz
```

---

### Post by Alaksandu on 2010-09-26
Thank you very much realzippy and Temüjin! I'm now running on glorious 85 Hz, and it appears to be both persistent across boots *and* playing well with the Ati drivers!

I was willing to read man pages and did, but since I didn't know even the names of the relevant programs I would never have figured it out myself. Thank you for saving me from buying/switching hardware because of a software issue!

---

