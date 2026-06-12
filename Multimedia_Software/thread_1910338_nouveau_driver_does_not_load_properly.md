---
title: "nouveau driver does not load properly"
date: 2012-01-16
forum: Multimedia Software
---

### Post by xzased on 2012-01-16
Hi all. I have a dell latitude e6520 laptop, the gpu is GF108 (Quadro NVS 4200M). I'm running Oneiric. For some reason the nouveau driver is not loading correctly. From the xorg logs, it seems the vesa driver is taking over, the maximum resolution is set at 1024x768 (the monitor's default is 1360x768). Here is my xorg log:

```
[    22.568]
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    22.732] X Protocol Version 11, Revision 0
[    22.732] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    22.732] Current Operating System: Linux xzased-latitude 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64
[    22.732] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=5c261e65-2a80-4fbc-bcff-49e3570702e0 ro quiet splash vt.handoff=7
[    22.732] Build Date: 19 October 2011  05:21:26AM
[    22.732] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support)
[    22.732] Current version of pixman: 0.22.2
[    22.732] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    22.732] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.732] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan 16 21:03:54 2012
[    22.765] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.765] (==) No Layout section.  Using the first Screen section.
[    22.765] (==) No screen section available. Using defaults.
[    22.765] (**) |-->Screen "Default Screen Section" (0)
[    22.765] (**) |   |-->Monitor "<default monitor>"
[    22.765] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    22.765] (==) Automatically adding devices
[    22.765] (==) Automatically enabling devices
[    22.765] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.765] 	Entry deleted from font path.
[    22.765] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    22.765] 	Entry deleted from font path.
[    22.765] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    22.765] 	Entry deleted from font path.
[    22.765] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    22.765] 	Entry deleted from font path.
[    22.765] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    22.765] 	Entry deleted from font path.
[    22.765] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    22.765] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.765] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    22.765] (II) Loader magic: 0x7e0220
[    22.765] (II) Module ABI versions:
[    22.765] 	X.Org ANSI C Emulation: 0.4
[    22.765] 	X.Org Video Driver: 10.0
[    22.765] 	X.Org XInput driver : 12.3
[    22.765] 	X.Org Server Extension : 5.0
[    22.766] (--) PCI:*(0:1:0:0) 10de:1056:1028:0494 rev 161, Mem @ 0xe4000000/16777216, 0xd0000000/268435456, 0xe0000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/524288
[    22.766] (II) Open ACPI successful (/var/run/acpid.socket)
[    22.766] (II) LoadModule: "extmod"
[    22.766] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    22.766] (II) Module extmod: vendor="X.Org Foundation"
[    22.766] 	compiled for 1.10.4, module version = 1.0.0
[    22.766] 	Module class: X.Org Server Extension
[    22.766] 	ABI class: X.Org Server Extension, version 5.0
[    22.766] (II) Loading extension MIT-SCREEN-SAVER
[    22.766] (II) Loading extension XFree86-VidModeExtension
[    22.766] (II) Loading extension XFree86-DGA
[    22.766] (II) Loading extension DPMS
[    22.766] (II) Loading extension XVideo
[    22.766] (II) Loading extension XVideo-MotionCompensation
[    22.766] (II) Loading extension X-Resource
[    22.766] (II) LoadModule: "dbe"
[    22.766] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    22.766] (II) Module dbe: vendor="X.Org Foundation"
[    22.766] 	compiled for 1.10.4, module version = 1.0.0
[    22.766] 	Module class: X.Org Server Extension
[    22.766] 	ABI class: X.Org Server Extension, version 5.0
[    22.766] (II) Loading extension DOUBLE-BUFFER
[    22.766] (II) LoadModule: "glx"
[    22.766] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    22.987] (II) Module glx: vendor="X.Org Foundation"
[    22.987] 	compiled for 1.10.4, module version = 1.0.0
[    22.987] 	ABI class: X.Org Server Extension, version 5.0
[    22.987] (==) AIGLX enabled
[    22.987] (II) Loading extension GLX
[    22.987] (II) LoadModule: "record"
[    22.987] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    22.987] (II) Module record: vendor="X.Org Foundation"
[    22.987] 	compiled for 1.10.4, module version = 1.13.0
[    22.987] 	Module class: X.Org Server Extension
[    22.987] 	ABI class: X.Org Server Extension, version 5.0
[    22.987] (II) Loading extension RECORD
[    22.987] (II) LoadModule: "dri"
[    22.987] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    22.987] (II) Module dri: vendor="X.Org Foundation"
[    22.987] 	compiled for 1.10.4, module version = 1.0.0
[    22.987] 	ABI class: X.Org Server Extension, version 5.0
[    22.987] (II) Loading extension XFree86-DRI
[    22.987] (II) LoadModule: "dri2"
[    22.988] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.988] (II) Module dri2: vendor="X.Org Foundation"
[    22.988] 	compiled for 1.10.4, module version = 1.2.0
[    22.988] 	ABI class: X.Org Server Extension, version 5.0
[    22.988] (II) Loading extension DRI2
[    22.988] (==) Matched nvidia as autoconfigured driver 0
[    22.988] (==) Matched nouveau as autoconfigured driver 1
[    22.988] (==) Matched nv as autoconfigured driver 2
[    22.988] (==) Matched vesa as autoconfigured driver 3
[    22.988] (==) Matched fbdev as autoconfigured driver 4
[    22.988] (==) Assigned the driver to the xf86ConfigLayout
[    22.988] (II) LoadModule: "nvidia"
[    23.016] (WW) Warning, couldn't open module nvidia
[    23.016] (II) UnloadModule: "nvidia"
[    23.016] (II) Unloading nvidia
[    23.016] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    23.016] (II) LoadModule: "nouveau"
[    23.016] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    23.127] (II) Module nouveau: vendor="X.Org Foundation"
[    23.127] 	compiled for 1.10.1, module version = 0.0.16
[    23.127] 	Module class: X.Org Video Driver
[    23.127] 	ABI class: X.Org Video Driver, version 10.0
[    23.127] (II) LoadModule: "nv"
[    23.127] (WW) Warning, couldn't open module nv
[    23.127] (II) UnloadModule: "nv"
[    23.127] (II) Unloading nv
[    23.127] (EE) Failed to load module "nv" (module does not exist, 0)
[    23.127] (II) LoadModule: "vesa"
[    23.128] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    23.424] (II) Module vesa: vendor="X.Org Foundation"
[    23.424] 	compiled for 1.10.2, module version = 2.3.0
[    23.424] 	Module class: X.Org Video Driver
[    23.424] 	ABI class: X.Org Video Driver, version 10.0
[    23.424] (II) LoadModule: "fbdev"
[    23.424] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    23.490] (II) Module fbdev: vendor="X.Org Foundation"
[    23.490] 	compiled for 1.10.0, module version = 0.4.2
[    23.490] 	ABI class: X.Org Video Driver, version 10.0
[    23.490] (II) NOUVEAU driver Date:   Thu Mar 24 02:13:12 2011 +1000
[    23.490] (II) NOUVEAU driver for NVIDIA chipset families :
[    23.490] 	RIVA TNT        (NV04)
[    23.490] 	RIVA TNT2       (NV05)
[    23.490] 	GeForce 256     (NV10)
[    23.490] 	GeForce 2       (NV11, NV15)
[    23.490] 	GeForce 4MX     (NV17, NV18)
[    23.490] 	GeForce 3       (NV20)
[    23.490] 	GeForce 4Ti     (NV25, NV28)
[    23.490] 	GeForce FX      (NV3x)
[    23.490] 	GeForce 6       (NV4x)
[    23.490] 	GeForce 7       (G7x)
[    23.490] 	GeForce 8       (G8x)
[    23.490] 	GeForce GTX 200 (NVA0)
[    23.490] 	GeForce GTX 400 (NVC0)
[    23.490] (II) VESA: driver for VESA chipsets: vesa
[    23.490] (II) FBDEV: driver for framebuffer: fbdev
[    23.490] (++) using VT number 7

[    23.490] drmOpenDevice: node name is /dev/dri/card0
[    23.495] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    23.495] drmOpenDevice: node name is /dev/dri/card0
[    23.499] drmOpenByBusid: drmOpenMinor returns -1
[    23.499] drmOpenDevice: node name is /dev/dri/card1
[    23.503] drmOpenByBusid: drmOpenMinor returns -1
[    23.503] drmOpenDevice: node name is /dev/dri/card2
[    23.507] drmOpenByBusid: drmOpenMinor returns -1
[    23.507] drmOpenDevice: node name is /dev/dri/card3
[    23.512] drmOpenByBusid: drmOpenMinor returns -1
[    23.512] drmOpenDevice: node name is /dev/dri/card4
[    23.516] drmOpenByBusid: drmOpenMinor returns -1
[    23.516] drmOpenDevice: node name is /dev/dri/card5
[    23.520] drmOpenByBusid: drmOpenMinor returns -1
[    23.520] drmOpenDevice: node name is /dev/dri/card6
[    23.524] drmOpenByBusid: drmOpenMinor returns -1
[    23.524] drmOpenDevice: node name is /dev/dri/card7
[    23.528] drmOpenByBusid: drmOpenMinor returns -1
[    23.528] drmOpenDevice: node name is /dev/dri/card8
[    23.532] drmOpenByBusid: drmOpenMinor returns -1
[    23.532] drmOpenDevice: node name is /dev/dri/card9
[    23.536] drmOpenByBusid: drmOpenMinor returns -1
[    23.536] drmOpenDevice: node name is /dev/dri/card10
[    23.540] drmOpenByBusid: drmOpenMinor returns -1
[    23.540] drmOpenDevice: node name is /dev/dri/card11
[    23.544] drmOpenByBusid: drmOpenMinor returns -1
[    23.544] drmOpenDevice: node name is /dev/dri/card12
[    23.548] drmOpenByBusid: drmOpenMinor returns -1
[    23.548] drmOpenDevice: node name is /dev/dri/card13
[    23.552] drmOpenByBusid: drmOpenMinor returns -1
[    23.552] drmOpenDevice: node name is /dev/dri/card14
[    23.556] drmOpenByBusid: drmOpenMinor returns -1
[    23.556] drmOpenDevice: node name is /dev/dri/card15
[    23.560] drmOpenByBusid: drmOpenMinor returns -1
[    23.560] drmOpenDevice: node name is /dev/dri/card0
[    23.565] drmOpenDevice: node name is /dev/dri/card0
[    23.569] drmOpenDevice: node name is /dev/dri/card1
[    23.573] drmOpenDevice: node name is /dev/dri/card2
[    23.577] drmOpenDevice: node name is /dev/dri/card3
[    23.581] drmOpenDevice: node name is /dev/dri/card4
[    23.585] drmOpenDevice: node name is /dev/dri/card5
[    23.589] drmOpenDevice: node name is /dev/dri/card6
[    23.593] drmOpenDevice: node name is /dev/dri/card7
[    23.597] drmOpenDevice: node name is /dev/dri/card8
[    23.601] drmOpenDevice: node name is /dev/dri/card9
[    23.606] drmOpenDevice: node name is /dev/dri/card10
[    23.640] drmOpenDevice: node name is /dev/dri/card11
[    23.644] drmOpenDevice: node name is /dev/dri/card12
[    23.649] drmOpenDevice: node name is /dev/dri/card13
[    23.653] drmOpenDevice: node name is /dev/dri/card14
[    23.657] drmOpenDevice: node name is /dev/dri/card15
[    23.661] (EE) [drm] failed to open device
[    23.661] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    23.661] (WW) Falling back to old probe method for fbdev
[    23.661] (II) Loading sub module "fbdevhw"
[    23.661] (II) LoadModule: "fbdevhw"
[    23.661] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    23.968] (II) Module fbdevhw: vendor="X.Org Foundation"
[    23.968] 	compiled for 1.10.4, module version = 0.0.2
[    23.968] 	ABI class: X.Org Video Driver, version 10.0
[    23.968] (II) Loading sub module "vbe"
[    23.968] (II) LoadModule: "vbe"
[    23.968] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    24.059] (II) Module vbe: vendor="X.Org Foundation"
[    24.059] 	compiled for 1.10.4, module version = 1.1.0
[    24.059] 	ABI class: X.Org Video Driver, version 10.0
[    24.059] (II) Loading sub module "int10"
[    24.059] (II) LoadModule: "int10"
[    24.059] (II) Loading /usr/lib/xorg/modules/libint10.so
[    24.090] (II) Module int10: vendor="X.Org Foundation"
[    24.090] 	compiled for 1.10.4, module version = 1.0.0
[    24.090] 	ABI class: X.Org Video Driver, version 10.0
[    24.090] (II) VESA(0): initializing int10
[    24.090] (II) VESA(0): Bad V_BIOS checksum
[    24.090] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    24.138] (II) VESA(0): VESA BIOS detected
[    24.138] (II) VESA(0): VESA VBE Version 3.0
[    24.138] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[    24.138] (II) VESA(0): VESA VBE OEM: NVIDIA
[    24.138] (II) VESA(0): VESA VBE OEM Software Rev: 117.25
[    24.138] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    24.138] (II) VESA(0): VESA VBE OEM Product: nVIDIA N12P-NS2  - mcln0561
[    24.138] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev
[    24.218] (II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    24.218] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    24.218] (==) VESA(0): RGB weight 888
[    24.218] (==) VESA(0): Default visual is TrueColor
[    24.218] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    24.218] (II) Loading sub module "ddc"
[    24.218] (II) LoadModule: "ddc"
[    24.218] (II) Module "ddc" already built-in
[    24.221] (II) VESA(0): VESA VBE DDC supported
[    24.221] (II) VESA(0): VESA VBE DDC Level none
[    24.221] (II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
[    24.378] (II) VESA(0): VESA VBE DDC read failed
[    24.378] (II) VESA(0): VESA VBE PanelID read failed
[    24.378] (II) VESA(0): Searching for matching VESA mode(s):
[    24.379] Mode: 100 (640x400)
[    24.379] 	ModeAttributes: 0x3bf
[    24.379] 	WinAAttributes: 0x7
[    24.379] 	WinBAttributes: 0x0
[    24.379] 	WinGranularity: 64
[    24.379] 	WinSize: 64
[    24.379] 	WinASegment: 0xa000
[    24.379] 	WinBSegment: 0x0
[    24.379] 	WinFuncPtr: 0xc000825b
[    24.379] 	BytesPerScanline: 640
[    24.379] 	XResolution: 640
[    24.379] 	YResolution: 400
[    24.379] 	XCharSize: 8
[    24.379] 	YCharSize: 16
[    24.379] 	NumberOfPlanes: 1
[    24.379] 	BitsPerPixel: 8
[    24.379] 	NumberOfBanks: 1
[    24.379] 	MemoryModel: 4
[    24.379] 	BankSize: 0
[    24.379] 	NumberOfImages: 14
[    24.379] 	RedMaskSize: 0
[    24.379] 	RedFieldPosition: 0
[    24.379] 	GreenMaskSize: 0
[    24.379] 	GreenFieldPosition: 0
[    24.379] 	BlueMaskSize: 0
[    24.379] 	BlueFieldPosition: 0
[    24.379] 	RsvdMaskSize: 0
[    24.379] 	RsvdFieldPosition: 0
[    24.379] 	DirectColorModeInfo: 0
[    24.379] 	PhysBasePtr: 0xe1000000
[    24.379] 	LinBytesPerScanLine: 640
[    24.379] 	BnkNumberOfImagePages: 14
[    24.379] 	LinNumberOfImagePages: 14
[    24.379] 	LinRedMaskSize: 0
[    24.379] 	LinRedFieldPosition: 0
[    24.379] 	LinGreenMaskSize: 0
[    24.379] 	LinGreenFieldPosition: 0
[    24.379] 	LinBlueMaskSize: 0
[    24.379] 	LinBlueFieldPosition: 0
[    24.379] 	LinRsvdMaskSize: 0
[    24.379] 	LinRsvdFieldPosition: 0
[    24.379] 	MaxPixelClock: 229500000
[    24.381] Mode: 101 (640x480)
[    24.381] 	ModeAttributes: 0x3bf
[    24.381] 	WinAAttributes: 0x7
[    24.381] 	WinBAttributes: 0x0
[    24.381] 	WinGranularity: 64
[    24.381] 	WinSize: 64
[    24.381] 	WinASegment: 0xa000
[    24.381] 	WinBSegment: 0x0
[    24.381] 	WinFuncPtr: 0xc000825b
[    24.381] 	BytesPerScanline: 640
[    24.381] 	XResolution: 640
[    24.381] 	YResolution: 480
[    24.381] 	XCharSize: 8
[    24.381] 	YCharSize: 16
[    24.381] 	NumberOfPlanes: 1
[    24.381] 	BitsPerPixel: 8
[    24.381] 	NumberOfBanks: 1
[    24.381] 	MemoryModel: 4
[    24.381] 	BankSize: 0
[    24.381] 	NumberOfImages: 10
[    24.381] 	RedMaskSize: 0
[    24.381] 	RedFieldPosition: 0
[    24.381] 	GreenMaskSize: 0
[    24.381] 	GreenFieldPosition: 0
[    24.381] 	BlueMaskSize: 0
[    24.381] 	BlueFieldPosition: 0
[    24.381] 	RsvdMaskSize: 0
[    24.381] 	RsvdFieldPosition: 0
[    24.381] 	DirectColorModeInfo: 0
[    24.381] 	PhysBasePtr: 0xe1000000
[    24.381] 	LinBytesPerScanLine: 640
[    24.381] 	BnkNumberOfImagePages: 10
[    24.381] 	LinNumberOfImagePages: 10
[    24.381] 	LinRedMaskSize: 0
[    24.381] 	LinRedFieldPosition: 0
[    24.381] 	LinGreenMaskSize: 0
[    24.381] 	LinGreenFieldPosition: 0
[    24.381] 	LinBlueMaskSize: 0
[    24.381] 	LinBlueFieldPosition: 0
[    24.381] 	LinRsvdMaskSize: 0
[    24.381] 	LinRsvdFieldPosition: 0
[    24.381] 	MaxPixelClock: 229500000
[    24.382] Mode: 102 (800x600)
[    24.382] 	ModeAttributes: 0x33f
[    24.382] 	WinAAttributes: 0x7
[    24.382] 	WinBAttributes: 0x0
[    24.382] 	WinGranularity: 64
[    24.382] 	WinSize: 64
[    24.382] 	WinASegment: 0xa000
[    24.382] 	WinBSegment: 0x0
[    24.382] 	WinFuncPtr: 0xc000825b
[    24.382] 	BytesPerScanline: 100
[    24.382] 	XResolution: 800
[    24.382] 	YResolution: 600
[    24.382] 	XCharSize: 8
[    24.382] 	YCharSize: 16
[    24.382] 	NumberOfPlanes: 4
[    24.382] 	BitsPerPixel: 4
[    24.382] 	NumberOfBanks: 1
[    24.382] 	MemoryModel: 3
[    24.382] 	BankSize: 0
[    24.382] 	NumberOfImages: 2
[    24.382] 	RedMaskSize: 0
[    24.382] 	RedFieldPosition: 0
[    24.382] 	GreenMaskSize: 0
[    24.382] 	GreenFieldPosition: 0
[    24.382] 	BlueMaskSize: 0
[    24.382] 	BlueFieldPosition: 0
[    24.382] 	RsvdMaskSize: 0
[    24.382] 	RsvdFieldPosition: 0
[    24.382] 	DirectColorModeInfo: 0
[    24.382] 	PhysBasePtr: 0x0
[    24.382] 	LinBytesPerScanLine: 100
[    24.382] 	BnkNumberOfImagePages: 2
[    24.382] 	LinNumberOfImagePages: 2
[    24.382] 	LinRedMaskSize: 0
[    24.382] 	LinRedFieldPosition: 0
[    24.382] 	LinGreenMaskSize: 0
[    24.382] 	LinGreenFieldPosition: 0
[    24.382] 	LinBlueMaskSize: 0
[    24.382] 	LinBlueFieldPosition: 0
[    24.382] 	LinRsvdMaskSize: 0
[    24.382] 	LinRsvdFieldPosition: 0
[    24.382] 	MaxPixelClock: 108500000
[    24.384] Mode: 103 (800x600)
[    24.384] 	ModeAttributes: 0x3bf
[    24.384] 	WinAAttributes: 0x7
[    24.384] 	WinBAttributes: 0x0
[    24.384] 	WinGranularity: 64
[    24.384] 	WinSize: 64
[    24.384] 	WinASegment: 0xa000
[    24.384] 	WinBSegment: 0x0
[    24.384] 	WinFuncPtr: 0xc000825b
[    24.384] 	BytesPerScanline: 800
[    24.384] 	XResolution: 800
[    24.384] 	YResolution: 600
[    24.384] 	XCharSize: 8
[    24.384] 	YCharSize: 16
[    24.384] 	NumberOfPlanes: 1
[    24.384] 	BitsPerPixel: 8
[    24.384] 	NumberOfBanks: 1
[    24.384] 	MemoryModel: 4
[    24.384] 	BankSize: 0
[    24.384] 	NumberOfImages: 6
[    24.384] 	RedMaskSize: 0
[    24.384] 	RedFieldPosition: 0
[    24.384] 	GreenMaskSize: 0
[    24.384] 	GreenFieldPosition: 0
[    24.384] 	BlueMaskSize: 0
[    24.384] 	BlueFieldPosition: 0
[    24.384] 	RsvdMaskSize: 0
[    24.384] 	RsvdFieldPosition: 0
[    24.384] 	DirectColorModeInfo: 0
[    24.384] 	PhysBasePtr: 0xe1000000
[    24.384] 	LinBytesPerScanLine: 800
[    24.384] 	BnkNumberOfImagePages: 6
[    24.384] 	LinNumberOfImagePages: 6
[    24.384] 	LinRedMaskSize: 0
[    24.384] 	LinRedFieldPosition: 0
[    24.384] 	LinGreenMaskSize: 0
[    24.384] 	LinGreenFieldPosition: 0
[    24.384] 	LinBlueMaskSize: 0
[    24.384] 	LinBlueFieldPosition: 0
[    24.384] 	LinRsvdMaskSize: 0
[    24.384] 	LinRsvdFieldPosition: 0
[    24.384] 	MaxPixelClock: 229500000
[    24.385] Mode: 104 (1024x768)
[    24.385] 	ModeAttributes: 0x33f
[    24.385] 	WinAAttributes: 0x7
[    24.385] 	WinBAttributes: 0x0
[    24.385] 	WinGranularity: 64
[    24.385] 	WinSize: 64
[    24.385] 	WinASegment: 0xa000
[    24.385] 	WinBSegment: 0x0
[    24.385] 	WinFuncPtr: 0xc000825b
[    24.385] 	BytesPerScanline: 128
[    24.385] 	XResolution: 1024
[    24.385] 	YResolution: 768
[    24.385] 	XCharSize: 8
[    24.385] 	YCharSize: 16
[    24.385] 	NumberOfPlanes: 4
[    24.385] 	BitsPerPixel: 4
[    24.385] 	NumberOfBanks: 1
[    24.385] 	MemoryModel: 3
[    24.385] 	BankSize: 0
[    24.385] 	NumberOfImages: 1
[    24.385] 	RedMaskSize: 0
[    24.385] 	RedFieldPosition: 0
[    24.385] 	GreenMaskSize: 0
[    24.385] 	GreenFieldPosition: 0
[    24.385] 	BlueMaskSize: 0
[    24.385] 	BlueFieldPosition: 0
[    24.385] 	RsvdMaskSize: 0
[    24.385] 	RsvdFieldPosition: 0
[    24.385] 	DirectColorModeInfo: 0
[    24.385] 	PhysBasePtr: 0x0
[    24.385] 	LinBytesPerScanLine: 128
[    24.385] 	BnkNumberOfImagePages: 1
[    24.385] 	LinNumberOfImagePages: 1
[    24.385] 	LinRedMaskSize: 0
[    24.385] 	LinRedFieldPosition: 0
[    24.385] 	LinGreenMaskSize: 0
[    24.385] 	LinGreenFieldPosition: 0
[    24.385] 	LinBlueMaskSize: 0
[    24.385] 	LinBlueFieldPosition: 0
[    24.385] 	LinRsvdMaskSize: 0
[    24.385] 	LinRsvdFieldPosition: 0
[    24.385] 	MaxPixelClock: 108500000
[    24.387] Mode: 105 (1024x768)
[    24.387] 	ModeAttributes: 0x3bf
[    24.387] 	WinAAttributes: 0x7
[    24.387] 	WinBAttributes: 0x0
[    24.387] 	WinGranularity: 64
[    24.387] 	WinSize: 64
[    24.387] 	WinASegment: 0xa000
[    24.387] 	WinBSegment: 0x0
[    24.387] 	WinFuncPtr: 0xc000825b
[    24.387] 	BytesPerScanline: 1024
[    24.387] 	XResolution: 1024
[    24.387] 	YResolution: 768
[    24.387] 	XCharSize: 8
[    24.387] 	YCharSize: 16
[    24.387] 	NumberOfPlanes: 1
[    24.387] 	BitsPerPixel: 8
[    24.387] 	NumberOfBanks: 1
[    24.387] 	MemoryModel: 4
[    24.387] 	BankSize: 0
[    24.387] 	NumberOfImages: 3
[    24.387] 	RedMaskSize: 0
[    24.387] 	RedFieldPosition: 0
[    24.387] 	GreenMaskSize: 0
[    24.387] 	GreenFieldPosition: 0
[    24.387] 	BlueMaskSize: 0
[    24.387] 	BlueFieldPosition: 0
[    24.387] 	RsvdMaskSize: 0
[    24.387] 	RsvdFieldPosition: 0
[    24.387] 	DirectColorModeInfo: 0
[    24.387] 	PhysBasePtr: 0xe1000000
[    24.387] 	LinBytesPerScanLine: 1024
[    24.387] 	BnkNumberOfImagePages: 3
[    24.387] 	LinNumberOfImagePages: 3
[    24.387] 	LinRedMaskSize: 0
[    24.387] 	LinRedFieldPosition: 0
[    24.387] 	LinGreenMaskSize: 0
[    24.387] 	LinGreenFieldPosition: 0
[    24.387] 	LinBlueMaskSize: 0
[    24.387] 	LinBlueFieldPosition: 0
[    24.387] 	LinRsvdMaskSize: 0
[    24.387] 	LinRsvdFieldPosition: 0
[    24.387] 	MaxPixelClock: 229500000
[    24.388] Mode: 10e (320x200)
[    24.388] 	ModeAttributes: 0x3bf
[    24.388] 	WinAAttributes: 0x7
[    24.388] 	WinBAttributes: 0x0
[    24.388] 	WinGranularity: 64
[    24.388] 	WinSize: 64
[    24.388] 	WinASegment: 0xa000
[    24.388] 	WinBSegment: 0x0
[    24.388] 	WinFuncPtr: 0xc000825b
[    24.388] 	BytesPerScanline: 640
[    24.388] 	XResolution: 320
[    24.388] 	YResolution: 200
[    24.388] 	XCharSize: 8
[    24.388] 	YCharSize: 8
[    24.388] 	NumberOfPlanes: 1
[    24.388] 	BitsPerPixel: 16
[    24.388] 	NumberOfBanks: 1
[    24.388] 	MemoryModel: 6
[    24.388] 	BankSize: 0
[    24.388] 	NumberOfImages: 30
[    24.388] 	RedMaskSize: 5
[    24.388] 	RedFieldPosition: 11
[    24.388] 	GreenMaskSize: 6
[    24.388] 	GreenFieldPosition: 5
[    24.388] 	BlueMaskSize: 5
[    24.388] 	BlueFieldPosition: 0
[    24.388] 	RsvdMaskSize: 0
[    24.388] 	RsvdFieldPosition: 0
[    24.388] 	DirectColorModeInfo: 0
[    24.388] 	PhysBasePtr: 0xe1000000
[    24.388] 	LinBytesPerScanLine: 640
[    24.388] 	BnkNumberOfImagePages: 30
[    24.388] 	LinNumberOfImagePages: 30
[    24.388] 	LinRedMaskSize: 5
[    24.388] 	LinRedFieldPosition: 11
[    24.388] 	LinGreenMaskSize: 6
[    24.388] 	LinGreenFieldPosition: 5
[    24.388] 	LinBlueMaskSize: 5
[    24.388] 	LinBlueFieldPosition: 0
[    24.388] 	LinRsvdMaskSize: 0
[    24.388] 	LinRsvdFieldPosition: 0
[    24.388] 	MaxPixelClock: 229500000
[    24.389] *Mode: 10f (320x200)
[    24.389] 	ModeAttributes: 0x3bf
[    24.389] 	WinAAttributes: 0x7
[    24.389] 	WinBAttributes: 0x0
[    24.389] 	WinGranularity: 64
[    24.389] 	WinSize: 64
[    24.389] 	WinASegment: 0xa000
[    24.389] 	WinBSegment: 0x0
[    24.389] 	WinFuncPtr: 0xc000825b
[    24.389] 	BytesPerScanline: 1280
[    24.389] 	XResolution: 320
[    24.389] 	YResolution: 200
[    24.389] 	XCharSize: 8
[    24.389] 	YCharSize: 8
[    24.389] 	NumberOfPlanes: 1
[    24.389] 	BitsPerPixel: 32
[    24.389] 	NumberOfBanks: 1
[    24.389] 	MemoryModel: 6
[    24.389] 	BankSize: 0
[    24.389] 	NumberOfImages: 14
[    24.389] 	RedMaskSize: 8
[    24.389] 	RedFieldPosition: 16
[    24.389] 	GreenMaskSize: 8
[    24.389] 	GreenFieldPosition: 8
[    24.389] 	BlueMaskSize: 8
[    24.389] 	BlueFieldPosition: 0
[    24.389] 	RsvdMaskSize: 8
[    24.389] 	RsvdFieldPosition: 24
[    24.389] 	DirectColorModeInfo: 0
[    24.389] 	PhysBasePtr: 0xe1000000
[    24.389] 	LinBytesPerScanLine: 1280
[    24.389] 	BnkNumberOfImagePages: 14
[    24.389] 	LinNumberOfImagePages: 14
[    24.389] 	LinRedMaskSize: 8
[    24.389] 	LinRedFieldPosition: 16
[    24.389] 	LinGreenMaskSize: 8
[    24.389] 	LinGreenFieldPosition: 8
[    24.389] 	LinBlueMaskSize: 8
[    24.390] 	LinBlueFieldPosition: 0
[    24.390] 	LinRsvdMaskSize: 8
[    24.390] 	LinRsvdFieldPosition: 24
[    24.390] 	MaxPixelClock: 229500000
[    24.391] Mode: 111 (640x480)
[    24.391] 	ModeAttributes: 0x3bf
[    24.391] 	WinAAttributes: 0x7
[    24.391] 	WinBAttributes: 0x0
[    24.391] 	WinGranularity: 64
[    24.391] 	WinSize: 64
[    24.391] 	WinASegment: 0xa000
[    24.391] 	WinBSegment: 0x0
[    24.391] 	WinFuncPtr: 0xc000825b
[    24.391] 	BytesPerScanline: 1280
[    24.391] 	XResolution: 640
[    24.391] 	YResolution: 480
[    24.391] 	XCharSize: 8
[    24.391] 	YCharSize: 16
[    24.391] 	NumberOfPlanes: 1
[    24.391] 	BitsPerPixel: 16
[    24.391] 	NumberOfBanks: 1
[    24.391] 	MemoryModel: 6
[    24.391] 	BankSize: 0
[    24.391] 	NumberOfImages: 4
[    24.391] 	RedMaskSize: 5
[    24.391] 	RedFieldPosition: 11
[    24.391] 	GreenMaskSize: 6
[    24.391] 	GreenFieldPosition: 5
[    24.391] 	BlueMaskSize: 5
[    24.391] 	BlueFieldPosition: 0
[    24.391] 	RsvdMaskSize: 0
[    24.391] 	RsvdFieldPosition: 0
[    24.391] 	DirectColorModeInfo: 0
[    24.391] 	PhysBasePtr: 0xe1000000
[    24.391] 	LinBytesPerScanLine: 1280
[    24.391] 	BnkNumberOfImagePages: 4
[    24.391] 	LinNumberOfImagePages: 4
[    24.391] 	LinRedMaskSize: 5
[    24.391] 	LinRedFieldPosition: 11
[    24.391] 	LinGreenMaskSize: 6
[    24.391] 	LinGreenFieldPosition: 5
[    24.391] 	LinBlueMaskSize: 5
[    24.391] 	LinBlueFieldPosition: 0
[    24.391] 	LinRsvdMaskSize: 0
[    24.391] 	LinRsvdFieldPosition: 0
[    24.391] 	MaxPixelClock: 229500000
[    24.392] *Mode: 112 (640x480)
[    24.392] 	ModeAttributes: 0x3bf
[    24.392] 	WinAAttributes: 0x7
[    24.392] 	WinBAttributes: 0x0
[    24.392] 	WinGranularity: 64
[    24.392] 	WinSize: 64
[    24.392] 	WinASegment: 0xa000
[    24.392] 	WinBSegment: 0x0
[    24.392] 	WinFuncPtr: 0xc000825b
[    24.392] 	BytesPerScanline: 2560
[    24.392] 	XResolution: 640
[    24.392] 	YResolution: 480
[    24.392] 	XCharSize: 8
[    24.392] 	YCharSize: 16
[    24.392] 	NumberOfPlanes: 1
[    24.392] 	BitsPerPixel: 32
[    24.392] 	NumberOfBanks: 1
[    24.392] 	MemoryModel: 6
[    24.392] 	BankSize: 0
[    24.392] 	NumberOfImages: 1
[    24.392] 	RedMaskSize: 8
[    24.392] 	RedFieldPosition: 16
[    24.392] 	GreenMaskSize: 8
[    24.392] 	GreenFieldPosition: 8
[    24.392] 	BlueMaskSize: 8
[    24.392] 	BlueFieldPosition: 0
[    24.392] 	RsvdMaskSize: 8
[    24.392] 	RsvdFieldPosition: 24
[    24.392] 	DirectColorModeInfo: 0
[    24.392] 	PhysBasePtr: 0xe1000000
[    24.392] 	LinBytesPerScanLine: 2560
[    24.392] 	BnkNumberOfImagePages: 1
[    24.392] 	LinNumberOfImagePages: 1
[    24.392] 	LinRedMaskSize: 8
[    24.392] 	LinRedFieldPosition: 16
[    24.392] 	LinGreenMaskSize: 8
[    24.392] 	LinGreenFieldPosition: 8
[    24.392] 	LinBlueMaskSize: 8
[    24.392] 	LinBlueFieldPosition: 0
[    24.392] 	LinRsvdMaskSize: 8
[    24.392] 	LinRsvdFieldPosition: 24
[    24.392] 	MaxPixelClock: 229500000
[    24.394] Mode: 114 (800x600)
[    24.394] 	ModeAttributes: 0x3bf
[    24.394] 	WinAAttributes: 0x7
[    24.394] 	WinBAttributes: 0x0
[    24.394] 	WinGranularity: 64
[    24.394] 	WinSize: 64
[    24.394] 	WinASegment: 0xa000
[    24.394] 	WinBSegment: 0x0
[    24.394] 	WinFuncPtr: 0xc000825b
[    24.394] 	BytesPerScanline: 1600
[    24.394] 	XResolution: 800
[    24.394] 	YResolution: 600
[    24.394] 	XCharSize: 8
[    24.394] 	YCharSize: 16
[    24.394] 	NumberOfPlanes: 1
[    24.394] 	BitsPerPixel: 16
[    24.394] 	NumberOfBanks: 1
[    24.394] 	MemoryModel: 6
[    24.394] 	BankSize: 0
[    24.394] 	NumberOfImages: 2
[    24.394] 	RedMaskSize: 5
[    24.394] 	RedFieldPosition: 11
[    24.394] 	GreenMaskSize: 6
[    24.394] 	GreenFieldPosition: 5
[    24.394] 	BlueMaskSize: 5
[    24.394] 	BlueFieldPosition: 0
[    24.394] 	RsvdMaskSize: 0
[    24.394] 	RsvdFieldPosition: 0
[    24.394] 	DirectColorModeInfo: 0
[    24.394] 	PhysBasePtr: 0xe1000000
[    24.394] 	LinBytesPerScanLine: 1600
[    24.394] 	BnkNumberOfImagePages: 2
[    24.394] 	LinNumberOfImagePages: 2
[    24.394] 	LinRedMaskSize: 5
[    24.394] 	LinRedFieldPosition: 11
[    24.394] 	LinGreenMaskSize: 6
[    24.394] 	LinGreenFieldPosition: 5
[    24.394] 	LinBlueMaskSize: 5
[    24.394] 	LinBlueFieldPosition: 0
[    24.394] 	LinRsvdMaskSize: 0
[    24.394] 	LinRsvdFieldPosition: 0
[    24.394] 	MaxPixelClock: 229500000
[    24.395] *Mode: 115 (800x600)
[    24.395] 	ModeAttributes: 0x3bf
[    24.395] 	WinAAttributes: 0x7
[    24.395] 	WinBAttributes: 0x0
[    24.395] 	WinGranularity: 64
[    24.395] 	WinSize: 64
[    24.395] 	WinASegment: 0xa000
[    24.395] 	WinBSegment: 0x0
[    24.395] 	WinFuncPtr: 0xc000825b
[    24.395] 	BytesPerScanline: 3200
[    24.395] 	XResolution: 800
[    24.395] 	YResolution: 600
[    24.395] 	XCharSize: 8
[    24.395] 	YCharSize: 16
[    24.395] 	NumberOfPlanes: 1
[    24.395] 	BitsPerPixel: 32
[    24.395] 	NumberOfBanks: 1
[    24.395] 	MemoryModel: 6
[    24.395] 	BankSize: 0
[    24.395] 	NumberOfImages: 1
[    24.395] 	RedMaskSize: 8
[    24.395] 	RedFieldPosition: 16
[    24.395] 	GreenMaskSize: 8
[    24.395] 	GreenFieldPosition: 8
[    24.395] 	BlueMaskSize: 8
[    24.395] 	BlueFieldPosition: 0
[    24.395] 	RsvdMaskSize: 8
[    24.395] 	RsvdFieldPosition: 24
[    24.395] 	DirectColorModeInfo: 0
[    24.395] 	PhysBasePtr: 0xe1000000
[    24.395] 	LinBytesPerScanLine: 3200
[    24.395] 	BnkNumberOfImagePages: 1
[    24.395] 	LinNumberOfImagePages: 1
[    24.395] 	LinRedMaskSize: 8
[    24.395] 	LinRedFieldPosition: 16
[    24.395] 	LinGreenMaskSize: 8
[    24.395] 	LinGreenFieldPosition: 8
[    24.395] 	LinBlueMaskSize: 8
[    24.395] 	LinBlueFieldPosition: 0
[    24.395] 	LinRsvdMaskSize: 8
[    24.395] 	LinRsvdFieldPosition: 24
[    24.395] 	MaxPixelClock: 229500000
[    24.397] Mode: 117 (1024x768)
[    24.397] 	ModeAttributes: 0x3bf
[    24.397] 	WinAAttributes: 0x7
[    24.397] 	WinBAttributes: 0x0
[    24.397] 	WinGranularity: 64
[    24.397] 	WinSize: 64
[    24.397] 	WinASegment: 0xa000
[    24.397] 	WinBSegment: 0x0
[    24.397] 	WinFuncPtr: 0xc000825b
[    24.397] 	BytesPerScanline: 2048
[    24.397] 	XResolution: 1024
[    24.397] 	YResolution: 768
[    24.397] 	XCharSize: 8
[    24.397] 	YCharSize: 16
[    24.397] 	NumberOfPlanes: 1
[    24.397] 	BitsPerPixel: 16
[    24.397] 	NumberOfBanks: 1
[    24.397] 	MemoryModel: 6
[    24.397] 	BankSize: 0
[    24.397] 	NumberOfImages: 1
[    24.397] 	RedMaskSize: 5
[    24.397] 	RedFieldPosition: 11
[    24.397] 	GreenMaskSize: 6
[    24.397] 	GreenFieldPosition: 5
[    24.397] 	BlueMaskSize: 5
[    24.397] 	BlueFieldPosition: 0
[    24.397] 	RsvdMaskSize: 0
[    24.397] 	RsvdFieldPosition: 0
[    24.397] 	DirectColorModeInfo: 0
[    24.397] 	PhysBasePtr: 0xe1000000
[    24.397] 	LinBytesPerScanLine: 2048
[    24.397] 	BnkNumberOfImagePages: 1
[    24.397] 	LinNumberOfImagePages: 1
[    24.397] 	LinRedMaskSize: 5
[    24.397] 	LinRedFieldPosition: 11
[    24.397] 	LinGreenMaskSize: 6
[    24.397] 	LinGreenFieldPosition: 5
[    24.397] 	LinBlueMaskSize: 5
[    24.397] 	LinBlueFieldPosition: 0
[    24.397] 	LinRsvdMaskSize: 0
[    24.397] 	LinRsvdFieldPosition: 0
[    24.397] 	MaxPixelClock: 229500000
[    24.398] *Mode: 118 (1024x768)
[    24.398] 	ModeAttributes: 0x3bf
[    24.398] 	WinAAttributes: 0x7
[    24.398] 	WinBAttributes: 0x0
[    24.398] 	WinGranularity: 64
[    24.398] 	WinSize: 64
[    24.398] 	WinASegment: 0xa000
[    24.398] 	WinBSegment: 0x0
[    24.398] 	WinFuncPtr: 0xc000825b
[    24.398] 	BytesPerScanline: 4096
[    24.398] 	XResolution: 1024
[    24.398] 	YResolution: 768
[    24.398] 	XCharSize: 8
[    24.398] 	YCharSize: 16
[    24.398] 	NumberOfPlanes: 1
[    24.398] 	BitsPerPixel: 32
[    24.398] 	NumberOfBanks: 1
[    24.398] 	MemoryModel: 6
[    24.398] 	BankSize: 0
[    24.398] 	NumberOfImages: 1
[    24.398] 	RedMaskSize: 8
[    24.398] 	RedFieldPosition: 16
[    24.398] 	GreenMaskSize: 8
[    24.398] 	GreenFieldPosition: 8
[    24.398] 	BlueMaskSize: 8
[    24.398] 	BlueFieldPosition: 0
[    24.398] 	RsvdMaskSize: 8
[    24.398] 	RsvdFieldPosition: 24
[    24.398] 	DirectColorModeInfo: 0
[    24.398] 	PhysBasePtr: 0xe1000000
[    24.398] 	LinBytesPerScanLine: 4096
[    24.398] 	BnkNumberOfImagePages: 1
[    24.398] 	LinNumberOfImagePages: 1
[    24.398] 	LinRedMaskSize: 8
[    24.398] 	LinRedFieldPosition: 16
[    24.398] 	LinGreenMaskSize: 8
[    24.398] 	LinGreenFieldPosition: 8
[    24.398] 	LinBlueMaskSize: 8
[    24.398] 	LinBlueFieldPosition: 0
[    24.398] 	LinRsvdMaskSize: 8
[    24.398] 	LinRsvdFieldPosition: 24
[    24.398] 	MaxPixelClock: 229500000
[    24.399] Mode: 130 (320x200)
[    24.399] 	ModeAttributes: 0x3bf
[    24.399] 	WinAAttributes: 0x7
[    24.399] 	WinBAttributes: 0x0
[    24.399] 	WinGranularity: 64
[    24.399] 	WinSize: 64
[    24.399] 	WinASegment: 0xa000
[    24.399] 	WinBSegment: 0x0
[    24.399] 	WinFuncPtr: 0xc000825b
[    24.399] 	BytesPerScanline: 320
[    24.399] 	XResolution: 320
[    24.399] 	YResolution: 200
[    24.399] 	XCharSize: 8
[    24.399] 	YCharSize: 8
[    24.399] 	NumberOfPlanes: 1
[    24.399] 	BitsPerPixel: 8
[    24.399] 	NumberOfBanks: 1
[    24.399] 	MemoryModel: 4
[    24.399] 	BankSize: 0
[    24.399] 	NumberOfImages: 62
[    24.399] 	RedMaskSize: 0
[    24.399] 	RedFieldPosition: 0
[    24.399] 	GreenMaskSize: 0
[    24.399] 	GreenFieldPosition: 0
[    24.399] 	BlueMaskSize: 0
[    24.399] 	BlueFieldPosition: 0
[    24.399] 	RsvdMaskSize: 0
[    24.399] 	RsvdFieldPosition: 0
[    24.399] 	DirectColorModeInfo: 0
[    24.399] 	PhysBasePtr: 0xe1000000
[    24.400] 	LinBytesPerScanLine: 320
[    24.400] 	BnkNumberOfImagePages: 62
[    24.400] 	LinNumberOfImagePages: 62
[    24.400] 	LinRedMaskSize: 0
[    24.400] 	LinRedFieldPosition: 0
[    24.400] 	LinGreenMaskSize: 0
[    24.400] 	LinGreenFieldPosition: 0
[    24.400] 	LinBlueMaskSize: 0
[    24.400] 	LinBlueFieldPosition: 0
[    24.400] 	LinRsvdMaskSize: 0
[    24.400] 	LinRsvdFieldPosition: 0
[    24.400] 	MaxPixelClock: 229500000
[    24.401] Mode: 131 (320x400)
[    24.401] 	ModeAttributes: 0x3bf
[    24.401] 	WinAAttributes: 0x7
[    24.401] 	WinBAttributes: 0x0
[    24.401] 	WinGranularity: 64
[    24.401] 	WinSize: 64
[    24.401] 	WinASegment: 0xa000
[    24.401] 	WinBSegment: 0x0
[    24.401] 	WinFuncPtr: 0xc000825b
[    24.401] 	BytesPerScanline: 320
[    24.401] 	XResolution: 320
[    24.401] 	YResolution: 400
[    24.401] 	XCharSize: 8
[    24.401] 	YCharSize: 16
[    24.401] 	NumberOfPlanes: 1
[    24.401] 	BitsPerPixel: 8
[    24.401] 	NumberOfBanks: 1
[    24.401] 	MemoryModel: 4
[    24.401] 	BankSize: 0
[    24.401] 	NumberOfImages: 30
[    24.401] 	RedMaskSize: 0
[    24.401] 	RedFieldPosition: 0
[    24.401] 	GreenMaskSize: 0
[    24.401] 	GreenFieldPosition: 0
[    24.401] 	BlueMaskSize: 0
[    24.401] 	BlueFieldPosition: 0
[    24.401] 	RsvdMaskSize: 0
[    24.401] 	RsvdFieldPosition: 0
[    24.401] 	DirectColorModeInfo: 0
[    24.401] 	PhysBasePtr: 0xe1000000
[    24.401] 	LinBytesPerScanLine: 320
[    24.401] 	BnkNumberOfImagePages: 30
[    24.401] 	LinNumberOfImagePages: 30
[    24.401] 	LinRedMaskSize: 0
[    24.401] 	LinRedFieldPosition: 0
[    24.401] 	LinGreenMaskSize: 0
[    24.401] 	LinGreenFieldPosition: 0
[    24.401] 	LinBlueMaskSize: 0
[    24.401] 	LinBlueFieldPosition: 0
[    24.401] 	LinRsvdMaskSize: 0
[    24.401] 	LinRsvdFieldPosition: 0
[    24.401] 	MaxPixelClock: 229500000
[    24.402] Mode: 132 (320x400)
[    24.402] 	ModeAttributes: 0x3bf
[    24.402] 	WinAAttributes: 0x7
[    24.402] 	WinBAttributes: 0x0
[    24.402] 	WinGranularity: 64
[    24.402] 	WinSize: 64
[    24.402] 	WinASegment: 0xa000
[    24.402] 	WinBSegment: 0x0
[    24.402] 	WinFuncPtr: 0xc000825b
[    24.402] 	BytesPerScanline: 640
[    24.402] 	XResolution: 320
[    24.402] 	YResolution: 400
[    24.402] 	XCharSize: 8
[    24.402] 	YCharSize: 16
[    24.402] 	NumberOfPlanes: 1
[    24.402] 	BitsPerPixel: 16
[    24.402] 	NumberOfBanks: 1
[    24.402] 	MemoryModel: 6
[    24.402] 	BankSize: 0
[    24.402] 	NumberOfImages: 14
[    24.402] 	RedMaskSize: 5
[    24.402] 	RedFieldPosition: 11
[    24.402] 	GreenMaskSize: 6
[    24.402] 	GreenFieldPosition: 5
[    24.402] 	BlueMaskSize: 5
[    24.402] 	BlueFieldPosition: 0
[    24.402] 	RsvdMaskSize: 0
[    24.402] 	RsvdFieldPosition: 0
[    24.402] 	DirectColorModeInfo: 0
[    24.402] 	PhysBasePtr: 0xe1000000
[    24.402] 	LinBytesPerScanLine: 640
[    24.402] 	BnkNumberOfImagePages: 14
[    24.402] 	LinNumberOfImagePages: 14
[    24.402] 	LinRedMaskSize: 5
[    24.402] 	LinRedFieldPosition: 11
[    24.402] 	LinGreenMaskSize: 6
[    24.402] 	LinGreenFieldPosition: 5
[    24.402] 	LinBlueMaskSize: 5
[    24.402] 	LinBlueFieldPosition: 0
[    24.402] 	LinRsvdMaskSize: 0
[    24.402] 	LinRsvdFieldPosition: 0
[    24.402] 	MaxPixelClock: 229500000
[    24.404] *Mode: 133 (320x400)
[    24.404] 	ModeAttributes: 0x3bf
[    24.404] 	WinAAttributes: 0x7
[    24.404] 	WinBAttributes: 0x0
[    24.404] 	WinGranularity: 64
[    24.404] 	WinSize: 64
[    24.404] 	WinASegment: 0xa000
[    24.404] 	WinBSegment: 0x0
[    24.404] 	WinFuncPtr: 0xc000825b
[    24.404] 	BytesPerScanline: 1280
[    24.404] 	XResolution: 320
[    24.404] 	YResolution: 400
[    24.404] 	XCharSize: 8
[    24.404] 	YCharSize: 16
[    24.404] 	NumberOfPlanes: 1
[    24.404] 	BitsPerPixel: 32
[    24.404] 	NumberOfBanks: 1
[    24.404] 	MemoryModel: 6
[    24.404] 	BankSize: 0
[    24.404] 	NumberOfImages: 6
[    24.404] 	RedMaskSize: 8
[    24.404] 	RedFieldPosition: 16
[    24.404] 	GreenMaskSize: 8
[    24.404] 	GreenFieldPosition: 8
[    24.404] 	BlueMaskSize: 8
[    24.404] 	BlueFieldPosition: 0
[    24.404] 	RsvdMaskSize: 8
[    24.404] 	RsvdFieldPosition: 24
[    24.404] 	DirectColorModeInfo: 0
[    24.404] 	PhysBasePtr: 0xe1000000
[    24.404] 	LinBytesPerScanLine: 1280
[    24.404] 	BnkNumberOfImagePages: 6
[    24.404] 	LinNumberOfImagePages: 6
[    24.404] 	LinRedMaskSize: 8
[    24.404] 	LinRedFieldPosition: 16
[    24.404] 	LinGreenMaskSize: 8
[    24.404] 	LinGreenFieldPosition: 8
[    24.404] 	LinBlueMaskSize: 8
[    24.404] 	LinBlueFieldPosition: 0
[    24.404] 	LinRsvdMaskSize: 8
[    24.404] 	LinRsvdFieldPosition: 24
[    24.404] 	MaxPixelClock: 229500000
[    24.405] Mode: 134 (320x240)
[    24.405] 	ModeAttributes: 0x3bf
[    24.405] 	WinAAttributes: 0x7
[    24.405] 	WinBAttributes: 0x0
[    24.405] 	WinGranularity: 64
[    24.405] 	WinSize: 64
[    24.405] 	WinASegment: 0xa000
[    24.405] 	WinBSegment: 0x0
[    24.405] 	WinFuncPtr: 0xc000825b
[    24.405] 	BytesPerScanline: 320
[    24.405] 	XResolution: 320
[    24.405] 	YResolution: 240
[    24.405] 	XCharSize: 8
[    24.405] 	YCharSize: 8
[    24.405] 	NumberOfPlanes: 1
[    24.405] 	BitsPerPixel: 8
[    24.405] 	NumberOfBanks: 1
[    24.405] 	MemoryModel: 4
[    24.405] 	BankSize: 0
[    24.405] 	NumberOfImages: 30
[    24.405] 	RedMaskSize: 0
[    24.405] 	RedFieldPosition: 0
[    24.405] 	GreenMaskSize: 0
[    24.405] 	GreenFieldPosition: 0
[    24.405] 	BlueMaskSize: 0
[    24.405] 	BlueFieldPosition: 0
[    24.405] 	RsvdMaskSize: 0
[    24.405] 	RsvdFieldPosition: 0
[    24.405] 	DirectColorModeInfo: 0
[    24.405] 	PhysBasePtr: 0xe1000000
[    24.405] 	LinBytesPerScanLine: 320
[    24.405] 	BnkNumberOfImagePages: 30
[    24.405] 	LinNumberOfImagePages: 30
[    24.405] 	LinRedMaskSize: 0
[    24.405] 	LinRedFieldPosition: 0
[    24.405] 	LinGreenMaskSize: 0
[    24.405] 	LinGreenFieldPosition: 0
[    24.405] 	LinBlueMaskSize: 0
[    24.405] 	LinBlueFieldPosition: 0
[    24.405] 	LinRsvdMaskSize: 0
[    24.405] 	LinRsvdFieldPosition: 0
[    24.405] 	MaxPixelClock: 229500000
[    24.406] Mode: 135 (320x240)
[    24.406] 	ModeAttributes: 0x3bf
[    24.406] 	WinAAttributes: 0x7
[    24.406] 	WinBAttributes: 0x0
[    24.406] 	WinGranularity: 64
[    24.406] 	WinSize: 64
[    24.406] 	WinASegment: 0xa000
[    24.406] 	WinBSegment: 0x0
[    24.407] 	WinFuncPtr: 0xc000825b
[    24.407] 	BytesPerScanline: 640
[    24.407] 	XResolution: 320
[    24.407] 	YResolution: 240
[    24.407] 	XCharSize: 8
[    24.407] 	YCharSize: 8
[    24.407] 	NumberOfPlanes: 1
[    24.407] 	BitsPerPixel: 16
[    24.407] 	NumberOfBanks: 1
[    24.407] 	MemoryModel: 6
[    24.407] 	BankSize: 0
[    24.407] 	NumberOfImages: 19
[    24.407] 	RedMaskSize: 5
[    24.407] 	RedFieldPosition: 11
[    24.407] 	GreenMaskSize: 6
[    24.407] 	GreenFieldPosition: 5
[    24.407] 	BlueMaskSize: 5
[    24.407] 	BlueFieldPosition: 0
[    24.407] 	RsvdMaskSize: 0
[    24.407] 	RsvdFieldPosition: 0
[    24.407] 	DirectColorModeInfo: 0
[    24.407] 	PhysBasePtr: 0xe1000000
[    24.407] 	LinBytesPerScanLine: 640
[    24.407] 	BnkNumberOfImagePages: 19
[    24.407] 	LinNumberOfImagePages: 19
[    24.407] 	LinRedMaskSize: 5
[    24.407] 	LinRedFieldPosition: 11
[    24.407] 	LinGreenMaskSize: 6
[    24.407] 	LinGreenFieldPosition: 5
[    24.407] 	LinBlueMaskSize: 5
[    24.407] 	LinBlueFieldPosition: 0
[    24.407] 	LinRsvdMaskSize: 0
[    24.407] 	LinRsvdFieldPosition: 0
[    24.407] 	MaxPixelClock: 229500000
[    24.408] *Mode: 136 (320x240)
[    24.408] 	ModeAttributes: 0x3bf
[    24.408] 	WinAAttributes: 0x7
[    24.408] 	WinBAttributes: 0x0
[    24.408] 	WinGranularity: 64
[    24.408] 	WinSize: 64
[    24.408] 	WinASegment: 0xa000
[    24.408] 	WinBSegment: 0x0
[    24.408] 	WinFuncPtr: 0xc000825b
[    24.408] 	BytesPerScanline: 1280
[    24.408] 	XResolution: 320
[    24.408] 	YResolution: 240
[    24.408] 	XCharSize: 8
[    24.408] 	YCharSize: 8
[    24.408] 	NumberOfPlanes: 1
[    24.408] 	BitsPerPixel: 32
[    24.408] 	NumberOfBanks: 1
[    24.408] 	MemoryModel: 6
[    24.408] 	BankSize: 0
[    24.408] 	NumberOfImages: 10
[    24.408] 	RedMaskSize: 8
[    24.408] 	RedFieldPosition: 16
[    24.408] 	GreenMaskSize: 8
[    24.408] 	GreenFieldPosition: 8
[    24.408] 	BlueMaskSize: 8
[    24.408] 	BlueFieldPosition: 0
[    24.408] 	RsvdMaskSize: 8
[    24.408] 	RsvdFieldPosition: 24
[    24.408] 	DirectColorModeInfo: 0
[    24.408] 	PhysBasePtr: 0xe1000000
[    24.408] 	LinBytesPerScanLine: 1280
[    24.408] 	BnkNumberOfImagePages: 10
[    24.408] 	LinNumberOfImagePages: 10
[    24.408] 	LinRedMaskSize: 8
[    24.408] 	LinRedFieldPosition: 16
[    24.408] 	LinGreenMaskSize: 8
[    24.408] 	LinGreenFieldPosition: 8
[    24.408] 	LinBlueMaskSize: 8
[    24.408] 	LinBlueFieldPosition: 0
[    24.408] 	LinRsvdMaskSize: 8
[    24.408] 	LinRsvdFieldPosition: 24
[    24.408] 	MaxPixelClock: 229500000
[    24.409] Mode: 13d (640x400)
[    24.409] 	ModeAttributes: 0x3bf
[    24.409] 	WinAAttributes: 0x7
[    24.409] 	WinBAttributes: 0x0
[    24.409] 	WinGranularity: 64
[    24.409] 	WinSize: 64
[    24.409] 	WinASegment: 0xa000
[    24.409] 	WinBSegment: 0x0
[    24.409] 	WinFuncPtr: 0xc000825b
[    24.409] 	BytesPerScanline: 1280
[    24.409] 	XResolution: 640
[    24.409] 	YResolution: 400
[    24.409] 	XCharSize: 8
[    24.409] 	YCharSize: 16
[    24.409] 	NumberOfPlanes: 1
[    24.409] 	BitsPerPixel: 16
[    24.409] 	NumberOfBanks: 1
[    24.409] 	MemoryModel: 6
[    24.409] 	BankSize: 0
[    24.409] 	NumberOfImages: 6
[    24.409] 	RedMaskSize: 5
[    24.409] 	RedFieldPosition: 11
[    24.409] 	GreenMaskSize: 6
[    24.409] 	GreenFieldPosition: 5
[    24.409] 	BlueMaskSize: 5
[    24.409] 	BlueFieldPosition: 0
[    24.409] 	RsvdMaskSize: 0
[    24.409] 	RsvdFieldPosition: 0
[    24.409] 	DirectColorModeInfo: 0
[    24.409] 	PhysBasePtr: 0xe1000000
[    24.409] 	LinBytesPerScanLine: 1280
[    24.409] 	BnkNumberOfImagePages: 6
[    24.409] 	LinNumberOfImagePages: 6
[    24.409] 	LinRedMaskSize: 5
[    24.409] 	LinRedFieldPosition: 11
[    24.409] 	LinGreenMaskSize: 6
[    24.409] 	LinGreenFieldPosition: 5
[    24.409] 	LinBlueMaskSize: 5
[    24.409] 	LinBlueFieldPosition: 0
[    24.409] 	LinRsvdMaskSize: 0
[    24.409] 	LinRsvdFieldPosition: 0
[    24.409] 	MaxPixelClock: 229500000
[    24.411] *Mode: 13e (640x400)
[    24.411] 	ModeAttributes: 0x3bf
[    24.411] 	WinAAttributes: 0x7
[    24.411] 	WinBAttributes: 0x0
[    24.411] 	WinGranularity: 64
[    24.411] 	WinSize: 64
[    24.411] 	WinASegment: 0xa000
[    24.411] 	WinBSegment: 0x0
[    24.411] 	WinFuncPtr: 0xc000825b
[    24.411] 	BytesPerScanline: 2560
[    24.411] 	XResolution: 640
[    24.411] 	YResolution: 400
[    24.411] 	XCharSize: 8
[    24.411] 	YCharSize: 16
[    24.411] 	NumberOfPlanes: 1
[    24.411] 	BitsPerPixel: 32
[    24.411] 	NumberOfBanks: 1
[    24.411] 	MemoryModel: 6
[    24.411] 	BankSize: 0
[    24.411] 	NumberOfImages: 2
[    24.411] 	RedMaskSize: 8
[    24.411] 	RedFieldPosition: 16
[    24.411] 	GreenMaskSize: 8
[    24.411] 	GreenFieldPosition: 8
[    24.411] 	BlueMaskSize: 8
[    24.411] 	BlueFieldPosition: 0
[    24.411] 	RsvdMaskSize: 8
[    24.411] 	RsvdFieldPosition: 24
[    24.411] 	DirectColorModeInfo: 0
[    24.411] 	PhysBasePtr: 0xe1000000
[    24.411] 	LinBytesPerScanLine: 2560
[    24.411] 	BnkNumberOfImagePages: 2
[    24.411] 	LinNumberOfImagePages: 2
[    24.411] 	LinRedMaskSize: 8
[    24.411] 	LinRedFieldPosition: 16
[    24.411] 	LinGreenMaskSize: 8
[    24.411] 	LinGreenFieldPosition: 8
[    24.411] 	LinBlueMaskSize: 8
[    24.411] 	LinBlueFieldPosition: 0
[    24.411] 	LinRsvdMaskSize: 8
[    24.411] 	LinRsvdFieldPosition: 24
[    24.411] 	MaxPixelClock: 229500000
[    24.412] Mode: 14b (1360x768)
[    24.412] 	ModeAttributes: 0x3bf
[    24.412] 	WinAAttributes: 0x7
[    24.412] 	WinBAttributes: 0x0
[    24.412] 	WinGranularity: 64
[    24.412] 	WinSize: 64
[    24.412] 	WinASegment: 0xa000
[    24.412] 	WinBSegment: 0x0
[    24.412] 	WinFuncPtr: 0xc000825b
[    24.412] 	BytesPerScanline: 1360
[    24.412] 	XResolution: 1360
[    24.412] 	YResolution: 768
[    24.412] 	XCharSize: 8
[    24.412] 	YCharSize: 16
[    24.412] 	NumberOfPlanes: 1
[    24.412] 	BitsPerPixel: 8
[    24.412] 	NumberOfBanks: 1
[    24.412] 	MemoryModel: 4
[    24.412] 	BankSize: 0
[    24.412] 	NumberOfImages: 1
[    24.412] 	RedMaskSize: 0
[    24.412] 	RedFieldPosition: 0
[    24.412] 	GreenMaskSize: 0
[    24.412] 	GreenFieldPosition: 0
[    24.412] 	BlueMaskSize: 0
[    24.412] 	BlueFieldPosition: 0
[    24.412] 	RsvdMaskSize: 0
[    24.412] 	RsvdFieldPosition: 0
[    24.412] 	DirectColorModeInfo: 0
[    24.412] 	PhysBasePtr: 0xe1000000
[    24.412] 	LinBytesPerScanLine: 1360
[    24.412] 	BnkNumberOfImagePages: 1
[    24.412] 	LinNumberOfImagePages: 1
[    24.412] 	LinRedMaskSize: 0
[    24.412] 	LinRedFieldPosition: 0
[    24.412] 	LinGreenMaskSize: 0
[    24.412] 	LinGreenFieldPosition: 0
[    24.412] 	LinBlueMaskSize: 0
[    24.412] 	LinBlueFieldPosition: 0
[    24.412] 	LinRsvdMaskSize: 0
[    24.412] 	LinRsvdFieldPosition: 0
[    24.412] 	MaxPixelClock: 229500000
[    24.414] Mode: 14c (1360x768)
[    24.414] 	ModeAttributes: 0x3bf
[    24.414] 	WinAAttributes: 0x7
[    24.414] 	WinBAttributes: 0x0
[    24.414] 	WinGranularity: 64
[    24.414] 	WinSize: 64
[    24.414] 	WinASegment: 0xa000
[    24.414] 	WinBSegment: 0x0
[    24.414] 	WinFuncPtr: 0xc000825b
[    24.414] 	BytesPerScanline: 2720
[    24.414] 	XResolution: 1360
[    24.414] 	YResolution: 768
[    24.414] 	XCharSize: 8
[    24.414] 	YCharSize: 16
[    24.414] 	NumberOfPlanes: 1
[    24.414] 	BitsPerPixel: 16
[    24.414] 	NumberOfBanks: 1
[    24.414] 	MemoryModel: 6
[    24.414] 	BankSize: 0
[    24.414] 	NumberOfImages: 1
[    24.414] 	RedMaskSize: 5
[    24.414] 	RedFieldPosition: 11
[    24.414] 	GreenMaskSize: 6
[    24.414] 	GreenFieldPosition: 5
[    24.414] 	BlueMaskSize: 5
[    24.414] 	BlueFieldPosition: 0
[    24.414] 	RsvdMaskSize: 0
[    24.414] 	RsvdFieldPosition: 0
[    24.414] 	DirectColorModeInfo: 0
[    24.414] 	PhysBasePtr: 0xe1000000
[    24.414] 	LinBytesPerScanLine: 2720
[    24.414] 	BnkNumberOfImagePages: 1
[    24.414] 	LinNumberOfImagePages: 1
[    24.414] 	LinRedMaskSize: 5
[    24.414] 	LinRedFieldPosition: 11
[    24.414] 	LinGreenMaskSize: 6
[    24.414] 	LinGreenFieldPosition: 5
[    24.414] 	LinBlueMaskSize: 5
[    24.414] 	LinBlueFieldPosition: 0
[    24.414] 	LinRsvdMaskSize: 0
[    24.414] 	LinRsvdFieldPosition: 0
[    24.414] 	MaxPixelClock: 229500000
[    24.415] *Mode: 14d (1360x768)
[    24.415] 	ModeAttributes: 0x3bf
[    24.415] 	WinAAttributes: 0x7
[    24.415] 	WinBAttributes: 0x0
[    24.415] 	WinGranularity: 64
[    24.415] 	WinSize: 64
[    24.415] 	WinASegment: 0xa000
[    24.415] 	WinBSegment: 0x0
[    24.415] 	WinFuncPtr: 0xc000825b
[    24.415] 	BytesPerScanline: 5440
[    24.415] 	XResolution: 1360
[    24.415] 	YResolution: 768
[    24.415] 	XCharSize: 8
[    24.415] 	YCharSize: 16
[    24.415] 	NumberOfPlanes: 1
[    24.415] 	BitsPerPixel: 32
[    24.415] 	NumberOfBanks: 1
[    24.415] 	MemoryModel: 6
[    24.415] 	BankSize: 0
[    24.415] 	NumberOfImages: 1
[    24.415] 	RedMaskSize: 8
[    24.415] 	RedFieldPosition: 16
[    24.415] 	GreenMaskSize: 8
[    24.415] 	GreenFieldPosition: 8
[    24.415] 	BlueMaskSize: 8
[    24.415] 	BlueFieldPosition: 0
[    24.415] 	RsvdMaskSize: 8
[    24.415] 	RsvdFieldPosition: 24
[    24.415] 	DirectColorModeInfo: 0
[    24.415] 	PhysBasePtr: 0xe1000000
[    24.415] 	LinBytesPerScanLine: 5440
[    24.415] 	BnkNumberOfImagePages: 1
[    24.415] 	LinNumberOfImagePages: 1
[    24.415] 	LinRedMaskSize: 8
[    24.415] 	LinRedFieldPosition: 16
[    24.415] 	LinGreenMaskSize: 8
[    24.415] 	LinGreenFieldPosition: 8
[    24.415] 	LinBlueMaskSize: 8
[    24.415] 	LinBlueFieldPosition: 0
[    24.415] 	LinRsvdMaskSize: 8
[    24.415] 	LinRsvdFieldPosition: 24
[    24.415] 	MaxPixelClock: 229500000
[    24.415]
[    24.415] (II) VESA(0): Total Memory: 224 64KB banks (14336kB)
[    24.415] (II) VESA(0): <default monitor>: Using default hsync range of 31.50-48.00 kHz
[    24.415] (II) VESA(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
[    24.415] (II) VESA(0): <default monitor>: Using default maximum pixel clock of 65.00 MHz
[    24.415] (WW) VESA(0): Unable to estimate virtual size
[    24.415] (II) VESA(0): Not using built-in mode "1360x768" (no mode of this name)
[    24.415] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    24.415] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    24.415] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    24.415] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[    24.415] (II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
[    24.415] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    24.415] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    24.415] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    24.415] (II) VESA(0): <default monitor>: Using hsync range of 31.50-48.00 kHz
[    24.415] (II) VESA(0): <default monitor>: Using vrefresh range of 50.00-70.00 Hz
[    24.415] (II) VESA(0): <default monitor>: Using maximum pixel clock of 65.00 MHz
[    24.415] (WW) VESA(0): Unable to estimate virtual size
[    24.415] (II) VESA(0): Not using built-in mode "1360x768" (hsync out of range)
[    24.415] (II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
[    24.415] (II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
[    24.415] (II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
[    24.415] (II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
[    24.415] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[    24.415] (**) VESA(0): *Built-in mode "1024x768"
[    24.415] (**) VESA(0): *Built-in mode "800x600"
[    24.415] (**) VESA(0): *Built-in mode "640x480"
[    24.415] (==) VESA(0): DPI set to (96, 96)
[    24.415] (II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (118)
[    24.416] (II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
[    24.416] (II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
[    24.417] (**) VESA(0): Using "Shadow Framebuffer"
[    24.417] (II) Loading sub module "shadow"
[    24.417] (II) LoadModule: "shadow"
[    24.417] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    24.517] (II) Module shadow: vendor="X.Org Foundation"
[    24.517] 	compiled for 1.10.4, module version = 1.1.0
[    24.517] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    24.517] (II) Loading sub module "fb"
[    24.517] (II) LoadModule: "fb"
[    24.517] (II) Loading /usr/lib/xorg/modules/libfb.so
[    24.517] (II) Module fb: vendor="X.Org Foundation"
[    24.517] 	compiled for 1.10.4, module version = 1.0.0
[    24.517] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    24.517] (II) UnloadModule: "fbdev"
[    24.517] (II) Unloading fbdev
[    24.517] (II) UnloadModule: "fbdevhw"
[    24.517] (II) Unloading fbdevhw
[    24.517] (==) Depth 24 pixmap format is 32 bpp
[    24.518] (II) Loading sub module "int10"
[    24.518] (II) LoadModule: "int10"
[    24.518] (II) Loading /usr/lib/xorg/modules/libint10.so
[    24.518] (II) Module int10: vendor="X.Org Foundation"
[    24.518] 	compiled for 1.10.4, module version = 1.0.0
[    24.518] 	ABI class: X.Org Video Driver, version 10.0
[    24.518] (II) VESA(0): initializing int10
[    24.518] (II) VESA(0): Bad V_BIOS checksum
[    24.518] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    24.566] (II) VESA(0): VESA BIOS detected
[    24.566] (II) VESA(0): VESA VBE Version 3.0
[    24.566] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[    24.566] (II) VESA(0): VESA VBE OEM: NVIDIA
[    24.566] (II) VESA(0): VESA VBE OEM Software Rev: 117.25
[    24.566] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    24.566] (II) VESA(0): VESA VBE OEM Product: nVIDIA N12P-NS2  - mcln0561
[    24.566] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev
[    24.569] (II) VESA(0): virtual address = 0x7fab13eec000,
	physical address = 0xe1000000, size = 14680064
[    24.573] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[    24.651] (==) VESA(0): Default visual is TrueColor
[    24.713] (==) VESA(0): Backing store disabled
[    24.713] (==) VESA(0): DPMS enabled
[    24.713] (==) RandR enabled
[    24.713] (II) Initializing built-in extension Generic Event Extension
[    24.713] (II) Initializing built-in extension SHAPE
[    24.713] (II) Initializing built-in extension MIT-SHM
[    24.713] (II) Initializing built-in extension XInputExtension
[    24.713] (II) Initializing built-in extension XTEST
[    24.713] (II) Initializing built-in extension BIG-REQUESTS
[    24.713] (II) Initializing built-in extension SYNC
[    24.713] (II) Initializing built-in extension XKEYBOARD
[    24.713] (II) Initializing built-in extension XC-MISC
[    24.713] (II) Initializing built-in extension SECURITY
[    24.713] (II) Initializing built-in extension XINERAMA
[    24.713] (II) Initializing built-in extension XFIXES
[    24.713] (II) Initializing built-in extension RENDER
[    24.713] (II) Initializing built-in extension RANDR
[    24.713] (II) Initializing built-in extension COMPOSITE
[    24.713] (II) Initializing built-in extension DAMAGE
[    24.713] (II) Initializing built-in extension GESTURE
[    24.719] (II) AIGLX: Screen 0 is not DRI2 capable
[    24.719] (II) AIGLX: Screen 0 is not DRI capable
[    24.719] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
[    25.218] (II) AIGLX: Loaded and initialized swrast
[    25.218] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    25.223] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.230] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    25.230] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.230] (II) LoadModule: "evdev"
[    25.230] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.230] (II) Module evdev: vendor="X.Org Foundation"
[    25.230] 	compiled for 1.10.2, module version = 2.6.0
[    25.230] 	Module class: X.Org XInput Driver
[    25.230] 	ABI class: X.Org XInput driver, version 12.3
[    25.230] (II) Using input driver 'evdev' for 'Power Button'
[    25.230] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.230] (**) Power Button: always reports core events
[    25.230] (**) Power Button: Device: "/dev/input/event3"
[    25.230] (--) Power Button: Found keys
[    25.231] (II) Power Button: Configuring as keyboard
[    25.231] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    25.231] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    25.231] (**) Option "xkb_rules" "evdev"
[    25.231] (**) Option "xkb_model" "pc105"
[    25.231] (**) Option "xkb_layout" "us"
[    25.233] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    25.233] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    25.233] (II) Using input driver 'evdev' for 'Video Bus'
[    25.233] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.233] (**) Video Bus: always reports core events
[    25.233] (**) Video Bus: Device: "/dev/input/event5"
[    25.233] (--) Video Bus: Found keys
[    25.233] (II) Video Bus: Configuring as keyboard
[    25.233] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:13/LNXVIDEO:00/input/input5/event5"
[    25.233] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    25.233] (**) Option "xkb_rules" "evdev"
[    25.233] (**) Option "xkb_model" "pc105"
[    25.233] (**) Option "xkb_layout" "us"
[    25.237] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    25.237] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.237] (II) Using input driver 'evdev' for 'Power Button'
[    25.237] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.237] (**) Power Button: always reports core events
[    25.237] (**) Power Button: Device: "/dev/input/event1"
[    25.237] (--) Power Button: Found keys
[    25.237] (II) Power Button: Configuring as keyboard
[    25.237] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    25.237] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    25.237] (**) Option "xkb_rules" "evdev"
[    25.237] (**) Option "xkb_model" "pc105"
[    25.237] (**) Option "xkb_layout" "us"
[    25.237] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    25.237] (II) No input driver/identifier specified (ignoring)
[    25.238] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    25.238] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    25.238] (II) Using input driver 'evdev' for 'Sleep Button'
[    25.238] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.238] (**) Sleep Button: always reports core events
[    25.238] (**) Sleep Button: Device: "/dev/input/event2"
[    25.238] (--) Sleep Button: Found keys
[    25.238] (II) Sleep Button: Configuring as keyboard
[    25.238] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    25.238] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    25.238] (**) Option "xkb_rules" "evdev"
[    25.238] (**) Option "xkb_model" "pc105"
[    25.238] (**) Option "xkb_layout" "us"
[    25.238] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event13)
[    25.238] (II) No input driver/identifier specified (ignoring)
[    25.239] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event14)
[    25.239] (II) No input driver/identifier specified (ignoring)
[    25.239] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event15)
[    25.239] (II) No input driver/identifier specified (ignoring)
[    25.239] (II) config/udev: Adding input device Laptop_Integrated_Webcam_FHD (/dev/input/event6)
[    25.239] (**) Laptop_Integrated_Webcam_FHD: Applying InputClass "evdev keyboard catchall"
[    25.239] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_FHD'
[    25.239] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.239] (**) Laptop_Integrated_Webcam_FHD: always reports core events
[    25.239] (**) Laptop_Integrated_Webcam_FHD: Device: "/dev/input/event6"
[    25.239] (--) Laptop_Integrated_Webcam_FHD: Found keys
[    25.239] (II) Laptop_Integrated_Webcam_FHD: Configuring as keyboard
[    25.239] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input6/event6"
[    25.239] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_FHD" (type: KEYBOARD)
[    25.239] (**) Option "xkb_rules" "evdev"
[    25.239] (**) Option "xkb_model" "pc105"
[    25.239] (**) Option "xkb_layout" "us"
[    25.240] (II) config/udev: Adding input device HDA Intel PCH HP Out at Ext Left Jack (/dev/input/event10)
[    25.240] (II) No input driver/identifier specified (ignoring)
[    25.240] (II) config/udev: Adding input device HDA Intel PCH Mic at Sep Left Jack (/dev/input/event7)
[    25.240] (II) No input driver/identifier specified (ignoring)
[    25.240] (II) config/udev: Adding input device HDA Intel PCH Mic at Ext Left Jack (/dev/input/event8)
[    25.240] (II) No input driver/identifier specified (ignoring)
[    25.240] (II) config/udev: Adding input device HDA Intel PCH Line Out at Sep Left Jack (/dev/input/event9)
[    25.240] (II) No input driver/identifier specified (ignoring)
[    25.243] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    25.243] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    25.243] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    25.243] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.243] (**) AT Translated Set 2 keyboard: always reports core events
[    25.243] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    25.243] (--) AT Translated Set 2 keyboard: Found keys
[    25.243] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    25.243] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    25.243] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    25.243] (**) Option "xkb_rules" "evdev"
[    25.243] (**) Option "xkb_model" "pc105"
[    25.243] (**) Option "xkb_layout" "us"
[    25.243] (II) config/udev: Adding input device ImPS/2 ALPS GlidePoint (/dev/input/event12)
[    25.243] (**) ImPS/2 ALPS GlidePoint: Applying InputClass "evdev pointer catchall"
[    25.243] (II) Using input driver 'evdev' for 'ImPS/2 ALPS GlidePoint'
[    25.243] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.243] (**) ImPS/2 ALPS GlidePoint: always reports core events
[    25.243] (**) ImPS/2 ALPS GlidePoint: Device: "/dev/input/event12"
[    25.243] (--) ImPS/2 ALPS GlidePoint: Found 3 mouse buttons
[    25.243] (--) ImPS/2 ALPS GlidePoint: Found scroll wheel(s)
[    25.243] (--) ImPS/2 ALPS GlidePoint: Found relative axes
[    25.243] (--) ImPS/2 ALPS GlidePoint: Found x and y relative axes
[    25.243] (II) ImPS/2 ALPS GlidePoint: Configuring as mouse
[    25.243] (II) ImPS/2 ALPS GlidePoint: Adding scrollwheel support
[    25.243] (**) ImPS/2 ALPS GlidePoint: YAxisMapping: buttons 4 and 5
[    25.243] (**) ImPS/2 ALPS GlidePoint: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    25.243] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input12/event12"
[    25.243] (II) XINPUT: Adding extended input device "ImPS/2 ALPS GlidePoint" (type: MOUSE)
[    25.244] (II) ImPS/2 ALPS GlidePoint: initialized for relative axes.
[    25.244] (**) ImPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    25.244] (**) ImPS/2 ALPS GlidePoint: (accel) acceleration profile 0
[    25.244] (**) ImPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    25.244] (**) ImPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    25.244] (II) config/udev: Adding input device ImPS/2 ALPS GlidePoint (/dev/input/mouse0)
[    25.244] (II) No input driver/identifier specified (ignoring)
[    25.247] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event11)
[    25.247] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    25.247] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    25.247] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.247] (**) Dell WMI hotkeys: always reports core events
[    25.247] (**) Dell WMI hotkeys: Device: "/dev/input/event11"
[    25.247] (--) Dell WMI hotkeys: Found keys
[    25.247] (II) Dell WMI hotkeys: Configuring as keyboard
[    25.247] (**) Option "config_info" "udev:/sys/devices/virtual/input/input11/event11"
[    25.247] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[    25.247] (**) Option "xkb_rules" "evdev"
[    25.247] (**) Option "xkb_model" "pc105"
[    25.247] (**) Option "xkb_layout" "us"

```

The output of xrandr is:

```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
   640x480        60.0  

```

Can someone help me out?

---

### Post by xzased on 2012-01-17
Solved, on dmesg I was getting this message:

```
[   19.233406] [drm] nouveau 0000:01:00.0: Unsupported chipset 0x0d9160a1
```

Turns out you must enable optimus in the bios settings to have the card recognized, yep, enable optimus :popcorn:

---

