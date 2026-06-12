---
title: "Force DVI Output Even with no monitor connected"
date: 2013-01-25
forum: Mythbuntu
---

### Post by tez1982 on 2013-01-25
My media centre sometimes has the TV (connected via DVI) powered off on boot. When this happens, I power on the TV and get no signal. A normal boot with the TV powered on works fine.

Is there a way to force the graphics card to output through DVI (DFP1) even if no monitor is detected?

System Info:
Mythbuntu 12.04
Radeon HD 3000
fglrx driver
Mythtv 0.26


Xorg.conf
```

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:5:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        DefaultDepth     24
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

```

Xorg.0.log
```
[    19.687]
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    19.687] X Protocol Version 11, Revision 0
[    19.687] Build Operating System: Linux 2.6.42-23-generic x86_64 Ubuntu
[    19.687] Current Operating System: Linux mediacentre 3.2.0-35-generic #55-Ubuntu SMP Wed Dec 5 17:42:16 UTC 2012 x86_64
[    19.687] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-35-generic root=UUID=15e12c46-6e77-40e4-a0cd-082074da7a44 ro quiet splash radeon.audio=1 vt.handoff=7
[    19.687] Build Date: 29 August 2012  12:12:33AM
[    19.687] xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see http://www.ubuntu.com/support)
[    19.687] Current version of pixman: 0.24.4
[    19.687]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    19.687] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.687] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan 25 17:11:50 2013
[    19.687] (==) Using config file: "/etc/X11/xorg.conf"
[    19.687] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.687] (==) ServerLayout "aticonfig Layout"
[    19.687] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    19.687] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    19.687] (**) |   |-->Device "aticonfig-Device[0]-0"
[    19.687] (==) Automatically adding devices
[    19.687] (==) Automatically enabling devices
[    19.687] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.687]    Entry deleted from font path.
[    19.687] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    19.687]    Entry deleted from font path.
[    19.687] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    19.687]    Entry deleted from font path.
[    19.687] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    19.687]    Entry deleted from font path.
[    19.687] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    19.687]    Entry deleted from font path.
[    19.687] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    19.687]    Entry deleted from font path.
[    19.687] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[    19.687] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.687] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    19.687] (II) Loader magic: 0x7f77b3100b00
[    19.687] (II) Module ABI versions:
[    19.687]    X.Org ANSI C Emulation: 0.4
[    19.687]    X.Org Video Driver: 11.0
[    19.687]    X.Org ANSI C Emulation: 0.4
[    19.687]    X.Org Video Driver: 11.0
[    19.687]    X.Org XInput driver : 16.0
[    19.687]    X.Org Server Extension : 6.0
[    19.688] (--) PCI:*(0:1:5:0) 1002:9616:1043:8388 rev 0, Mem @ 0xd0000000/268435456, 0xfe9f0000/65536, 0xfe800000/1048576, I/O @ 0x0000d000/256
[    19.688] (II) Open ACPI successful (/var/run/acpid.socket)
[    19.688] (II) "extmod" will be loaded by default.
[    19.688] (II) "dbe" will be loaded by default.
[    19.688] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    19.688] (II) "record" will be loaded by default.
[    19.688] (II) "dri" will be loaded by default.
[    19.688] (II) "dri2" will be loaded by default.
[    19.688] (II) LoadModule: "glx"
[    19.722] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[    19.722] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    19.722]    compiled for 6.9.0, module version = 1.0.0
[    19.723] (II) Loading extension GLX
[    19.723] (II) LoadModule: "extmod"
[    19.723] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    19.723] (II) Module extmod: vendor="X.Org Foundation"
[    19.723]    compiled for 1.11.3, module version = 1.0.0
[    19.723]    Module class: X.Org Server Extension
[    19.723]    ABI class: X.Org Server Extension, version 6.0
[    19.723] (II) Loading extension MIT-SCREEN-SAVER
[    19.723] (II) Loading extension XFree86-VidModeExtension
[    19.723] (II) Loading extension XFree86-DGA
[    19.723] (II) Loading extension DPMS
[    19.723] (II) Loading extension XVideo
[    19.723] (II) Loading extension XVideo-MotionCompensation
[    19.723] (II) Loading extension X-Resource
[    19.723] (II) LoadModule: "dbe"
[    19.723] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    19.723] (II) Module dbe: vendor="X.Org Foundation"
[    19.723]    compiled for 1.11.3, module version = 1.0.0
[    19.723]    Module class: X.Org Server Extension
[    19.723]    ABI class: X.Org Server Extension, version 6.0
[    19.723] (II) Loading extension DOUBLE-BUFFER
[    19.723] (II) LoadModule: "record"
[    19.723] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    19.723] (II) Module record: vendor="X.Org Foundation"
[    19.723]    compiled for 1.11.3, module version = 1.13.0
[    19.723]    Module class: X.Org Server Extension
[    19.723]    ABI class: X.Org Server Extension, version 6.0
[    19.723] (II) Loading extension RECORD
[    19.723] (II) LoadModule: "dri"
[    19.724] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    19.724] (II) Module dri: vendor="X.Org Foundation"
[    19.724] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    19.724] (II) Module dri: vendor="X.Org Foundation"
[    19.724]    compiled for 1.11.3, module version = 1.0.0
[    19.724]    ABI class: X.Org Server Extension, version 6.0
[    19.724] (II) Loading extension XFree86-DRI
[    19.724] (II) LoadModule: "dri2"
[    19.724] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.724] (II) Module dri2: vendor="X.Org Foundation"
[    19.724]    compiled for 1.11.3, module version = 1.2.0
[    19.724]    ABI class: X.Org Server Extension, version 6.0
[    19.724] (II) Loading extension DRI2
[    19.724] (II) LoadModule: "fglrx"
[    19.724] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    19.739] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    19.739]    compiled for 1.4.99.906, module version = 8.96.4
[    19.739]    Module class: X.Org Video Driver
[    19.739] (II) Loading sub module "fglrxdrm"
[    19.739] (II) LoadModule: "fglrxdrm"
[    19.739] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    19.739] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    19.739]    compiled for 1.4.99.906, module version = 8.96.4
[    19.739] (II) ATI Proprietary Linux Driver Version Identifier:8.96.4
[    19.739] (II) ATI Proprietary Linux Driver Release Identifier: 8.96.7
[    19.739] (II) ATI Proprietary Linux Driver Build Date: Mar 12 2012 13:06:50
[    19.739] (++) using VT number 7

[    19.739] (WW) Falling back to old probe method for fglrx
[    19.744] (II) Loading PCS database from /etc/ati/amdpcsdb
[    19.744] (--) Chipset Supported AMD Graphics Processor (0x9616) found
[    19.744] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[    19.744] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[    19.744] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
[    19.744] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[    19.744] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[    19.744] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
[    19.744] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[    19.744] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[    19.744] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
[    19.744] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[    19.744] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[    19.744] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[    19.744] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
[    19.745] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    19.745] (II) AMD Video driver is signed
[    19.745] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    19.745] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    19.745] (II) fglrx(0): pEnt->device->identifier=0x7f77b3a1dec0
[    19.745] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    19.745] (II) fglrx(0): pEnt->device->identifier=0x7f77b3a1dec0
[    19.745] (II) fglrx(0): === [xdl_xs111_atiddxPreInit] === begin
[    19.745] (II) Loading sub module "vgahw"
[    19.745] (II) LoadModule: "vgahw"
[    19.745] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    19.745] (II) Module vgahw: vendor="X.Org Foundation"
[    19.745]    compiled for 1.11.3, module version = 0.1.0
[    19.745]    ABI class: X.Org Video Driver, version 11.0
[    19.745] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    19.745] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    19.745] (==) fglrx(0): Default visual is TrueColor
[    19.745] (**) fglrx(0): Option "DPMS" "true"
[    19.745] (==) fglrx(0): RGB weight 888
[    19.745] (II) fglrx(0): Using 8 bits per RGB
[    19.745] (==) fglrx(0): Buffer Tiling is ON
[    19.745] (II) Loading sub module "fglrxdrm"
[    19.745] (II) LoadModule: "fglrxdrm"
[    19.745] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    19.745] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    19.745]    compiled for 1.4.99.906, module version = 8.96.4
[    19.747] ukiDynamicMajor: found major device number 249
[    19.747] ukiDynamicMajor: found major device number 249
[    19.747] ukiOpenByBusid: Searching for BusID PCI:1:5:0
[    19.747] ukiOpenDevice: node name is /dev/ati/card0
[    19.747] ukiOpenDevice: open result is 12, (OK)
[    19.747] ukiOpenByBusid: ukiOpenMinor returns 12
[    19.747] ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
[    19.747] (**) fglrx(0): NoAccel = NO
[    19.747] (**) fglrx(0): ATI 2D Acceleration Architecture enabled
[    19.747] (--) fglrx(0): Chipset: "ATI Radeon 3000 Graphics" (Chipset = 0x9616)
[    19.747] (--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x8388)
[    19.747] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    19.747] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    19.747] (--) fglrx(0): MMIO registers at 0xfe9f0000
[    19.747] (--) fglrx(0): I/O port at 0x0000d000
[    19.747] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    19.748] (II) fglrx(0): AC Adapter is used
[    19.754] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    19.755] (II) Loading sub module "vbe"
[    19.755] (II) LoadModule: "vbe"
[    19.755] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    19.755] (II) Module vbe: vendor="X.Org Foundation"
[    19.755]    compiled for 1.11.3, module version = 1.1.0
[    19.755]    ABI class: X.Org Video Driver, version 11.0
[    19.755] (II) fglrx(0): VESA BIOS detected
[    19.755] (II) fglrx(0): VESA VBE Version 3.0
[    19.755] (II) fglrx(0): VESA BIOS detected
[    19.755] (II) fglrx(0): VESA VBE Version 3.0
[    19.755] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    19.755] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    19.755] (II) fglrx(0): VESA VBE OEM Software Rev: 10.82
[    19.755] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc.
[    19.755] (II) fglrx(0): VESA VBE OEM Product: RS780
[    19.755] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    19.762] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    19.762] (--) fglrx(0): Video RAM: 262144 kByte, Type: DDR2
[    19.762] (II) fglrx(0): PCIE card detected
[    19.762] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    19.762] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    19.767] (II) fglrx(0): Using adapter: 1:5.0.
[    19.776] (II) fglrx(0): [FB] MC range(MCFBBase = 0xc0000000, MCFBSize = 0x10000000)
[    19.797] (II) fglrx(0): Interrupt handler installed at IRQ 18.
[    19.798] (II) fglrx(0): RandR 1.2 support is enabled!
[    19.798] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    19.798] (==) fglrx(0): Center Mode is disabled
[    19.798] (II) Loading sub module "fb"
[    19.798] (II) LoadModule: "fb"
[    19.798] (II) Loading /usr/lib/xorg/modules/libfb.so
[    19.798] (II) Module fb: vendor="X.Org Foundation"
[    19.798]    compiled for 1.11.3, module version = 1.0.0
[    19.798]    ABI class: X.Org ANSI C Emulation, version 0.4
[    19.798] (II) Loading sub module "ddc"
[    19.798] (II) LoadModule: "ddc"
[    19.798] (II) Module "ddc" already built-in
[    20.724] (II) fglrx(0): Finished Initialize PPLIB!
[    20.746] (II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
[    20.746] (II) fglrx(0): Output CRT1 has no monitor section
[    20.746] (II) Loading sub module "ddc"
[    20.746] (II) LoadModule: "ddc"
[    20.746] (II) Module "ddc" already built-in
[    20.746] (II) fglrx(0): Connected Display0: DFP1
[    20.746] (II) fglrx(0): Display0 EDID data ---------------------------
[    20.746] (II) fglrx(0): Manufacturer: CVT  Model: 1080  Serial#: 20070707
[    20.746] (II) fglrx(0): Year: 2007  Week: 32
[    20.746] (II) fglrx(0): EDID Version: 1.3
[    20.746] (II) fglrx(0): Digital Display Input
[    20.746] (II) fglrx(0): Max Image Size [cm]: horiz.: 70  vert.: 40
[    20.746] (II) fglrx(0): Gamma: 2.20
[    20.746] (II) fglrx(0): No DPMS capabilities specified
[    20.746] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
[    20.746] (II) fglrx(0): First detailed timing is preferred mode
[    20.746] (II) fglrx(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[    20.746] (II) fglrx(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
[    20.746] (II) fglrx(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[    20.746] (II) fglrx(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
[    20.746] (II) fglrx(0): Manufacturer's mask: 0
[    20.746] (II) fglrx(0): Supported detailed timing:
[    20.746] (II) fglrx(0): clock: 148.5 MHz   Image Size:  735 x 420 mm
[    20.746] (II) fglrx(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[    20.746] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    20.746] (II) fglrx(0): Supported detailed timing:
[    20.746] (II) fglrx(0): clock: 27.0 MHz   Image Size:  735 x 420 mm
[    20.746] (II) fglrx(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    20.746] (II) fglrx(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    20.746] (II) fglrx(0): Monitor name: CVTE TV
[    20.746] (II) fglrx(0): Ranges: V min: 48 V max: 62 Hz, H min: 14 H max: 70 kHz, PixClock max 155 MHz
[    20.746] (II) fglrx(0): Number of EDID sections to follow: 1
[    20.746] (II) fglrx(0): EDID (in hex):
[    20.746] (II) fglrx(0):     00ffffffffffff000ed4801033413201
[    20.746] (II) fglrx(0):     20110103804628780aee91a3544c9926
[    20.746] (II) fglrx(0):     0f505400000001010101010101010101
[    20.746] (II) fglrx(0):     010101010101023a80d072382d40102c
[    20.746] (II) fglrx(0):     4580dfa42100001e8c0ad08a20e02d10
[    20.746] (II) fglrx(0):     103e9600dfa421000018000000fc0043
[    20.746] (II) fglrx(0):     5654452054560a2020202020000000fd
[    20.746] (II) fglrx(0):     00303e0e460f000a2020202020200196
[    20.746] (II) fglrx(0): End of Display0 EDID data --------------------
[    20.840] (II) fglrx(0): EDID for output DFP1
[    20.840] (II) fglrx(0): Manufacturer: CVT  Model: 1080  Serial#: 20070707
[    20.840] (II) fglrx(0): Year: 2007  Week: 32
[    20.840] (II) fglrx(0): EDID Version: 1.3
[    20.840] (II) fglrx(0): Digital Display Input
[    20.840] (II) fglrx(0): Max Image Size [cm]: horiz.: 70  vert.: 40
[    20.840] (II) fglrx(0): Gamma: 2.20
[    20.840] (II) fglrx(0): No DPMS capabilities specified
[    20.840] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
[    20.840] (II) fglrx(0): First detailed timing is preferred mode
[    20.840] (II) fglrx(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[    20.840] (II) fglrx(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
[    20.840] (II) fglrx(0): Manufacturer's mask: 0
[    20.840] (II) fglrx(0): Supported detailed timing:
[    20.840] (II) fglrx(0): clock: 148.5 MHz   Image Size:  735 x 420 mm
[    20.840] (II) fglrx(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[    20.840] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    20.840] (II) fglrx(0): Supported detailed timing:
[    20.840] (II) fglrx(0): clock: 27.0 MHz   Image Size:  735 x 420 mm
[    20.840] (II) fglrx(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    20.840] (II) fglrx(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    20.840] (II) fglrx(0): Monitor name: CVTE TV
[    20.840] (II) fglrx(0): Ranges: V min: 48 V max: 62 Hz, H min: 14 H max: 70 kHz, PixClock max 155 MHz
[    20.840] (II) fglrx(0): Monitor name: CVTE TV
[    20.840] (II) fglrx(0): Ranges: V min: 48 V max: 62 Hz, H min: 14 H max: 70 kHz, PixClock max 155 MHz
[    20.840] (II) fglrx(0): Number of EDID sections to follow: 1
[    20.840] (II) fglrx(0): EDID (in hex):
[    20.840] (II) fglrx(0):     00ffffffffffff000ed4801033413201
[    20.840] (II) fglrx(0):     20110103804628780aee91a3544c9926
[    20.840] (II) fglrx(0):     0f505400000001010101010101010101
[    20.840] (II) fglrx(0):     010101010101023a80d072382d40102c
[    20.840] (II) fglrx(0):     4580dfa42100001e8c0ad08a20e02d10
[    20.840] (II) fglrx(0):     103e9600dfa421000018000000fc0043
[    20.840] (II) fglrx(0):     5654452054560a2020202020000000fd
[    20.840] (II) fglrx(0):     00303e0e460f000a2020202020200196
[    20.840] (II) fglrx(0): EDID vendor "CVT", prod id 4224
[    20.840] (II) fglrx(0): Using EDID range info for horizontal sync
[    20.840] (II) fglrx(0): Using EDID range info for vertical refresh
[    20.840] (II) fglrx(0): Printing DDC gathered Modelines:
[    20.840] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    20.840] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    20.840] (II) fglrx(0): Printing probed modes for output DFP1
[    20.840] (II) fglrx(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz)
[    20.840] (II) fglrx(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 -hsync -vsync (56.2 kHz)
[    20.841] (II) fglrx(0): Modeline "1920x1080"x30.0   74.25  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (33.8 kHz)
[    20.841] (II) fglrx(0): Modeline "1920x1080"x25.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 -hsync -vsync (28.1 kHz)
[    20.841] (II) fglrx(0): Modeline "1920x1080"x24.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 -hsync -vsync (27.0 kHz)
[    20.841] (II) fglrx(0): Modeline "1776x1000"x60.0  147.05  1776 1880 2072 2368  1000 1001 1004 1035 +hsync -vsync (62.1 kHz)
[    20.841] (II) fglrx(0): Modeline "1776x1000"x50.0  120.18  1776 1872 2056 2336  1000 1001 1004 1029 +hsync -vsync (51.4 kHz)
[    20.841] (II) fglrx(0): Modeline "1776x1000"x30.0   67.92  1776 1824 2000 2224  1000 1001 1004 1018 +hsync -vsync (30.5 kHz)
[    20.841] (II) fglrx(0): Modeline "1776x1000"x25.0   55.21  1776 1800 1976 2176  1000 1001 1004 1015 +hsync -vsync (25.4 kHz)
[    20.841] (II) fglrx(0): Modeline "1776x1000"x24.0   52.56  1776 1792 1968 2160  1000 1001 1004 1014 +hsync -vsync (24.3 kHz)
[    20.841] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync (65.3 kHz)
[    20.841] (II) fglrx(0): Modeline "1680x1050"x50.0  120.20  1680 1776 1952 2224  1050 1051 1054 1081 +hsync -vsync (54.0 kHz)
[    20.841] (II) fglrx(0): Modeline "1680x1050"x24.0   52.34  1680 1704 1864 2048  1050 1051 1054 1065 +hsync -vsync (25.6 kHz)
[    20.841] (II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync -vsync (65.3 kHz)
[    20.841] (II) fglrx(0): Modeline "1400x1050"x50.0   99.88  1400 1480 1624 1848  1050 1051 1054 1081 +hsync -vsync (54.0 kHz)
[    20.841] (II) fglrx(0): Modeline "1400x1050"x24.0   43.96  1400 1424 1560 1720  1050 1051 1054 1065 +hsync -vsync (25.6 kHz)
[    20.841] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 -hsync -vsync (64.0 kHz)
[    20.841] (II) fglrx(0): Modeline "1280x1024"x50.0   89.37  1280 1352 1488 1696  1024 1025 1028 1054 +hsync -vsync (52.7 kHz)
[    20.841] (II) fglrx(0): Modeline "1280x1024"x24.0   39.10  1280 1296 1424 1568  1024 1025 1028 1039 +hsync -vsync (24.9 kHz)
[    20.841] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync (55.9 kHz)
[    20.841] (II) fglrx(0): Modeline "1440x900"x50.0   87.41  1440 1512 1664 1888  900 901 904 926 +hsync -vsync (46.3 kHz)
[    20.841] (II) fglrx(0): Modeline "1440x900"x24.0   37.86  1440 1448 1584 1728  900 901 904 913 +hsync -vsync (21.9 kHz)
[    20.841] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 -hsync -vsync (60.0 kHz)
[    20.841] (II) fglrx(0): Modeline "1280x960"x50.0   82.99  1280 1344 1480 1680  960 961 964 988 +hsync -vsync (49.4 kHz)
[    20.841] (II) fglrx(0): Modeline "1280x960"x24.0   36.28  1280 1288 1416 1552  960 961 964 974 +hsync -vsync (23.4 kHz)
[    20.841] (II) fglrx(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 +hsync -vsync (49.7 kHz)
[    20.841] (II) fglrx(0): Modeline "1280x800"x50.0   68.55  1280 1336 1472 1664  800 801 804 824 +hsync -vsync (41.2 kHz)
[    20.841] (II) fglrx(0): Modeline "1280x800"x24.0   29.30  1280 1272 1392 1504  800 801 804 812 +hsync -vsync (19.5 kHz)
[    20.841] (II) fglrx(0): Modeline "1280x800"x50.0   68.55  1280 1336 1472 1664  800 801 804 824 +hsync -vsync (41.2 kHz)
[    20.841] (II) fglrx(0): Modeline "1280x800"x24.0   29.30  1280 1272 1392 1504  800 801 804 812 +hsync -vsync (19.5 kHz)
[    20.841] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync -vsync (53.7 kHz)
[    20.841] (II) fglrx(0): Modeline "1152x864"x50.0   66.85  1152 1208 1328 1504  864 865 868 889 +hsync -vsync (44.4 kHz)
[    20.841] (II) fglrx(0): Modeline "1152x864"x24.0   28.62  1152 1144 1256 1360  864 865 868 877 +hsync -vsync (21.0 kHz)
[    20.841] (II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
[    20.841] (II) fglrx(0): Modeline "1280x768"x50.0   65.17  1280 1336 1464 1648  768 769 772 791 +hsync -vsync (39.5 kHz)
[    20.841] (II) fglrx(0): Modeline "1280x768"x24.0   27.82  1280 1264 1384 1488  768 769 772 779 +hsync -vsync (18.7 kHz)
[    20.841] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 -hsync -vsync (45.0 kHz)
[    20.841] (II) fglrx(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 -hsync -vsync (37.5 kHz)
[    20.841] (II) fglrx(0): Modeline "1280x720"x24.0   25.82  1280 1256 1376 1472  720 721 724 731 +hsync -vsync (17.5 kHz)
[    20.841] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
[    20.841] (II) fglrx(0): Modeline "1024x768"x50.0   51.89  1024 1064 1168 1312  768 769 772 791 +hsync -vsync (39.6 kHz)
[    20.841] (II) fglrx(0): Modeline "1024x768"x24.0   22.13  1024 1008 1104 1184  768 769 772 779 +hsync -vsync (18.7 kHz)
[    20.841] (II) fglrx(0): Modeline "1152x648"x60.0   59.90  1152 1200 1320 1488  648 649 652 671 +hsync -vsync (40.3 kHz)
[    20.841] (II) fglrx(0): Modeline "1152x648"x50.0   48.55  1152 1184 1304 1456  648 649 652 667 +hsync -vsync (33.3 kHz)
[    20.841] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 -hsync -vsync (37.9 kHz)
[    20.841] (II) fglrx(0): Modeline "800x600"x50.0   31.14  800 824 904 1008  600 601 604 618 +hsync -vsync (30.9 kHz)
[    20.841] (II) fglrx(0): Modeline "800x600"x24.0   12.86  800 768 840 880  600 601 604 609 +hsync -vsync (14.6 kHz)
[    20.841] (II) fglrx(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 +hsync +vsync (31.2 kHz)
[    20.841] (II) fglrx(0): Modeline "720x480"x60.0   27.00  720 736 798 858  480 489 495 525 +hsync +vsync (31.5 kHz)
[    20.841] (II) fglrx(0): Modeline "720x480"x50.0   21.78  720 728 800 880  480 481 484 495 +hsync -vsync (24.8 kHz)
[    20.841] (II) fglrx(0): Modeline "720x480"x24.0    8.78  720 672 736 752  480 481 484 487 +hsync -vsync (11.7 kHz)
[    20.841] (II) fglrx(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
[    20.841] (II) fglrx(0): Modeline "640x480"x50.0   19.40  640 648 712 784  480 481 484 495 +hsync -vsync (24.7 kHz)
[    20.841] (II) fglrx(0): Modeline "640x480"x24.0    7.85  640 600 656 672  480 481 484 487 +hsync -vsync (11.7 kHz)
[    20.841] (II) fglrx(0): EDID for output CRT1
[    20.841] (II) fglrx(0): Output DFP1 connected
[    20.841] (II) fglrx(0): Output CRT1 disconnected
[    20.841] (II) fglrx(0): Using exact sizes for initial modes
[    20.841] (II) fglrx(0): Output DFP1 using initial mode 1920x1080
[    20.841] (II) fglrx(0): Display dimensions: (700, 400) mm
[    20.841] (II) fglrx(0): DPI set to (69, 69)
[    20.841] (II) fglrx(0): Adapter ATI Radeon 3000 Graphics has 2 configurable heads and 1 displays connected.
[    20.841] (==) fglrx(0):  PseudoColor visuals disabled
[    20.841] (II) Loading sub module "ramdac"
[    20.841] (II) LoadModule: "ramdac"
[    20.841] (II) Module "ramdac" already built-in
[    20.841] (==) fglrx(0): NoDRI = NO
[    20.841] (==) fglrx(0): Capabilities: 0x00000000
[    20.841] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    20.841] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    20.841] (==) fglrx(0): UseFastTLS=0
[    20.841] (==) fglrx(0): BlockSignalsOnLock=1
[    20.841] (II) fglrx(0): Desktop Vsync is enabled.
[    20.841] (--) Depth 24 pixmap format is 32 bpp
[    20.842] (II) Loading extension ATIFGLRXDRI
[    20.841] (--) Depth 24 pixmap format is 32 bpp
[    20.842] (II) Loading extension ATIFGLRXDRI
[    20.842] (II) fglrx(0): doing swlDriScreenInit
[    20.842] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    20.842] ukiDynamicMajor: found major device number 249
[    20.842] ukiDynamicMajor: found major device number 249
[    20.842] ukiDynamicMajor: found major device number 249
[    20.842] ukiOpenByBusid: Searching for BusID PCI:1:5:0
[    20.842] ukiOpenDevice: node name is /dev/ati/card0
[    20.842] ukiOpenDevice: open result is 17, (OK)
[    20.842] ukiOpenByBusid: ukiOpenMinor returns 17
[    20.842] ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
[    20.842] (II) fglrx(0): [uki] DRM interface version 1.0
[    20.842] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:5:0"
[    20.842] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    20.842] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f77ad950000
[    20.842] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    20.842] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    20.842] (II) fglrx(0): swlDriScreenInit done
[    20.842] (II) fglrx(0): Kernel Module Version Information:
[    20.842] (II) fglrx(0):     Name: fglrx
[    20.842] (II) fglrx(0):     Version: 8.96.4
[    20.842] (II) fglrx(0):     Date: Mar 12 2012
[    20.842] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    20.842] (II) fglrx(0): Kernel Module version matches driver.
[    20.842] (II) fglrx(0): Kernel Module Build Time Information:
[    20.842] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.2.0-35-generic
[    20.842] (II) fglrx(0):     Build-Kernel MODVERSIONS:        no
[    20.842] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    20.842] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    20.842] (II) fglrx(0): [uki] register handle = 0x00004000
[    20.857] (II) fglrx(0): DRI initialization successfull
[    20.857] (II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x0100e000
[    20.857] (==) fglrx(0): Backing store disabled
[    20.857] (II) Loading extension FGLRXEXTENSION
[    20.857] (**) fglrx(0): DPMS enabled
[    20.858] (II) fglrx(0): Initialized in-driver Xinerama extension
[    20.858] (**) fglrx(0): Textured Video is enabled.
[    20.858] (II) LoadModule: "glesx"
[    20.858] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/glesx.so
[    20.858] (II) Module glesx: vendor="X.Org Foundation"
[    20.858]    compiled for 1.4.99.906, module version = 1.0.0
[    20.858] (II) Loading extension GLESX
[    20.858] (II) fglrx(0): GLESX enableFlags = 528
[    20.858] (II) fglrx(0): GLESX is enabled
[    20.858] (II) LoadModule: "amdxmm"
[    20.859] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/amdxmm.so
[    20.858] (II) LoadModule: "amdxmm"
[    20.859] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/amdxmm.so
[    20.859] (II) Module amdxmm: vendor="X.Org Foundation"
[    20.859]    compiled for 1.4.99.906, module version = 2.0.0
[    20.859] (II) Loading extension AMDXVOPL
[    20.859] (II) Loading extension AMDXVBA
[    20.860] (II) fglrx(0): UVD feature is enabled(II) fglrx(0):
[    20.862] (II) fglrx(0): Enable composite support successfully
[    20.862] (WW) fglrx(0): Option "VendorName" is not used
[    20.862] (WW) fglrx(0): Option "ModelName" is not used
[    20.862] (II) fglrx(0): X context handle = 0x1
[    20.862] (II) fglrx(0): [DRI] installation complete
[    20.863] (==) fglrx(0): Silken mouse enabled
[    20.863] (==) fglrx(0): Using HW cursor of display infrastructure!
[    20.863] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    20.956] (--) RandR disabled
[    20.956] (II) Initializing built-in extension Generic Event Extension
[    20.956] (II) Initializing built-in extension SHAPE
[    20.956] (II) Initializing built-in extension MIT-SHM
[    20.956] (II) Initializing built-in extension XInputExtension
[    20.956] (II) Initializing built-in extension XTEST
[    20.956] (II) Initializing built-in extension BIG-REQUESTS
[    20.956] (II) Initializing built-in extension SYNC
[    20.956] (II) Initializing built-in extension XKEYBOARD
[    20.956] (II) Initializing built-in extension XC-MISC
[    20.956] (II) Initializing built-in extension SECURITY
[    20.956] (II) Initializing built-in extension XINERAMA
[    20.956] (II) Initializing built-in extension XFIXES
[    20.956] (II) Initializing built-in extension RENDER
[    20.956] (II) Initializing built-in extension RANDR
[    20.956] (II) Initializing built-in extension COMPOSITE
[    20.956] (II) Initializing built-in extension DAMAGE
[    21.085] ukiDynamicMajor: found major device number 249
[    21.086] ukiDynamicMajor: found major device number 249
[    21.086] ukiOpenByBusid: Searching for BusID PCI:1:5:0
[    21.086] ukiOpenDevice: node name is /dev/ati/card0
[    21.087] ukiOpenDevice: open result is 19, (OK)
[    21.087] ukiOpenByBusid: ukiOpenMinor returns 19
[    21.087] ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
[    21.162] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    21.162] (II) fglrx(0): Enable the clock gating!
[    21.206] (II) fglrx(0): Desktop Vsync is enabled.
[    21.206] (II) fglrx(0): Setting screen physical size to 508 x 285
[    21.212] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    21.214] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    21.215] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.215] (II) LoadModule: "evdev"
[    21.215] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.215] (II) LoadModule: "evdev"
[    21.227] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.227] (II) Module evdev: vendor="X.Org Foundation"
[    21.228]    compiled for 1.11.3, module version = 2.7.0
[    21.228]    Module class: X.Org XInput Driver
[    21.228]    ABI class: X.Org XInput driver, version 16.0
[    21.228] (II) Using input driver 'evdev' for 'Power Button'
[    21.228] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.228] (**) Power Button: always reports core events
[    21.228] (**) evdev: Power Button: Device: "/dev/input/event1"
[    21.228] (--) evdev: Power Button: Vendor 0 Product 0x1
[    21.228] (--) evdev: Power Button: Found keys
[    21.228] (II) evdev: Power Button: Configuring as keyboard
[    21.228] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    21.228] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    21.228] (**) Option "xkb_rules" "evdev"
[    21.228] (**) Option "xkb_model" "pc105"
[    21.228] (**) Option "xkb_layout" "gb"
[    21.229] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    21.230] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    21.230] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.230] (II) Using input driver 'evdev' for 'Power Button'
[    21.230] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.230] (**) Power Button: always reports core events
[    21.230] (**) evdev: Power Button: Device: "/dev/input/event0"
[    21.230] (--) evdev: Power Button: Vendor 0 Product 0x1
[    21.230] (--) evdev: Power Button: Found keys
[    21.230] (II) evdev: Power Button: Configuring as keyboard
[    21.230] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    21.230] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    21.230] (**) Option "xkb_rules" "evdev"
[    21.230] (**) Option "xkb_model" "pc105"
[    21.230] (**) Option "xkb_layout" "gb"
[    21.230] (II) config/udev: Adding input device saa716x IR (TurboSight TBS 6280) (/dev/input/event4)
[    21.230] (**) saa716x IR (TurboSight TBS 6280): Applying InputClass "evdev keyboard catchall"
[    21.230] (II) Using input driver 'evdev' for 'saa716x IR (TurboSight TBS 6280)'
[    21.230] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.230] (**) saa716x IR (TurboSight TBS 6280): always reports core events
[    21.230] (**) evdev: saa716x IR (TurboSight TBS 6280): Device: "/dev/input/event4"
[    21.230] (--) evdev: saa716x IR (TurboSight TBS 6280): Vendor 0x6280 Product 0x11
[    21.230] (--) evdev: saa716x IR (TurboSight TBS 6280): Found keys
[    21.230] (II) evdev: saa716x IR (TurboSight TBS 6280): Configuring as keyboard
[    21.230] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/rc/rc0/input4/event4"
[    21.230] (II) XINPUT: Adding extended input device "saa716x IR (TurboSight TBS 6280)" (type: KEYBOARD, id 8)
[    21.230] (**) Option "xkb_rules" "evdev"
[    21.230] (**) Option "xkb_model" "pc105"
[    21.230] (**) Option "xkb_rules" "evdev"
[    21.230] (**) Option "xkb_model" "pc105"
[    21.230] (**) Option "xkb_layout" "gb"
[    21.231] (II) config/udev: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1 (/dev/input/event2)
[    21.231] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: Applying InputClass "evdev keyboard catchall"
[    21.231] (II) Using input driver 'evdev' for 'Microsft Microsoft Wireless Desktop Receiver 3.1'
[    21.231] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.231] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: always reports core events
[    21.231] (**) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Device: "/dev/input/event2"
[    21.231] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Vendor 0x45e Product 0xf9
[    21.231] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Found keys
[    21.231] (II) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as keyboard
[    21.231] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input2/event2"
[    21.231] (II) XINPUT: Adding extended input device "Microsft Microsoft Wireless Desktop Receiver 3.1" (type: KEYBOARD, id 9)
[    21.231] (**) Option "xkb_rules" "evdev"
[    21.231] (**) Option "xkb_model" "pc105"
[    21.231] (**) Option "xkb_layout" "gb"
[    21.231] (II) config/udev: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1 (/dev/input/event3)
[    21.231] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: Applying InputClass "evdev pointer catchall"
[    21.231] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: Applying InputClass "evdev keyboard catchall"
[    21.231] (II) Using input driver 'evdev' for 'Microsft Microsoft Wireless Desktop Receiver 3.1'
[    21.231] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.231] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: always reports core events
[    21.231] (**) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Device: "/dev/input/event3"
[    21.231] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Vendor 0x45e Product 0xf9
[    21.232] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Found 9 mouse buttons
[    21.232] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Found scroll wheel(s)
[    21.232] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Found relative axes
[    21.232] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Found x and y relative axes
[    21.232] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Found absolute axes
[    21.232] (II) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Forcing absolute x/y axes to exist.
[    21.232] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Found keys
[    21.232] (II) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as mouse
[    21.232] (II) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as keyboard
[    21.232] (II) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Adding scrollwheel support
[    21.232] (**) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: YAxisMapping: buttons 4 and 5
[    21.232] (**) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.232] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.1/input/input3/event3"
[    21.232] (II) XINPUT: Adding extended input device "Microsft Microsoft Wireless Desktop Receiver 3.1" (type: KEYBOARD, id 10)
[    21.232] (**) Option "xkb_rules" "evdev"
[    21.232] (**) Option "xkb_model" "pc105"
[    21.232] (**) Option "xkb_layout" "gb"
[    21.232] (II) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: initialized for relative axes.
[    21.232] (WW) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: ignoring absolute axes.
[    21.232] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) keeping acceleration scheme 1
[    21.232] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) acceleration profile 0
[    21.232] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) acceleration factor: 2.000
[    21.232] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) acceleration profile 0
[    21.232] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) acceleration factor: 2.000
[    21.232] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) acceleration threshold: 4
[    21.232] (II) config/udev: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1 (/dev/input/mouse0)
[    21.232] (II) No input driver specified, ignoring this device.
[    21.232] (II) This device may have been added with another device file.
[    21.232] (II) config/udev: Adding input device pac207 (/dev/input/event6)
[    21.232] (**) pac207: Applying InputClass "evdev keyboard catchall"
[    21.232] (II) Using input driver 'evdev' for 'pac207'
[    21.232] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.233] (**) pac207: always reports core events
[    21.233] (**) evdev: pac207: Device: "/dev/input/event6"
[    21.233] (--) evdev: pac207: Vendor 0x93a Product 0x2468
[    21.233] (--) evdev: pac207: Found keys
[    21.233] (II) evdev: pac207: Configuring as keyboard
[    21.233] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.1/usb4/4-1/input/input6/event6"
[    21.233] (II) XINPUT: Adding extended input device "pac207" (type: KEYBOARD, id 11)
[    21.233] (**) Option "xkb_rules" "evdev"
[    21.233] (**) Option "xkb_model" "pc105"
[    21.233] (**) Option "xkb_layout" "gb"
[    21.233] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event10)
[    21.233] (II) No input driver specified, ignoring this device.
[    21.233] (II) This device may have been added with another device file.
[    21.233] (II) config/udev: Adding input device HDA ATI SB Line-Out (/dev/input/event11)
[    21.233] (II) No input driver specified, ignoring this device.
[    21.233] (II) This device may have been added with another device file.
[    21.233] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event7)
[    21.233] (II) No input driver specified, ignoring this device.
[    21.233] (II) This device may have been added with another device file.
[    21.234] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event8)
[    21.234] (II) No input driver specified, ignoring this device.
[    21.234] (II) This device may have been added with another device file.
[    21.234] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event9)
[    21.234] (II) No input driver specified, ignoring this device.
[    21.234] (II) This device may have been added with another device file.
[    21.235] (II) config/udev: Adding input device MCE IR Keyboard/Mouse (saa716x) (/dev/input/event5)
[    21.235] (**) MCE IR Keyboard/Mouse (saa716x): Applying InputClass "evdev pointer catchall"
[    21.235] (**) MCE IR Keyboard/Mouse (saa716x): Applying InputClass "evdev keyboard catchall"
[    21.235] (II) Using input driver 'evdev' for 'MCE IR Keyboard/Mouse (saa716x)'
[    21.235] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.235] (**) MCE IR Keyboard/Mouse (saa716x): always reports core events
[    21.235] (**) evdev: MCE IR Keyboard/Mouse (saa716x): Device: "/dev/input/event5"
[    21.235] (--) evdev: MCE IR Keyboard/Mouse (saa716x): Vendor 0 Product 0
[    21.235] (--) evdev: MCE IR Keyboard/Mouse (saa716x): Found 3 mouse buttons
[    21.235] (--) evdev: MCE IR Keyboard/Mouse (saa716x): Found relative axes
[    21.235] (--) evdev: MCE IR Keyboard/Mouse (saa716x): Found x and y relative axes
[    21.235] (--) evdev: MCE IR Keyboard/Mouse (saa716x): Found keys
[    21.235] (--) evdev: MCE IR Keyboard/Mouse (saa716x): Found x and y relative axes
[    21.235] (--) evdev: MCE IR Keyboard/Mouse (saa716x): Found keys
[    21.235] (II) evdev: MCE IR Keyboard/Mouse (saa716x): Configuring as mouse
[    21.235] (II) evdev: MCE IR Keyboard/Mouse (saa716x): Configuring as keyboard
[    21.235] (**) evdev: MCE IR Keyboard/Mouse (saa716x): YAxisMapping: buttons 4 and 5
[    21.235] (**) evdev: MCE IR Keyboard/Mouse (saa716x): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.235] (**) Option "config_info" "udev:/sys/devices/virtual/input/input5/event5"
[    21.235] (II) XINPUT: Adding extended input device "MCE IR Keyboard/Mouse (saa716x)" (type: KEYBOARD, id 12)
[    21.235] (**) Option "xkb_rules" "evdev"
[    21.235] (**) Option "xkb_model" "pc105"
[    21.235] (**) Option "xkb_layout" "gb"
[    21.235] (II) evdev: MCE IR Keyboard/Mouse (saa716x): initialized for relative axes.
[    21.235] (**) MCE IR Keyboard/Mouse (saa716x): (accel) keeping acceleration scheme 1
[    21.235] (**) MCE IR Keyboard/Mouse (saa716x): (accel) acceleration profile 0
[    21.235] (**) MCE IR Keyboard/Mouse (saa716x): (accel) acceleration factor: 2.000
[    21.235] (**) MCE IR Keyboard/Mouse (saa716x): (accel) acceleration threshold: 4
[    21.236] (II) config/udev: Adding input device MCE IR Keyboard/Mouse (saa716x) (/dev/input/mouse1)
[    21.236] (II) No input driver specified, ignoring this device.
[    21.236] (II) This device may have been added with another device file.
[    21.263] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    22.058] (II) fglrx(0): EDID vendor "CVT", prod id 4224
[    22.058] (II) fglrx(0): Using hsync ranges from config file
[    22.058] (II) fglrx(0): Using vrefresh ranges from config file
[    22.058] (II) fglrx(0): Printing DDC gathered Modelines:
[    22.058] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    22.058] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    22.181] (II) fglrx(0): EDID vendor "CVT", prod id 4224
[    22.181] (II) fglrx(0): Using hsync ranges from config file
[    22.181] (II) fglrx(0): Using vrefresh ranges from config file
[    22.181] (II) fglrx(0): Printing DDC gathered Modelines:
[    22.181] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    22.181] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    22.278] (II) fglrx(0): EDID vendor "CVT", prod id 4224
[    22.279] (II) fglrx(0): Using hsync ranges from config file
[    22.279] (II) fglrx(0): Using vrefresh ranges from config file
[    22.279] (II) fglrx(0): Printing DDC gathered Modelines:
[    22.279] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    22.279] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    22.711] (II) fglrx(0): EDID vendor "CVT", prod id 4224
[    22.711] (II) fglrx(0): Using hsync ranges from config file
[    22.711] (II) fglrx(0): Using vrefresh ranges from config file
[    22.711] (II) fglrx(0): Printing DDC gathered Modelines:
[    22.711] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    22.711] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    22.810] (II) fglrx(0): EDID vendor "CVT", prod id 4224
[    22.810] (II) fglrx(0): Using hsync ranges from config file
[    22.810] (II) fglrx(0): Using vrefresh ranges from config file
[    22.810] (II) fglrx(0): Using hsync ranges from config file
[    22.810] (II) fglrx(0): Using vrefresh ranges from config file
[    22.810] (II) fglrx(0): Printing DDC gathered Modelines:
[    22.810] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    22.810] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    23.128] (II) fglrx(0): EDID vendor "CVT", prod id 4224
[    23.128] (II) fglrx(0): Using hsync ranges from config file
[    23.128] (II) fglrx(0): Using vrefresh ranges from config file
[    23.128] (II) fglrx(0): Printing DDC gathered Modelines:
[    23.128] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    23.128] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    23.618] (II) fglrx(0): EDID vendor "CVT", prod id 4224
[    23.618] (II) fglrx(0): Using hsync ranges from config file
[    23.618] (II) fglrx(0): Using vrefresh ranges from config file
[    23.618] (II) fglrx(0): Printing DDC gathered Modelines:
[    23.618] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    23.618] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    23.724] (II) fglrx(0): EDID vendor "CVT", prod id 4224
[    23.724] (II) fglrx(0): Using hsync ranges from config file
[    23.724] (II) fglrx(0): Using vrefresh ranges from config file
[    23.724] (II) fglrx(0): Printing DDC gathered Modelines:
[    23.724] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    23.724] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    65.717] (II) fglrx(0): EDID vendor "CVT", prod id 4224
[    65.717] (II) fglrx(0): Using hsync ranges from config file
[    65.717] (II) fglrx(0): Using vrefresh ranges from config file
[    65.717] (II) fglrx(0): Printing DDC gathered Modelines:
[    65.717] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    65.717] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    65.814] (II) fglrx(0): EDID vendor "CVT", prod id 4224
[    65.814] (II) fglrx(0): Using hsync ranges from config file
[    65.814] (II) fglrx(0): Using vrefresh ranges from config file
[    65.814] (II) fglrx(0): Printing DDC gathered Modelines:
[    65.814] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    65.814] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    71.657] (II) fglrx(0): EDID vendor "CVT", prod id 4224
[    71.657] (II) fglrx(0): Using hsync ranges from config file
[    71.657] (II) fglrx(0): Using vrefresh ranges from config file
[    71.657] (II) fglrx(0): Printing DDC gathered Modelines:
[    71.657] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    71.657] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    71.754] (II) fglrx(0): EDID vendor "CVT", prod id 4224
[    71.754] (II) fglrx(0): Using hsync ranges from config file
[    71.754] (II) fglrx(0): Using vrefresh ranges from config file
[    71.754] (II) fglrx(0): Printing DDC gathered Modelines:
[    71.754] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    71.754] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    71.754] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    71.754] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)

```

---

### Post by tgalati4 on 2013-01-25
I presume that you checked the BIOS for a switch to use PCI video for primary?

I know the open source radeon driver has some switches to force video:

[https://wiki.archlinux.org/index.php/ATI#Dual_Head_Setup](https://wiki.archlinux.org/index.php/ATI#Dual_Head_Setup)

Perhaps there are similar switches in the proprietary driver?

---

