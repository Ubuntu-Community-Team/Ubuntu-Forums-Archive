---
title: "triple monitor CCC/FGLRX issues"
date: 2013-09-05
forum: Multimedia Software
---

### Post by GizahNL on 2013-09-05
OK here goes:

I've got a triple monitor setup on my Ati HD57xx, 1 DVI one HDMI->DVI and one DP->DVI, all screens are completely identical. 

Now running the opensource radeon drivers I've got all screens working without trouble, sometimes after a fresh install not all screens are probed well enough (need to hot plug once or twice) but after that all systems are go and i have no problems, except for performance which is getting more and more ****** since unity. 

If I switch to the binary fglrx blob performance is good but now using the system settings display configuration to enable the third screen results in an "could not set the configuration for crtc 148" error (this is after I used the CCC to enable the third screen and did the advised reboot).

Xorg.log shows nothing interesting, but here it is anyway
```
  X.Org X Server 1.11.3Release Date: 2011-12-16
[     6.655] X Protocol Version 11, Revision 0
[     6.655] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[     6.655] Current Operating System: Linux gijs-desktop 3.5.0-39-generic #60~precise1-Ubuntu SMP Wed Aug 14 15:38:41 UTC 2013 x86_64
[     6.655] Kernel command line: BOOT_IMAGE=/vmlinuz-3.5.0-39-generic root=UUID=0c27116f-3eb8-4c65-ac65-c9f5d0f33a3f ro quiet splash vt.handoff=7
[     6.655] Build Date: 11 April 2013  01:05:39PM
[     6.655] xorg-server 2:1.11.4-0ubuntu10.13 (For technical support please see http://www.ubuntu.com/support) 
[     6.655] Current version of pixman: 0.24.4
[     6.655]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     6.655] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     6.655] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep  5 10:29:55 2013
[     6.656] (==) Using config file: "/etc/X11/xorg.conf"
[     6.656] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     6.658] (==) ServerLayout "amdcccle Layout"
[     6.658] (**) |-->Screen "amdcccle-Screen[1]-0" (0)
[     6.658] (**) |   |-->Monitor "<default monitor>"
[     6.659] (**) |   |-->Device "amdcccle-Device[1]-0"
[     6.659] (==) No monitor specified for screen "amdcccle-Screen[1]-0".
    Using a default monitor configuration.
[     6.659] (==) Automatically adding devices
[     6.659] (==) Automatically enabling devices
[     6.661] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     6.661]     Entry deleted from font path.
[     6.661] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     6.661]     Entry deleted from font path.
[     6.661] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     6.661]     Entry deleted from font path.
[     6.661] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     6.661]     Entry deleted from font path.
[     6.661] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     6.661]     Entry deleted from font path.
[     6.661] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     6.661]     Entry deleted from font path.
[     6.661] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     6.661] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     6.661] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     6.661] (II) Loader magic: 0x7f0b71619b00
[     6.661] (II) Module ABI versions:
[     6.661]     X.Org ANSI C Emulation: 0.4
[     6.661]     X.Org Video Driver: 11.0
[     6.661]     X.Org XInput driver : 16.0
[     6.661]     X.Org Server Extension : 6.0
[     6.662] (--) PCI:*(0:1:0:0) 1002:68be:174b:e144 rev 0, Mem @ 0xd0000000/268435456, 0xfea20000/131072, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[     6.662] (II) Open ACPI successful (/var/run/acpid.socket)
[     6.662] (II) "extmod" will be loaded by default.
[     6.662] (II) "dbe" will be loaded by default.
[     6.662] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[     6.662] (II) "record" will be loaded by default.
[     6.662] (II) "dri" will be loaded by default.
[     6.662] (II) "dri2" will be loaded by default.
[     6.662] (II) LoadModule: "glx"
[     6.664] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[     6.667] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[     6.667]     compiled for 6.9.0, module version = 1.0.0
[     6.667] (II) Loading extension GLX
[     6.667] (II) LoadModule: "extmod"
[     6.668] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     6.670] (II) Module extmod: vendor="X.Org Foundation"
[     6.670]     compiled for 1.11.3, module version = 1.0.0
[     6.670]     Module class: X.Org Server Extension
[     6.670]     ABI class: X.Org Server Extension, version 6.0
[     6.670] (II) Loading extension MIT-SCREEN-SAVER
[     6.670] (II) Loading extension XFree86-VidModeExtension
[     6.670] (II) Loading extension XFree86-DGA
[     6.670] (II) Loading extension DPMS
[     6.670] (II) Loading extension XVideo
[     6.670] (II) Loading extension XVideo-MotionCompensation
[     6.670] (II) Loading extension X-Resource
[     6.670] (II) LoadModule: "dbe"
[     6.670] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     6.671] (II) Module dbe: vendor="X.Org Foundation"
[     6.671]     compiled for 1.11.3, module version = 1.0.0
[     6.671]     Module class: X.Org Server Extension
[     6.671]     ABI class: X.Org Server Extension, version 6.0
[     6.671] (II) Loading extension DOUBLE-BUFFER
[     6.671] (II) LoadModule: "record"
[     6.671] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     6.672] (II) Module record: vendor="X.Org Foundation"
[     6.672]     compiled for 1.11.3, module version = 1.13.0
[     6.672]     Module class: X.Org Server Extension
[     6.672]     ABI class: X.Org Server Extension, version 6.0
[     6.672] (II) Loading extension RECORD
[     6.672] (II) LoadModule: "dri"
[     6.672] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     6.674] (II) Module dri: vendor="X.Org Foundation"
[     6.674]     compiled for 1.11.3, module version = 1.0.0
[     6.674]     ABI class: X.Org Server Extension, version 6.0
[     6.674] (II) Loading extension XFree86-DRI
[     6.674] (II) LoadModule: "dri2"
[     6.674] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     6.675] (II) Module dri2: vendor="X.Org Foundation"
[     6.675]     compiled for 1.11.3, module version = 1.2.0
[     6.675]     ABI class: X.Org Server Extension, version 6.0
[     6.675] (II) Loading extension DRI2
[     6.675] (II) LoadModule: "fglrx"
[     6.675] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[     6.728] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[     6.728]     compiled for 1.4.99.906, module version = 13.10.10
[     6.728]     Module class: X.Org Video Driver
[     6.729] (II) Loading sub module "fglrxdrm"
[     6.729] (II) LoadModule: "fglrxdrm"
[     6.729] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[     6.731] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[     6.731]     compiled for 1.4.99.906, module version = 13.10.10
[     6.731] (II) AMD Proprietary Linux Driver Version Identifier:13.10.10
[     6.731] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-13.101                   
[     6.731] (II) AMD Proprietary Linux Driver Build Date: May 23 2013 15:49:35
[     6.731] (++) using VT number 7


[     6.731] (WW) Falling back to old probe method for fglrx
[     6.742] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[     6.757] ukiDynamicMajor: found major device number 249
[     6.757] ukiDynamicMajor: found major device number 249
[     6.757] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     6.757] ukiOpenDevice: node name is /dev/ati/card0
[     6.757] ukiOpenDevice: open result is 8, (OK)
[     6.835] ukiOpenByBusid: ukiOpenMinor returns 8
[     6.835] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     6.838] (--) Chipset Supported AMD Graphics Processor (0x68BE) found
[     6.839] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:0:0) found
[     6.839] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:2:0) found
[     6.839] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:9:0) found
[     6.839] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:10:0) found
[     6.839] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[     6.839] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[     6.839] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[     6.839] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[     6.839] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[     6.839] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[     6.839] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[     6.839] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[     6.839] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[     6.839] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
[     6.839] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:0) found
[     6.839] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:0) found
[     6.839] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:2) found
[     6.839] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[     6.839] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[     6.839] (II) AMD Video driver is signed
[     6.840] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[     6.840] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[     6.840] (II) fglrx(0): pEnt->device->identifier=0x7f0b73461a20
[     6.840] (II) fglrx(0): === [xdl_xs111_atiddxPreInit] === begin
[     6.840] (II) Loading sub module "vgahw"
[     6.840] (II) LoadModule: "vgahw"
[     6.840] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[     6.841] (II) Module vgahw: vendor="X.Org Foundation"
[     6.841]     compiled for 1.11.3, module version = 0.1.0
[     6.841]     ABI class: X.Org Video Driver, version 11.0
[     6.841] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[     6.841] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[     6.841] (==) fglrx(0): Default visual is TrueColor
[     6.841] (==) fglrx(0): RGB weight 888
[     6.841] (II) fglrx(0): Using 8 bits per RGB 
[     6.841] (==) fglrx(0): Buffer Tiling is ON
[     6.842] (II) Loading sub module "fglrxdrm"
[     6.842] (II) LoadModule: "fglrxdrm"
[     6.842] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[     6.842] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[     6.842]     compiled for 1.4.99.906, module version = 13.10.10
[     6.854] ukiDynamicMajor: found major device number 249
[     6.854] ukiDynamicMajor: found major device number 249
[     6.854] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     6.854] ukiOpenDevice: node name is /dev/ati/card0
[     6.854] ukiOpenDevice: open result is 11, (OK)
[     6.854] ukiOpenByBusid: ukiOpenMinor returns 11
[     6.854] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     6.854] (**) fglrx(0): NoAccel = NO
[     6.854] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[     6.854] (--) fglrx(0): Chipset: "ATI Radeon HD 5700 Series " (Chipset = 0x68be)
[     6.854] (--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0xe144)
[     6.854] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[     6.854] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[     6.854] (--) fglrx(0): MMIO registers at 0xfea20000
[     6.854] (--) fglrx(0): I/O port at 0x0000e000
[     6.854] (==) fglrx(0): ROM-BIOS at 0x000c0000
[     6.855] (II) fglrx(0): AC Adapter is used
[     6.856] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[     6.856] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
[     6.856] (II) fglrx(0): PCIE card detected
[     6.856] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[     6.856] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[     6.856] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[     6.856] (II) fglrx(0): RandR 1.2 support is enabled!
[     6.856] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[     6.856] (==) fglrx(0): Center Mode is disabled 
[     6.856] (II) Loading sub module "fb"
[     6.856] (II) LoadModule: "fb"
[     6.856] (II) Loading /usr/lib/xorg/modules/libfb.so
[     6.857] (II) Module fb: vendor="X.Org Foundation"
[     6.857]     compiled for 1.11.3, module version = 1.0.0
[     6.857]     ABI class: X.Org ANSI C Emulation, version 0.4
[     6.858] (II) Loading sub module "ddc"
[     6.858] (II) LoadModule: "ddc"
[     6.858] (II) Module "ddc" already built-in
[     6.999] (II) fglrx(0): Output DFP1 using monitor section 0-DFP1
[     6.999] (**) fglrx(0): Option "PreferredMode" "1280x1024"
[     6.999] (**) fglrx(0): Option "Position" "1280 0"
[     6.999] (**) fglrx(0): Option "Disable" "false"
[     6.999] (**) fglrx(0): Option "Rotate" "normal"
[     6.999] (**) fglrx(0): Option "TargetRefresh" "60"
[     6.999] (II) fglrx(0): Output DFP2 using monitor section 0-DFP2
[     6.999] (**) fglrx(0): Option "Position" "1280 0"
[     6.999] (**) fglrx(0): Option "Disable" "true"
[     6.999] (**) fglrx(0): Option "Rotate" "normal"
[     6.999] (**) fglrx(0): Option "TargetRefresh" "60"
[     6.999] (II) fglrx(0): Output DFP3 using monitor section 0-DFP3
[     6.999] (**) fglrx(0): Option "PreferredMode" "1280x1024"
[     6.999] (**) fglrx(0): Option "Position" "0 0"
[     6.999] (**) fglrx(0): Option "Disable" "false"
[     6.999] (**) fglrx(0): Option "Rotate" "normal"
[     6.999] (**) fglrx(0): Option "TargetRefresh" "75"
[     6.999] (II) fglrx(0): Output CRT1 has no monitor section
[     6.999] (II) Loading sub module "ddc"
[     6.999] (II) LoadModule: "ddc"
[     6.999] (II) Module "ddc" already built-in
[     6.999] (II) fglrx(0): Connected Display0: DFP1
[     6.999] (II) fglrx(0):  Display0: Failed to get EDID information. 
[     6.999] (II) fglrx(0): Connected Display1: DFP2
[     6.999] (II) fglrx(0):  Display1: Failed to get EDID information. 
[     6.999] (II) fglrx(0): Connected Display2: DFP3
[     6.999] (II) fglrx(0):  Display2: Failed to get EDID information. 
[     7.000] (II) fglrx(0): EDID for output DFP1
[     7.000] (II) fglrx(0): Manufacturer: HWP  Model: 26ea  Serial#: 16843009
[     7.000] (II) fglrx(0): Year: 2008  Week: 35
[     7.000] (II) fglrx(0): EDID Version: 1.3
[     7.000] (II) fglrx(0): Digital Display Input
[     7.000] (II) fglrx(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[     7.000] (II) fglrx(0): Gamma: 2.40
[     7.000] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[     7.000] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     7.000] (II) fglrx(0): Default color space is primary color space
[     7.000] (II) fglrx(0): First detailed timing is preferred mode
[     7.000] (II) fglrx(0): redX: 0.639 redY: 0.342   greenX: 0.297 greenY: 0.614
[     7.000] (II) fglrx(0): blueX: 0.146 blueY: 0.067   whiteX: 0.312 whiteY: 0.328
[     7.000] (II) fglrx(0): Supported established timings:
[     7.000] (II) fglrx(0): 720x400@70Hz
[     7.000] (II) fglrx(0): 640x480@60Hz
[     7.000] (II) fglrx(0): 640x480@72Hz
[     7.000] (II) fglrx(0): 640x480@75Hz
[     7.000] (II) fglrx(0): 800x600@60Hz
[     7.000] (II) fglrx(0): 800x600@72Hz
[     7.000] (II) fglrx(0): 800x600@75Hz
[     7.000] (II) fglrx(0): 832x624@75Hz
[     7.000] (II) fglrx(0): 1024x768@60Hz
[     7.000] (II) fglrx(0): 1024x768@70Hz
[     7.000] (II) fglrx(0): 1024x768@75Hz
[     7.000] (II) fglrx(0): 1280x1024@75Hz
[     7.000] (II) fglrx(0): 1152x864@75Hz
[     7.000] (II) fglrx(0): Manufacturer's mask: 0
[     7.000] (II) fglrx(0): Supported standard timings:
[     7.000] (II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[     7.000] (II) fglrx(0): Supported detailed timing:
[     7.000] (II) fglrx(0): clock: 108.0 MHz   Image Size:  340 x 270 mm
[     7.000] (II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[     7.000] (II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[     7.000] (II) fglrx(0): Ranges: V min: 50 V max: 77 Hz, H min: 24 H max: 83 kHz, PixClock max 145 MHz
[     7.000] (II) fglrx(0): Monitor name: HP L1750
[     7.000] (II) fglrx(0): Serial No: CNC835RV5Q
[     7.000] (II) fglrx(0): EDID (in hex):
[     7.000] (II) fglrx(0):     00ffffffffffff0022f0ea2601010101
[     7.000] (II) fglrx(0):     2312010380221b8ceea150a3574c9d25
[     7.000] (II) fglrx(0):     115054adef8081800101010101010101
[     7.000] (II) fglrx(0):     010101010101302a009851002a403070
[     7.000] (II) fglrx(0):     1300540e1100001e000000fd00324d18
[     7.000] (II) fglrx(0):     530e000a202020202020000000fc0048
[     7.000] (II) fglrx(0):     50204c313735300a20202020000000ff
[     7.000] (II) fglrx(0):     00434e43383335525635510a202000a5
[     7.000] (II) fglrx(0): EDID vendor "HWP", prod id 9962
[     7.000] (II) fglrx(0): Using EDID range info for horizontal sync
[     7.000] (II) fglrx(0): Using EDID range info for vertical refresh
[     7.000] (II) fglrx(0): Printing DDC gathered Modelines:
[     7.000] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[     7.000] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[     7.000] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[     7.000] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[     7.000] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[     7.000] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[     7.000] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[     7.000] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[     7.000] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[     7.000] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[     7.000] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[     7.000] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[     7.000] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[     7.000] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[     7.000] (II) fglrx(0): Printing probed modes for output DFP1
[     7.000] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[     7.001] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[     7.001] (II) fglrx(0): Modeline "1280x960"x75.0  135.00  1280 1296 1440 1688  960 1025 1028 1066 +hsync +vsync (80.0 kHz)
[     7.001] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1328 1440 1688  960 1025 1028 1066 +hsync +vsync (64.0 kHz)
[     7.001] (II) fglrx(0): Modeline "1280x768"x75.0  135.00  1280 1296 1440 1688  768 1025 1028 1066 +hsync +vsync (80.0 kHz)
[     7.001] (II) fglrx(0): Modeline "1280x768"x60.0  108.00  1280 1328 1440 1688  768 1025 1028 1066 +hsync +vsync (64.0 kHz)
[     7.001] (II) fglrx(0): Modeline "1280x720"x75.0  135.00  1280 1296 1440 1688  720 1025 1028 1066 +hsync +vsync (80.0 kHz)
[     7.001] (II) fglrx(0): Modeline "1280x720"x60.0  108.00  1280 1328 1440 1688  720 1025 1028 1066 +hsync +vsync (64.0 kHz)
[     7.001] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[     7.001] (II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[     7.001] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[     7.001] (II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[     7.001] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[     7.001] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[     7.001] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[     7.001] (II) fglrx(0): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 -hsync -vsync (37.9 kHz)
[     7.001] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[     7.001] (II) fglrx(0): EDID for output DFP2
[     7.001] (II) fglrx(0): EDID for output DFP3
[     7.001] (II) fglrx(0): Manufacturer: HWP  Model: 26ea  Serial#: 16843009
[     7.001] (II) fglrx(0): Year: 2008  Week: 41
[     7.001] (II) fglrx(0): EDID Version: 1.3
[     7.001] (II) fglrx(0): Digital Display Input
[     7.001] (II) fglrx(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[     7.001] (II) fglrx(0): Gamma: 2.40
[     7.001] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[     7.001] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     7.001] (II) fglrx(0): Default color space is primary color space
[     7.001] (II) fglrx(0): First detailed timing is preferred mode
[     7.001] (II) fglrx(0): redX: 0.639 redY: 0.342   greenX: 0.297 greenY: 0.614
[     7.001] (II) fglrx(0): blueX: 0.146 blueY: 0.067   whiteX: 0.312 whiteY: 0.328
[     7.001] (II) fglrx(0): Supported established timings:
[     7.001] (II) fglrx(0): 720x400@70Hz
[     7.001] (II) fglrx(0): 640x480@60Hz
[     7.001] (II) fglrx(0): 640x480@72Hz
[     7.001] (II) fglrx(0): 640x480@75Hz
[     7.001] (II) fglrx(0): 800x600@60Hz
[     7.001] (II) fglrx(0): 800x600@72Hz
[     7.001] (II) fglrx(0): 800x600@75Hz
[     7.001] (II) fglrx(0): 832x624@75Hz
[     7.001] (II) fglrx(0): 1024x768@60Hz
[     7.001] (II) fglrx(0): 1024x768@70Hz
[     7.001] (II) fglrx(0): 1024x768@75Hz
[     7.001] (II) fglrx(0): 1280x1024@75Hz
[     7.001] (II) fglrx(0): 1152x864@75Hz
[     7.001] (II) fglrx(0): Manufacturer's mask: 0
[     7.001] (II) fglrx(0): Supported standard timings:
[     7.001] (II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[     7.001] (II) fglrx(0): Supported detailed timing:
[     7.001] (II) fglrx(0): clock: 108.0 MHz   Image Size:  340 x 270 mm
[     7.001] (II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[     7.001] (II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[     7.001] (II) fglrx(0): Ranges: V min: 50 V max: 77 Hz, H min: 24 H max: 83 kHz, PixClock max 145 MHz
[     7.001] (II) fglrx(0): Monitor name: HP L1750
[     7.001] (II) fglrx(0): Serial No: CNC841RGX4
[     7.001] (II) fglrx(0): EDID (in hex):
[     7.001] (II) fglrx(0):     00ffffffffffff0022f0ea2601010101
[     7.001] (II) fglrx(0):     2912010380221b8ceea150a3574c9d25
[     7.001] (II) fglrx(0):     115054adef8081800101010101010101
[     7.001] (II) fglrx(0):     010101010101302a009851002a403070
[     7.001] (II) fglrx(0):     1300540e1100001e000000fd00324d18
[     7.001] (II) fglrx(0):     530e000a202020202020000000fc0048
[     7.001] (II) fglrx(0):     50204c313735300a20202020000000ff
[     7.001] (II) fglrx(0):     00434e43383431524758340a202000ab
[     7.001] (II) fglrx(0): Printing probed modes for output DFP3
[     7.001] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[     7.001] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[     7.001] (II) fglrx(0): Modeline "1280x960"x75.0  135.00  1280 1296 1440 1688  960 1025 1028 1066 +hsync +vsync (80.0 kHz)
[     7.001] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1328 1440 1688  960 1025 1028 1066 +hsync +vsync (64.0 kHz)
[     7.001] (II) fglrx(0): Modeline "1280x768"x75.0  135.00  1280 1296 1440 1688  768 1025 1028 1066 +hsync +vsync (80.0 kHz)
[     7.001] (II) fglrx(0): Modeline "1280x768"x60.0  108.00  1280 1328 1440 1688  768 1025 1028 1066 +hsync +vsync (64.0 kHz)
[     7.001] (II) fglrx(0): Modeline "1280x720"x75.0  135.00  1280 1296 1440 1688  720 1025 1028 1066 +hsync +vsync (80.0 kHz)
[     7.001] (II) fglrx(0): Modeline "1280x720"x60.0  108.00  1280 1328 1440 1688  720 1025 1028 1066 +hsync +vsync (64.0 kHz)
[     7.001] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[     7.001] (II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[     7.001] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[     7.001] (II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[     7.001] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[     7.001] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[     7.001] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[     7.001] (II) fglrx(0): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 -hsync -vsync (37.9 kHz)
[     7.001] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[     7.001] (II) fglrx(0): EDID for output CRT1
[     7.001] (II) fglrx(0): Output DFP1 connected
[     7.001] (II) fglrx(0): Output DFP2 disabled by config file
[     7.001] (II) fglrx(0): Output DFP3 connected
[     7.001] (II) fglrx(0): Output CRT1 disconnected
[     7.001] (II) fglrx(0): Using user preference for initial modes
[     7.001] (II) fglrx(0): Output DFP1 using initial mode 1280x1024
[     7.001] (II) fglrx(0): Output DFP3 using initial mode 1280x1024
[     7.001] (II) fglrx(0): Display dimensions: (340, 270) mm
[     7.001] (II) fglrx(0): DPI set to (96, 96)
[     7.001] (II) fglrx(0): Eyefinity capable adapter detected.
[     7.001] (II) fglrx(0): Adapter ATI Radeon HD 5700 Series  has 5 configurable heads and 3 displays connected.
[     7.001] (==) fglrx(0):  PseudoColor visuals disabled
[     7.001] (II) Loading sub module "ramdac"
[     7.001] (II) LoadModule: "ramdac"
[     7.001] (II) Module "ramdac" already built-in
[     7.001] (==) fglrx(0): NoDRI = NO
[     7.001] (==) fglrx(0): Capabilities: 0x00000000
[     7.001] (==) fglrx(0): CapabilitiesEx: 0x00000000
[     7.001] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[     7.001] (==) fglrx(0): UseFastTLS=0
[     7.001] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[     7.001] (--) Depth 24 pixmap format is 32 bpp
[     7.001] (II) Loading extension ATIFGLRXDRI
[     7.001] (II) fglrx(0): doing swlDriScreenInit
[     7.001] (II) fglrx(0): swlDriScreenInit for fglrx driver
[     7.001] ukiDynamicMajor: found major device number 249
[     7.001] ukiDynamicMajor: found major device number 249
[     7.001] ukiDynamicMajor: found major device number 249
[     7.001] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     7.002] ukiOpenDevice: node name is /dev/ati/card0
[     7.002] ukiOpenDevice: open result is 12, (OK)
[     7.002] ukiOpenByBusid: ukiOpenMinor returns 12
[     7.002] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     7.002] (II) fglrx(0): [uki] DRM interface version 1.0
[     7.002] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[     7.002] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[     7.002] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f0b7121c000
[     7.002] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[     7.002] (II) fglrx(0): [uki] added 1 reserved context for kernel
[     7.002] (II) fglrx(0): swlDriScreenInit done
[     7.002] (II) fglrx(0): Kernel Module Version Information:
[     7.002] (II) fglrx(0):     Name: fglrx
[     7.002] (II) fglrx(0):     Version: 13.10.10
[     7.002] (II) fglrx(0):     Date: May 23 2013
[     7.002] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[     7.002] (II) fglrx(0): Kernel Module version matches driver.
[     7.002] (II) fglrx(0): Kernel Module Build Time Information:
[     7.002] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.5.0-39-generic
[     7.002] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[     7.002] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[     7.002] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[     7.002] (II) fglrx(0): [uki] register handle = 0x00004000
[     7.004] (II) fglrx(0): DRI initialization successfull
[     7.005] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x012c0000
[     7.006] (==) fglrx(0): Backing store disabled
[     7.006] (II) Loading extension FGLRXEXTENSION
[     7.006] (==) fglrx(0): DPMS enabled
[     7.006] (II) fglrx(0): Initialized in-driver Xinerama extension
[     7.006] (**) fglrx(0): Textured Video is enabled.
[     7.006] (II) LoadModule: "glesx"
[     7.007] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/glesx.so
[     7.018] (II) Module glesx: vendor="X.Org Foundation"
[     7.018]     compiled for 1.4.99.906, module version = 1.0.0
[     7.018] (II) Loading extension GLESX
[     7.018] (II) fglrx(0): GLESX enableFlags = 592
[     7.019] (II) fglrx(0): GLESX is enabled
[     7.019] (II) LoadModule: "amdxmm"
[     7.019] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/amdxmm.so
[     7.020] (II) Module amdxmm: vendor="X.Org Foundation"
[     7.020]     compiled for 1.4.99.906, module version = 2.0.0
[     7.039] (II) Loading extension AMDXVOPL
[     7.039] (II) Loading extension AMDXVBA
[     7.040] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[     7.043] (II) fglrx(0): Enable composite support successfully
[     7.043] (II) fglrx(0): X context handle = 0x1
[     7.043] (II) fglrx(0): [DRI] installation complete
[     7.043] (==) fglrx(0): Silken mouse enabled
[     7.043] (==) fglrx(0): Using HW cursor of display infrastructure!
[     7.044] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[     7.052] (II) fglrx(0): User Preference Output DFP1 using refresh rate 60.0 Hz.
[     7.096] (II) fglrx(0): User Preference Output DFP3 using refresh rate 75.0 Hz.
[     7.118] (WW) fglrx(0): Framebuffer compression is disabled by the driver: Video Ram = 262144 kByte
[     7.118] (--) RandR disabled
[     7.118] (II) Initializing built-in extension Generic Event Extension
[     7.118] (II) Initializing built-in extension SHAPE
[     7.118] (II) Initializing built-in extension MIT-SHM
[     7.118] (II) Initializing built-in extension XInputExtension
[     7.118] (II) Initializing built-in extension XTEST
[     7.118] (II) Initializing built-in extension BIG-REQUESTS
[     7.118] (II) Initializing built-in extension SYNC
[     7.118] (II) Initializing built-in extension XKEYBOARD
[     7.118] (II) Initializing built-in extension XC-MISC
[     7.118] (II) Initializing built-in extension SECURITY
[     7.118] (II) Initializing built-in extension XINERAMA
[     7.118] (II) Initializing built-in extension XFIXES
[     7.118] (II) Initializing built-in extension RENDER
[     7.118] (II) Initializing built-in extension RANDR
[     7.118] (II) Initializing built-in extension COMPOSITE
[     7.118] (II) Initializing built-in extension DAMAGE
[     7.121] ukiDynamicMajor: found major device number 249
[     7.121] ukiDynamicMajor: found major device number 249
[     7.121] ukiDynamicMajor: found major device number 249
[     7.121] ukiOpenDevice: node name is /dev/ati/card0
[     7.121] ukiOpenDevice: open result is 13, (OK)
[     7.121] ukiGetBusid returned 'PCI:1:0:0'
[     7.121] ukiOpenDevice: node name is /dev/ati/card1
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: Open failed
[     7.121] ukiOpenDevice: node name is /dev/ati/card2
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: Open failed
[     7.121] ukiOpenDevice: node name is /dev/ati/card3
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: Open failed
[     7.121] ukiOpenDevice: node name is /dev/ati/card4
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: Open failed
[     7.121] ukiOpenDevice: node name is /dev/ati/card5
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: Open failed
[     7.121] ukiOpenDevice: node name is /dev/ati/card6
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: Open failed
[     7.121] ukiOpenDevice: node name is /dev/ati/card7
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: Open failed
[     7.121] ukiOpenDevice: node name is /dev/ati/card8
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: Open failed
[     7.121] ukiOpenDevice: node name is /dev/ati/card9
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: Open failed
[     7.121] ukiOpenDevice: node name is /dev/ati/card10
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: Open failed
[     7.121] ukiOpenDevice: node name is /dev/ati/card11
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: Open failed
[     7.121] ukiOpenDevice: node name is /dev/ati/card12
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: Open failed
[     7.121] ukiOpenDevice: node name is /dev/ati/card13
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: Open failed
[     7.121] ukiOpenDevice: node name is /dev/ati/card14
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: Open failed
[     7.121] ukiOpenDevice: node name is /dev/ati/card15
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: open result is -1, (No such device)
[     7.121] ukiOpenDevice: Open failed
[     7.121] ukiDynamicMajor: found major device number 249
[     7.121] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     7.121] ukiOpenDevice: node name is /dev/ati/card0
[     7.121] ukiOpenDevice: open result is 13, (OK)
[     7.121] ukiOpenByBusid: ukiOpenMinor returns 13
[     7.121] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     7.142] ukiDynamicMajor: found major device number 249
[     7.142] ukiDynamicMajor: found major device number 249
[     7.142] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     7.142] ukiOpenDevice: node name is /dev/ati/card0
[     7.142] ukiOpenDevice: open result is 13, (OK)
[     7.142] ukiOpenByBusid: ukiOpenMinor returns 13
[     7.142] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     7.170] ukiDynamicMajor: found major device number 249
[     7.170] ukiDynamicMajor: found major device number 249
[     7.170] ukiDynamicMajor: found major device number 249
[     7.170] ukiOpenDevice: node name is /dev/ati/card0
[     7.170] ukiOpenDevice: open result is 14, (OK)
[     7.170] ukiGetBusid returned 'PCI:1:0:0'
[     7.170] ukiOpenDevice: node name is /dev/ati/card1
[     7.170] ukiOpenDevice: open result is -1, (No such device)
[     7.170] ukiOpenDevice: open result is -1, (No such device)
[     7.170] ukiOpenDevice: Open failed
[     7.170] ukiOpenDevice: node name is /dev/ati/card2
[     7.170] ukiOpenDevice: open result is -1, (No such device)
[     7.170] ukiOpenDevice: open result is -1, (No such device)
[     7.170] ukiOpenDevice: Open failed
[     7.170] ukiOpenDevice: node name is /dev/ati/card3
[     7.170] ukiOpenDevice: open result is -1, (No such device)
[     7.170] ukiOpenDevice: open result is -1, (No such device)
[     7.170] ukiOpenDevice: Open failed
[     7.170] ukiOpenDevice: node name is /dev/ati/card4
[     7.170] ukiOpenDevice: open result is -1, (No such device)
[     7.170] ukiOpenDevice: open result is -1, (No such device)
[     7.170] ukiOpenDevice: Open failed
[     7.170] ukiOpenDevice: node name is /dev/ati/card5
[     7.170] ukiOpenDevice: open result is -1, (No such device)
[     7.171] ukiOpenDevice: open result is -1, (No such device)
[     7.171] ukiOpenDevice: Open failed
[     7.171] ukiOpenDevice: node name is /dev/ati/card6
[     7.171] ukiOpenDevice: open result is -1, (No such device)
[     7.171] ukiOpenDevice: open result is -1, (No such device)
[     7.171] ukiOpenDevice: Open failed
[     7.171] ukiOpenDevice: node name is /dev/ati/card7
[     7.171] ukiOpenDevice: open result is -1, (No such device)
[     7.171] ukiOpenDevice: open result is -1, (No such device)
[     7.171] ukiOpenDevice: Open failed
[     7.171] ukiOpenDevice: node name is /dev/ati/card8
[     7.171] ukiOpenDevice: open result is -1, (No such device)
[     7.171] ukiOpenDevice: open result is -1, (No such device)
[     7.171] ukiOpenDevice: Open failed
[     7.171] ukiOpenDevice: node name is /dev/ati/card9
[     7.171] ukiOpenDevice: open result is -1, (No such device)
[     7.171] ukiOpenDevice: open result is -1, (No such device)
[     7.171] ukiOpenDevice: Open failed
[     7.171] ukiOpenDevice: node name is /dev/ati/card10
[     7.171] ukiOpenDevice: open result is -1, (No such device)
[     7.171] ukiOpenDevice: open result is -1, (No such device)
[     7.171] ukiOpenDevice: Open failed
[     7.171] ukiOpenDevice: node name is /dev/ati/card11
[     7.171] ukiOpenDevice: open result is -1, (No such device)
[     7.171] ukiOpenDevice: open result is -1, (No such device)
[     7.171] ukiOpenDevice: Open failed
[     7.171] ukiOpenDevice: node name is /dev/ati/card12
[     7.171] ukiOpenDevice: open result is -1, (No such device)
[     7.171] ukiOpenDevice: open result is -1, (No such device)
[     7.171] ukiOpenDevice: Open failed
[     7.171] ukiOpenDevice: node name is /dev/ati/card13
[     7.171] ukiOpenDevice: open result is -1, (No such device)
[     7.171] ukiOpenDevice: open result is -1, (No such device)
[     7.171] ukiOpenDevice: Open failed
[     7.171] ukiOpenDevice: node name is /dev/ati/card14
[     7.171] ukiOpenDevice: open result is -1, (No such device)
[     7.171] ukiOpenDevice: open result is -1, (No such device)
[     7.171] ukiOpenDevice: Open failed
[     7.171] ukiOpenDevice: node name is /dev/ati/card15
[     7.171] ukiOpenDevice: open result is -1, (No such device)
[     7.171] ukiOpenDevice: open result is -1, (No such device)
[     7.171] ukiOpenDevice: Open failed
[     7.171] ukiDynamicMajor: found major device number 249
[     7.171] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     7.171] ukiOpenDevice: node name is /dev/ati/card0
[     7.171] ukiOpenDevice: open result is 14, (OK)
[     7.171] ukiOpenByBusid: ukiOpenMinor returns 14
[     7.171] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     7.328] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[     7.328] (II) fglrx(0): OverDrive5 Detected!
[     7.348] (II) fglrx(0): Setting screen physical size to 677 x 270
[     7.358] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     7.360] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     7.361] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     7.361] (II) LoadModule: "evdev"
[     7.361] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.362] (II) Module evdev: vendor="X.Org Foundation"
[     7.363]     compiled for 1.11.3, module version = 2.7.0
[     7.363]     Module class: X.Org XInput Driver
[     7.363]     ABI class: X.Org XInput driver, version 16.0
[     7.363] (II) Using input driver 'evdev' for 'Power Button'
[     7.363] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.363] (**) Power Button: always reports core events
[     7.363] (**) evdev: Power Button: Device: "/dev/input/event1"
[     7.363] (--) evdev: Power Button: Vendor 0 Product 0x1
[     7.363] (--) evdev: Power Button: Found keys
[     7.363] (II) evdev: Power Button: Configuring as keyboard
[     7.363] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     7.363] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     7.363] (**) Option "xkb_rules" "evdev"
[     7.363] (**) Option "xkb_model" "pc105"
[     7.363] (**) Option "xkb_layout" "us"
[     7.363] (**) Option "xkb_variant" "intl"
[     7.364] (II) XKB: reuse xkmfile /var/lib/xkb/server-A5431D4A34463C892C9E905E2E421B30A3CC30DD.xkm
[     7.365] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     7.365] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     7.365] (II) Using input driver 'evdev' for 'Power Button'
[     7.365] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.365] (**) Power Button: always reports core events
[     7.365] (**) evdev: Power Button: Device: "/dev/input/event0"
[     7.365] (--) evdev: Power Button: Vendor 0 Product 0x1
[     7.365] (--) evdev: Power Button: Found keys
[     7.365] (II) evdev: Power Button: Configuring as keyboard
[     7.365] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     7.365] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     7.365] (**) Option "xkb_rules" "evdev"
[     7.365] (**) Option "xkb_model" "pc105"
[     7.365] (**) Option "xkb_layout" "us"
[     7.365] (**) Option "xkb_variant" "intl"
[     7.365] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event10)
[     7.366] (II) No input driver specified, ignoring this device.
[     7.366] (II) This device may have been added with another device file.
[     7.366] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event3)
[     7.366] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[     7.366] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[     7.366] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.366] (**) Logitech USB Optical Mouse: always reports core events
[     7.366] (**) evdev: Logitech USB Optical Mouse: Device: "/dev/input/event3"
[     7.366] (--) evdev: Logitech USB Optical Mouse: Vendor 0x46d Product 0xc05a
[     7.366] (--) evdev: Logitech USB Optical Mouse: Found 3 mouse buttons
[     7.366] (--) evdev: Logitech USB Optical Mouse: Found scroll wheel(s)
[     7.366] (--) evdev: Logitech USB Optical Mouse: Found relative axes
[     7.366] (--) evdev: Logitech USB Optical Mouse: Found x and y relative axes
[     7.366] (II) evdev: Logitech USB Optical Mouse: Configuring as mouse
[     7.366] (II) evdev: Logitech USB Optical Mouse: Adding scrollwheel support
[     7.366] (**) evdev: Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[     7.366] (**) evdev: Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     7.366] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1.2/2-1.2:1.0/input/input3/event3"
[     7.366] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 8)
[     7.366] (II) evdev: Logitech USB Optical Mouse: initialized for relative axes.
[     7.366] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[     7.366] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[     7.366] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[     7.366] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[     7.366] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse0)
[     7.366] (II) No input driver specified, ignoring this device.
[     7.366] (II) This device may have been added with another device file.
[     7.366] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event4)
[     7.366] (II) No input driver specified, ignoring this device.
[     7.366] (II) This device may have been added with another device file.
[     7.367] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event5)
[     7.367] (II) No input driver specified, ignoring this device.
[     7.367] (II) This device may have been added with another device file.
[     7.367] (II) config/udev: Adding input device HDA ATI SB Line Out Side (/dev/input/event6)
[     7.367] (II) No input driver specified, ignoring this device.
[     7.367] (II) This device may have been added with another device file.
[     7.367] (II) config/udev: Adding input device HDA ATI SB Line Out CLFE (/dev/input/event7)
[     7.367] (II) No input driver specified, ignoring this device.
[     7.367] (II) This device may have been added with another device file.
[     7.367] (II) config/udev: Adding input device HDA ATI SB Line Out Surround (/dev/input/event8)
[     7.367] (II) No input driver specified, ignoring this device.
[     7.367] (II) This device may have been added with another device file.
[     7.367] (II) config/udev: Adding input device HDA ATI SB Line Out Front (/dev/input/event9)
[     7.367] (II) No input driver specified, ignoring this device.
[     7.367] (II) This device may have been added with another device file.
[     7.367] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[     7.367] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     7.367] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     7.367] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.367] (**) AT Translated Set 2 keyboard: always reports core events
[     7.367] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[     7.368] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[     7.368] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     7.368] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     7.368] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[     7.368] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[     7.368] (**) Option "xkb_rules" "evdev"
[     7.368] (**) Option "xkb_model" "pc105"
[     7.368] (**) Option "xkb_layout" "us"
[     7.368] (**) Option "xkb_variant" "intl"
[     7.393] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[     7.805] (II) fglrx(0): EDID vendor "HWP", prod id 9962
[     7.805] (II) fglrx(0): Using hsync ranges from config file
[     7.805] (II) fglrx(0): Using vrefresh ranges from config file
[     7.805] (II) fglrx(0): Printing DDC gathered Modelines:
[     7.805] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[     7.805] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[     7.805] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[     7.805] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[     7.805] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[     7.805] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[     7.805] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[     7.805] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[     7.805] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[     7.805] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[     7.805] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[     7.805] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[     7.805] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[     7.805] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[     8.009] (II) fglrx(0): EDID vendor "HWP", prod id 9962
[     8.009] (II) fglrx(0): Using hsync ranges from config file
[     8.009] (II) fglrx(0): Using vrefresh ranges from config file
[     8.009] (II) fglrx(0): Printing DDC gathered Modelines:
[     8.009] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[     8.009] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[     8.009] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[     8.009] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[     8.009] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[     8.009] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[     8.009] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[     8.009] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[     8.009] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[     8.009] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[     8.009] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[     8.009] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[     8.009] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[     8.009] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    81.025] (II) fglrx(0): EDID vendor "HWP", prod id 9962
[    81.025] (II) fglrx(0): Using hsync ranges from config file
[    81.025] (II) fglrx(0): Using vrefresh ranges from config file
[    81.025] (II) fglrx(0): Printing DDC gathered Modelines:
[    81.025] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    81.025] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    81.025] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    81.025] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    81.025] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    81.025] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    81.025] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    81.025] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    81.025] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    81.025] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    81.025] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    81.025] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    81.025] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    81.025] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    81.532] (II) fglrx(0): EDID vendor "HWP", prod id 9962
[    81.532] (II) fglrx(0): Using hsync ranges from config file
[    81.532] (II) fglrx(0): Using vrefresh ranges from config file
[    81.532] (II) fglrx(0): Printing DDC gathered Modelines:
[    81.532] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    81.532] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    81.532] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    81.532] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    81.532] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    81.532] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    81.532] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    81.532] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    81.532] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    81.532] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    81.532] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    81.532] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    81.532] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    81.532] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    81.788] (II) fglrx(0): EDID vendor "HWP", prod id 9962
[    81.788] (II) fglrx(0): Using hsync ranges from config file
[    81.788] (II) fglrx(0): Using vrefresh ranges from config file
[    81.788] (II) fglrx(0): Printing DDC gathered Modelines:
[    81.788] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    81.788] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    81.788] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    81.788] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    81.788] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    81.788] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    81.788] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    81.788] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    81.788] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    81.788] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    81.788] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    81.788] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    81.788] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    81.788] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    84.482] (II) XKB: reuse xkmfile /var/lib/xkb/server-66EE0154F48ACA3B8B41E2DABCBEB27CFFFED199.xkm
[   100.590] (II) fglrx(0): EDID vendor "HWP", prod id 9962
[   100.590] (II) fglrx(0): Using hsync ranges from config file
[   100.590] (II) fglrx(0): Using vrefresh ranges from config file
[   100.590] (II) fglrx(0): Printing DDC gathered Modelines:
[   100.590] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   100.590] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   100.590] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   100.590] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   100.590] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   100.590] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   100.590] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   100.590] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   100.590] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   100.590] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   100.590] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   100.590] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   100.590] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   100.590] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   102.282] (II) fglrx(0): EDID vendor "HWP", prod id 9962
[   102.282] (II) fglrx(0): Using hsync ranges from config file
[   102.285] (II) fglrx(0): Using vrefresh ranges from config file
[   102.285] (II) fglrx(0): Printing DDC gathered Modelines:
[   102.285] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   102.285] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   102.285] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   102.285] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   102.285] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   102.285] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   102.285] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   102.285] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   102.286] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   102.286] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   102.286] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   102.286] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   102.286] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   102.286] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   123.771] (II) fglrx(0): EDID vendor "HWP", prod id 9962
[   123.771] (II) fglrx(0): Using hsync ranges from config file
[   123.771] (II) fglrx(0): Using vrefresh ranges from config file
[   123.771] (II) fglrx(0): Printing DDC gathered Modelines:
[   123.771] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   123.771] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   123.771] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   123.771] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   123.771] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   123.771] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   123.771] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   123.771] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   123.771] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   123.771] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   123.771] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   123.771] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   123.771] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   123.771] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   127.442] (II) fglrx(0): EDID vendor "HWP", prod id 9962
[   127.442] (II) fglrx(0): Using hsync ranges from config file
[   127.442] (II) fglrx(0): Using vrefresh ranges from config file
[   127.442] (II) fglrx(0): Printing DDC gathered Modelines:
[   127.442] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   127.442] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   127.442] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   127.442] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   127.442] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   127.442] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   127.442] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   127.442] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   127.443] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   127.443] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   127.443] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   127.443] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   127.443] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   127.443] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   314.073] (II) fglrx(0): EDID vendor "HWP", prod id 9962
[   314.073] (II) fglrx(0): Using hsync ranges from config file
[   314.073] (II) fglrx(0): Using vrefresh ranges from config file
[   314.073] (II) fglrx(0): Printing DDC gathered Modelines:
[   314.073] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   314.073] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   314.073] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   314.073] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   314.073] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   314.073] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   314.073] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   314.073] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   314.073] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   314.073] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   314.073] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   314.073] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   314.073] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   314.073] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   314.082] (II) fglrx(0): xdl_xs111_atiddxDisplayScreenEnableDisplays
[   314.108] (II) fglrx(0): User Preference Output DFP2 using refresh rate 60.0 Hz.
[   314.260] (II) fglrx(0): xdl_xs111_atiddxDisplayScreenEnableDisplays
[  1278.495] (II) fglrx(0): EDID vendor "HWP", prod id 9962
[  1278.495] (II) fglrx(0): Using hsync ranges from config file
[  1278.495] (II) fglrx(0): Using vrefresh ranges from config file
[  1278.495] (II) fglrx(0): Printing DDC gathered Modelines:
[  1278.495] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1278.495] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1278.495] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  1278.495] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  1278.495] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1278.495] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1278.495] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  1278.495] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  1278.495] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  1278.495] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1278.495] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  1278.495] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1278.495] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  1278.495] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  1278.503] (II) fglrx(0): xdl_xs111_atiddxDisplayScreenEnableDisplays
[  1278.518] (II) fglrx(0): User Preference Output DFP1 using refresh rate 60.0 Hz.
 
```

any advice ???

---

### Post by GizahNL on 2013-09-07
shameless bump ;) 

Anybody got any solutions ??? Working with just 2 screens is quite a bitch :/

---

