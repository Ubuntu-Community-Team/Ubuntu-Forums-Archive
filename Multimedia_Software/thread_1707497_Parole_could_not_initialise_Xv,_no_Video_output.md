---
title: "Parole could not initialise Xv, no Video output"
date: 2011-03-15
forum: Multimedia Software
---

### Post by Frankynstone on 2011-03-15
Hi X11 experts and Xfce users,

I've just installed Xubuntu 10.10 on a ThinkPad R50e and on a R51. I want to get them working as fast as possible. Of cause, all updates are done and all codecs for gstreamer have been installed, too.

Parole Media Player tells me to not be able to initialise Xv output, so no video appears on screen.

Then I've started to search for the cause of trouble. Seems to be an **Intel** grafics adaptor handled by the **Vesa** module, which I don't know how to change to the correct Intel module (which is installed, by the way).

I've googled for this issue and found few other people talking about. But there was no solution, at least none that I could understand.

Now, I would be really glad if you could help me to find a working solution during the next few days.

so long and sorry for bad English

Franky

```
~$ xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present
```
```
~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
02:00.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 03)
02:00.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82541GI Gigabit Ethernet Controller
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
```
Xorg.0.log
```
[    14.247] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    14.247] X Protocol Version 11, Revision 0
[    14.247] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    14.247] Current Operating System: Linux noob5 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011 i686
[    14.247] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-27-generic root=UUID=960750fe-abfd-4bfd-88f9-cd00ca53fdeb ro quiet splash
[    14.247] Build Date: 09 January 2011  12:14:58PM
[    14.247] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    14.247] Current version of pixman: 0.18.4
[    14.247] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    14.247] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.247] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar 15 12:13:49 2011
[    14.286] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.498] (==) No Layout section.  Using the first Screen section.
[    14.498] (==) No screen section available. Using defaults.
[    14.498] (**) |-->Screen "Default Screen Section" (0)
[    14.498] (**) |   |-->Monitor "<default monitor>"
[    14.499] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    14.499] (==) Automatically adding devices
[    14.499] (==) Automatically enabling devices
[    14.677] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.677] 	Entry deleted from font path.
[    14.723] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    14.723] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.723] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.723] (II) Loader magic: 0x81f9b00
[    14.723] (II) Module ABI versions:
[    14.723] 	X.Org ANSI C Emulation: 0.4
[    14.723] 	X.Org Video Driver: 8.0
[    14.723] 	X.Org XInput driver : 11.0
[    14.723] 	X.Org Server Extension : 4.0
[    14.724] (--) PCI:*(0:0:2:0) 8086:3582:1014:0557 rev 2, Mem @ 0xe0000000/134217728, 0xd0000000/524288, I/O @ 0x00001800/8
[    14.724] (--) PCI: (0:0:2:1) 8086:3582:1014:0557 rev 2, Mem @ 0xe8000000/134217728, 0xd0080000/524288
[    14.725] (II) Open ACPI successful (/var/run/acpid.socket)
[    14.725] (II) LoadModule: "extmod"
[    14.858] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.866] (II) Module extmod: vendor="X.Org Foundation"
[    14.866] 	compiled for 1.9.0, module version = 1.0.0
[    14.866] 	Module class: X.Org Server Extension
[    14.866] 	ABI class: X.Org Server Extension, version 4.0
[    14.866] (II) Loading extension MIT-SCREEN-SAVER
[    14.866] (II) Loading extension XFree86-VidModeExtension
[    14.866] (II) Loading extension XFree86-DGA
[    14.866] (II) Loading extension DPMS
[    14.866] (II) Loading extension XVideo
[    14.866] (II) Loading extension XVideo-MotionCompensation
[    14.866] (II) Loading extension X-Resource
[    14.866] (II) LoadModule: "dbe"
[    14.867] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.876] (II) Module dbe: vendor="X.Org Foundation"
[    14.876] 	compiled for 1.9.0, module version = 1.0.0
[    14.876] 	Module class: X.Org Server Extension
[    14.876] 	ABI class: X.Org Server Extension, version 4.0
[    14.876] (II) Loading extension DOUBLE-BUFFER
[    14.876] (II) LoadModule: "glx"
[    14.876] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.883] (II) Module glx: vendor="X.Org Foundation"
[    14.883] 	compiled for 1.9.0, module version = 1.0.0
[    14.883] 	ABI class: X.Org Server Extension, version 4.0
[    14.885] (==) AIGLX enabled
[    14.885] (II) Loading extension GLX
[    14.885] (II) LoadModule: "record"
[    14.885] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.894] (II) Module record: vendor="X.Org Foundation"
[    14.894] 	compiled for 1.9.0, module version = 1.13.0
[    14.894] 	Module class: X.Org Server Extension
[    14.894] 	ABI class: X.Org Server Extension, version 4.0
[    14.894] (II) Loading extension RECORD
[    14.894] (II) LoadModule: "dri"
[    14.894] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.907] (II) Module dri: vendor="X.Org Foundation"
[    14.907] 	compiled for 1.9.0, module version = 1.0.0
[    14.907] 	ABI class: X.Org Server Extension, version 4.0
[    14.907] (II) Loading extension XFree86-DRI
[    14.907] (II) LoadModule: "dri2"
[    14.907] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.908] (II) Module dri2: vendor="X.Org Foundation"
[    14.908] 	compiled for 1.9.0, module version = 1.2.0
[    14.908] 	ABI class: X.Org Server Extension, version 4.0
[    14.908] (II) Loading extension DRI2
[    14.908] (==) Matched vesa as autoconfigured driver 0
[    14.908] (==) Matched fbdev as autoconfigured driver 1
[    14.908] (==) Assigned the driver to the xf86ConfigLayout
[    14.908] (II) LoadModule: "vesa"
[    14.908] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.912] (II) Module vesa: vendor="X.Org Foundation"
[    14.912] 	compiled for 1.8.99.905, module version = 2.3.0
[    14.912] 	Module class: X.Org Video Driver
[    14.912] 	ABI class: X.Org Video Driver, version 8.0
[    14.912] (II) LoadModule: "fbdev"
[    14.912] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.924] (II) Module fbdev: vendor="X.Org Foundation"
[    14.924] 	compiled for 1.8.99.905, module version = 0.4.2
[    14.924] 	ABI class: X.Org Video Driver, version 8.0
[    14.924] (II) VESA: driver for VESA chipsets: vesa
[    14.924] (II) FBDEV: driver for framebuffer: fbdev
[    14.924] (++) using VT number 7

[    14.924] (EE) VESA: Kernel modesetting driver in use, refusing to load
[    14.924] (WW) Falling back to old probe method for vesa
[    14.924] (II) Loading sub module "fbdevhw"
[    14.924] (II) LoadModule: "fbdevhw"
[    14.925] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    14.926] (II) Module fbdevhw: vendor="X.Org Foundation"
[    14.926] 	compiled for 1.9.0, module version = 0.0.2
[    14.926] 	ABI class: X.Org Video Driver, version 8.0
[    14.926] (**) FBDEV(0): claimed PCI slot 0@0:2:0
[    14.926] (II) FBDEV(0): using default device
[    14.926] (II) FBDEV(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    14.926] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    14.926] (==) FBDEV(0): RGB weight 888
[    14.926] (==) FBDEV(0): Default visual is TrueColor
[    14.926] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    14.926] (II) FBDEV(0): hardware: inteldrmfb (video memory: 3072kB)
[    14.926] (II) FBDEV(0): checking modes against framebuffer device...
[    14.926] (II) FBDEV(0): checking modes against monitor...
[    14.926] (--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
[    14.926] (**) FBDEV(0):  Built-in mode "current"
[    14.926] (==) FBDEV(0): DPI set to (96, 96)
[    14.926] (II) Loading sub module "fb"
[    14.926] (II) LoadModule: "fb"
[    14.926] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.004] (II) Module fb: vendor="X.Org Foundation"
[    15.004] 	compiled for 1.9.0, module version = 1.0.0
[    15.004] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    15.004] (**) FBDEV(0): using shadow framebuffer
[    15.004] (II) Loading sub module "shadow"
[    15.004] (II) LoadModule: "shadow"
[    15.005] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    15.005] (II) Module shadow: vendor="X.Org Foundation"
[    15.005] 	compiled for 1.9.0, module version = 1.1.0
[    15.006] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    15.006] (==) Depth 24 pixmap format is 32 bpp
[    15.402] (==) FBDEV(0): Backing store disabled
[    15.402] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.402] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.402] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.402] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.402] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.402] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.402] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.402] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.402] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.402] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.403] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.404] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.405] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.406] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.407] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.407] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.407] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.407] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.407] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.407] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.407] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.407] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.407] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.407] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.407] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.407] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.407] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.407] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.407] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.407] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    15.407] (==) FBDEV(0): DPMS enabled
[    15.407] (==) RandR enabled
[    15.407] (II) Initializing built-in extension Generic Event Extension
[    15.407] (II) Initializing built-in extension SHAPE
[    15.407] (II) Initializing built-in extension MIT-SHM
[    15.407] (II) Initializing built-in extension XInputExtension
[    15.407] (II) Initializing built-in extension XTEST
[    15.407] (II) Initializing built-in extension BIG-REQUESTS
[    15.407] (II) Initializing built-in extension SYNC
[    15.407] (II) Initializing built-in extension XKEYBOARD
[    15.407] (II) Initializing built-in extension XC-MISC
[    15.407] (II) Initializing built-in extension SECURITY
[    15.407] (II) Initializing built-in extension XINERAMA
[    15.407] (II) Initializing built-in extension XFIXES
[    15.407] (II) Initializing built-in extension RENDER
[    15.407] (II) Initializing built-in extension RANDR
[    15.407] (II) Initializing built-in extension COMPOSITE
[    15.407] (II) Initializing built-in extension DAMAGE
[    15.407] (II) Initializing built-in extension GESTURE
[    15.431] (II) AIGLX: Screen 0 is not DRI2 capable
[    15.431] (II) AIGLX: Screen 0 is not DRI capable
[    15.551] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[    15.551] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    15.968] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    16.009] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    16.009] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.009] (II) LoadModule: "evdev"
[    16.052] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.162] (II) Module evdev: vendor="X.Org Foundation"
[    16.162] 	compiled for 1.9.0, module version = 2.3.2
[    16.162] 	Module class: X.Org XInput Driver
[    16.162] 	ABI class: X.Org XInput driver, version 11.0
[    16.162] (**) Power Button: always reports core events
[    16.162] (**) Power Button: Device: "/dev/input/event2"
[    16.162] (II) Power Button: Found keys
[    16.162] (II) Power Button: Configuring as keyboard
[    16.162] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    16.162] (**) Option "xkb_rules" "evdev"
[    16.162] (**) Option "xkb_model" "evdev"
[    16.162] (**) Option "xkb_layout" "de"
[    16.167] (II) XKB: reuse xkmfile /var/lib/xkb/server-1B5353734E7854C1F2B0553E65A16986C9AAC402.xkm
[    16.174] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    16.174] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    16.174] (**) Video Bus: always reports core events
[    16.174] (**) Video Bus: Device: "/dev/input/event5"
[    16.174] (II) Video Bus: Found keys
[    16.174] (II) Video Bus: Configuring as keyboard
[    16.174] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    16.175] (**) Option "xkb_rules" "evdev"
[    16.175] (**) Option "xkb_model" "evdev"
[    16.175] (**) Option "xkb_layout" "de"
[    16.176] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    16.176] (II) No input driver/identifier specified (ignoring)
[    16.177] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    16.177] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    16.177] (**) Sleep Button: always reports core events
[    16.177] (**) Sleep Button: Device: "/dev/input/event1"
[    16.177] (II) Sleep Button: Found keys
[    16.177] (II) Sleep Button: Configuring as keyboard
[    16.177] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    16.177] (**) Option "xkb_rules" "evdev"
[    16.177] (**) Option "xkb_model" "evdev"
[    16.177] (**) Option "xkb_layout" "de"
[    16.184] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    16.184] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    16.184] (**) AT Translated Set 2 keyboard: always reports core events
[    16.184] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    16.184] (II) AT Translated Set 2 keyboard: Found keys
[    16.184] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    16.184] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    16.184] (**) Option "xkb_rules" "evdev"
[    16.184] (**) Option "xkb_model" "evdev"
[    16.184] (**) Option "xkb_layout" "de"
[    16.185] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[    16.185] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    16.185] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    16.185] (II) LoadModule: "synaptics"
[    16.185] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    16.204] (II) Module synaptics: vendor="X.Org Foundation"
[    16.204] 	compiled for 1.9.0, module version = 1.2.2
[    16.204] 	Module class: X.Org XInput Driver
[    16.204] 	ABI class: X.Org XInput driver, version 11.0
[    16.204] (II) Synaptics touchpad driver version 1.2.2
[    16.204] (**) Option "Device" "/dev/input/event6"
[    16.204] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    16.204] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    16.204] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    16.204] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    16.204] (II) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    16.204] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    16.204] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    16.204] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    16.204] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    16.204] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    16.204] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    16.204] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    16.205] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    16.205] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    16.205] (II) No input driver/identifier specified (ignoring)
[    16.205] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event7)
[    16.205] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[    16.205] (**) TPPS/2 IBM TrackPoint: always reports core events
[    16.205] (**) TPPS/2 IBM TrackPoint: Device: "/dev/input/event7"
[    16.205] (II) TPPS/2 IBM TrackPoint: Found 3 mouse buttons
[    16.205] (II) TPPS/2 IBM TrackPoint: Found relative axes
[    16.205] (II) TPPS/2 IBM TrackPoint: Found x and y relative axes
[    16.206] (II) TPPS/2 IBM TrackPoint: Configuring as mouse
[    16.206] (**) TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
[    16.206] (**) TPPS/2 IBM TrackPoint: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.206] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE)
[    16.206] (II) TPPS/2 IBM TrackPoint: initialized for relative axes.
[    16.206] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse1)
[    16.206] (II) No input driver/identifier specified (ignoring)
[    16.207] (II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event4)
[    16.207] (**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
[    16.207] (**) ThinkPad Extra Buttons: always reports core events
[    16.207] (**) ThinkPad Extra Buttons: Device: "/dev/input/event4"
[    16.207] (II) ThinkPad Extra Buttons: Found keys
[    16.207] (II) ThinkPad Extra Buttons: Configuring as keyboard
[    16.207] (II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD)
[    16.207] (**) Option "xkb_rules" "evdev"
[    16.207] (**) Option "xkb_model" "evdev"
[    16.207] (**) Option "xkb_layout" "de"

```

---

### Post by Frankynstone on 2011-03-15
Well, a friend found a possible solution and it works :popcorn: finally it's cinema time.

/etc/X11/Xorg.conf did not exist and had to be created with the following contents:
```
Section "Device"
Identifier     "Intel "
Driver         "intel"
EndSection
```
After reboot, Xorg.0.log contains several intel entries which means that Xorg.conf is effective, indeed. Parole plays fine, but I think its reactions on mouse ore keyboard actions are not as fast as of Totem.

I'll stick with Parole, just to don't mix Gnome and Xfce not too much :P

---

### Post by Jerome Warnier on 2012-05-08
Actually, some drivers do not support Xv at all.
In this case, you can still use the "--xv false" option to Parole on the command-line to permanently tell him not to use Xv. And to change it back: "parole --xv true".

Hope it helps

---

### Post by tbc on 2012-09-29
This was my problem. Your explanation solved it. Thank you!

---

