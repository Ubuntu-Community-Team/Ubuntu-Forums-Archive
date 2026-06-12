---
title: "Sloppy graphics with fglrx installed"
date: 2013-01-26
forum: Multimedia Software
---

### Post by Lukfi on 2013-01-26
Hi,
I have a setup with a Radeon HD 3450 graphics card. The OS is Ubuntu 12.04.
On default, the graphics driver was reported as Gallium 0.4. I wanted to install AMD drivers. I followed this tutorial [http://www.upubuntu.com/2012/06/install-amd-ati-catalyst-126-display.html](http://www.upubuntu.com/2012/06/install-amd-ati-catalyst-126-display.html) to no avail, there were errors during the installation and aticonfig would not run. I finally "succeeded" by using
```
sudo apt-get install fglrx
```In system settings, the graphics card is now reported as VESA RV620. fglrx appears in lsmod. But the system is extremely sloppy, maybe worse than it was originally.

This is my auto generated xorg.conf
```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
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

```And this is my Xorg.0.log (no errors, apparently)
```
[    23.467] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    23.467] X Protocol Version 11, Revision 0
[    23.467] Build Operating System: Linux 2.6.42-26-generic i686 Ubuntu
[    23.467] Current Operating System: Linux ubuntu 3.2.0-36-generic-pae #57-Ubuntu SMP Tue Jan 8 22:01:06 UTC 2013 i686
[    23.467] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-36-generic-pae root=UUID=eb5aa52d-f997-4b3e-99e4-2ae98a5d59cd ro quiet splash vt.handoff=7
[    23.467] Build Date: 29 August 2012  12:10:05AM
[    23.467] xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see http://www.ubuntu.com/support) 
[    23.467] Current version of pixman: 0.24.4
[    23.467]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    23.467] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    23.468] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan 26 14:20:33 2013
[    23.523] (==) Using config file: "/etc/X11/xorg.conf"
[    23.523] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    23.598] (==) ServerLayout "aticonfig Layout"
[    23.598] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    23.599] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    23.613] (**) |   |-->Device "aticonfig-Device[0]-0"
[    23.613] (==) Automatically adding devices
[    23.613] (==) Automatically enabling devices
[    23.644] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    23.644]     Entry deleted from font path.
[    23.644] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    23.644]     Entry deleted from font path.
[    23.644] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    23.644]     Entry deleted from font path.
[    23.644] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    23.644]     Entry deleted from font path.
[    23.644] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    23.644]     Entry deleted from font path.
[    23.644] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    23.644]     Entry deleted from font path.
[    23.644] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    23.644] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    23.644] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    23.664] (II) Loader magic: 0xabc5a0
[    23.664] (II) Module ABI versions:
[    23.664]     X.Org ANSI C Emulation: 0.4
[    23.664]     X.Org Video Driver: 11.0
[    23.664]     X.Org XInput driver : 16.0
[    23.664]     X.Org Server Extension : 6.0
[    23.666] (--) PCI:*(0:1:0:0) 1002:95c6:1043:0028 rev 0, Mem @ 0xe0000000/268435456, 0xf9000000/65536, I/O @ 0x0000a000/256, BIOS @ 0x????????/131072
[    23.667] (II) Open ACPI successful (/var/run/acpid.socket)
[    23.667] (II) "extmod" will be loaded by default.
[    23.667] (II) "dbe" will be loaded by default.
[    23.667] (II) "glx" will be loaded by default.
[    23.667] (II) "record" will be loaded by default.
[    23.667] (II) "dri" will be loaded by default.
[    23.667] (II) "dri2" will be loaded by default.
[    23.667] (II) LoadModule: "extmod"
[    23.945] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    23.963] (II) Module extmod: vendor="X.Org Foundation"
[    23.963]     compiled for 1.11.3, module version = 1.0.0
[    23.963]     Module class: X.Org Server Extension
[    23.963]     ABI class: X.Org Server Extension, version 6.0
[    23.964] (II) Loading extension MIT-SCREEN-SAVER
[    23.964] (II) Loading extension XFree86-VidModeExtension
[    23.964] (II) Loading extension XFree86-DGA
[    23.964] (II) Loading extension DPMS
[    23.964] (II) Loading extension XVideo
[    23.964] (II) Loading extension XVideo-MotionCompensation
[    23.964] (II) Loading extension X-Resource
[    23.964] (II) LoadModule: "dbe"
[    23.965] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    23.975] (II) Module dbe: vendor="X.Org Foundation"
[    23.975]     compiled for 1.11.3, module version = 1.0.0
[    23.975]     Module class: X.Org Server Extension
[    23.975]     ABI class: X.Org Server Extension, version 6.0
[    23.975] (II) Loading extension DOUBLE-BUFFER
[    23.975] (II) LoadModule: "glx"
[    23.976] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[    24.008] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    24.008]     compiled for 6.9.0, module version = 1.0.0
[    24.009] (II) Loading extension GLX
[    24.009] (II) LoadModule: "record"
[    24.010] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    24.033] (II) Module record: vendor="X.Org Foundation"
[    24.033]     compiled for 1.11.3, module version = 1.13.0
[    24.033]     Module class: X.Org Server Extension
[    24.033]     ABI class: X.Org Server Extension, version 6.0
[    24.033] (II) Loading extension RECORD
[    24.033] (II) LoadModule: "dri"
[    24.034] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    24.036] (II) Module dri: vendor="X.Org Foundation"
[    24.036]     compiled for 1.11.3, module version = 1.0.0
[    24.036]     ABI class: X.Org Server Extension, version 6.0
[    24.036] (II) Loading extension XFree86-DRI
[    24.036] (II) LoadModule: "dri2"
[    24.036] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    24.037] (II) Module dri2: vendor="X.Org Foundation"
[    24.038]     compiled for 1.11.3, module version = 1.2.0
[    24.038]     ABI class: X.Org Server Extension, version 6.0
[    24.038] (II) Loading extension DRI2
[    24.038] (II) LoadModule: "fglrx"
[    24.038] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    24.419] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    24.419]     compiled for 1.4.99.906, module version = 8.96.4
[    24.419]     Module class: X.Org Video Driver
[    24.421] (II) Loading sub module "fglrxdrm"
[    24.421] (II) LoadModule: "fglrxdrm"
[    24.422] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    24.450] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    24.450]     compiled for 1.4.99.906, module version = 8.96.4
[    24.466] (II) ATI Proprietary Linux Driver Version Identifier:8.96.4
[    24.466] (II) ATI Proprietary Linux Driver Release Identifier: 8.96.7                               
[    24.466] (II) ATI Proprietary Linux Driver Build Date: Mar 12 2012 13:06:47
[    24.466] (++) using VT number 7

[    24.466] (WW) Falling back to old probe method for fglrx
[    24.584] (II) PCS database file /etc/ati/amdpcsdb not found
[    24.584] (II)   Creating PCS database from initial defaults instead
[    24.623] (--) Chipset Supported AMD Graphics Processor (0x95C6) found
[    24.623] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    24.624] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    24.625] (II) AMD Video driver is signed
[    24.625] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    24.625] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    24.625] (II) fglrx(0): pEnt->device->identifier=0x21c3e088
[    24.625] (II) fglrx(0): === [xdl_xs111_atiddxPreInit] === begin
[    24.626] (II) Loading sub module "vgahw"
[    24.626] (II) LoadModule: "vgahw"
[    24.627] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    24.643] (II) Module vgahw: vendor="X.Org Foundation"
[    24.643]     compiled for 1.11.3, module version = 0.1.0
[    24.643]     ABI class: X.Org Video Driver, version 11.0
[    24.643] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    24.643] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    24.643] (==) fglrx(0): Default visual is TrueColor
[    24.643] (**) fglrx(0): Option "DPMS" "true"
[    24.643] (==) fglrx(0): RGB weight 888
[    24.643] (II) fglrx(0): Using 8 bits per RGB 
[    24.644] (==) fglrx(0): Buffer Tiling is ON
[    24.650] (II) Loading sub module "fglrxdrm"
[    24.650] (II) LoadModule: "fglrxdrm"
[    24.651] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    24.651] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    24.651]     compiled for 1.4.99.906, module version = 8.96.4
[    24.659] ukiDynamicMajor: found major device number 250
[    24.660] ukiDynamicMajor: found major device number 250
[    24.660] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    24.660] ukiOpenDevice: node name is /dev/ati/card0
[    24.661] ukiOpenDevice: open result is 12, (OK)
[    24.661] ukiOpenByBusid: ukiOpenMinor returns 12
[    24.662] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    24.663] (**) fglrx(0): NoAccel = NO
[    24.664] (**) fglrx(0): ATI 2D Acceleration Architecture enabled
[    24.664] (--) fglrx(0): Chipset: "ATI Radeon HD 3450 " (Chipset = 0x95c6)
[    24.665] (--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x0028)
[    24.665] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    24.665] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[    24.665] (--) fglrx(0): MMIO registers at 0xf9000000
[    24.665] (--) fglrx(0): I/O port at 0x0000a000
[    24.665] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    24.678] (II) fglrx(0): AC Adapter is used
[    24.735] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    24.745] (II) Loading sub module "vbe"
[    24.745] (II) LoadModule: "vbe"
[    24.746] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    24.754] (II) Module vbe: vendor="X.Org Foundation"
[    24.754]     compiled for 1.11.3, module version = 1.1.0
[    24.754]     ABI class: X.Org Video Driver, version 11.0
[    24.755] (II) fglrx(0): VESA BIOS detected
[    24.755] (II) fglrx(0): VESA VBE Version 3.0
[    24.755] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    24.755] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    24.755] (II) fglrx(0): VESA VBE OEM Software Rev: 10.88
[    24.755] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    24.755] (II) fglrx(0): VESA VBE OEM Product: RV620
[    24.755] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    24.805] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    24.805] (--) fglrx(0): Video RAM: 262144 kByte, Type: DDR2
[    24.805] (II) fglrx(0): AGP card detected
[    24.806] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    24.844] (II) fglrx(0): Using adapter: 1:0.0.
[    24.903] (II) fglrx(0): [FB] MC range(MCFBBase = 0xe0000000, MCFBSize = 0x10000000)
[    24.903] (II) fglrx(0): [pci] find AGP GART
[    24.903] (II) fglrx(0): [agp] AGP protocol is enabled for graphics board.(cmd=0x1f004312)
[    24.903] (II) fglrx(0): [agp] graphics chipset has AGP v3.0 (native mode)
[    25.083] (II) fglrx(0): Interrupt handler installed at IRQ 16.
[    25.085] (II) fglrx(0): RandR 1.2 support is enabled!
[    25.085] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    25.085] (==) fglrx(0): Center Mode is disabled 
[    25.085] (II) Loading sub module "fb"
[    25.085] (II) LoadModule: "fb"
[    25.086] (II) Loading /usr/lib/xorg/modules/libfb.so
[    25.112] (II) Module fb: vendor="X.Org Foundation"
[    25.112]     compiled for 1.11.3, module version = 1.0.0
[    25.112]     ABI class: X.Org ANSI C Emulation, version 0.4
[    25.112] (II) Loading sub module "ddc"
[    25.112] (II) LoadModule: "ddc"
[    25.112] (II) Module "ddc" already built-in
[    26.638] (II) fglrx(0): Finished Initialize PPLIB!
[    26.948] (II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
[    26.948] (II) fglrx(0): Output CRT1 has no monitor section
[    26.948] (II) fglrx(0): Output CRT2 has no monitor section
[    26.948] (II) fglrx(0): Output TV has no monitor section
[    26.948] (II) fglrx(0): Output CV has no monitor section
[    26.948] (II) Loading sub module "ddc"
[    26.949] (II) LoadModule: "ddc"
[    26.949] (II) Module "ddc" already built-in
[    26.949] (II) fglrx(0): Connected Display0: DFP1
[    26.949] (II) fglrx(0): Display0 EDID data ---------------------------
[    26.949] (II) fglrx(0): Manufacturer: SAM  Model: 304  Serial#: 1346712114
[    26.949] (II) fglrx(0): Year: 2008  Week: 7
[    26.949] (II) fglrx(0): EDID Version: 1.3
[    26.949] (II) fglrx(0): Digital Display Input
[    26.949] (II) fglrx(0): Max Image Size [cm]: horiz.: 49  vert.: 32
[    26.949] (II) fglrx(0): Gamma: 2.20
[    26.949] (II) fglrx(0): DPMS capabilities: Off
[    26.949] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    26.949] (II) fglrx(0): First detailed timing is preferred mode
[    26.949] (II) fglrx(0): redX: 0.639 redY: 0.333   greenX: 0.289 greenY: 0.597
[    26.949] (II) fglrx(0): blueX: 0.153 blueY: 0.082   whiteX: 0.313 whiteY: 0.329
[    26.949] (II) fglrx(0): Supported established timings:
[    26.949] (II) fglrx(0): 720x400@70Hz
[    26.949] (II) fglrx(0): 640x480@60Hz
[    26.949] (II) fglrx(0): 640x480@67Hz
[    26.949] (II) fglrx(0): 640x480@72Hz
[    26.949] (II) fglrx(0): 640x480@75Hz
[    26.949] (II) fglrx(0): 800x600@56Hz
[    26.949] (II) fglrx(0): 800x600@60Hz
[    26.949] (II) fglrx(0): 800x600@72Hz
[    26.949] (II) fglrx(0): 800x600@75Hz
[    26.949] (II) fglrx(0): 832x624@75Hz
[    26.949] (II) fglrx(0): 1024x768@60Hz
[    26.949] (II) fglrx(0): 1024x768@70Hz
[    26.949] (II) fglrx(0): 1024x768@75Hz
[    26.949] (II) fglrx(0): 1280x1024@75Hz
[    26.949] (II) fglrx(0): 1152x864@75Hz
[    26.949] (II) fglrx(0): Manufacturer's mask: 0
[    26.949] (II) fglrx(0): Supported standard timings:
[    26.949] (II) fglrx(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    26.949] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    26.949] (II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    26.949] (II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    26.950] (II) fglrx(0): Supported detailed timing:
[    26.950] (II) fglrx(0): clock: 119.0 MHz   Image Size:  494 x 320 mm
[    26.950] (II) fglrx(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[    26.950] (II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[    26.950] (II) fglrx(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 145 MHz
[    26.950] (II) fglrx(0): Monitor name: SyncMaster
[    26.950] (II) fglrx(0): Serial No: H9XQ205128
[    26.950] (II) fglrx(0): EDID (in hex):
[    26.950] (II) fglrx(0):     00ffffffffffff004c2d040332324550
[    26.950] (II) fglrx(0):     07120103803120782a9345a3554a9827
[    26.950] (II) fglrx(0):     155054bfef80b30081808140714f0101
[    26.950] (II) fglrx(0):     0101010101017c2e90a0601a1e403020
[    26.950] (II) fglrx(0):     3600ee401100001a000000fd00384b1e
[    26.950] (II) fglrx(0):     510e000a202020202020000000fc0053
[    26.950] (II) fglrx(0):     796e634d61737465720a2020000000ff
[    26.950] (II) fglrx(0):     00483958513230353132380a202000b4
[    26.950] (II) fglrx(0): End of Display0 EDID data --------------------
[    27.370] (II) fglrx(0): EDID for output DFP1
[    27.370] (II) fglrx(0): Manufacturer: SAM  Model: 304  Serial#: 1346712114
[    27.370] (II) fglrx(0): Year: 2008  Week: 7
[    27.370] (II) fglrx(0): EDID Version: 1.3
[    27.371] (II) fglrx(0): Digital Display Input
[    27.371] (II) fglrx(0): Max Image Size [cm]: horiz.: 49  vert.: 32
[    27.371] (II) fglrx(0): Gamma: 2.20
[    27.371] (II) fglrx(0): DPMS capabilities: Off
[    27.371] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    27.371] (II) fglrx(0): First detailed timing is preferred mode
[    27.371] (II) fglrx(0): redX: 0.639 redY: 0.333   greenX: 0.289 greenY: 0.597
[    27.371] (II) fglrx(0): blueX: 0.153 blueY: 0.082   whiteX: 0.313 whiteY: 0.329
[    27.371] (II) fglrx(0): Supported established timings:
[    27.371] (II) fglrx(0): 720x400@70Hz
[    27.371] (II) fglrx(0): 640x480@60Hz
[    27.371] (II) fglrx(0): 640x480@67Hz
[    27.371] (II) fglrx(0): 640x480@72Hz
[    27.371] (II) fglrx(0): 640x480@75Hz
[    27.371] (II) fglrx(0): 800x600@56Hz
[    27.371] (II) fglrx(0): 800x600@60Hz
[    27.371] (II) fglrx(0): 800x600@72Hz
[    27.371] (II) fglrx(0): 800x600@75Hz
[    27.371] (II) fglrx(0): 832x624@75Hz
[    27.371] (II) fglrx(0): 1024x768@60Hz
[    27.371] (II) fglrx(0): 1024x768@70Hz
[    27.371] (II) fglrx(0): 1024x768@75Hz
[    27.371] (II) fglrx(0): 1280x1024@75Hz
[    27.371] (II) fglrx(0): 1152x864@75Hz
[    27.371] (II) fglrx(0): Manufacturer's mask: 0
[    27.371] (II) fglrx(0): Supported standard timings:
[    27.371] (II) fglrx(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    27.371] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    27.371] (II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    27.371] (II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    27.371] (II) fglrx(0): Supported detailed timing:
[    27.371] (II) fglrx(0): clock: 119.0 MHz   Image Size:  494 x 320 mm
[    27.371] (II) fglrx(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[    27.371] (II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[    27.371] (II) fglrx(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 145 MHz
[    27.371] (II) fglrx(0): Monitor name: SyncMaster
[    27.371] (II) fglrx(0): Serial No: H9XQ205128
[    27.371] (II) fglrx(0): EDID (in hex):
[    27.371] (II) fglrx(0):     00ffffffffffff004c2d040332324550
[    27.371] (II) fglrx(0):     07120103803120782a9345a3554a9827
[    27.371] (II) fglrx(0):     155054bfef80b30081808140714f0101
[    27.371] (II) fglrx(0):     0101010101017c2e90a0601a1e403020
[    27.371] (II) fglrx(0):     3600ee401100001a000000fd00384b1e
[    27.371] (II) fglrx(0):     510e000a202020202020000000fc0053
[    27.371] (II) fglrx(0):     796e634d61737465720a2020000000ff
[    27.371] (II) fglrx(0):     00483958513230353132380a202000b4
[    27.372] (II) fglrx(0): EDID vendor "SAM", prod id 772
[    27.372] (II) fglrx(0): Using EDID range info for horizontal sync
[    27.372] (II) fglrx(0): Using EDID range info for vertical refresh
[    27.372] (II) fglrx(0): Printing DDC gathered Modelines:
[    27.372] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    27.372] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    27.372] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    27.372] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    27.372] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    27.372] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    27.372] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    27.372] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    27.372] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    27.372] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    27.372] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    27.372] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    27.372] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    27.372] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    27.372] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    27.372] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    27.372] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    27.372] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    27.372] (II) fglrx(0): Printing probed modes for output DFP1
[    27.372] (II) fglrx(0): Modeline "1680x1050"x60.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync +vsync (64.7 kHz)
[    27.373] (II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync -vsync (65.3 kHz)
[    27.373] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync (55.9 kHz)
[    27.373] (II) fglrx(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 +hsync -vsync (49.7 kHz)
[    27.373] (II) fglrx(0): Modeline "1152x648"x60.0   59.90  1152 1200 1320 1488  648 649 652 671 +hsync -vsync (40.3 kHz)
[    27.373] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 -hsync -vsync (80.0 kHz)
[    27.373] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 -hsync -vsync (64.0 kHz)
[    27.373] (II) fglrx(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 +hsync -vsync (75.2 kHz)
[    27.373] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 -hsync -vsync (60.0 kHz)
[    27.373] (II) fglrx(0): Modeline "1280x800"x75.0  107.21  1280 1360 1496 1712  800 801 804 835 +hsync -vsync (62.6 kHz)
[    27.373] (II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 -hsync -vsync (67.5 kHz)
[    27.373] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync -vsync (53.7 kHz)
[    27.373] (II) fglrx(0): Modeline "1280x768"x75.0  102.25  1280 1360 1488 1696  768 771 778 805 +hsync -vsync (60.3 kHz)
[    27.373] (II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
[    27.373] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 -hsync -vsync (45.0 kHz)
[    27.373] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[    27.373] (II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
[    27.373] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
[    27.373] (II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 -hsync -vsync (48.1 kHz)
[    27.373] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 -hsync -vsync (46.9 kHz)
[    27.373] (II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync -vsync (43.8 kHz)
[    27.373] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 -hsync -vsync (37.9 kHz)
[    27.373] (II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 -hsync -vsync (35.2 kHz)
[    27.373] (II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync -vsync (29.8 kHz)
[    27.373] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
[    27.373] (II) fglrx(0): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 +hsync +vsync (37.9 kHz)
[    27.373] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 +hsync +vsync (31.5 kHz)
[    27.373] (II) fglrx(0): EDID for output CRT1
[    27.373] (II) fglrx(0): EDID for output CRT2
[    27.373] (II) fglrx(0): EDID for output TV
[    27.373] (II) fglrx(0): EDID for output CV
[    27.373] (II) fglrx(0): Output DFP1 connected
[    27.373] (II) fglrx(0): Output CRT1 disconnected
[    27.373] (II) fglrx(0): Output CRT2 disconnected
[    27.373] (II) fglrx(0): Output TV disconnected
[    27.373] (II) fglrx(0): Output CV disconnected
[    27.374] (II) fglrx(0): Using exact sizes for initial modes
[    27.374] (II) fglrx(0): Output DFP1 using initial mode 1680x1050
[    27.374] (II) fglrx(0): Display dimensions: (490, 320) mm
[    27.374] (II) fglrx(0): DPI set to (87, 83)
[    27.374] (II) fglrx(0): Adapter ATI Radeon HD 3450  has 2 configurable heads and 1 displays connected.
[    27.374] (==) fglrx(0):  PseudoColor visuals disabled
[    27.374] (II) Loading sub module "ramdac"
[    27.374] (II) LoadModule: "ramdac"
[    27.374] (II) Module "ramdac" already built-in
[    27.374] (==) fglrx(0): NoDRI = NO
[    27.374] (==) fglrx(0): Capabilities: 0x00000000
[    27.374] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    27.374] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    27.375] (==) fglrx(0): UseFastTLS=0
[    27.375] (==) fglrx(0): BlockSignalsOnLock=1
[    27.375] (--) Depth 24 pixmap format is 32 bpp
[    27.375] (II) Loading extension ATIFGLRXDRI
[    27.376] (II) fglrx(0): doing swlDriScreenInit
[    27.376] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    27.376] ukiDynamicMajor: found major device number 250
[    27.376] ukiDynamicMajor: found major device number 250
[    27.376] ukiDynamicMajor: found major device number 250
[    27.376] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    27.376] ukiOpenDevice: node name is /dev/ati/card0
[    27.376] ukiOpenDevice: open result is 17, (OK)
[    27.376] ukiOpenByBusid: ukiOpenMinor returns 17
[    27.376] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    27.376] (II) fglrx(0): [uki] DRM interface version 1.0
[    27.376] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    27.377] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    27.377] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0xb77c0000
[    27.377] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    27.377] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    27.377] (II) fglrx(0): swlDriScreenInit done
[    27.377] (II) fglrx(0): Kernel Module Version Information:
[    27.377] (II) fglrx(0):     Name: fglrx
[    27.377] (II) fglrx(0):     Version: 8.96.4
[    27.377] (II) fglrx(0):     Date: Mar 12 2012
[    27.377] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    27.377] (II) fglrx(0): Kernel Module version matches driver.
[    27.377] (II) fglrx(0): Kernel Module Build Time Information:
[    27.377] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.2.0-36-generic-pae
[    27.377] (II) fglrx(0):     Build-Kernel MODVERSIONS:        no
[    27.377] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    27.377] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    27.377] (II) fglrx(0): [uki] register handle = 0x00004000
[    27.482] (II) fglrx(0): DRI initialization successfull
[    27.497] (II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x01008000
[    27.506] (==) fglrx(0): Backing store disabled
[    27.506] (II) Loading extension FGLRXEXTENSION
[    27.507] (**) fglrx(0): DPMS enabled
[    27.507] (II) fglrx(0): Initialized in-driver Xinerama extension
[    27.507] (**) fglrx(0): Textured Video is enabled.
[    27.508] (II) LoadModule: "glesx"
[    27.508] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/glesx.so
[    27.665] (II) Module glesx: vendor="X.Org Foundation"
[    27.666]     compiled for 1.4.99.906, module version = 1.0.0
[    27.666] (II) Loading extension GLESX
[    27.666] (II) fglrx(0): GLESX enableFlags = 528
[    27.667] (II) fglrx(0): GLESX is enabled
[    27.667] (II) LoadModule: "amdxmm"
[    27.667] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/amdxmm.so
[    27.677] (II) Module amdxmm: vendor="X.Org Foundation"
[    27.677]     compiled for 1.4.99.906, module version = 2.0.0
[    27.678] (II) Loading extension AMDXVOPL
[    27.678] (II) Loading extension AMDXVBA
[    27.690] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    27.696] (II) fglrx(0): Enable composite support successfully
[    27.696] (WW) fglrx(0): Option "VendorName" is not used
[    27.696] (WW) fglrx(0): Option "ModelName" is not used
[    27.696] (II) fglrx(0): X context handle = 0x1
[    27.696] (II) fglrx(0): [DRI] installation complete
[    27.697] (==) fglrx(0): Silken mouse enabled
[    27.698] (==) fglrx(0): Using HW cursor of display infrastructure!
[    27.698] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    27.698] (II) fglrx(0): Cannot get TV Format. Set all TV geometry value to zero!
[    27.699] (II) fglrx(0): Cannot set TV horizontal size.
[    27.699] (II) fglrx(0): Cannot get TV Format for trying to adjust horizontal position after horizontal size changed. 
[    27.699] (II) fglrx(0): Cannot set TV horizontal position.
[    27.699] (II) fglrx(0): Cannot set TV vertical position.
[    27.960] (--) RandR disabled
[    27.960] (II) Initializing built-in extension Generic Event Extension
[    27.960] (II) Initializing built-in extension SHAPE
[    27.960] (II) Initializing built-in extension MIT-SHM
[    27.961] (II) Initializing built-in extension XInputExtension
[    27.961] (II) Initializing built-in extension XTEST
[    27.961] (II) Initializing built-in extension BIG-REQUESTS
[    27.961] (II) Initializing built-in extension SYNC
[    27.961] (II) Initializing built-in extension XKEYBOARD
[    27.961] (II) Initializing built-in extension XC-MISC
[    27.961] (II) Initializing built-in extension SECURITY
[    27.961] (II) Initializing built-in extension XINERAMA
[    27.961] (II) Initializing built-in extension XFIXES
[    27.961] (II) Initializing built-in extension RENDER
[    27.961] (II) Initializing built-in extension RANDR
[    27.961] (II) Initializing built-in extension COMPOSITE
[    27.961] (II) Initializing built-in extension DAMAGE
[    27.967] ukiDynamicMajor: found major device number 250
[    27.968] ukiDynamicMajor: found major device number 250
[    27.968] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    27.968] ukiOpenDevice: node name is /dev/ati/card0
[    27.968] ukiOpenDevice: open result is 18, (OK)
[    27.968] ukiOpenByBusid: ukiOpenMinor returns 18
[    27.968] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    29.228] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    29.370] (II) fglrx(0): Enable the clock gating!
[    29.370] (II) fglrx(0): Setting screen physical size to 444 x 277
[    29.498] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    29.526] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    29.526] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.526] (II) LoadModule: "evdev"
[    29.550] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.588] (II) Module evdev: vendor="X.Org Foundation"
[    29.588]     compiled for 1.11.3, module version = 2.7.0
[    29.588]     Module class: X.Org XInput Driver
[    29.588]     ABI class: X.Org XInput driver, version 16.0
[    29.588] (II) Using input driver 'evdev' for 'Power Button'
[    29.588] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.588] (**) Power Button: always reports core events
[    29.588] (**) evdev: Power Button: Device: "/dev/input/event1"
[    29.589] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.589] (--) evdev: Power Button: Found keys
[    29.589] (II) evdev: Power Button: Configuring as keyboard
[    29.589] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    29.589] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    29.589] (**) Option "xkb_rules" "evdev"
[    29.589] (**) Option "xkb_model" "pc105"
[    29.589] (**) Option "xkb_layout" "cz"
[    29.594] (II) XKB: reuse xkmfile /var/lib/xkb/server-583B992BBA3776030BA62AC94FC7F0AE9B04119F.xkm
[    29.611] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    29.611] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.611] (II) Using input driver 'evdev' for 'Power Button'
[    29.611] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.611] (**) Power Button: always reports core events
[    29.611] (**) evdev: Power Button: Device: "/dev/input/event0"
[    29.611] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.611] (--) evdev: Power Button: Found keys
[    29.611] (II) evdev: Power Button: Configuring as keyboard
[    29.611] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    29.611] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    29.611] (**) Option "xkb_rules" "evdev"
[    29.612] (**) Option "xkb_model" "pc105"
[    29.612] (**) Option "xkb_layout" "cz"
[    29.614] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event4)
[    29.614] (II) No input driver specified, ignoring this device.
[    29.614] (II) This device may have been added with another device file.
[    29.615] (II) config/udev: Adding input device HID 1241:1166 (/dev/input/event3)
[    29.615] (**) HID 1241:1166: Applying InputClass "evdev pointer catchall"
[    29.615] (II) Using input driver 'evdev' for 'HID 1241:1166'
[    29.615] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.615] (**) HID 1241:1166: always reports core events
[    29.616] (**) evdev: HID 1241:1166: Device: "/dev/input/event3"
[    29.616] (--) evdev: HID 1241:1166: Vendor 0x1241 Product 0x1166
[    29.616] (--) evdev: HID 1241:1166: Found 9 mouse buttons
[    29.616] (--) evdev: HID 1241:1166: Found scroll wheel(s)
[    29.616] (--) evdev: HID 1241:1166: Found relative axes
[    29.616] (--) evdev: HID 1241:1166: Found x and y relative axes
[    29.616] (II) evdev: HID 1241:1166: Configuring as mouse
[    29.616] (II) evdev: HID 1241:1166: Adding scrollwheel support
[    29.616] (**) evdev: HID 1241:1166: YAxisMapping: buttons 4 and 5
[    29.616] (**) evdev: HID 1241:1166: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    29.616] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input3/event3"
[    29.616] (II) XINPUT: Adding extended input device "HID 1241:1166" (type: MOUSE, id 8)
[    29.616] (II) evdev: HID 1241:1166: initialized for relative axes.
[    29.617] (**) HID 1241:1166: (accel) keeping acceleration scheme 1
[    29.617] (**) HID 1241:1166: (accel) acceleration profile 0
[    29.617] (**) HID 1241:1166: (accel) acceleration factor: 2.000
[    29.617] (**) HID 1241:1166: (accel) acceleration threshold: 4
[    29.618] (II) config/udev: Adding input device HID 1241:1166 (/dev/input/mouse0)
[    29.618] (II) No input driver specified, ignoring this device.
[    29.618] (II) This device may have been added with another device file.
[    29.619] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    29.619] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    29.619] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    29.619] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.619] (**) AT Translated Set 2 keyboard: always reports core events
[    29.619] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    29.619] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    29.619] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    29.619] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    29.619] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    29.619] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    29.619] (**) Option "xkb_rules" "evdev"
[    29.619] (**) Option "xkb_model" "pc105"
[    29.619] (**) Option "xkb_layout" "cz"
[    29.861] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    37.352] (II) fglrx(0): EDID vendor "SAM", prod id 772
[    37.352] (II) fglrx(0): Using hsync ranges from config file
[    37.352] (II) fglrx(0): Using vrefresh ranges from config file
[    37.352] (II) fglrx(0): Printing DDC gathered Modelines:
[    37.352] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    37.352] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    37.352] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    37.352] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    37.352] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    37.352] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    37.352] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    37.352] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    37.352] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    37.352] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    37.352] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    37.352] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    37.352] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    37.352] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    37.352] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    37.352] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    37.352] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    37.352] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    37.618] (WW) fglrx(0): Cannot get updated TV attributes.
[    44.815] (II) fglrx(0): EDID vendor "SAM", prod id 772
[    44.815] (II) fglrx(0): Using hsync ranges from config file
[    44.815] (II) fglrx(0): Using vrefresh ranges from config file
[    44.815] (II) fglrx(0): Printing DDC gathered Modelines:
[    44.815] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    44.816] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    44.816] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    44.816] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    44.816] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    44.816] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    44.816] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    44.816] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    44.816] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    44.816] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    44.816] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    44.816] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    44.816] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    44.816] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    44.816] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    44.816] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    44.816] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    44.816] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    52.585] (II) fglrx(0): EDID vendor "SAM", prod id 772
[    52.585] (II) fglrx(0): Using hsync ranges from config file
[    52.585] (II) fglrx(0): Using vrefresh ranges from config file
[    52.585] (II) fglrx(0): Printing DDC gathered Modelines:
[    52.585] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    52.585] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    52.585] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    52.585] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    52.585] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    52.585] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    52.585] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    52.585] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    52.585] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    52.585] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    52.585] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    52.585] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    52.585] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    52.585] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    52.586] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    52.586] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    52.586] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    52.586] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    52.915] (WW) fglrx(0): Cannot get updated TV attributes.
[    64.635] (II) fglrx(0): EDID vendor "SAM", prod id 772
[    64.635] (II) fglrx(0): Using hsync ranges from config file
[    64.635] (II) fglrx(0): Using vrefresh ranges from config file
[    64.635] (II) fglrx(0): Printing DDC gathered Modelines:
[    64.635] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    64.635] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    64.635] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    64.635] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    64.635] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    64.635] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    64.635] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    64.635] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    64.635] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    64.635] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    64.635] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    64.635] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    64.635] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    64.635] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    64.635] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    64.635] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    64.635] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    64.635] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    65.026] (WW) fglrx(0): Cannot get updated TV attributes.
[    68.134] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[   182.400] (II) fglrx(0): EDID vendor "SAM", prod id 772
[   182.400] (II) fglrx(0): Using hsync ranges from config file
[   182.400] (II) fglrx(0): Using vrefresh ranges from config file
[   182.400] (II) fglrx(0): Printing DDC gathered Modelines:
[   182.400] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   182.400] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   182.400] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   182.400] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   182.400] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   182.400] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   182.400] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   182.400] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   182.400] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   182.401] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   182.401] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   182.401] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   182.401] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   182.401] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   182.401] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   182.401] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   182.401] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   182.401] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   239.270] (II) fglrx(0): Desktop Vsync is enabled.
```What am I doing wrong?

---

### Post by Laiquendi on 2013-01-26
As far as I'm concerned, ATI proprietary drivers do not support models below 4xxx any more. Yes, ATI does not give a damn about you. But we do! ;)

I would suggest using open-sorce driver, the one you had at the beginning. IT works on my old laptop with 2400.

---

### Post by Yellow Pasque on 2013-01-26
> **Laiquendi said:**
> As far as I'm concerned, ATI proprietary drivers do not support models below 4xxx any more.
That's true on Ubuntu 12.10 (though there are ways around it), but we're talking about Ubuntu 12.04 here..

> Yes, ATI does not give a damn about you...
That's not true either. If AMD/ATI didn't care, the open-source driver wouldn't be half as developed as it is. They provided a lot of documentation as well as hiring freelance devs that were already working on the driver. Their open-source effort isn't perfect (especially when it comes to video decoding accel), but it clearly shows AMD/ATI cares to some degree.

> I would suggest using open-source driver
Yeah, it's probably a better choice for an older AGP system.

---

### Post by Lukfi on 2013-01-26
You mean the Gallium driver? Its performance is very unsatisfactory, scrolling on websites is very painful. At least I think this is a VGA driver issue.

---

### Post by Lukfi on 2013-01-26
I probably need the radeonhd driver, but it's not in standard repositories and it fails to install from a .deb package. There's an error, but no sensible description. This is just great. No, wait, it's not great, it's a clusterfuck of epic proportions =D>

---

### Post by deadflowr on 2013-01-26
When you apt-get installed the fglrx driver, did it install the catalyst control center too?
Maybe see if it was installed and open it to see if tweaking some of the setting might help.
It'll be listed in the dash as AMD Catalyst Control Center.
If it isn't installed
```
sudo apt-get install fglrx-amdcccle
```

It's best to launch the root version so system changes can be made.

---

### Post by Yellow Pasque on 2013-01-26
> **Lukfi said:**
> I probably need the radeonhd driver

No, development stopped on that one a while ago and radeon driver now supports all Radeon/HD cards. You're barking up the wrong tree on that one.

---

### Post by jessepage1989 on 2013-01-26
have you tried amd's drivers? 


[http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx)

once you download and extract place the .run file in your home directory then
```
 sudo chmod +x (filename)
sudo ./(filename) 
```

just make sure you have previous proprietary drivers uninstalled before you do this.

---

### Post by Lukfi on 2013-01-26
> **deadflowr said:**
> ```
sudo apt-get install fglrx-amdcccle
```
So I should install fglrx even though my card is a legacy model?

> **jessepage1989 said:**
> have you tried amd's drivers?
That's exactly what I did. Like I said in the first post, I was following these instructions: [http://www.upubuntu.com/2012/06/install-amd-ati-catalyst-126-display.html](http://www.upubuntu.com/2012/06/install-amd-ati-catalyst-126-display.html) (so the previous drivers would have been uninstalled, yes).
But after installation, aticonfig would not run, saying
```
aticonfig: No supported adapters detected.
```aticonfig only ran when I used apt-get install fglrx.

[COLOR=Red]// EDIT:[/COLOR]
Installed flgrx through apt-get, amdcccle gets installed automatically with it. glxinfo gets me this:
```
lukfi@ubuntu:~$ glxinfo | grep OpenGL
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 3450 
OpenGL version string: 3.3.11627 Compatibility Profile Context
OpenGL shading language version string: 3.30
OpenGL extensions:

```
But performance is still very bad, websites don't scroll smoothly. It's not a RAM problem, the machine has 1.5 GB.

---

### Post by Lukfi on 2013-01-28
(Up)

---

### Post by apochry on 2013-01-28
Hi,

I doubt I could help much but I can share my experience on that.
I have an older Sony laptop with the Ati HD3470 card using the Gallium 0.4 driver. It worked very well out of the box on 12.10. The performance is good, probably not for 3d apps, but I don't experience any lag on webpages or similar whatsoever. Even the vsync works perfectly and I get tear-free video playback, which is not the case on my current system with the 6600 card and proprietary driver.

Is the card really on AGP? Someone mentioned that above but i read in your very first post:
> ```
Section "Device"
Identifier  "aticonfig-Device[0]-0"
Driver      "fglrx"
BusID       "PCI:1:0:0"
```You could one more time go back to Galluim and run some performance test, e.g. GtkPerf, in order to be sure it's not a browser issue.
How are videos playing? Try some hi-res ones.

Good luck on that!
 - Christo

---

### Post by Lukfi on 2013-01-28
Yes, the card is for AGP. Whoever built the system (the computer is not mine) made some unorthodox choices - setup is as follows:
- Celeron D 2,4 GHz (Prescott-256K, sc478)
- Gigabyte GA-8IK1100 board with i875P chipset (yes you read that right)
- 1GB and 512MB RAM modules that don't work in dual channel
- and the AGP Radeon HD 3450 (obviously used to upgrade a legacy PC)

I tried some videos on YouTube and they did play smoothly, but probably using just the CPU and not GPU. The problem is that when I load a website - be it the youtube mainpage, or a page on these forums - I can't scroll smoothly, it's worse than on an underpowered smartphone. Like it's missing 2D acceleration or something.

It gives me no pleasure to say this, but if nobody can help me, I'll have to put this adorable pangolin down.

[IMG]http://www.factzoo.com/sites/all/img/mammals/baby-pangolin.jpg[/IMG] -- "Please don't kill me"

[B]// EDIT:
[/B]Tried again now, looks like the cycle of installing and uinstalling drivers has taken its toll, font in the top bar (in Unity) looks weird, with colored pixels around the edges, and dragging windows or scrolling websites is not smooth, videos on youtube are also unwatchable.

[B]// EDIT 2:
[/B]Slightly better after rebooting, but still - why is Gallium used instead of a proper driver?

---

### Post by Yellow Pasque on 2013-01-28
> why is Gallium used instead of a proper driver?
Why isn't Gallium a "proper" driver?

Post your Xorg.0.log from booting with open-source radeon/Gallium driver.

---

### Post by Bucky Ball on 2013-01-28
*Thread moved to **Multimedia & Graphics***

---

### Post by Lukfi on 2013-01-28
> **Temüjin said:**
> Why isn't Gallium a "proper" driver?
In my opinion a proper driver is "radeon" for ATI, "nouveau" for nVidia, "openchrome" for VIA/S3 and so on :) Gallium just runs on everything, it's like a stand-in or something.
I have an even older setup with a VIA KM400 chipset. I could not for the love of god install openchrome drivers on it, glxinfo still just said "Gallium on softpipe". No luck with a GeForce 4 MX and nouveau/official nVidia drivers, either. Here it says "Gallium on AMD RV620", so I guess that's better...
> Post your Xorg.0.log from booting with open-source radeon/Gallium driver.```
[    23.663] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    23.663] X Protocol Version 11, Revision 0
[    23.663] Build Operating System: Linux 2.6.42-26-generic i686 Ubuntu
[    23.663] Current Operating System: Linux ubuntu 3.2.0-36-generic-pae #57-Ubuntu SMP Tue Jan 8 22:01:06 UTC 2013 i686
[    23.663] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-36-generic-pae root=UUID=eb5aa52d-f997-4b3e-99e4-2ae98a5d59cd ro quiet splash vt.handoff=7
[    23.663] Build Date: 29 August 2012  12:10:05AM
[    23.668] xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see http://www.ubuntu.com/support) 
[    23.668] Current version of pixman: 0.24.4
[    23.668]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    23.668] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    23.669] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan 28 21:09:51 2013
[    23.698] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    23.699] (==) No Layout section.  Using the first Screen section.
[    23.699] (==) No screen section available. Using defaults.
[    23.699] (**) |-->Screen "Default Screen Section" (0)
[    23.699] (**) |   |-->Monitor "<default monitor>"
[    23.699] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    23.699] (==) Automatically adding devices
[    23.699] (==) Automatically enabling devices
[    23.700] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    23.700]     Entry deleted from font path.
[    23.700] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    23.700]     Entry deleted from font path.
[    23.700] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    23.700]     Entry deleted from font path.
[    23.700] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    23.700]     Entry deleted from font path.
[    23.700] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    23.700]     Entry deleted from font path.
[    23.700] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    23.700]     Entry deleted from font path.
[    23.700] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    23.700] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    23.700] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    23.700] (II) Loader magic: 0xb2d5a0
[    23.701] (II) Module ABI versions:
[    23.701]     X.Org ANSI C Emulation: 0.4
[    23.701]     X.Org Video Driver: 11.0
[    23.701]     X.Org XInput driver : 16.0
[    23.701]     X.Org Server Extension : 6.0
[    23.702] (--) PCI:*(0:1:0:0) 1002:95c6:1043:0028 rev 0, Mem @ 0xe0000000/268435456, 0xf9000000/65536, I/O @ 0x0000a000/256, BIOS @ 0x????????/131072
[    23.704] (II) Open ACPI successful (/var/run/acpid.socket)
[    23.705] (II) LoadModule: "extmod"
[    23.862] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    23.863] (II) Module extmod: vendor="X.Org Foundation"
[    23.863]     compiled for 1.11.3, module version = 1.0.0
[    23.863]     Module class: X.Org Server Extension
[    23.863]     ABI class: X.Org Server Extension, version 6.0
[    23.863] (II) Loading extension MIT-SCREEN-SAVER
[    23.863] (II) Loading extension XFree86-VidModeExtension
[    23.863] (II) Loading extension XFree86-DGA
[    23.863] (II) Loading extension DPMS
[    23.863] (II) Loading extension XVideo
[    23.863] (II) Loading extension XVideo-MotionCompensation
[    23.863] (II) Loading extension X-Resource
[    23.863] (II) LoadModule: "dbe"
[    23.863] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    23.863] (II) Module dbe: vendor="X.Org Foundation"
[    23.864]     compiled for 1.11.3, module version = 1.0.0
[    23.864]     Module class: X.Org Server Extension
[    23.864]     ABI class: X.Org Server Extension, version 6.0
[    23.864] (II) Loading extension DOUBLE-BUFFER
[    23.864] (II) LoadModule: "glx"
[    23.864] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    23.865] (II) Module glx: vendor="X.Org Foundation"
[    23.865]     compiled for 1.11.3, module version = 1.0.0
[    23.865]     ABI class: X.Org Server Extension, version 6.0
[    23.865] (==) AIGLX enabled
[    23.865] (II) Loading extension GLX
[    23.865] (II) LoadModule: "record"
[    23.865] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    23.865] (II) Module record: vendor="X.Org Foundation"
[    23.866]     compiled for 1.11.3, module version = 1.13.0
[    23.866]     Module class: X.Org Server Extension
[    23.866]     ABI class: X.Org Server Extension, version 6.0
[    23.866] (II) Loading extension RECORD
[    23.866] (II) LoadModule: "dri"
[    23.866] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    23.867] (II) Module dri: vendor="X.Org Foundation"
[    23.867]     compiled for 1.11.3, module version = 1.0.0
[    23.867]     ABI class: X.Org Server Extension, version 6.0
[    23.867] (II) Loading extension XFree86-DRI
[    23.867] (II) LoadModule: "dri2"
[    23.867] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    23.867] (II) Module dri2: vendor="X.Org Foundation"
[    23.867]     compiled for 1.11.3, module version = 1.2.0
[    23.867]     ABI class: X.Org Server Extension, version 6.0
[    23.867] (II) Loading extension DRI2
[    23.881] (==) Matched fglrx as autoconfigured driver 0
[    23.881] (==) Matched ati as autoconfigured driver 1
[    23.881] (==) Matched vesa as autoconfigured driver 2
[    23.881] (==) Matched fbdev as autoconfigured driver 3
[    23.881] (==) Assigned the driver to the xf86ConfigLayout
[    23.881] (II) LoadModule: "fglrx"
[    23.919] (WW) Warning, couldn't open module fglrx
[    23.919] (II) UnloadModule: "fglrx"
[    23.919] (II) Unloading fglrx
[    23.919] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    23.919] (II) LoadModule: "ati"
[    23.919] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    23.936] (II) Module ati: vendor="X.Org Foundation"
[    23.936]     compiled for 1.11.3, module version = 6.14.99
[    23.936]     Module class: X.Org Video Driver
[    23.936]     ABI class: X.Org Video Driver, version 11.0
[    23.936] (II) LoadModule: "radeon"
[    23.937] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    23.979] (II) Module radeon: vendor="X.Org Foundation"
[    23.979]     compiled for 1.11.3, module version = 6.14.99
[    23.979]     Module class: X.Org Video Driver
[    23.979]     ABI class: X.Org Video Driver, version 11.0
[    23.988] (II) LoadModule: "vesa"
[    23.989] (WW) Warning, couldn't open module vesa
[    23.989] (II) UnloadModule: "vesa"
[    23.989] (II) Unloading vesa
[    23.989] (EE) Failed to load module "vesa" (module does not exist, 0)
[    23.989] (II) LoadModule: "fbdev"
[    23.990] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    23.990] (II) Module fbdev: vendor="X.Org Foundation"
[    23.990]     compiled for 1.11.3, module version = 0.4.2
[    23.990]     ABI class: X.Org Video Driver, version 11.0
[    23.990] (==) Matched fglrx as autoconfigured driver 0
[    23.990] (==) Matched ati as autoconfigured driver 1
[    23.990] (==) Matched vesa as autoconfigured driver 2
[    23.990] (==) Matched fbdev as autoconfigured driver 3
[    23.990] (==) Assigned the driver to the xf86ConfigLayout
[    23.990] (II) LoadModule: "fglrx"
[    23.991] (WW) Warning, couldn't open module fglrx
[    23.991] (II) UnloadModule: "fglrx"
[    23.991] (II) Unloading fglrx
[    23.991] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    23.991] (II) LoadModule: "ati"
[    23.992] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    23.992] (II) Module ati: vendor="X.Org Foundation"
[    23.992]     compiled for 1.11.3, module version = 6.14.99
[    23.992]     Module class: X.Org Video Driver
[    23.992]     ABI class: X.Org Video Driver, version 11.0
[    23.992] (II) LoadModule: "vesa"
[    23.993] (WW) Warning, couldn't open module vesa
[    23.994] (II) UnloadModule: "vesa"
[    23.994] (II) Unloading vesa
[    23.994] (EE) Failed to load module "vesa" (module does not exist, 0)
[    23.994] (II) LoadModule: "fbdev"
[    23.994] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    23.994] (II) Module fbdev: vendor="X.Org Foundation"
[    23.994]     compiled for 1.11.3, module version = 0.4.2
[    23.994]     ABI class: X.Org Video Driver, version 11.0
[    23.994] (II) UnloadModule: "fbdev"
[    23.994] (II) Unloading fbdev
[    23.994] (II) Failed to load module "fbdev" (already loaded, 0)
[    23.995] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
    ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
    ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
    SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
    CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS
[    24.003] (II) FBDEV: driver for framebuffer: fbdev
[    24.003] (++) using VT number 7

[    24.004] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    24.004] (II) [KMS] Kernel modesetting enabled.
[    24.004] (WW) Falling back to old probe method for fbdev
[    24.004] (II) Loading sub module "fbdevhw"
[    24.004] (II) LoadModule: "fbdevhw"
[    24.005] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    24.005] (II) Module fbdevhw: vendor="X.Org Foundation"
[    24.005]     compiled for 1.11.3, module version = 0.0.2
[    24.005]     ABI class: X.Org Video Driver, version 11.0
[    24.005] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    24.005] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    24.006] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    24.006] (==) RADEON(0): Default visual is TrueColor
[    24.007] (==) RADEON(0): RGB weight 888
[    24.007] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    24.007] (--) RADEON(0): Chipset: "ATI Radeon HD 3450" (ChipID = 0x95c6)
[    24.007] (II) RADEON(0): AGP card detected
[    24.007] drmOpenDevice: node name is /dev/dri/card0
[    24.007] drmOpenDevice: open result is 9, (OK)
[    24.007] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    24.007] drmOpenDevice: node name is /dev/dri/card0
[    24.007] drmOpenDevice: open result is 9, (OK)
[    24.007] drmOpenByBusid: drmOpenMinor returns 9
[    24.007] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    24.007] (II) Loading sub module "exa"
[    24.007] (II) LoadModule: "exa"
[    24.009] (II) Loading /usr/lib/xorg/modules/libexa.so
[    24.024] (II) Module exa: vendor="X.Org Foundation"
[    24.024]     compiled for 1.11.3, module version = 2.5.0
[    24.025]     ABI class: X.Org Video Driver, version 11.0
[    24.025] (II) RADEON(0): KMS Color Tiling: enabled
[    24.025] (II) RADEON(0): KMS Pageflipping: enabled
[    24.025] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    24.048] (II) RADEON(0): Output VGA-0 has no monitor section
[    24.072] (II) RADEON(0): Output DIN has no monitor section
[    24.137] (II) RADEON(0): Output HDMI-0 has no monitor section
[    24.266] (II) RADEON(0): Output VGA-1 has no monitor section
[    24.292] (II) RADEON(0): EDID for output VGA-0
[    24.316] (II) RADEON(0): EDID for output DIN
[    24.381] (II) RADEON(0): EDID for output HDMI-0
[    24.381] (II) RADEON(0): Manufacturer: SAM  Model: 304  Serial#: 1346712114
[    24.381] (II) RADEON(0): Year: 2008  Week: 7
[    24.381] (II) RADEON(0): EDID Version: 1.3
[    24.381] (II) RADEON(0): Digital Display Input
[    24.381] (II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 32
[    24.381] (II) RADEON(0): Gamma: 2.20
[    24.381] (II) RADEON(0): DPMS capabilities: Off
[    24.381] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    24.381] (II) RADEON(0): First detailed timing is preferred mode
[    24.381] (II) RADEON(0): redX: 0.639 redY: 0.333   greenX: 0.289 greenY: 0.597
[    24.381] (II) RADEON(0): blueX: 0.153 blueY: 0.082   whiteX: 0.313 whiteY: 0.329
[    24.381] (II) RADEON(0): Supported established timings:
[    24.381] (II) RADEON(0): 720x400@70Hz
[    24.381] (II) RADEON(0): 640x480@60Hz
[    24.381] (II) RADEON(0): 640x480@67Hz
[    24.381] (II) RADEON(0): 640x480@72Hz
[    24.381] (II) RADEON(0): 640x480@75Hz
[    24.381] (II) RADEON(0): 800x600@56Hz
[    24.381] (II) RADEON(0): 800x600@60Hz
[    24.381] (II) RADEON(0): 800x600@72Hz
[    24.381] (II) RADEON(0): 800x600@75Hz
[    24.381] (II) RADEON(0): 832x624@75Hz
[    24.381] (II) RADEON(0): 1024x768@60Hz
[    24.381] (II) RADEON(0): 1024x768@70Hz
[    24.381] (II) RADEON(0): 1024x768@75Hz
[    24.382] (II) RADEON(0): 1280x1024@75Hz
[    24.382] (II) RADEON(0): 1152x864@75Hz
[    24.382] (II) RADEON(0): Manufacturer's mask: 0
[    24.382] (II) RADEON(0): Supported standard timings:
[    24.382] (II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    24.382] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    24.382] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    24.382] (II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    24.382] (II) RADEON(0): Supported detailed timing:
[    24.382] (II) RADEON(0): clock: 119.0 MHz   Image Size:  494 x 320 mm
[    24.382] (II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[    24.382] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[    24.382] (II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 145 MHz
[    24.382] (II) RADEON(0): Monitor name: SyncMaster
[    24.382] (II) RADEON(0): Serial No: H9XQ205128
[    24.382] (II) RADEON(0): EDID (in hex):
[    24.382] (II) RADEON(0):     00ffffffffffff004c2d040332324550
[    24.382] (II) RADEON(0):     07120103803120782a9345a3554a9827
[    24.382] (II) RADEON(0):     155054bfef80b30081808140714f0101
[    24.382] (II) RADEON(0):     0101010101017c2e90a0601a1e403020
[    24.382] (II) RADEON(0):     3600ee401100001a000000fd00384b1e
[    24.382] (II) RADEON(0):     510e000a202020202020000000fc0053
[    24.382] (II) RADEON(0):     796e634d61737465720a2020000000ff
[    24.382] (II) RADEON(0):     00483958513230353132380a202000b4
[    24.382] (II) RADEON(0): Printing probed modes for output HDMI-0
[    24.382] (II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    24.382] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    24.382] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    24.382] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    24.382] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    24.382] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    24.382] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    24.382] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    24.382] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    24.382] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    24.382] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    24.383] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    24.383] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    24.383] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[    24.383] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    24.383] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    24.383] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    24.383] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    24.511] (II) RADEON(0): EDID for output VGA-1
[    24.511] (II) RADEON(0): Output VGA-0 disconnected
[    24.511] (II) RADEON(0): Output DIN disconnected
[    24.511] (II) RADEON(0): Output HDMI-0 connected
[    24.511] (II) RADEON(0): Output VGA-1 disconnected
[    24.511] (II) RADEON(0): Using exact sizes for initial modes
[    24.511] (II) RADEON(0): Output HDMI-0 using initial mode 1680x1050
[    24.511] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    24.511] (II) RADEON(0): mem size init: gart size :7dff000 vram size: s:10000000 visible:f8ca000
[    24.511] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    24.511] (==) RADEON(0): DPI set to (96, 96)
[    24.511] (II) Loading sub module "fb"
[    24.511] (II) LoadModule: "fb"
[    24.512] (II) Loading /usr/lib/xorg/modules/libfb.so
[    24.512] (II) Module fb: vendor="X.Org Foundation"
[    24.512]     compiled for 1.11.3, module version = 1.0.0
[    24.512]     ABI class: X.Org ANSI C Emulation, version 0.4
[    24.512] (II) Loading sub module "ramdac"
[    24.512] (II) LoadModule: "ramdac"
[    24.512] (II) Module "ramdac" already built-in
[    24.512] (II) UnloadModule: "fbdev"
[    24.512] (II) Unloading fbdev
[    24.512] (II) UnloadModule: "fbdevhw"
[    24.513] (II) Unloading fbdevhw
[    24.513] (--) Depth 24 pixmap format is 32 bpp
[    24.513] (II) RADEON(0): [DRI2] Setup complete
[    24.513] (II) RADEON(0): [DRI2]   DRI driver: r600
[    24.513] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[    24.513] (II) RADEON(0): Front buffer size: 7128K
[    24.514] (II) RADEON(0): VRAM usage limit set to 222868K
[    24.514] (==) RADEON(0): Backing store disabled
[    24.514] (II) RADEON(0): Direct rendering enabled
[    24.528] (II) RADEON(0): Setting EXA maxPitchBytes
[    24.528] (II) EXA(0): Driver allocated offscreen pixmaps
[    24.528] (II) EXA(0): Driver registered support for the following operations:
[    24.528] (II)         Solid
[    24.528] (II)         Copy
[    24.528] (II)         Composite (RENDER acceleration)
[    24.528] (II)         UploadToScreen
[    24.528] (II)         DownloadFromScreen
[    24.528] (II) RADEON(0): Acceleration enabled
[    24.528] (==) RADEON(0): DPMS enabled
[    24.528] (==) RADEON(0): Silken mouse enabled
[    24.540] (II) RADEON(0): Set up textured video
[    24.540] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    24.540] (II) RADEON(0): [XvMC] Extension initialized.
[    24.540] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    24.540] (--) RandR disabled
[    24.540] (II) Initializing built-in extension Generic Event Extension
[    24.540] (II) Initializing built-in extension SHAPE
[    24.540] (II) Initializing built-in extension MIT-SHM
[    24.540] (II) Initializing built-in extension XInputExtension
[    24.540] (II) Initializing built-in extension XTEST
[    24.541] (II) Initializing built-in extension BIG-REQUESTS
[    24.541] (II) Initializing built-in extension SYNC
[    24.541] (II) Initializing built-in extension XKEYBOARD
[    24.541] (II) Initializing built-in extension XC-MISC
[    24.541] (II) Initializing built-in extension SECURITY
[    24.541] (II) Initializing built-in extension XINERAMA
[    24.541] (II) Initializing built-in extension XFIXES
[    24.541] (II) Initializing built-in extension RENDER
[    24.541] (II) Initializing built-in extension RANDR
[    24.541] (II) Initializing built-in extension COMPOSITE
[    24.541] (II) Initializing built-in extension DAMAGE
[    24.661] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    24.661] (II) AIGLX: enabled GLX_INTEL_swap_event
[    24.661] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    24.662] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    24.662] (II) AIGLX: Loaded and initialized r600
[    24.662] (II) GLX: Initialized DRI2 GL provider for screen 0
[    24.675] (II) RADEON(0): Setting screen physical size to 444 x 277
[    24.694] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    24.702] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    24.702] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    24.702] (II) LoadModule: "evdev"
[    24.702] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.703] (II) Module evdev: vendor="X.Org Foundation"
[    24.703]     compiled for 1.11.3, module version = 2.7.0
[    24.703]     Module class: X.Org XInput Driver
[    24.703]     ABI class: X.Org XInput driver, version 16.0
[    24.703] (II) Using input driver 'evdev' for 'Power Button'
[    24.703] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.703] (**) Power Button: always reports core events
[    24.703] (**) evdev: Power Button: Device: "/dev/input/event1"
[    24.704] (--) evdev: Power Button: Vendor 0 Product 0x1
[    24.704] (--) evdev: Power Button: Found keys
[    24.704] (II) evdev: Power Button: Configuring as keyboard
[    24.704] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    24.704] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    24.704] (**) Option "xkb_rules" "evdev"
[    24.704] (**) Option "xkb_model" "pc105"
[    24.704] (**) Option "xkb_layout" "cz"
[    24.709] (II) XKB: reuse xkmfile /var/lib/xkb/server-583B992BBA3776030BA62AC94FC7F0AE9B04119F.xkm
[    24.711] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    24.714] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    24.714] (II) Using input driver 'evdev' for 'Power Button'
[    24.714] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.715] (**) Power Button: always reports core events
[    24.715] (**) evdev: Power Button: Device: "/dev/input/event0"
[    24.715] (--) evdev: Power Button: Vendor 0 Product 0x1
[    24.715] (--) evdev: Power Button: Found keys
[    24.715] (II) evdev: Power Button: Configuring as keyboard
[    24.715] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    24.715] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    24.715] (**) Option "xkb_rules" "evdev"
[    24.715] (**) Option "xkb_model" "pc105"
[    24.715] (**) Option "xkb_layout" "cz"
[    24.718] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event4)
[    24.718] (II) No input driver specified, ignoring this device.
[    24.718] (II) This device may have been added with another device file.
[    24.720] (II) config/udev: Adding input device HID 1241:1166 (/dev/input/event3)
[    24.720] (**) HID 1241:1166: Applying InputClass "evdev pointer catchall"
[    24.720] (II) Using input driver 'evdev' for 'HID 1241:1166'
[    24.720] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.720] (**) HID 1241:1166: always reports core events
[    24.721] (**) evdev: HID 1241:1166: Device: "/dev/input/event3"
[    24.721] (--) evdev: HID 1241:1166: Vendor 0x1241 Product 0x1166
[    24.721] (--) evdev: HID 1241:1166: Found 9 mouse buttons
[    24.721] (--) evdev: HID 1241:1166: Found scroll wheel(s)
[    24.721] (--) evdev: HID 1241:1166: Found relative axes
[    24.721] (--) evdev: HID 1241:1166: Found x and y relative axes
[    24.721] (II) evdev: HID 1241:1166: Configuring as mouse
[    24.721] (II) evdev: HID 1241:1166: Adding scrollwheel support
[    24.721] (**) evdev: HID 1241:1166: YAxisMapping: buttons 4 and 5
[    24.721] (**) evdev: HID 1241:1166: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.721] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input3/event3"
[    24.721] (II) XINPUT: Adding extended input device "HID 1241:1166" (type: MOUSE, id 8)
[    24.721] (II) evdev: HID 1241:1166: initialized for relative axes.
[    24.722] (**) HID 1241:1166: (accel) keeping acceleration scheme 1
[    24.722] (**) HID 1241:1166: (accel) acceleration profile 0
[    24.722] (**) HID 1241:1166: (accel) acceleration factor: 2.000
[    24.723] (**) HID 1241:1166: (accel) acceleration threshold: 4
[    24.724] (II) config/udev: Adding input device HID 1241:1166 (/dev/input/mouse0)
[    24.724] (II) No input driver specified, ignoring this device.
[    24.724] (II) This device may have been added with another device file.
[    24.726] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    24.726] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    24.726] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    24.726] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.726] (**) AT Translated Set 2 keyboard: always reports core events
[    24.726] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    24.727] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    24.727] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    24.727] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    24.727] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    24.727] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    24.727] (**) Option "xkb_rules" "evdev"
[    24.727] (**) Option "xkb_model" "pc105"
[    24.727] (**) Option "xkb_layout" "cz"
[    26.437] (II) RADEON(0): EDID vendor "SAM", prod id 772
[    26.437] (II) RADEON(0): Using EDID range info for horizontal sync
[    26.437] (II) RADEON(0): Using EDID range info for vertical refresh
[    26.437] (II) RADEON(0): Printing DDC gathered Modelines:
[    26.437] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    26.437] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    26.437] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    26.437] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    26.437] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    26.437] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    26.437] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    26.437] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    26.437] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    26.437] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    26.437] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    26.437] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    26.437] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    26.438] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    26.438] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    26.438] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    26.438] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    26.438] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    29.740] (II) RADEON(0): EDID vendor "SAM", prod id 772
[    29.741] (II) RADEON(0): Using hsync ranges from config file
[    29.741] (II) RADEON(0): Using vrefresh ranges from config file
[    29.741] (II) RADEON(0): Printing DDC gathered Modelines:
[    29.741] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    29.741] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    29.741] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    29.741] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    29.741] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    29.741] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    29.741] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    29.741] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    29.741] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    29.741] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    29.741] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    29.741] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    29.741] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    29.741] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    29.741] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    29.741] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    29.741] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    29.741] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    33.286] (II) RADEON(0): EDID vendor "SAM", prod id 772
[    33.286] (II) RADEON(0): Using hsync ranges from config file
[    33.286] (II) RADEON(0): Using vrefresh ranges from config file
[    33.286] (II) RADEON(0): Printing DDC gathered Modelines:
[    33.286] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    33.286] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    33.286] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    33.286] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    33.286] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    33.286] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    33.286] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    33.286] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    33.286] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    33.286] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    33.286] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    33.286] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    33.286] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    33.286] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    33.287] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    33.287] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    33.287] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    33.287] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    40.816] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[    50.407] (II) RADEON(0): EDID vendor "SAM", prod id 772
[    50.408] (II) RADEON(0): Using hsync ranges from config file
[    50.408] (II) RADEON(0): Using vrefresh ranges from config file
[    50.408] (II) RADEON(0): Printing DDC gathered Modelines:
[    50.408] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    50.408] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    50.408] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    50.408] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    50.408] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    50.408] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    50.408] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    50.408] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    50.408] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    50.408] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    50.408] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    50.408] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    50.408] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    50.408] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    50.408] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    50.408] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    50.408] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    50.408] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
```And gtkperf for good measure
```
GtkPerf 0.40 - Starting testing: Mon Jan 28 21:22:27 2013

GtkEntry - time:  0,29
GtkComboBox - time:  5,60
GtkComboBoxEntry - time:  3,30
GtkSpinButton - time:  1,11
GtkProgressBar - time:  1,03
GtkToggleButton - time:  3,11
GtkCheckButton - time:  0,73
GtkRadioButton - time:  1,40
GtkTextView - Add text - time:  2,19
GtkTextView - Scroll - time:  0,76
GtkDrawingArea - Lines - time: 14,41
GtkDrawingArea - Circles - time: 27,45
GtkDrawingArea - Text - time: 10,23
GtkDrawingArea - Pixbufs - time:  1,74
 --- 
Total time: 73,38
```Is that good or not?

// EDIT:
It's not so sloppy now, I can browse the web quite OK. But youtube videos still don't play smoothly - I guess that's another issue? I know this PC is old, but a HD 3450 should play HD videos with ease. Hell, even Atom or smartphone chips can play HD video.

---

### Post by Yellow Pasque on 2013-01-28
> **Lukfi said:**
> In my opinion a proper driver is "radeon" for ATI,  Gallium just runs on everything, it's like a stand-in or something.
You ARE using the radeon kernel driver, and the 3D gallium driver you're using is r600g (which is specifically for RadeonHD cards). The generic Gallium driver is the softpipe or llvmpipe driver that accelerates 3D using the CPU on systems without decent GPU's (like crappy old VIA-based systems ;P )


> But youtube videos still don't play smoothly - I guess that's another issue?
Yeah, the Linux version of the Adobe Flash plugin that yt uses doesn't take advantage of video acceleration from the GPU, so you need a fairly beefy CPU (Celeron D won't cut it).

---

### Post by Lukfi on 2013-01-29
> **Temüjin said:**
> You ARE using the radeon kernel driver, and the 3D gallium driver you're using is r600g (which is specifically for RadeonHD cards). The generic Gallium driver is the softpipe or llvmpipe driver that accelerates 3D using the CPU on systems without decent GPU's (like crappy old VIA-based systems ;P )
If I'm using the right driver, why does a screensaver, which is simple 2D graphics, run at ~10 fps or less with 100% CPU load? I mean, I know this PC is ancient, but what if you had a low clocked AMD Zacate or an Atom with integrated graphics, would Linux run so badly on it as well?
> Yeah, the Linux version of the Adobe Flash plugin that yt uses doesn't take advantage of video acceleration from the GPU, so you need a fairly beefy CPU (Celeron D won't cut it).
That's bad, because I consider video playback a basic functionality. Isn't there another way? What about that "Pepper" Flash player I've read about?
Or let's go back to the beginning - there must be a way to get the official AMD drivers to work, if these drivers exist, no?

---

### Post by jessepage1989 on 2013-01-29
Not sure but i found a link to a legacy driver that is suppose to support hd2000/3000/4000

[http://packages.qa.debian.org/f/fglrx-legacy-driver.html](http://packages.qa.debian.org/f/fglrx-legacy-driver.html)

---

### Post by Lukfi on 2013-01-30
I guess I could try that. How do I install it?

---

### Post by Lukfi on 2013-01-30
I added the debian experimental repository to my apt sources, but if I do
```
sudo apt-get install fglrx-legacy-driver
```
no package is found :(

---

### Post by Yellow Pasque on 2013-01-30
Adding debian experimental repo is not a good idea. If you want to build the fglrx legacy driver for ubuntu:

```
cd ~/
wget http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases linux-headers-generic
unzip amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip
chmod +x amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run
sudo sh ./amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run --buildpkg Ubuntu/precise
sudo dpkg -i fglrx*.deb
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo amdconfig --initial -f
```

If it still doesn't work well after reboot, then maybe you should try a different desktop environment (like lxde).

---

### Post by Lukfi on 2013-01-31
It doesn't work before the reboot.
```
amdconfig: No supported adapters detected
```
By the way. the AMD website clearly states that the drivers (13.1, released this month) are for "kernel up to 3.4", while Precise already has kernel 3.50. Could that be the problem? Long term support my ***... although I know it's AMD who screwed the pooch on this one.

---

### Post by Lukfi on 2013-02-02
AMD officially supports openSUSE, so as a last-ditch effort, I installed openSUSE 12.1 on the machine. Still doesn't work, same amdconfig error.

Lessons learned: Open source drivers suck, AMD drivers for Linux don't work at all. Therefore, by extension, all Linux sucks because it's impossible to get working drivers with half-decent performance for it.

---

