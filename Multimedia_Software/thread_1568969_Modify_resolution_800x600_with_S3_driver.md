---
title: "Modify resolution 800x600 with S3 driver"
date: 2010-09-06
forum: Multimedia Software
---

### Post by c.monty on 2010-09-06
Hello!

I've performed a fresh installation of Lubuntu 10.04 on a rather old PC hardware. Unfortunatly the displayed resolution is only 800x600 although the used graphic card can run with higher resolution (at least with Windows).

According to this [thread]("http://ubuntuforums.org/showthread.php?t=1270996") one could modify the resolution using xorg.conf.

Below the information for the graphic card:
```

benutzer@pc1-lubuntu:~$ hwinfo --gfxcard
19: PCI 09.0: 0300 VGA compatible controller (VGA)              
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_5333_8811
  Unique ID: WL76.Sb41r_OO4UA
  SysFS ID: /devices/pci0000:00/0000:00:09.0
  SysFS BusID: 0000:00:09.0
  Hardware Class: graphics card
  Model: "S3 86c764/765 [Trio32/64/64V+]"
  Vendor: pci 0x5333 "S3 Inc."
  Device: pci 0x8811 "86c764/765 [Trio32/64/64V+]"
  Driver: "s3fb"
  Driver Modules: "s3fb"
  Memory Range: 0x20000000-0x207fffff (rw,non-prefetchable)
  Memory Range: 0xcf7f0000-0xcf7fffff (ro,prefetchable,disabled)
  IRQ: 17 (no events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00005333d00008811sv00000000sd00000000bc03sc00i00"
  Driver Info #0:
    Driver Status: s3fb is active
    Driver Activation Cmd: "modprobe s3fb"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

Primary display adapter: #19

benutzer@pc1-lubuntu:~$ lspci -nnk | grep -i VGA -A2
00:09.0 VGA compatible controller [0300]: S3 Inc. 86c764/765 [Trio32/64/64V+] [5333:8811]
	Kernel driver in use: s3fb
	Kernel modules: s3fb

```

I'm not sure whether Xorg.0.log provides information for the cause:
```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux pc1-lubuntu 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=404d05ac-f0b8-4ceb-ad3a-4c768c2360f8 ro quiet splash
Build Date: 21 July 2010  12:47:34PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 30 18:32:55 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
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

(--) PCI:*(0:0:9:0) 5333:8811:0000:0000 S3 Inc. 86c764/765 [Trio32/64/64V+] rev 0, Mem @ 0x20000000/8388608, BIOS @ 0x????????/65536
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
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
(==) Matched s3 as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "s3"
(II) Loading /usr/lib/xorg/modules/drivers/s3_drv.so
(II) Module s3: vendor="X.Org Foundation"
	compiled for 1.7.2, module version = 0.6.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.4.1
	ABI class: X.Org Video Driver, version 6.0
(II) S3: driver (version 0.6.3 for S3 chipset: 964-0, 964-1, 968,
	Trio32/64, Aurora64V+, Trio64UV+, Trio64V2/DX/GX
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:09:0
(WW) Falling back to old probe method for s3
(--) Assigning device section with no busID to primary device
(--) Chipset Trio32/64 found
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.1.0
	ABI class: X.Org Video Driver, version 6.0
(II) s3(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) s3(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) s3(0): Depth 24, (--) framebuffer bpp 32
(==) s3(0): RGB weight 888
(==) s3(0): Default visual is TrueColor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Video Driver, version 6.0
(II) s3(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Video Driver, version 6.0
(II) s3(0): VESA BIOS detected
(II) s3(0): VESA VBE Version 1.2
(II) s3(0): VESA VBE Total Mem: 2048 kB
(II) s3(0): VESA VBE OEM: S3 Incorporated. Trio64
(==) s3(0): Using gamma correction (1.0, 1.0, 1.0)
(**) s3(0): Chipset: "Trio32/64"
(--) s3(0): Framebuffer @ 0x20000000
(--) s3(0): videoRam = 2048 Kb
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(WW) s3(0): libpciaccess failed to read video BIOS: Unknown error 4294967282
(--) s3(0): MCLK 59.957 Mhz
(--) s3(0): RefClock: 16000
(--) s3(0): Max pixel clock at this depth is 50 Mhz
(II) s3(0): <default monitor>: Using default hsync range of 31.50-37.90 kHz
(II) s3(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
(WW) s3(0): Unable to estimate virtual size
(II) s3(0): Clock range:  15.60 to  50.00 MHz
(II) s3(0): Not using default mode "640x350" (vrefresh out of range)
(II) s3(0): Not using default mode "320x175" (vrefresh out of range)
(II) s3(0): Not using default mode "640x400" (vrefresh out of range)
(II) s3(0): Not using default mode "320x200" (vrefresh out of range)
(II) s3(0): Not using default mode "720x400" (vrefresh out of range)
(II) s3(0): Not using default mode "360x200" (vrefresh out of range)
(II) s3(0): Not using default mode "640x480" (vrefresh out of range)
(II) s3(0): Not using default mode "320x240" (vrefresh out of range)
(II) s3(0): Not using default mode "640x480" (vrefresh out of range)
(II) s3(0): Not using default mode "320x240" (vrefresh out of range)
(II) s3(0): Not using default mode "640x480" (hsync out of range)
(II) s3(0): Not using default mode "320x240" (hsync out of range)
(II) s3(0): Not using default mode "800x600" (hsync out of range)
(II) s3(0): Not using default mode "400x300" (hsync out of range)
(II) s3(0): Not using default mode "800x600" (hsync out of range)
(II) s3(0): Not using default mode "400x300" (hsync out of range)
(II) s3(0): Not using default mode "800x600" (hsync out of range)
(II) s3(0): Not using default mode "400x300" (hsync out of range)
(II) s3(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) s3(0): Not using default mode "512x384" (vrefresh out of range)
(II) s3(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) s3(0): Not using default mode "512x384" (hsync out of range)
(II) s3(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) s3(0): Not using default mode "512x384" (hsync out of range)
(II) s3(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) s3(0): Not using default mode "512x384" (hsync out of range)
(II) s3(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) s3(0): Not using default mode "512x384" (hsync out of range)
(II) s3(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) s3(0): Not using default mode "576x432" (hsync out of range)
(II) s3(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) s3(0): Not using default mode "640x480" (hsync out of range)
(II) s3(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) s3(0): Not using default mode "640x480" (hsync out of range)
(II) s3(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) s3(0): Not using default mode "640x512" (hsync out of range)
(II) s3(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) s3(0): Not using default mode "640x512" (hsync out of range)
(II) s3(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) s3(0): Not using default mode "640x512" (hsync out of range)
(II) s3(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) s3(0): Not using default mode "800x600" (hsync out of range)
(II) s3(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) s3(0): Not using default mode "800x600" (hsync out of range)
(II) s3(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) s3(0): Not using default mode "800x600" (hsync out of range)
(II) s3(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) s3(0): Not using default mode "800x600" (hsync out of range)
(II) s3(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) s3(0): Not using default mode "800x600" (hsync out of range)
(II) s3(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) s3(0): Not using default mode "896x672" (insufficient memory for mode)
(II) s3(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) s3(0): Not using default mode "896x672" (insufficient memory for mode)
(II) s3(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) s3(0): Not using default mode "928x696" (insufficient memory for mode)
(II) s3(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) s3(0): Not using default mode "928x696" (insufficient memory for mode)
(II) s3(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) s3(0): Not using default mode "960x720" (insufficient memory for mode)
(II) s3(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) s3(0): Not using default mode "960x720" (insufficient memory for mode)
(II) s3(0): Not using default mode "832x624" (hsync out of range)
(II) s3(0): Not using default mode "416x312" (hsync out of range)
(II) s3(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) s3(0): Not using default mode "576x432" (hsync out of range)
(II) s3(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) s3(0): Not using default mode "576x432" (hsync out of range)
(II) s3(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) s3(0): Not using default mode "576x432" (hsync out of range)
(II) s3(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) s3(0): Not using default mode "576x432" (hsync out of range)
(II) s3(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) s3(0): Not using default mode "576x432" (hsync out of range)
(II) s3(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) s3(0): Not using default mode "576x432" (hsync out of range)
(II) s3(0): Not using default mode "1360x768" (insufficient memory for mode)
(II) s3(0): Not using default mode "680x384" (hsync out of range)
(II) s3(0): Not using default mode "1360x768" (insufficient memory for mode)
(II) s3(0): Not using default mode "680x384" (hsync out of range)
(II) s3(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) s3(0): Not using default mode "700x525" (hsync out of range)
(II) s3(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) s3(0): Not using default mode "700x525" (hsync out of range)
(II) s3(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) s3(0): Not using default mode "700x525" (hsync out of range)
(II) s3(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) s3(0): Not using default mode "700x525" (hsync out of range)
(II) s3(0): Not using default mode "1440x900" (insufficient memory for mode)
(II) s3(0): Not using default mode "720x450" (hsync out of range)
(II) s3(0): Not using default mode "1600x1024" (insufficient memory for mode)
(II) s3(0): Not using default mode "800x512" (hsync out of range)
(II) s3(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) s3(0): Not using default mode "840x525" (hsync out of range)
(II) s3(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) s3(0): Not using default mode "840x525" (hsync out of range)
(II) s3(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) s3(0): Not using default mode "840x525" (hsync out of range)
(II) s3(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) s3(0): Not using default mode "840x525" (hsync out of range)
(II) s3(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) s3(0): Not using default mode "840x525" (hsync out of range)
(II) s3(0): Not using default mode "1920x1080" (insufficient memory for mode)
(II) s3(0): Not using default mode "960x540" (hsync out of range)
(II) s3(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) s3(0): Not using default mode "960x600" (insufficient memory for mode)
(II) s3(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) s3(0): Not using default mode "960x720" (insufficient memory for mode)
(II) s3(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) s3(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) s3(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) s3(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) s3(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) s3(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) s3(0): Not using mode "320x240" (bad mode clock/interlace/doublescan)
(--) s3(0): Virtual size is 800x600 (pitch 800)
(**) s3(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) s3(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) s3(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) s3(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) s3(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) s3(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) s3(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) s3(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) s3(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) s3(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(==) s3(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.1
	ABI class: X.Org Video Driver, version 6.0
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(==) s3(0): Backing store disabled
(II) s3(0): Memory manager initialized to (0,0) (800,655)
(II) s3(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Lines
	Setting up tile and stipple cache:
		7 32x55 slots
(II) s3(0): Acceleration enabled
(II) s3(0): Using PIO
(II) s3(0): Using SW cursor
(==) s3(0): DPMS enabled
(**) s3(0): Overlay video isn't supported by video hardware. Disabled.
(==) RandR enabled
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
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
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
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "de"
(**) Option "xkb_variant" "nodeadkeys"
(II) XKB: reuse xkmfile /var/lib/xkb/server-84CA2CD290FA78358D33127D25A86D7EAC12A9E5.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "de"
(**) Option "xkb_variant" "nodeadkeys"
(II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event4)
(**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) Logitech USB-PS/2 Optical Mouse: always reports core events
(**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event4"
(II) Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
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
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "de"
(**) Option "xkb_variant" "nodeadkeys"
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

```

Attached you'll find output of glxinfo and complete Xorg.0.log.

Kann I somehow force the usage of higher resolution 1024x768? Is the xorg.conf needed for that?

Thanks for your support.

---

### Post by realzippy on 2010-09-06
(II) s3(0): Not using default mode "1024x768" ([COLOR="Red"]insufficient memory for mode[/COLOR])

..looks like your graphics card has not enough RAM for displaying 1024x768

Decreasing (xorg.conf) colour depth from 24 to 16
might allow 1024x768....


You not seem to have a xorg.conf file,so you had to create one.
If you need help on this,just ask...

---

