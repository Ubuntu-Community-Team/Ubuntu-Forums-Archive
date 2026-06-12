---
title: "ubuntu 12.04lts screen brightness won't change"
date: 2013-10-22
forum: Multimedia Software
---

### Post by n3wbvip3r on 2013-10-22
i know its been asked before, but nothing i do, fixes the issue. i have changed the xorg and grub files, with all different settings and changes to no use. changing those, the issue gets worse. when i use the FN key along with the brightness, it shows the brightness value going up and down, but the screen does nothing. after changing the grub file 10 times with different settings, upon logging back from reboot, the FN function no longer works. now, when first installed, the brightness worked perfect. up until i installed the 13.4 catalyst driver for my ati. my pc is an acer 5253, c50 with integrated 6250 graphics. i notice a nice difference in performance, plus can play video in higher res. i'd like to keep this driver. but, i'd like my FN key to work. the driver is working, i checked, but how can i fix this!! driving me crazy lol. change reboot change reboot change reboot has been my past 2 days. i am a bit of a beginner, but learning quickly. any help would be great. thanks!

---

### Post by cmcanulty on 2013-10-22
have you tried installing xbacklight and making it a startup app

---

### Post by n3wbvip3r on 2013-10-22
from what i have read from other posts, that program requires the terminal to use. which seems like a ton of work just to dim my screen. i'll check it out, and if its not that way, than this is just me being ignorant. lol. i have no problem with the brightness of my screen, but i want to be able to turn it down when i am low on battery. i know there is a ton of hack workarounds. i don't want to use hack workarounds, i was wondering if there is a fix i haven't tried to solve the issue. i imagine that there would be a command or something to fix what is wrong. i am leaning towards it being my ati driver. i see a ton of posts with this issue related to nvidia drivers, which if you add a line to xorg, it works. but i am having a hard time tracking down a fix with ati drivers. if i roll back to the radeon driver, it works. but when adding the 13.4 CCC drivers from ati, it stops.

---

### Post by n3wbvip3r on 2013-10-22
well, here is something new. when i mash on the key 100 times the brightness will eventually do something. not consistent. random. i don't know what to do anymore. i tried:

[http://ubuntuforums.org/showthread.php?t=1994654](http://ubuntuforums.org/showthread.php?t=1994654)

and editing xorg. but my org looks like:

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection


Section "Module"
EndSection


Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection


Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:0:1:0"
EndSection


Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


now, i heard the "device" section is where to put an "option" but i see the one above that has all my ati stuff with "options".

any tips and help appreciated.

---

### Post by Toz on 2013-10-22
What is your current kernel command line:
```
cat /proc/cmdline
```
...and what backlight interfaces do you have and what brightness values do they contain:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```


Also helpful might be your Xorg log file. Either:
```
pastebinit /var/log/Xorg.0.log
```
...and paste back the link that is generated. If the program pastebinit isn't installed, either install it via:
```
sudo apt-get install pastebinit
```
...or copy/past the contents of that file between **[noparse]```
 
```[/noparse]** tags.

Sorry about the terminal commands, but its just much simpler to get the information using this method.

---

### Post by n3wbvip3r on 2013-10-23
```
 BOOT_IMAGE=/boot/vmlinuz-3.5.0-41-generic root=UUID=9355bf7b-4949-452a-ac3c-a444683ce3d7 ro quiet splash vt.handoff=7 
```

```
 [    23.087] X.Org X Server 1.13.0
Release Date: 2012-09-05
[    23.087] X Protocol Version 11, Revision 0
[    23.087] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[    23.087] Current Operating System: Linux Computer-Aspire-5253 3.5.0-41-generic #64~precise1-Ubuntu SMP Thu Sep 12 16:50:04 UTC 2013 x86_64
[    23.087] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-41-generic root=UUID=9355bf7b-4949-452a-ac3c-a444683ce3d7 ro quiet splash vt.handoff=7
[    23.093] Build Date: 16 October 2013  04:43:36PM
[    23.093] xorg-server 2:1.13.0-0ubuntu6.1~precise4 (For technical support please see http://www.ubuntu.com/support) 
[    23.093] Current version of pixman: 0.24.4
[    23.093]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    23.093] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    23.094] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 23 00:31:33 2013
[    23.095] (==) Using config file: "/etc/X11/xorg.conf"
[    23.095] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    23.096] (==) ServerLayout "aticonfig Layout"
[    23.096] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    23.096] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    23.097] (**) |   |-->Device "aticonfig-Device[0]-0"
[    23.097] (==) Automatically adding devices
[    23.097] (==) Automatically enabling devices
[    23.097] (==) Automatically adding GPU devices
[    23.097] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    23.097]     Entry deleted from font path.
[    23.097] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    23.097]     Entry deleted from font path.
[    23.097] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    23.097]     Entry deleted from font path.
[    23.097] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    23.097]     Entry deleted from font path.
[    23.097] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    23.097]     Entry deleted from font path.
[    23.097] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    23.097]     Entry deleted from font path.
[    23.097] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    23.097] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    23.097] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    23.097] (II) Loader magic: 0x7f2503f7ec20
[    23.097] (II) Module ABI versions:
[    23.097]     X.Org ANSI C Emulation: 0.4
[    23.097]     X.Org Video Driver: 13.0
[    23.097]     X.Org XInput driver : 18.0
[    23.097]     X.Org Server Extension : 7.0
[    23.117] (--) PCI:*(0:0:1:0) 1002:9804:1025:0520 rev 0, Mem @ 0xc0000000/268435456, 0xd0400000/262144, I/O @ 0x00004000/256
[    23.118] (II) Open ACPI successful (/var/run/acpid.socket)
[    23.118] Initializing built-in extension Generic Event Extension
[    23.118] Initializing built-in extension SHAPE
[    23.118] Initializing built-in extension MIT-SHM
[    23.118] Initializing built-in extension XInputExtension
[    23.118] Initializing built-in extension XTEST
[    23.118] Initializing built-in extension BIG-REQUESTS
[    23.118] Initializing built-in extension SYNC
[    23.118] Initializing built-in extension XKEYBOARD
[    23.118] Initializing built-in extension XC-MISC
[    23.118] Initializing built-in extension SECURITY
[    23.118] Initializing built-in extension XINERAMA
[    23.118] Initializing built-in extension XFIXES
[    23.118] Initializing built-in extension RENDER
[    23.118] Initializing built-in extension RANDR
[    23.118] Initializing built-in extension COMPOSITE
[    23.118] Initializing built-in extension DAMAGE
[    23.118] Initializing built-in extension MIT-SCREEN-SAVER
[    23.118] Initializing built-in extension DOUBLE-BUFFER
[    23.119] Initializing built-in extension RECORD
[    23.119] Initializing built-in extension DPMS
[    23.119] Initializing built-in extension X-Resource
[    23.119] Initializing built-in extension XVideo
[    23.119] Initializing built-in extension XVideo-MotionCompensation
[    23.119] Initializing built-in extension XFree86-VidModeExtension
[    23.119] Initializing built-in extension XFree86-DGA
[    23.119] Initializing built-in extension XFree86-DRI
[    23.119] Initializing built-in extension DRI2
[    23.119] (II) "glx" will be loaded by default.
[    23.119] (II) LoadModule: "glx"
[    23.144] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    23.145] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    23.145]     compiled for 6.9.0, module version = 1.0.0
[    23.145] Loading extension GLX
[    23.145] (II) LoadModule: "fglrx"
[    23.146] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[    23.218] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[    23.219]     compiled for 1.4.99.906, module version = 12.10.5
[    23.219]     Module class: X.Org Video Driver
[    23.219] (II) Loading sub module "fglrxdrm"
[    23.219] (II) LoadModule: "fglrxdrm"
[    23.220] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    23.221] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    23.221]     compiled for 1.4.99.906, module version = 12.10.5
[    23.221] (II) AMD Proprietary Linux Driver Version Identifier:12.10.05
[    23.221] (II) AMD Proprietary Linux Driver Release Identifier: 12.104                               
[    23.221] (II) AMD Proprietary Linux Driver Build Date: Mar 28 2013 21:07:25
[    23.221] (++) using VT number 7


[    23.221] (WW) Falling back to old probe method for fglrx
[    23.248] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[    23.253] ukiDynamicMajor: found major device number 251
[    23.253] ukiDynamicMajor: found major device number 251
[    23.254] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[    23.254] ukiOpenDevice: node name is /dev/ati/card0
[    23.254] ukiOpenDevice: open result is 10, (OK)
[    25.099] ukiOpenByBusid: ukiOpenMinor returns 10
[    25.099] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[    25.104] (--) Chipset Supported AMD Graphics Processor (0x9804) found
[    25.105] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:1:1) found
[    25.105] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[    25.105] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[    25.105] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[    25.105] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[    25.105] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[    25.105] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[    25.105] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[    25.105] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[    25.105] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[    25.105] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:0) found
[    25.105] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:2) found
[    25.105] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:3) found
[    25.107] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    25.107] (II) AMD Video driver is signed
[    25.109] (II) fglrx(0): pEnt->device->identifier=0x7f2505667400
[    25.109] (II) fglrx(0): === [xdl_xs113_atiddxPreInit] === begin
[    25.109] (II) Loading sub module "vgahw"
[    25.109] (II) LoadModule: "vgahw"
[    25.110] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    25.111] (II) Module vgahw: vendor="X.Org Foundation"
[    25.111]     compiled for 1.13.0, module version = 0.1.0
[    25.111]     ABI class: X.Org Video Driver, version 13.0
[    25.111] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    25.111] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    25.111] (==) fglrx(0): Default visual is TrueColor
[    25.111] (**) fglrx(0): Option "DPMS" "true"
[    25.111] (==) fglrx(0): RGB weight 888
[    25.111] (II) fglrx(0): Using 8 bits per RGB 
[    25.111] (==) fglrx(0): Buffer Tiling is ON
[    25.111] (II) Loading sub module "fglrxdrm"
[    25.111] (II) LoadModule: "fglrxdrm"
[    25.112] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    25.112] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    25.112]     compiled for 1.4.99.906, module version = 12.10.5
[    25.117] ukiDynamicMajor: found major device number 251
[    25.117] ukiDynamicMajor: found major device number 251
[    25.117] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[    25.117] ukiOpenDevice: node name is /dev/ati/card0
[    25.117] ukiOpenDevice: open result is 13, (OK)
[    25.118] ukiOpenByBusid: ukiOpenMinor returns 13
[    25.118] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[    25.118] (**) fglrx(0): NoAccel = NO
[    25.118] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[    25.118] (--) fglrx(0): Chipset: "AMD Radeon HD 6250 Graphics " (Chipset = 0x9804)
[    25.118] (--) fglrx(0): (PciSubVendor = 0x1025, PciSubDevice = 0x0520)
[    25.118] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[    25.118] (--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
[    25.118] (--) fglrx(0): MMIO registers at 0xd0400000
[    25.118] (--) fglrx(0): I/O port at 0x00004000
[    25.118] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    25.192] (II) fglrx(0): ATIF platform detected
[    25.196] (II) fglrx(0): Battery is used
[    25.196] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[    25.196] (--) fglrx(0): Video RAM: 262144 kByte, Type: DDR3
[    25.196] (II) fglrx(0): PCIE card detected
[    25.197] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    25.197] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    25.197] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x10000000)
[    25.197] (II) fglrx(0): RandR 1.2 support is enabled!
[    25.197] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    25.197] (==) fglrx(0): Center Mode is disabled 
[    25.197] (II) Loading sub module "fb"
[    25.197] (II) LoadModule: "fb"
[    25.198] (II) Loading /usr/lib/xorg/modules/libfb.so
[    25.198] (II) Module fb: vendor="X.Org Foundation"
[    25.198]     compiled for 1.13.0, module version = 1.0.0
[    25.198]     ABI class: X.Org ANSI C Emulation, version 0.4
[    25.198] (II) Loading sub module "ddc"
[    25.198] (II) LoadModule: "ddc"
[    25.198] (II) Module "ddc" already built-in
[    25.289] (II) fglrx(0): Output LVDS using monitor section aticonfig-Monitor[0]-0
[    25.289] (II) fglrx(0): Output DFP1 has no monitor section
[    25.289] (II) fglrx(0): Output CRT1 has no monitor section
[    25.289] (II) Loading sub module "ddc"
[    25.289] (II) LoadModule: "ddc"
[    25.289] (II) Module "ddc" already built-in
[    25.290] (II) fglrx(0): Connected Display0: LVDS
[    25.290] (II) fglrx(0):  Display0: Failed to get EDID information. 
[    25.292] (II) fglrx(0): EDID for output LVDS
[    25.292] (II) fglrx(0): Manufacturer: LGD  Model: 250  Serial#: 0
[    25.292] (II) fglrx(0): Year: 2010  Week: 0
[    25.292] (II) fglrx(0): EDID Version: 1.3
[    25.292] (II) fglrx(0): Digital Display Input
[    25.292] (II) fglrx(0): Max Image Size [cm]: horiz.: 35  vert.: 19
[    25.292] (II) fglrx(0): Gamma: 2.20
[    25.292] (II) fglrx(0): No DPMS capabilities specified
[    25.292] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    25.292] (II) fglrx(0): First detailed timing is preferred mode
[    25.292] (II) fglrx(0): redX: 0.612 redY: 0.375   greenX: 0.332 greenY: 0.619
[    25.292] (II) fglrx(0): blueX: 0.151 blueY: 0.099   whiteX: 0.313 whiteY: 0.329
[    25.292] (II) fglrx(0): Manufacturer's mask: 0
[    25.292] (II) fglrx(0): Supported detailed timing:
[    25.292] (II) fglrx(0): clock: 72.3 MHz   Image Size:  345 x 194 mm
[    25.292] (II) fglrx(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[    25.292] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[    25.292] (II) fglrx(0):  LG Display
[    25.292] (II) fglrx(0):  LP156WH2-TLEA
[    25.292] (II) fglrx(0): EDID (in hex):
[    25.292] (II) fglrx(0):     00ffffffffffff0030e4500200000000
[    25.292] (II) fglrx(0):     00140103802313780ac2d59c60559e26
[    25.292] (II) fglrx(0):     19505400000001010101010101010101
[    25.292] (II) fglrx(0):     0101010101013e1c56a0500016303020
[    25.292] (II) fglrx(0):     350059c2100000190000000000000000
[    25.292] (II) fglrx(0):     00000000000000000000000000fe004c
[    25.292] (II) fglrx(0):     4720446973706c61790a2020000000fe
[    25.292] (II) fglrx(0):     004c503135365748322d544c454100fd
[    25.293] (II) fglrx(0): EDID vendor "LGD", prod id 592
[    25.293] (II) fglrx(0): Printing DDC gathered Modelines:
[    25.293] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz eP)
[    25.293] (II) fglrx(0): Printing probed modes for output LVDS
[    25.293] (II) fglrx(0): Modeline "1366x768"x60.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz eP)
[    25.293] (II) fglrx(0): Modeline "1360x768"x60.0   72.30  1360 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz e)
[    25.293] (II) fglrx(0): Modeline "1280x768"x60.0   72.30  1280 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz e)
[    25.293] (II) fglrx(0): Modeline "1280x720"x60.0   72.30  1280 1414 1446 1526  720 771 776 790 -hsync -vsync (47.4 kHz e)
[    25.293] (II) fglrx(0): Modeline "1024x768"x60.0   72.30  1024 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz e)
[    25.293] (II) fglrx(0): Modeline "1024x600"x60.0   72.30  1024 1414 1446 1526  600 771 776 790 -hsync -vsync (47.4 kHz e)
[    25.293] (II) fglrx(0): Modeline "800x600"x60.0   72.30  800 1414 1446 1526  600 771 776 790 -hsync -vsync (47.4 kHz e)
[    25.293] (II) fglrx(0): Modeline "800x480"x60.0   72.30  800 1414 1446 1526  480 771 776 790 -hsync -vsync (47.4 kHz e)
[    25.293] (II) fglrx(0): Modeline "640x480"x60.0   72.30  640 1414 1446 1526  480 771 776 790 -hsync -vsync (47.4 kHz e)
[    25.293] (II) fglrx(0): EDID for output DFP1
[    25.293] (II) fglrx(0): EDID for output CRT1
[    25.293] (II) fglrx(0): Output LVDS connected
[    25.293] (II) fglrx(0): Output DFP1 disconnected
[    25.293] (II) fglrx(0): Output CRT1 disconnected
[    25.293] (II) fglrx(0): Using exact sizes for initial modes
[    25.293] (II) fglrx(0): Output LVDS using initial mode 1366x768
[    25.293] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    25.293] (II) fglrx(0): Display dimensions: (350, 190) mm
[    25.294] (II) fglrx(0): DPI set to (99, 102)
[    25.294] (II) fglrx(0): Adapter AMD Radeon HD 6250 Graphics  has 2 configurable heads and 1 displays connected.
[    25.294] (==) fglrx(0):  PseudoColor visuals disabled
[    25.294] (II) Loading sub module "ramdac"
[    25.294] (II) LoadModule: "ramdac"
[    25.294] (II) Module "ramdac" already built-in
[    25.294] (==) fglrx(0): NoDRI = NO
[    25.294] (==) fglrx(0): Capabilities: 0x00000000
[    25.294] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    25.294] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    25.294] (==) fglrx(0): UseFastTLS=0
[    25.294] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[    25.294] (--) Depth 24 pixmap format is 32 bpp
[    25.295] Loading extension ATIFGLRXDRI
[    25.295] (II) fglrx(0): doing swlDriScreenInit
[    25.295] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    25.296] ukiDynamicMajor: found major device number 251
[    25.296] ukiDynamicMajor: found major device number 251
[    25.296] ukiDynamicMajor: found major device number 251
[    25.296] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[    25.296] ukiOpenDevice: node name is /dev/ati/card0
[    25.296] ukiOpenDevice: open result is 14, (OK)
[    25.296] ukiOpenByBusid: ukiOpenMinor returns 14
[    25.296] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[    25.296] (II) fglrx(0): [uki] DRM interface version 1.0
[    25.296] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:0:1:0"
[    25.296] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    25.296] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f2503971000
[    25.296] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    25.297] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    25.297] (II) fglrx(0): swlDriScreenInit done
[    25.297] (II) fglrx(0): Kernel Module Version Information:
[    25.297] (II) fglrx(0):     Name: fglrx
[    25.297] (II) fglrx(0):     Version: 12.10.5
[    25.297] (II) fglrx(0):     Date: Mar 28 2013
[    25.297] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[    25.297] (II) fglrx(0): Kernel Module version matches driver.
[    25.297] (II) fglrx(0): Kernel Module Build Time Information:
[    25.297] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.5.0-41-generic
[    25.297] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    25.297] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    25.297] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    25.297] (II) fglrx(0): [uki] register handle = 0x00004000
[    25.299] (II) fglrx(0): DRI initialization successfull
[    25.299] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01004000
[    25.300] (==) fglrx(0): Backing store disabled
[    25.300] Loading extension FGLRXEXTENSION
[    25.300] (**) fglrx(0): DPMS enabled
[    25.301] (II) fglrx(0): Initialized in-driver Xinerama extension
[    25.301] (**) fglrx(0): Textured Video is enabled.
[    25.301] (II) LoadModule: "glesx"
[    25.302] (II) Loading /usr/lib/xorg/modules/glesx.so
[    25.303] (II) Module glesx: vendor="X.Org Foundation"
[    25.303]     compiled for 1.4.99.906, module version = 1.0.0
[    25.303] Loading extension GLESX
[    25.303] (II) fglrx(0): GLESX enableFlags = 592
[    25.304] (II) fglrx(0): GLESX is enabled
[    25.304] (II) LoadModule: "amdxmm"
[    25.304] (II) Loading /usr/lib/xorg/modules/amdxmm.so
[    25.305] (II) Module amdxmm: vendor="X.Org Foundation"
[    25.305]     compiled for 1.4.99.906, module version = 2.0.0
[    25.313] Loading extension AMDXVOPL
[    25.313] Loading extension AMDXVBA
[    25.315] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    25.322] (II) fglrx(0): Enable composite support successfully
[    25.322] (WW) fglrx(0): Option "VendorName" is not used
[    25.322] (WW) fglrx(0): Option "ModelName" is not used
[    25.322] (II) fglrx(0): X context handle = 0x1
[    25.322] (II) fglrx(0): [DRI] installation complete
[    25.322] (==) fglrx(0): Silken mouse enabled
[    25.323] (==) fglrx(0): Using HW cursor of display infrastructure!
[    25.323] (II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    25.324] (II) fglrx(0): 'LVDS LCD' ConnectorType, abstracted as 'Panel'
[    25.324] (II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'
[    26.350] (WW) fglrx(0): Framebuffer compression is disabled by the driver: Video Ram = 262144 kByte
[    26.350] (--) RandR disabled
[    26.372] ukiDynamicMajor: found major device number 251
[    26.372] ukiDynamicMajor: found major device number 251
[    26.372] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[    26.372] ukiOpenDevice: node name is /dev/ati/card0
[    26.372] ukiOpenDevice: open result is 15, (OK)
[    26.372] ukiOpenByBusid: ukiOpenMinor returns 15
[    26.372] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[    26.379] ukiDynamicMajor: found major device number 251
[    26.379] ukiDynamicMajor: found major device number 251
[    26.379] ukiDynamicMajor: found major device number 251
[    26.379] ukiOpenDevice: node name is /dev/ati/card0
[    26.380] ukiOpenDevice: open result is 16, (OK)
[    26.380] ukiGetBusid returned 'PCI:0:1:0'
[    26.380] ukiOpenDevice: node name is /dev/ati/card1
[    26.380] ukiOpenDevice: open result is -1, (No such device)
[    26.380] ukiOpenDevice: open result is -1, (No such device)
[    26.380] ukiOpenDevice: Open failed
[    26.380] ukiOpenDevice: node name is /dev/ati/card2
[    26.380] ukiOpenDevice: open result is -1, (No such device)
[    26.380] ukiOpenDevice: open result is -1, (No such device)
[    26.380] ukiOpenDevice: Open failed
[    26.380] ukiOpenDevice: node name is /dev/ati/card3
[    26.380] ukiOpenDevice: open result is -1, (No such device)
[    26.380] ukiOpenDevice: open result is -1, (No such device)
[    26.380] ukiOpenDevice: Open failed
[    26.380] ukiOpenDevice: node name is /dev/ati/card4
[    26.380] ukiOpenDevice: open result is -1, (No such device)
[    26.380] ukiOpenDevice: open result is -1, (No such device)
[    26.380] ukiOpenDevice: Open failed
[    26.381] ukiOpenDevice: node name is /dev/ati/card5
[    26.381] ukiOpenDevice: open result is -1, (No such device)
[    26.381] ukiOpenDevice: open result is -1, (No such device)
[    26.381] ukiOpenDevice: Open failed
[    26.381] ukiOpenDevice: node name is /dev/ati/card6
[    26.381] ukiOpenDevice: open result is -1, (No such device)
[    26.381] ukiOpenDevice: open result is -1, (No such device)
[    26.381] ukiOpenDevice: Open failed
[    26.381] ukiOpenDevice: node name is /dev/ati/card7
[    26.381] ukiOpenDevice: open result is -1, (No such device)
[    26.381] ukiOpenDevice: open result is -1, (No such device)
[    26.381] ukiOpenDevice: Open failed
[    26.381] ukiOpenDevice: node name is /dev/ati/card8
[    26.381] ukiOpenDevice: open result is -1, (No such device)
[    26.381] ukiOpenDevice: open result is -1, (No such device)
[    26.381] ukiOpenDevice: Open failed
[    26.381] ukiOpenDevice: node name is /dev/ati/card9
[    26.381] ukiOpenDevice: open result is -1, (No such device)
[    26.381] ukiOpenDevice: open result is -1, (No such device)
[    26.381] ukiOpenDevice: Open failed
[    26.381] ukiOpenDevice: node name is /dev/ati/card10
[    26.381] ukiOpenDevice: open result is -1, (No such device)
[    26.382] ukiOpenDevice: open result is -1, (No such device)
[    26.382] ukiOpenDevice: Open failed
[    26.382] ukiOpenDevice: node name is /dev/ati/card11
[    26.382] ukiOpenDevice: open result is -1, (No such device)
[    26.382] ukiOpenDevice: open result is -1, (No such device)
[    26.382] ukiOpenDevice: Open failed
[    26.382] ukiOpenDevice: node name is /dev/ati/card12
[    26.382] ukiOpenDevice: open result is -1, (No such device)
[    26.382] ukiOpenDevice: open result is -1, (No such device)
[    26.382] ukiOpenDevice: Open failed
[    26.382] ukiOpenDevice: node name is /dev/ati/card13
[    26.382] ukiOpenDevice: open result is -1, (No such device)
[    26.382] ukiOpenDevice: open result is -1, (No such device)
[    26.382] ukiOpenDevice: Open failed
[    26.382] ukiOpenDevice: node name is /dev/ati/card14
[    26.382] ukiOpenDevice: open result is -1, (No such device)
[    26.382] ukiOpenDevice: open result is -1, (No such device)
[    26.382] ukiOpenDevice: Open failed
[    26.382] ukiOpenDevice: node name is /dev/ati/card15
[    26.382] ukiOpenDevice: open result is -1, (No such device)
[    26.382] ukiOpenDevice: open result is -1, (No such device)
[    26.383] ukiOpenDevice: Open failed
[    26.383] ukiDynamicMajor: found major device number 251
[    26.383] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[    26.383] ukiOpenDevice: node name is /dev/ati/card0
[    26.383] ukiOpenDevice: open result is 16, (OK)
[    26.383] ukiOpenByBusid: ukiOpenMinor returns 16
[    26.383] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[    26.653] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    26.656] ukiDynamicMajor: found major device number 251
[    26.656] ukiDynamicMajor: found major device number 251
[    26.656] ukiDynamicMajor: found major device number 251
[    26.656] ukiOpenDevice: node name is /dev/ati/card0
[    26.656] ukiOpenDevice: open result is 17, (OK)
[    26.657] ukiGetBusid returned 'PCI:0:1:0'
[    26.657] ukiOpenDevice: node name is /dev/ati/card1
[    26.657] ukiOpenDevice: open result is -1, (No such device)
[    26.657] ukiOpenDevice: open result is -1, (No such device)
[    26.657] ukiOpenDevice: Open failed
[    26.657] ukiOpenDevice: node name is /dev/ati/card2
[    26.657] ukiOpenDevice: open result is -1, (No such device)
[    26.657] ukiOpenDevice: open result is -1, (No such device)
[    26.657] ukiOpenDevice: Open failed
[    26.657] ukiOpenDevice: node name is /dev/ati/card3
[    26.657] ukiOpenDevice: open result is -1, (No such device)
[    26.657] ukiOpenDevice: open result is -1, (No such device)
[    26.657] ukiOpenDevice: Open failed
[    26.657] ukiOpenDevice: node name is /dev/ati/card4
[    26.657] ukiOpenDevice: open result is -1, (No such device)
[    26.657] ukiOpenDevice: open result is -1, (No such device)
[    26.657] ukiOpenDevice: Open failed
[    26.657] ukiOpenDevice: node name is /dev/ati/card5
[    26.657] ukiOpenDevice: open result is -1, (No such device)
[    26.657] ukiOpenDevice: open result is -1, (No such device)
[    26.657] ukiOpenDevice: Open failed
[    26.658] ukiOpenDevice: node name is /dev/ati/card6
[    26.658] ukiOpenDevice: open result is -1, (No such device)
[    26.658] ukiOpenDevice: open result is -1, (No such device)
[    26.658] ukiOpenDevice: Open failed
[    26.658] ukiOpenDevice: node name is /dev/ati/card7
[    26.658] ukiOpenDevice: open result is -1, (No such device)
[    26.658] ukiOpenDevice: open result is -1, (No such device)
[    26.658] ukiOpenDevice: Open failed
[    26.658] ukiOpenDevice: node name is /dev/ati/card8
[    26.658] ukiOpenDevice: open result is -1, (No such device)
[    26.658] ukiOpenDevice: open result is -1, (No such device)
[    26.658] ukiOpenDevice: Open failed
[    26.658] ukiOpenDevice: node name is /dev/ati/card9
[    26.658] ukiOpenDevice: open result is -1, (No such device)
[    26.658] ukiOpenDevice: open result is -1, (No such device)
[    26.658] ukiOpenDevice: Open failed
[    26.658] ukiOpenDevice: node name is /dev/ati/card10
[    26.658] ukiOpenDevice: open result is -1, (No such device)
[    26.658] ukiOpenDevice: open result is -1, (No such device)
[    26.658] ukiOpenDevice: Open failed
[    26.658] ukiOpenDevice: node name is /dev/ati/card11
[    26.658] ukiOpenDevice: open result is -1, (No such device)
[    26.659] ukiOpenDevice: open result is -1, (No such device)
[    26.659] ukiOpenDevice: Open failed
[    26.659] ukiOpenDevice: node name is /dev/ati/card12
[    26.659] ukiOpenDevice: open result is -1, (No such device)
[    26.659] ukiOpenDevice: open result is -1, (No such device)
[    26.659] ukiOpenDevice: Open failed
[    26.659] ukiOpenDevice: node name is /dev/ati/card13
[    26.659] ukiOpenDevice: open result is -1, (No such device)
[    26.659] ukiOpenDevice: open result is -1, (No such device)
[    26.659] ukiOpenDevice: Open failed
[    26.659] ukiOpenDevice: node name is /dev/ati/card14
[    26.659] ukiOpenDevice: open result is -1, (No such device)
[    26.659] ukiOpenDevice: open result is -1, (No such device)
[    26.659] ukiOpenDevice: Open failed
[    26.659] ukiOpenDevice: node name is /dev/ati/card15
[    26.659] ukiOpenDevice: open result is -1, (No such device)
[    26.659] ukiOpenDevice: open result is -1, (No such device)
[    26.659] ukiOpenDevice: Open failed
[    26.659] ukiDynamicMajor: found major device number 251
[    26.659] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[    26.660] ukiOpenDevice: node name is /dev/ati/card0
[    26.660] ukiOpenDevice: open result is 17, (OK)
[    26.660] ukiOpenByBusid: ukiOpenMinor returns 17
[    26.660] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[    26.711] (II) fglrx(0): Setting screen physical size to 361 x 203
[    26.737] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    26.745] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    26.745] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.745] (II) LoadModule: "evdev"
[    26.746] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.746] (II) Module evdev: vendor="X.Org Foundation"
[    26.746]     compiled for 1.13.0, module version = 2.7.3
[    26.746]     Module class: X.Org XInput Driver
[    26.747]     ABI class: X.Org XInput driver, version 18.0
[    26.747] (II) Using input driver 'evdev' for 'Power Button'
[    26.747] (**) Power Button: always reports core events
[    26.747] (**) evdev: Power Button: Device: "/dev/input/event3"
[    26.747] (--) evdev: Power Button: Vendor 0 Product 0x1
[    26.747] (--) evdev: Power Button: Found keys
[    26.747] (II) evdev: Power Button: Configuring as keyboard
[    26.747] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    26.747] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    26.747] (**) Option "xkb_rules" "evdev"
[    26.747] (**) Option "xkb_model" "pc105"
[    26.747] (**) Option "xkb_layout" "us"
[    26.749] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    26.749] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    26.749] (II) Using input driver 'evdev' for 'Video Bus'
[    26.749] (**) Video Bus: always reports core events
[    26.749] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    26.749] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    26.749] (--) evdev: Video Bus: Found keys
[    26.749] (II) evdev: Video Bus: Configuring as keyboard
[    26.749] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5/event5"
[    26.749] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    26.750] (**) Option "xkb_rules" "evdev"
[    26.750] (**) Option "xkb_model" "pc105"
[    26.750] (**) Option "xkb_layout" "us"
[    26.751] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    26.751] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.751] (II) Using input driver 'evdev' for 'Power Button'
[    26.751] (**) Power Button: always reports core events
[    26.751] (**) evdev: Power Button: Device: "/dev/input/event0"
[    26.751] (--) evdev: Power Button: Vendor 0 Product 0x1
[    26.751] (--) evdev: Power Button: Found keys
[    26.751] (II) evdev: Power Button: Configuring as keyboard
[    26.752] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    26.752] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    26.752] (**) Option "xkb_rules" "evdev"
[    26.752] (**) Option "xkb_model" "pc105"
[    26.752] (**) Option "xkb_layout" "us"
[    26.753] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    26.753] (II) No input driver specified, ignoring this device.
[    26.753] (II) This device may have been added with another device file.
[    26.754] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    26.754] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    26.754] (II) Using input driver 'evdev' for 'Sleep Button'
[    26.754] (**) Sleep Button: always reports core events
[    26.754] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    26.754] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    26.754] (--) evdev: Sleep Button: Found keys
[    26.754] (II) evdev: Sleep Button: Configuring as keyboard
[    26.755] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[    26.755] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    26.755] (**) Option "xkb_rules" "evdev"
[    26.755] (**) Option "xkb_model" "pc105"
[    26.755] (**) Option "xkb_layout" "us"
[    26.756] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event9)
[    26.756] (II) No input driver specified, ignoring this device.
[    26.756] (II) This device may have been added with another device file.
[    26.757] (II) config/udev: Adding input device 1.3M HD WebCam (/dev/input/event8)
[    26.757] (**) 1.3M HD WebCam: Applying InputClass "evdev keyboard catchall"
[    26.757] (II) Using input driver 'evdev' for '1.3M HD WebCam'
[    26.757] (**) 1.3M HD WebCam: always reports core events
[    26.757] (**) evdev: 1.3M HD WebCam: Device: "/dev/input/event8"
[    26.758] (--) evdev: 1.3M HD WebCam: Vendor 0x4fc Product 0x2801
[    26.758] (--) evdev: 1.3M HD WebCam: Found keys
[    26.758] (II) evdev: 1.3M HD WebCam: Configuring as keyboard
[    26.758] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1:1.0/input/input8/event8"
[    26.758] (II) XINPUT: Adding extended input device "1.3M HD WebCam" (type: KEYBOARD, id 10)
[    26.758] (**) Option "xkb_rules" "evdev"
[    26.758] (**) Option "xkb_model" "pc105"
[    26.758] (**) Option "xkb_layout" "us"
[    26.759] (II) config/udev: Adding input device HDA ATI SB Mic (/dev/input/event10)
[    26.760] (II) No input driver specified, ignoring this device.
[    26.760] (II) This device may have been added with another device file.
[    26.760] (II) config/udev: Adding input device HDA ATI SB Headphone (/dev/input/event11)
[    26.760] (II) No input driver specified, ignoring this device.
[    26.760] (II) This device may have been added with another device file.
[    26.761] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    26.761] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    26.761] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    26.761] (**) AT Translated Set 2 keyboard: always reports core events
[    26.761] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    26.762] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    26.762] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    26.762] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    26.762] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    26.762] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    26.762] (**) Option "xkb_rules" "evdev"
[    26.762] (**) Option "xkb_model" "pc105"
[    26.762] (**) Option "xkb_layout" "us"
[    26.763] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event12)
[    26.763] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    26.763] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    26.764] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    26.764] (II) LoadModule: "synaptics"
[    26.764] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    26.764] (II) Module synaptics: vendor="X.Org Foundation"
[    26.764]     compiled for 1.13.0, module version = 1.6.2
[    26.764]     Module class: X.Org XInput Driver
[    26.765]     ABI class: X.Org XInput driver, version 18.0
[    26.765] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    26.765] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    26.765] (**) Option "Device" "/dev/input/event12"
[    26.766] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[    26.766] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5772
[    26.766] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 5086
[    26.766] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    26.766] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    26.766] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    26.766] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    26.766] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    26.766] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    26.767] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input12/event12"
[    26.767] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[    26.767] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    26.767] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    26.767] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.035
[    26.768] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    26.768] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    26.768] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    26.768] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    26.768] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    26.769] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    26.769] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    26.775] (II) config/udev: Adding input device Acer WMI hotkeys (/dev/input/event6)
[    26.775] (**) Acer WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    26.775] (II) Using input driver 'evdev' for 'Acer WMI hotkeys'
[    26.776] (**) Acer WMI hotkeys: always reports core events
[    26.776] (**) evdev: Acer WMI hotkeys: Device: "/dev/input/event6"
[    26.776] (--) evdev: Acer WMI hotkeys: Vendor 0 Product 0
[    26.776] (--) evdev: Acer WMI hotkeys: Found keys
[    26.776] (II) evdev: Acer WMI hotkeys: Configuring as keyboard
[    26.776] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event6"
[    26.776] (II) XINPUT: Adding extended input device "Acer WMI hotkeys" (type: KEYBOARD, id 13)
[    26.776] (**) Option "xkb_rules" "evdev"
[    26.776] (**) Option "xkb_model" "pc105"
[    26.776] (**) Option "xkb_layout" "us"
[    26.778] (II) config/udev: Adding input device Acer BMA150 accelerometer (/dev/input/event7)
[    26.778] (II) No input driver specified, ignoring this device.
[    26.778] (II) This device may have been added with another device file.
[    26.778] (II) config/udev: Adding input device Acer BMA150 accelerometer (/dev/input/js0)
[    26.778] (II) No input driver specified, ignoring this device.
[    26.778] (II) This device may have been added with another device file.
[    26.819] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    27.886] (II) fglrx(0): EDID vendor "LGD", prod id 592
[    27.886] (II) fglrx(0): Printing DDC gathered Modelines:
[    27.886] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz eP)
[    32.085] (II) fglrx(0): EDID vendor "LGD", prod id 592
[    32.085] (II) fglrx(0): Printing DDC gathered Modelines:
[    32.085] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz eP)
[    39.693] (II) fglrx(0): EDID vendor "LGD", prod id 592
[    39.693] (II) fglrx(0): Printing DDC gathered Modelines:
[    39.693] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz eP)
[    40.772] (II) fglrx(0): EDID vendor "LGD", prod id 592
[    40.772] (II) fglrx(0): Printing DDC gathered Modelines:
[    40.772] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz eP)
[    41.378] (II) fglrx(0): EDID vendor "LGD", prod id 592
[    41.378] (II) fglrx(0): Printing DDC gathered Modelines:
[    41.378] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz eP)
[    48.206] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[    62.007] (II) fglrx(0): EDID vendor "LGD", prod id 592
[    62.007] (II) fglrx(0): Printing DDC gathered Modelines:
[    62.007] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz eP) 
```

```
 X.Org X Server 1.13.0Release Date: 2012-09-05
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
Current Operating System: Linux Computer-Aspire-5253 3.5.0-41-generic #64~precise1-Ubuntu SMP Thu Sep 12 16:50:04 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-41-generic root=UUID=9355bf7b-4949-452a-ac3c-a444683ce3d7 ro quiet splash vt.handoff=7
Build Date: 16 October 2013  04:43:36PM
xorg-server 2:1.13.0-0ubuntu6.1~precise4 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.24.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.

```

i believe thats what you wanted. however the brightness commands i must be doing wrong. cant get them to display.

EDIT

```
 [COLOR=#333333][FONT=sans-serif]/sys/class/backlight/acpi_video0/brightness [/FONT][/COLOR]
```[COLOR=#333333][FONT=sans-serif]

 the number is 9.. for all the ones. actual and max aswell. which, i imagine, is bad. lol. yes?
[/FONT][/COLOR]

---

### Post by Toz on 2013-10-23
Can you post back exactly what gets returned on the terminal when you run:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

Also, what kernel modules are loaded and running:
```
lsmod
```

If you run this command, does the brightness change:
```
echo 5 | sudo tee /sys/class/backlight/acpi_video0/brightness
```
...enter your password when prompted.

---

### Post by n3wbvip3r on 2013-10-23
```
 /sys/class/backlight/acpi_video09
9
9

```

i imagine this is an issue. or should all be the same number?

```
 /sys/class/backlight/acpi_video05
5
9

```

after using the last code it did change the value, no change in brightness though. brightness issue remains. it changes at the top corner, but the screen stays the same.
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]```
Module                  Size  Used bycdc_acm                26992  0 
vesafb                 13846  1 
kvm_amd                56136  0 
kvm                   422160  1 kvm_amd
joydev                 17694  0 
acer_wmi               32845  0 
sparse_keymap          13891  1 acer_wmi
snd_hda_codec_conexant    62363  1 
snd_hda_codec_hdmi     32476  1 
snd_hda_intel          34063  5 
snd_hda_codec         135141  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
arc4                   12530  2 
snd_seq_midi_event     14900  1 snd_seq_midi
microcode              23030  0 
uvcvideo               78117  0 
ath9k                 133095  0 
videobuf2_core         33025  1 uvcvideo
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
videodev              125126  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
mac80211              555272  1 ath9k
snd_timer              29990  2 snd_pcm,snd_seq
ath9k_common           14054  1 ath9k
psmouse               102541  0 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
videobuf2_memops       13405  1 videobuf2_vmalloc
serio_raw              13216  0 
rfcomm                 47562  0 
ath9k_hw              399752  2 ath9k,ath9k_common
parport_pc             32867  0 
bnep                   18240  2 
ath                    24124  3 ath9k,ath9k_common,ath9k_hw
ppdev                  17114  0 
bluetooth             212001  10 rfcomm,bnep
k10temp                13174  0 
cfg80211              208382  3 ath9k,mac80211,ath
sp5100_tco             13792  0 
i2c_piix4              13302  0 
fglrx                5294799  124 
snd                    83674  20 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15092  1 snd
amd_iommu_v2           19228  1 fglrx
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
wmi                    19257  1 acer_wmi
mac_hid                13254  0 
video                  19653  1 acer_wmi
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
ums_realtek            18257  0 
usb_storage            49288  1 ums_realtek
atl1c                  42092  0 
ahci                   25869  2 
libahci                27338  1 ahci

```

i have been battling this for days it seems. i'm sure there is something i still can do to fix this, my luck i'll have to go in over my head.
[COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR]

---

### Post by Toz on 2013-10-23
Apart from the brightness not changing, I don't see anything wrong with the codes you've returned. Since the brightness changing works with the radeon drivers but not with the proprietary ATI drivers, its a good bet that the proprietary drivers are somehow not working properly (with respect to backlight control). 

The ATI drivers come with a control application. Is there anything in this app that allows you to set brightness? 

If you want a fix for this issue, I think your going to need to open a bug report. Otherwise, you can try workarounds like the one suggested by @cmcanulty using xbacklight or others that directly manipulates pci devices like setpci (if they work).

---

### Post by n3wbvip3r on 2013-10-23
hmm, i'm going to try this here:

[http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/126513#126513](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/126513#126513)

what i did was go to ati site, get package, and install. seems as tho it may not be as easy as this. if not, may try linux mint 15. hopping around til i find one i like. but i like ubuntu alot! which is sad. so hopefully this makes everything right.

EDIT

wow... there is a ton of things i need. i thought ubuntu already came x32 ready in x64 version. 250mb of stuff i needed. well, lets see how smooth things go after a reboot and install.

EDIT

```
Supported adapter detected.Check if system has the tools required for installation.
Uninstalling any previously installed drivers.


Creating symlink /var/lib/dkms/fglrx/12.104/source ->
                 /usr/src/fglrx-12.104


DKMS: add completed.


Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area....
cd /var/lib/dkms/fglrx/12.104/build; sh make.sh --nohints --uname_r=3.5.0-41-generic --norootcheck...........
cleaning build area....


DKMS: build completed.


fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-41-generic/updates/dkms/


depmod.........


DKMS: install completed.
[Reboot] Kernel Module : update-initramfs 
```

log after install. going to reboot now.

---

### Post by n3wbvip3r on 2013-10-23
issue still here... before when i purged, brightness worked fine. must be the 13.4 driver. hmm...

---

### Post by n3wbvip3r on 2013-10-23
Changing to solved.... somewhat. its a known issue with the CCC drivers by AMD past 13.2 v7 beta. if you have past this, expect brightness issues, and glitches like that. AMD drivers get worse and worse at the promise of better performance. and supposedly they are working with steam for a gaming OS? seams like a horrible idea... i know nvidia is not much better, but i'd of chose them over a company going in the toilet.. sudo end rant.. lol.

---

