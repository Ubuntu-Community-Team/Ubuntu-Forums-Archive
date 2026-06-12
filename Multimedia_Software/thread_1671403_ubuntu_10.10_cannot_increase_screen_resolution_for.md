---
title: "ubuntu 10.10 cannot increase screen resolution for 945GM/GMS/GME, 943/940GML  card"
date: 2011-01-20
forum: Multimedia Software
---

### Post by ravimannan2002 on 2011-01-20
Hello,
I cannot increase the screen resolution after installing ubuntu 10.10.

When I go to System>Preferences>Monitors>Resolution the highest I can have is 1280X800
Based on my lspci output, I believe I have the following graphics card:
> 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

Here is the entire lspci output:
> 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)



When I do ** Xorg -configure**, I get:
> 
Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log


 When I go to **/etc/X11/** and do ** find . -name *.conf** I find nothing.

When I go to System>Administration>Additional Drivers, I find none installed.
 
Help! Thanks! :popcorn:

---

### Post by BicyclerBoy on 2011-01-20
I don't think you can run the Xorg -configure while the X sever is running.

I don't know if there is a GUI config utility for intel X server either.

Anyway post your 
/var/log/Xorg.0.log

dmesg | grep intel

My guess is that you are not using the intel i915 driver  & you have some mode validation problem with video modes.

---

### Post by ravimannan2002 on 2011-01-20
here is the log file:
> 
[    18.395] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    18.395] X Protocol Version 11, Revision 0
[    18.395] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    18.395] Current Operating System: Linux asbhatt-laptop 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686
[    18.395] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=6f9eabe9-b0ba-48fc-b803-f1de003be8ba ro quiet splash
[    18.395] Build Date: 23 November 2010  09:54:06PM
[    18.395] xorg-server 2:1.9.0-0ubuntu7.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    18.395] Current version of pixman: 0.18.4
[    18.395] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    18.395] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.395] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan 20 09:21:39 2011
[    18.420] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.420] (==) No Layout section.  Using the first Screen section.
[    18.420] (==) No screen section available. Using defaults.
[    18.420] (**) |-->Screen "Default Screen Section" (0)
[    18.420] (**) |   |-->Monitor "<default monitor>"
[    18.421] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    18.421] (==) Automatically adding devices
[    18.421] (==) Automatically enabling devices
[    18.421] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.421] 	Entry deleted from font path.
[    18.421] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    18.421] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.421] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.421] (II) Loader magic: 0x81f8e00
[    18.421] (II) Module ABI versions:
[    18.421] 	X.Org ANSI C Emulation: 0.4
[    18.421] 	X.Org Video Driver: 8.0
[    18.421] 	X.Org XInput driver : 11.0
[    18.421] 	X.Org Server Extension : 4.0
[    18.422] (--) PCI:*(0:0:2:0) 8086:27a2:103c:30bb rev 3, Mem @ 0xd8100000/524288, 0xc0000000/268435456, 0xd8200000/262144, I/O @ 0x00001800/8
[    18.422] (--) PCI: (0:0:2:1) 8086:27a6:103c:30bb rev 3, Mem @ 0xd8180000/524288
[    18.423] (II) Open ACPI successful (/var/run/acpid.socket)
[    18.423] (II) LoadModule: "extmod"
[    18.451] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    18.451] (II) Module extmod: vendor="X.Org Foundation"
[    18.451] 	compiled for 1.9.0, module version = 1.0.0
[    18.451] 	Module class: X.Org Server Extension
[    18.451] 	ABI class: X.Org Server Extension, version 4.0
[    18.451] (II) Loading extension MIT-SCREEN-SAVER
[    18.451] (II) Loading extension XFree86-VidModeExtension
[    18.451] (II) Loading extension XFree86-DGA
[    18.451] (II) Loading extension DPMS
[    18.451] (II) Loading extension XVideo
[    18.451] (II) Loading extension XVideo-MotionCompensation
[    18.451] (II) Loading extension X-Resource
[    18.451] (II) LoadModule: "dbe"
[    18.452] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    18.452] (II) Module dbe: vendor="X.Org Foundation"
[    18.452] 	compiled for 1.9.0, module version = 1.0.0
[    18.452] 	Module class: X.Org Server Extension
[    18.452] 	ABI class: X.Org Server Extension, version 4.0
[    18.452] (II) Loading extension DOUBLE-BUFFER
[    18.452] (II) LoadModule: "glx"
[    18.452] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    18.452] (II) Module glx: vendor="X.Org Foundation"
[    18.452] 	compiled for 1.9.0, module version = 1.0.0
[    18.452] 	ABI class: X.Org Server Extension, version 4.0
[    18.452] (==) AIGLX enabled
[    18.452] (II) Loading extension GLX
[    18.452] (II) LoadModule: "record"
[    18.453] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    18.453] (II) Module record: vendor="X.Org Foundation"
[    18.453] 	compiled for 1.9.0, module version = 1.13.0
[    18.453] 	Module class: X.Org Server Extension
[    18.453] 	ABI class: X.Org Server Extension, version 4.0
[    18.453] (II) Loading extension RECORD
[    18.453] (II) LoadModule: "dri"
[    18.453] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    18.453] (II) Module dri: vendor="X.Org Foundation"
[    18.453] 	compiled for 1.9.0, module version = 1.0.0
[    18.453] 	ABI class: X.Org Server Extension, version 4.0
[    18.453] (II) Loading extension XFree86-DRI
[    18.454] (II) LoadModule: "dri2"
[    18.454] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.454] (II) Module dri2: vendor="X.Org Foundation"
[    18.454] 	compiled for 1.9.0, module version = 1.2.0
[    18.454] 	ABI class: X.Org Server Extension, version 4.0
[    18.454] (II) Loading extension DRI2
[    18.454] (==) Matched intel as autoconfigured driver 0
[    18.454] (==) Matched vesa as autoconfigured driver 1
[    18.454] (==) Matched fbdev as autoconfigured driver 2
[    18.454] (==) Assigned the driver to the xf86ConfigLayout
[    18.454] (II) LoadModule: "intel"
[    18.454] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    18.455] (II) Module intel: vendor="X.Org Foundation"
[    18.455] 	compiled for 1.9.0, module version = 2.12.0
[    18.455] 	Module class: X.Org Video Driver
[    18.455] 	ABI class: X.Org Video Driver, version 8.0
[    18.455] (II) LoadModule: "vesa"
[    18.455] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    18.455] (II) Module vesa: vendor="X.Org Foundation"
[    18.455] 	compiled for 1.8.99.905, module version = 2.3.0
[    18.455] 	Module class: X.Org Video Driver
[    18.455] 	ABI class: X.Org Video Driver, version 8.0
[    18.455] (II) LoadModule: "fbdev"
[    18.455] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    18.455] (II) Module fbdev: vendor="X.Org Foundation"
[    18.455] 	compiled for 1.8.99.905, module version = 0.4.2
[    18.455] 	ABI class: X.Org Video Driver, version 8.0
[    18.455] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    18.457] (II) VESA: driver for VESA chipsets: vesa
[    18.457] (II) FBDEV: driver for framebuffer: fbdev
[    18.457] (++) using VT number 7

[    18.457] (WW) Falling back to old probe method for vesa
[    18.457] (WW) Falling back to old probe method for fbdev
[    18.457] (II) Loading sub module "fbdevhw"
[    18.457] (II) LoadModule: "fbdevhw"
[    18.458] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    18.458] (II) Module fbdevhw: vendor="X.Org Foundation"
[    18.458] 	compiled for 1.9.0, module version = 0.0.2
[    18.458] 	ABI class: X.Org Video Driver, version 8.0
[    18.461] drmOpenDevice: node name is /dev/dri/card0
[    18.461] drmOpenDevice: open result is 9, (OK)
[    18.461] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    18.461] drmOpenDevice: node name is /dev/dri/card0
[    18.461] drmOpenDevice: open result is 9, (OK)
[    18.461] drmOpenByBusid: drmOpenMinor returns 9
[    18.461] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    18.461] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    18.461] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    18.461] (==) intel(0): RGB weight 888
[    18.461] (==) intel(0): Default visual is TrueColor
[    18.461] (II) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
[    18.461] (--) intel(0): Chipset: "945GM"
[    18.461] (==) intel(0): video overlay key set to 0x101fe
[    18.492] (II) intel(0): Output VGA1 has no monitor section
[    18.492] (II) intel(0): Output LVDS1 has no monitor section
[    18.780] (II) intel(0): Output TV1 has no monitor section
[    18.812] (II) intel(0): EDID for output VGA1
[    18.812] (II) intel(0): EDID for output LVDS1
[    18.812] (II) intel(0): Manufacturer: AUO  Model: 2174  Serial#: 0
[    18.812] (II) intel(0): Year: 2005  Week: 1
[    18.812] (II) intel(0): EDID Version: 1.3
[    18.812] (II) intel(0): Digital Display Input
[    18.812] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    18.812] (II) intel(0): Gamma: 2.20
[    18.812] (II) intel(0): No DPMS capabilities specified
[    18.812] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    18.812] (II) intel(0): First detailed timing is preferred mode
[    18.812] (II) intel(0): redX: 0.590 redY: 0.345   greenX: 0.315 greenY: 0.555
[    18.812] (II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
[    18.812] (II) intel(0): Manufacturer's mask: 0
[    18.812] (II) intel(0): Supported detailed timing:
[    18.812] (II) intel(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
[    18.812] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
[    18.812] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
[    18.812] (II) intel(0): Unknown vendor-specific block f
[    18.812] (II) intel(0):  AUO
[    18.812] (II) intel(0):  B154EW02 V1
[    18.812] (II) intel(0): EDID (in hex):
[    18.812] (II) intel(0): 	00ffffffffffff0006af742100000000
[    18.812] (II) intel(0): 	010f0103802115780a1cf59758508e27
[    18.812] (II) intel(0): 	27505400000001010101010101010101
[    18.813] (II) intel(0): 	010101010101c71b00a0502017303020
[    18.813] (II) intel(0): 	36004bcf100000180000000f00000000
[    18.813] (II) intel(0): 	00000000000000000020000000fe0041
[    18.813] (II) intel(0): 	554f0a202020202020202020000000fe
[    18.813] (II) intel(0): 	004231353445573032205631200a00aa
[    18.813] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    18.813] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    18.813] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    18.813] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    18.813] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    18.813] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    18.813] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    18.813] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    18.813] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    18.813] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    18.813] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    18.813] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    18.813] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    18.813] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    18.813] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    18.813] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    18.813] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    18.813] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    18.813] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    18.813] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    18.813] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    18.813] (II) intel(0): Printing probed modes for output LVDS1
[    18.813] (II) intel(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
[    18.813] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.813] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.813] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    18.813] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    19.100] (II) intel(0): EDID for output TV1
[    19.100] (II) intel(0): Output VGA1 disconnected
[    19.100] (II) intel(0): Output LVDS1 connected
[    19.100] (II) intel(0): Output TV1 disconnected
[    19.100] (II) intel(0): Using exact sizes for initial modes
[    19.100] (II) intel(0): Output LVDS1 using initial mode 1280x800
[    19.100] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    19.100] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[    19.100] (==) intel(0): DPI set to (96, 96)
[    19.100] (II) Loading sub module "fb"
[    19.100] (II) LoadModule: "fb"
[    19.101] (II) Loading /usr/lib/xorg/modules/libfb.so
[    19.101] (II) Module fb: vendor="X.Org Foundation"
[    19.101] 	compiled for 1.9.0, module version = 1.0.0
[    19.101] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    19.101] (II) UnloadModule: "vesa"
[    19.101] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.101] (II) UnloadModule: "fbdev"
[    19.101] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    19.101] (II) UnloadModule: "fbdevhw"
[    19.101] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    19.101] (==) Depth 24 pixmap format is 32 bpp
[    19.101] (II) intel(0): [DRI2] Setup complete
[    19.101] (II) intel(0): [DRI2]   DRI driver: i915
[    19.101] (**) intel(0): Tiling enabled
[    19.101] (**) intel(0): SwapBuffers wait enabled
[    19.101] (==) intel(0): VideoRam: 262144 KB
[    19.101] (II) intel(0): Allocated new frame buffer 1280x800 stride 8192, tiled
[    19.101] (II) UXA(0): Driver registered support for the following operations:
[    19.101] (II)         solid
[    19.101] (II)         copy
[    19.101] (II)         composite (RENDER acceleration)
[    19.101] (II)         put_image
[    19.101] (II)         get_image
[    19.101] (==) intel(0): Backing store disabled
[    19.101] (==) intel(0): Silken mouse enabled
[    19.101] (II) intel(0): Initializing HW Cursor
[    19.140] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    19.140] (==) intel(0): DPMS enabled
[    19.140] (==) intel(0): Intel XvMC decoder disabled
[    19.140] (II) intel(0): Set up textured video
[    19.140] (II) intel(0): Set up overlay video
[    19.140] (II) intel(0): direct rendering: DRI2 Enabled
[    19.140] (--) RandR disabled
[    19.140] (II) Initializing built-in extension Generic Event Extension
[    19.140] (II) Initializing built-in extension SHAPE
[    19.140] (II) Initializing built-in extension MIT-SHM
[    19.140] (II) Initializing built-in extension XInputExtension
[    19.140] (II) Initializing built-in extension XTEST
[    19.140] (II) Initializing built-in extension BIG-REQUESTS
[    19.140] (II) Initializing built-in extension SYNC
[    19.140] (II) Initializing built-in extension XKEYBOARD
[    19.140] (II) Initializing built-in extension XC-MISC
[    19.140] (II) Initializing built-in extension SECURITY
[    19.140] (II) Initializing built-in extension XINERAMA
[    19.141] (II) Initializing built-in extension XFIXES
[    19.141] (II) Initializing built-in extension RENDER
[    19.141] (II) Initializing built-in extension RANDR
[    19.141] (II) Initializing built-in extension COMPOSITE
[    19.141] (II) Initializing built-in extension DAMAGE
[    19.141] (II) Initializing built-in extension GESTURE
[    19.158] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    19.158] (II) AIGLX: enabled GLX_INTEL_swap_event
[    19.158] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    19.158] (II) AIGLX: enabled GLX_SGI_make_current_read
[    19.158] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    19.158] (II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
[    19.158] (II) GLX: Initialized DRI2 GL provider for screen 0
[    19.159] (II) intel(0): Setting screen physical size to 338 x 211
[    19.184] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.194] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    19.194] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.194] (II) LoadModule: "evdev"
[    19.194] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.194] (II) Module evdev: vendor="X.Org Foundation"
[    19.194] 	compiled for 1.9.0, module version = 2.3.2
[    19.194] 	Module class: X.Org XInput Driver
[    19.194] 	ABI class: X.Org XInput driver, version 11.0
[    19.194] (**) Power Button: always reports core events
[    19.194] (**) Power Button: Device: "/dev/input/event3"
[    19.195] (II) Power Button: Found keys
[    19.195] (II) Power Button: Configuring as keyboard
[    19.195] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    19.195] (**) Option "xkb_rules" "evdev"
[    19.195] (**) Option "xkb_model" "pc105"
[    19.195] (**) Option "xkb_layout" "us"
[    19.195] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    19.195] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    19.195] (**) Video Bus: always reports core events
[    19.196] (**) Video Bus: Device: "/dev/input/event5"
[    19.196] (II) Video Bus: Found keys
[    19.196] (II) Video Bus: Configuring as keyboard
[    19.196] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    19.196] (**) Option "xkb_rules" "evdev"
[    19.196] (**) Option "xkb_model" "pc105"
[    19.196] (**) Option "xkb_layout" "us"
[    19.197] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    19.197] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.197] (**) Power Button: always reports core events
[    19.198] (**) Power Button: Device: "/dev/input/event0"
[    19.198] (II) Power Button: Found keys
[    19.198] (II) Power Button: Configuring as keyboard
[    19.198] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    19.198] (**) Option "xkb_rules" "evdev"
[    19.198] (**) Option "xkb_model" "pc105"
[    19.198] (**) Option "xkb_layout" "us"
[    19.198] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    19.198] (II) No input driver/identifier specified (ignoring)
[    19.198] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    19.198] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    19.199] (**) Sleep Button: always reports core events
[    19.199] (**) Sleep Button: Device: "/dev/input/event1"
[    19.199] (II) Sleep Button: Found keys
[    19.199] (II) Sleep Button: Configuring as keyboard
[    19.199] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    19.199] (**) Option "xkb_rules" "evdev"
[    19.199] (**) Option "xkb_model" "pc105"
[    19.199] (**) Option "xkb_layout" "us"
[    19.204] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    19.204] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    19.204] (**) AT Translated Set 2 keyboard: always reports core events
[    19.204] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    19.204] (II) AT Translated Set 2 keyboard: Found keys
[    19.204] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    19.204] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    19.204] (**) Option "xkb_rules" "evdev"
[    19.204] (**) Option "xkb_model" "pc105"
[    19.204] (**) Option "xkb_layout" "us"
[    19.205] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    19.205] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    19.205] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    19.205] (II) LoadModule: "synaptics"
[    19.205] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    19.205] (II) Module synaptics: vendor="X.Org Foundation"
[    19.205] 	compiled for 1.9.0, module version = 1.2.2
[    19.205] 	Module class: X.Org XInput Driver
[    19.205] 	ABI class: X.Org XInput driver, version 11.0
[    19.205] (II) Synaptics touchpad driver version 1.2.2
[    19.205] (**) Option "Device" "/dev/input/event7"
[    19.205] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    19.205] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    19.205] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    19.205] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    19.205] (II) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    19.205] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    19.205] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    19.205] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    19.205] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    19.205] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    19.205] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    19.205] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    19.206] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    19.206] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    19.206] (II) No input driver/identifier specified (ignoring)
[    19.209] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event6)
[    19.209] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    19.209] (**) HP WMI hotkeys: always reports core events
[    19.209] (**) HP WMI hotkeys: Device: "/dev/input/event6"
[    19.209] (II) HP WMI hotkeys: Found keys
[    19.209] (II) HP WMI hotkeys: Configuring as keyboard
[    19.209] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD)
[    19.209] (**) Option "xkb_rules" "evdev"
[    19.209] (**) Option "xkb_model" "pc105"
[    19.209] (**) Option "xkb_layout" "us"
[    19.712] (II) intel(0): EDID vendor "AUO", prod id 8564
[    19.712] (II) intel(0): Printing DDC gathered Modelines:
[    19.712] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
[    20.032] (II) intel(0): EDID vendor "AUO", prod id 8564
[    20.032] (II) intel(0): Printing DDC gathered Modelines:
[    20.032] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
[    20.360] (II) intel(0): EDID vendor "AUO", prod id 8564
[    20.360] (II) intel(0): Printing DDC gathered Modelines:
[    20.360] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
[    20.680] (II) intel(0): EDID vendor "AUO", prod id 8564
[    20.680] (II) intel(0): Printing DDC gathered Modelines:
[    20.680] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
[   931.884] (II) intel(0): EDID vendor "AUO", prod id 8564
[   931.884] (II) intel(0): Printing DDC gathered Modelines:
[   931.884] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
[  1238.372] (II) intel(0): EDID vendor "AUO", prod id 8564
[  1238.372] (II) intel(0): Printing DDC gathered Modelines:
[  1238.372] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
[  1238.708] (II) intel(0): EDID vendor "AUO", prod id 8564
[  1238.708] (II) intel(0): Printing DDC gathered Modelines:
[  1238.708] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
[  1239.028] (II) intel(0): EDID vendor "AUO", prod id 8564
[  1239.028] (II) intel(0): Printing DDC gathered Modelines:
[  1239.028] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
[  1239.920] (II) intel(0): EDID vendor "AUO", prod id 8564
[  1239.920] (II) intel(0): Printing DDC gathered Modelines:
[  1239.920] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
[  1245.244] (II) intel(0): EDID vendor "AUO", prod id 8564
[  1245.244] (II) intel(0): Printing DDC gathered Modelines:
[  1245.244] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)


**# dmesg | grep intel**> 
[    0.205277] intel_idle: MWAIT substates: 0x22220
[    0.205279] intel_idle: does not run on family 6 model 14
[   15.730435] intel_rng: FWH not detected
[   16.191004] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[   16.191458] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   16.253792] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   17.668327] fb0: inteldrmfb frame buffer device



---

### Post by BicyclerBoy on 2011-01-20
Your internal LCD panel is LVDS1.
This reports EDID okay & the max is 1280x800.
The video driver is i915.

All this looks okay to me..
Are you sure 1280x800 is NOT the native resolution of the LCD panel ?

---

### Post by ravimannan2002 on 2011-01-20
How do I check the max resolution for this graphics card? I've tried *googling*. My skills are not adequate I suppose.

I dual boot into windows xp. I will check the screen resolution available there.

Whoops! It looks like the resolution I have it at is the max!
D'OH!

The screen looked HUGE. I wasn't used to it. I just changed the font sizes under Appearance >Font.
Specifically the window title, desktop and application font.
It looks better now.

Thanks for the help!

---

