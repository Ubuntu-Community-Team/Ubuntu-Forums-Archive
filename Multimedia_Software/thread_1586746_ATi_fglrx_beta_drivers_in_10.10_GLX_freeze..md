---
title: "ATi fglrx beta drivers in 10.10: GLX freeze."
date: 2010-10-02
forum: Multimedia Software
---

### Post by Insidious611 on 2010-10-02
So, I have an ATi Radeon HD5570. I downloaded and installed the fglrx Catalyst 10.10 beta drivers using sudo apt-get install fglrx, after finding out that the 10.10 repositories had somewhat-recently gotten a hold of a copy of said drivers that works on the latest Xorg. And for the most part, it does. Compositing even works perfectly. The issue I have? GLX does not. Specifically, glxinfo, amdcccle, glxgears, fglrxinfo, fgl_glxgears, and any other GLX based program halts in its tracks. This is all the information I've been able to get on the issue, which is sparse due to the binary fglrx drivers lacking debug info:


```
dmorrison@dmorrison-desktop:~$ glxinfo
name of display: :0.0
(freezes here)
``````
dmorrison@dmorrison-desktop:~$ LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 8.78.30 fglrx (screen 0)
libGL: OpenDriver: trying /usr/lib/fglrx/dri/tls/fglrx_dri.so
libGL: OpenDriver: trying /usr/lib/fglrx/dri/fglrx_dri.so
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:2:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 5, (OK)
ukiOpenByBusid: ukiOpenMinor returns 5
ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
(freezes here)
``````
dmorrison@dmorrison-desktop:/$ LIBGL_DEBUG=verbose amdcccle
libGL: XF86DRIGetClientDriverName: 8.78.30 fglrx (screen 0)
libGL: OpenDriver: trying /usr/lib/fglrx/dri/tls/fglrx_dri.so
libGL: OpenDriver: trying /usr/lib/fglrx/dri/fglrx_dri.so
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:2:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 26, (OK)
ukiOpenByBusid: ukiOpenMinor returns 26
ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
(freezes here)
```Backtrace from glxinfo freeze:
```

ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 7, (OK)
ukiOpenByBusid: ukiOpenMinor returns 7
ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
^C
Program received signal SIGINT, Interrupt.
0x0012e416 in __kernel_vsyscall ()
(gdb) bt
#0  0x0012e416 in __kernel_vsyscall ()
#1  0x004c9f39 in ioctl () from /lib/libc.so.6
#2  0x01d8ea10 in ?? () from /usr/lib/fglrx/dri/fglrx_dri.so
#3  0x01d8ef5a in ?? () from /usr/lib/fglrx/dri/fglrx_dri.so
#4  0x01d81dc5 in ?? () from /usr/lib/fglrx/dri/fglrx_dri.so
(gdb) 
```This is my xorg.conf, its fairly basic:
```

dmorrison@dmorrison-desktop:/$ cat /etc/X11/xorg.conf 
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



Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
    Option "DAMAGE" "true"
    Option "Composite" "true"
EndSection

```Any ideas?

So far I'm impressed with the compositing and 2d acceleration, especially compared to earlier Catalyst revisions. Though I hear that was a 10.9 thing, but still, its nice.

Would just like to be able to try out 3d.

PS: Oh, here's Xorg.0.log, but I don't think it has anything useful in it, other than confirmation that GLX and DRI are supposed to be working. I grep -ved anything with "ModeLine" in it because there are a lot of them. :P

```

dmorrison@dmorrison-desktop:/$ cat /var/log/Xorg.0.log | grep -v Modeline
[    12.676] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    12.676] X Protocol Version 11, Revision 0
[    12.676] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    12.676] Current Operating System: Linux dmorrison-desktop 2.6.35-19-generic #28-Ubuntu SMP Sun Aug 29 06:36:51 UTC 2010 i686
[    12.676] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-19-generic root=UUID=d8c36804-6760-4f43-a4bf-c08a8cfd9cec ro quiet splash
[    12.676] Build Date: 30 August 2010  03:27:10PM
[    12.676] xorg-server 2:1.9.0-0ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    12.676] Current version of pixman: 0.18.2
[    12.676]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    12.676] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.676] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct  2 12:17:45 2010
[    12.677] (==) Using config file: "/etc/X11/xorg.conf"
[    12.677] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.679] (==) ServerLayout "aticonfig Layout"
[    12.679] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    12.679] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    12.679] (**) |   |-->Device "aticonfig-Device[0]-0"
[    12.679] (==) Automatically adding devices
[    12.679] (==) Automatically enabling devices
[    12.679] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.679]     Entry deleted from font path.
[    12.679] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    12.679] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    12.679] (**) Extension "DAMAGE" is enabled
[    12.679] (**) Extension "Composite" is enabled
[    12.679] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    12.679] (II) Loader magic: 0x81f8e00
[    12.679] (II) Module ABI versions:
[    12.679]     X.Org ANSI C Emulation: 0.4
[    12.679]     X.Org Video Driver: 8.0
[    12.680]     X.Org XInput driver : 11.0
[    12.680]     X.Org Server Extension : 4.0
[    12.680] (--) PCI:*(0:2:0:0) 1002:68d9:1682:3050 rev 0, Mem @ 0xd0000000/268435456, 0xfeac0000/131072, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[    12.680] (II) Open ACPI successful (/var/run/acpid.socket)
[    12.680] (II) "extmod" will be loaded by default.
[    12.680] (II) "dbe" will be loaded by default.
[    12.680] (II) "glx" will be loaded by default.
[    12.680] (II) "record" will be loaded by default.
[    12.680] (II) "dri" will be loaded by default.
[    12.681] (II) "dri2" will be loaded by default.
[    12.681] (II) LoadModule: "extmod"
[    12.701] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    12.701] (II) Module extmod: vendor="X.Org Foundation"
[    12.701]     compiled for 1.9.0, module version = 1.0.0
[    12.701]     Module class: X.Org Server Extension
[    12.701]     ABI class: X.Org Server Extension, version 4.0
[    12.701] (II) Loading extension MIT-SCREEN-SAVER
[    12.701] (II) Loading extension XFree86-VidModeExtension
[    12.701] (II) Loading extension XFree86-DGA
[    12.701] (II) Loading extension DPMS
[    12.701] (II) Loading extension XVideo
[    12.701] (II) Loading extension XVideo-MotionCompensation
[    12.701] (II) Loading extension X-Resource
[    12.701] (II) LoadModule: "dbe"
[    12.701] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    12.701] (II) Module dbe: vendor="X.Org Foundation"
[    12.701]     compiled for 1.9.0, module version = 1.0.0
[    12.701]     Module class: X.Org Server Extension
[    12.701]     ABI class: X.Org Server Extension, version 4.0
[    12.701] (II) Loading extension DOUBLE-BUFFER
[    12.701] (II) LoadModule: "glx"
[    12.701] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[    12.701] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    12.701]     compiled for 7.6.0, module version = 1.0.0
[    12.701] (II) Loading extension GLX
[    12.701] (II) LoadModule: "record"
[    12.702] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    12.702] (II) Module record: vendor="X.Org Foundation"
[    12.702]     compiled for 1.9.0, module version = 1.13.0
[    12.702]     Module class: X.Org Server Extension
[    12.702]     ABI class: X.Org Server Extension, version 4.0
[    12.702] (II) Loading extension RECORD
[    12.702] (II) LoadModule: "dri"
[    12.702] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    12.702] (II) Module dri: vendor="X.Org Foundation"
[    12.702]     compiled for 1.9.0, module version = 1.0.0
[    12.702]     ABI class: X.Org Server Extension, version 4.0
[    12.702] (II) Loading extension XFree86-DRI
[    12.702] (II) LoadModule: "dri2"
[    12.702] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    12.702] (II) Module dri2: vendor="X.Org Foundation"
[    12.702]     compiled for 1.9.0, module version = 1.2.0
[    12.702]     ABI class: X.Org Server Extension, version 4.0
[    12.702] (II) Loading extension DRI2
[    12.702] (II) LoadModule: "fglrx"
[    12.703] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    12.837] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    12.850]     compiled for 1.4.99.906, module version = 8.78.30
[    12.850]     Module class: X.Org Video Driver
[    12.861] (II) Loading sub module "fglrxdrm"
[    12.861] (II) LoadModule: "fglrxdrm"
[    12.861] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    12.874] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    12.874]     compiled for 1.8.99.905, module version = 8.78.30
[    12.874] (II) ATI Proprietary Linux Driver Version Identifier:8.78.30
[    12.874] (II) ATI Proprietary Linux Driver Release Identifier: 8.78.3                               
[    12.874] (II) ATI Proprietary Linux Driver Build Date: Sep 20 2010 21:30:49
[    12.874] (++) using VT number 7

[    12.880] (WW) Falling back to old probe method for fglrx
[    12.914] (II) Loading PCS database from /etc/ati/amdpcsdb
[    12.915] (--) Assigning device section with no busID to primary device
[    12.915] (--) Chipset Supported AMD Graphics Processor (0x68D9) found
[    12.915] (WW) fglrx: No matching Device section for instance (BusID PCI:0@2:0:1) found
[    12.915] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    12.916] (II) AMD Video driver is signed
[    12.916] (II) fglrx(0): pEnt->device->identifier=0x9185540
[    12.916] (II) fglrx(0): === [xdl_x760_atiddxPreInit] === begin
[    12.916] (II) Loading sub module "vgahw"
[    12.916] (II) LoadModule: "vgahw"
[    12.917] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    12.917] (II) Module vgahw: vendor="X.Org Foundation"
[    12.917]     compiled for 1.9.0, module version = 0.1.0
[    12.917]     ABI class: X.Org Video Driver, version 8.0
[    12.917] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    12.917] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    12.917] (==) fglrx(0): Default visual is TrueColor
[    12.917] (**) fglrx(0): Option "NoAccel" "no"
[    12.917] (**) fglrx(0): Option "NoDRI" "no"
[    12.917] (**) fglrx(0): Option "DPMS" "true"
[    12.917] (==) fglrx(0): RGB weight 888
[    12.917] (II) fglrx(0): Using 8 bits per RGB 
[    12.917] (==) fglrx(0): Buffer Tiling is ON
[    12.917] (II) Loading sub module "fglrxdrm"
[    12.917] (II) LoadModule: "fglrxdrm"
[    12.918] (II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    12.919] ukiDynamicMajor: found major device number 250
[    12.919] ukiDynamicMajor: found major device number 250
[    12.919] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    12.919] ukiOpenDevice: node name is /dev/ati/card0
[    12.919] ukiOpenDevice: open result is 11, (OK)
[    12.919] ukiOpenByBusid: ukiOpenMinor returns 11
[    12.919] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    12.919] (**) fglrx(0): NoAccel = NO
[    12.919] (**) fglrx(0): ATI 2D Acceleration Architecture enabled
[    12.919] (--) fglrx(0): Chipset: "ATI Radeon HD 5570" (Chipset = 0x68d9)
[    12.919] (--) fglrx(0): (PciSubVendor = 0x1682, PciSubDevice = 0x3050)
[    12.919] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    12.919] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    12.919] (--) fglrx(0): MMIO registers at 0xfeac0000
[    12.919] (--) fglrx(0): I/O port at 0x0000e000
[    12.919] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    12.931] (II) fglrx(0): AC Adapter is used
[    12.944] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    13.038] (II) Loading sub module "vbe"
[    13.038] (II) LoadModule: "vbe"
[    13.117] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    13.125] (II) Module vbe: vendor="X.Org Foundation"
[    13.125]     compiled for 1.9.0, module version = 1.1.0
[    13.125]     ABI class: X.Org Video Driver, version 8.0
[    13.125] (II) fglrx(0): VESA BIOS detected
[    13.125] (II) fglrx(0): VESA VBE Version 3.0
[    13.125] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    13.125] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    13.125] (II) fglrx(0): VESA VBE OEM Software Rev: 12.20
[    13.125] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    13.125] (II) fglrx(0): VESA VBE OEM Product: REDWOOD
[    13.125] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    13.152] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    13.152] (--) fglrx(0): Video RAM: 1048576 kByte, Type: DDR3
[    13.152] (II) fglrx(0): PCIE card detected
[    13.152] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    13.152] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    13.154] (II) fglrx(0): Using adapter: 2:0.0.
[    13.186] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    13.246] (II) fglrx(0): Interrupt handler installed at IRQ 67.
[    13.246] (II) fglrx(0): RandR 1.2 support is enabled!
[    13.246] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    13.246] (==) fglrx(0): Center Mode is disabled 
[    13.246] (II) Loading sub module "fb"
[    13.246] (II) LoadModule: "fb"
[    13.246] (II) Loading /usr/lib/xorg/modules/libfb.so
[    13.246] (II) Module fb: vendor="X.Org Foundation"
[    13.246]     compiled for 1.9.0, module version = 1.0.0
[    13.247]     ABI class: X.Org ANSI C Emulation, version 0.4
[    13.247] (==) fglrx(0): Active stereo disabled
[    13.247] (II) Loading sub module "ddc"
[    13.247] (II) LoadModule: "ddc"
[    13.247] (II) Module "ddc" already built-in
[    13.410] (II) fglrx(0): Finished Initialize PPLIB!
[    13.412] (II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
[    13.412] (II) fglrx(0): Output DFP2 has no monitor section
[    13.412] (II) fglrx(0): Output DFP3 has no monitor section
[    13.412] (II) fglrx(0): Output CRT1 has no monitor section
[    13.412] (II) Loading sub module "ddc"
[    13.412] (II) LoadModule: "ddc"
[    13.412] (II) Module "ddc" already built-in
[    13.412] (II) fglrx(0): Connected Display0: DFP3
[    13.412] (II) fglrx(0): Display0 EDID data ---------------------------
[    13.412] (II) fglrx(0): Manufacturer: HSD  Model: 11  Serial#: 1333
[    13.412] (II) fglrx(0): Year: 2007  Week: 48
[    13.412] (II) fglrx(0): EDID Version: 1.3
[    13.412] (II) fglrx(0): Digital Display Input
[    13.412] (II) fglrx(0): Max Image Size [cm]: horiz.: 37  vert.: 23
[    13.412] (II) fglrx(0): Gamma: 2.20
[    13.412] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[    13.412] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    13.412] (II) fglrx(0): First detailed timing is preferred mode
[    13.412] (II) fglrx(0): redX: 0.643 redY: 0.325   greenX: 0.295 greenY: 0.616
[    13.412] (II) fglrx(0): blueX: 0.143 blueY: 0.081   whiteX: 0.310 whiteY: 0.330
[    13.412] (II) fglrx(0): Supported established timings:
[    13.412] (II) fglrx(0): 720x400@70Hz
[    13.412] (II) fglrx(0): 640x480@60Hz
[    13.412] (II) fglrx(0): 640x480@67Hz
[    13.412] (II) fglrx(0): 640x480@72Hz
[    13.412] (II) fglrx(0): 640x480@75Hz
[    13.412] (II) fglrx(0): 800x600@56Hz
[    13.412] (II) fglrx(0): 800x600@60Hz
[    13.412] (II) fglrx(0): 800x600@72Hz
[    13.412] (II) fglrx(0): 800x600@75Hz
[    13.412] (II) fglrx(0): 832x624@75Hz
[    13.412] (II) fglrx(0): 1024x768@60Hz
[    13.412] (II) fglrx(0): 1024x768@70Hz
[    13.412] (II) fglrx(0): 1024x768@75Hz
[    13.412] (II) fglrx(0): 1280x1024@75Hz
[    13.412] (II) fglrx(0): 1152x864@75Hz
[    13.412] (II) fglrx(0): Manufacturer's mask: 0
[    13.412] (II) fglrx(0): Supported standard timings:
[    13.412] (II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    13.412] (II) fglrx(0): #1: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    13.412] (II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    13.412] (II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    13.412] (II) fglrx(0): #4: hsize: 1024  vsize 768  refresh: 66  vid: 18017
[    13.412] (II) fglrx(0): #5: hsize: 1400  vsize 1050  refresh: 75  vid: 20368
[    13.412] (II) fglrx(0): #6: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    13.412] (II) fglrx(0): Supported detailed timing:
[    13.412] (II) fglrx(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
[    13.412] (II) fglrx(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
[    13.412] (II) fglrx(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
[    13.412] (II) fglrx(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[    13.412] (II) fglrx(0): Serial No: 748NH3NA01333
[    13.412] (II) fglrx(0): Monitor name: Hanns.G HW173
[    13.412] (II) fglrx(0): EDID (in hex):
[    13.412] (II) fglrx(0):     00ffffffffffff002264110035050000
[    13.412] (II) fglrx(0):     3011010380251778ea9bb6a4534b9d24
[    13.412] (II) fglrx(0):     144f54bfef80818081c08140714f6146
[    13.412] (II) fglrx(0):     904f950f01019a29a0d0518422305098
[    13.412] (II) fglrx(0):     360098ff1000001e000000fd00374b1e
[    13.412] (II) fglrx(0):     530e0101010101010101000000ff0037
[    13.412] (II) fglrx(0):     34384e48334e413031333333000000fc
[    13.412] (II) fglrx(0):     0048616e6e732e4720485731373300b0
[    13.413] (II) fglrx(0): End of Display0 EDID data --------------------
[    13.426] (II) fglrx(0): Output DFP1 disconnected
[    13.426] (II) fglrx(0): Output DFP2 disconnected
[    13.426] (II) fglrx(0): Output DFP3 connected
[    13.426] (II) fglrx(0): Output CRT1 disconnected
[    13.426] (II) fglrx(0): Using exact sizes for initial modes
[    13.426] (II) fglrx(0): Output DFP3 using initial mode 1440x900
[    13.426] (II) fglrx(0): DPI set to (96, 96)
[    13.426] (II) fglrx(0): Eyefinity capable adapter detected.
[    13.426] (II) fglrx(0): Adapter ATI Radeon HD 5570 has 3 configurable heads and 1 displays connected.
[    13.426] (==) fglrx(0):  PseudoColor visuals disabled
[    13.426] (II) Loading sub module "ramdac"
[    13.426] (II) LoadModule: "ramdac"
[    13.426] (II) Module "ramdac" already built-in
[    13.426] (**) fglrx(0): NoDRI = NO
[    13.426] (==) fglrx(0): Capabilities: 0x00000000
[    13.426] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    13.426] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    13.426] (==) fglrx(0): UseFastTLS=0
[    13.426] (==) fglrx(0): BlockSignalsOnLock=1
[    13.426] (--) Depth 24 pixmap format is 32 bpp
[    13.426] (II) Loading extension ATIFGLRXDRI
[    13.426] (II) fglrx(0): doing swlDriScreenInit
[    13.426] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    13.427] ukiDynamicMajor: found major device number 250
[    13.427] ukiDynamicMajor: found major device number 250
[    13.427] ukiDynamicMajor: found major device number 250
[    13.427] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    13.427] ukiOpenDevice: node name is /dev/ati/card0
[    13.427] ukiOpenDevice: open result is 17, (OK)
[    13.427] ukiOpenByBusid: ukiOpenMinor returns 17
[    13.427] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    13.427] (II) fglrx(0): [uki] DRM interface version 1.0
[    13.427] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:2:0:0"
[    13.427] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    13.427] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0xb77d3000
[    13.427] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    13.427] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    13.427] (II) fglrx(0): swlDriScreenInit done
[    13.427] (II) fglrx(0): Kernel Module Version Information:
[    13.427] (II) fglrx(0):     Name: fglrx
[    13.427] (II) fglrx(0):     Version: 8.78.30
[    13.427] (II) fglrx(0):     Date: Sep 20 2010
[    13.427] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    13.427] (II) fglrx(0): Kernel Module version matches driver.
[    13.427] (II) fglrx(0): Kernel Module Build Time Information:
[    13.427] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.35-19-generic
[    13.427] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    13.427] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    13.427] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    13.427] (II) fglrx(0): [uki] register handle = 0x00004000
[    13.439] (II) fglrx(0): Display width adjusted to to 1536 due to alignment constraints
[    13.439] (II) fglrx(0): DRI initialization successfull
[    13.439] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x010e0000
[    13.440] (II) fglrx(0): FBMM initialized for area (0,0)-(1536,2880)
[    13.440] (II) fglrx(0): FBMM auto alloc for area (0,0)-(1536,1536) (front color buffer - assumption)
[    13.440] (II) fglrx(0): Largest offscreen area available: 1536 x 1344
[    13.440] (==) fglrx(0): Backing store disabled
[    13.440] (II) Loading extension FGLRXEXTENSION
[    13.440] (**) fglrx(0): DPMS enabled
[    13.440] (II) fglrx(0): Initialized in-driver Xinerama extension
[    13.440] (**) fglrx(0): Textured Video is enabled.
[    13.440] (II) LoadModule: "glesx"
[    13.440] (II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
[    13.567] (II) Module glesx: vendor="X.Org Foundation"
[    13.567]     compiled for 1.8.99.905, module version = 1.0.0
[    13.567] (II) Loading extension GLESX
[    13.567] (II) fglrx(0): GLESX enableFlags = 592
[    13.567] (II) fglrx(0): GLESX is enabled
[    13.567] (II) fglrx(0): Acceleration enabled
[    13.567] (II) LoadModule: "amdxmm"
[    13.567] (II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
[    13.574] (II) Module amdxmm: vendor="X.Org Foundation"
[    13.574]     compiled for 1.8.99.905, module version = 1.0.0
[    13.634] (II) Loading extension AMDXVOPL
[    13.645] (II) fglrx(0): UVD2 feature is available
[    13.646] (II) fglrx(0): Enable composite support successfully
[    13.646] (II) fglrx(0): X context handle = 0x1
[    13.646] (II) fglrx(0): [DRI] installation complete
[    13.646] (==) fglrx(0): Silken mouse enabled
[    13.647] (==) fglrx(0): Using HW cursor of display infrastructure!
[    13.647] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    13.711] (--) RandR disabled
[    13.711] (II) Initializing built-in extension Generic Event Extension
[    13.711] (II) Initializing built-in extension SHAPE
[    13.711] (II) Initializing built-in extension MIT-SHM
[    13.711] (II) Initializing built-in extension XInputExtension
[    13.711] (II) Initializing built-in extension XTEST
[    13.711] (II) Initializing built-in extension BIG-REQUESTS
[    13.711] (II) Initializing built-in extension SYNC
[    13.711] (II) Initializing built-in extension XKEYBOARD
[    13.711] (II) Initializing built-in extension XC-MISC
[    13.711] (II) Initializing built-in extension SECURITY
[    13.711] (II) Initializing built-in extension XINERAMA
[    13.711] (II) Initializing built-in extension XFIXES
[    13.711] (II) Initializing built-in extension RENDER
[    13.711] (II) Initializing built-in extension RANDR
[    13.711] (II) Initializing built-in extension COMPOSITE
[    13.711] (II) Initializing built-in extension DAMAGE
[    13.711] (II) Initializing built-in extension GESTURE
[    13.714] ukiDynamicMajor: found major device number 250
[    13.714] ukiDynamicMajor: found major device number 250
[    13.714] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    13.714] ukiOpenDevice: node name is /dev/ati/card0
[    13.714] ukiOpenDevice: open result is 18, (OK)
[    13.714] ukiOpenByBusid: ukiOpenMinor returns 18
[    13.714] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    14.166] (II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
[    14.166] (II) GLX: Initialized DRI GL provider for screen 0
[    14.217] (II) fglrx(0): Enable the clock gating!
[    14.217] (II) fglrx(0): Setting screen physical size to 380 x 238
[    14.244] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    14.250] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    14.250] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.250] (II) LoadModule: "evdev"
[    14.251] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.251] (II) Module evdev: vendor="X.Org Foundation"
[    14.251]     compiled for 1.9.0, module version = 2.3.2
[    14.251]     Module class: X.Org XInput Driver
[    14.251]     ABI class: X.Org XInput driver, version 11.0
[    14.251] (**) Power Button: always reports core events
[    14.251] (**) Power Button: Device: "/dev/input/event2"
[    14.264] (II) Power Button: Found keys
[    14.264] (II) Power Button: Configuring as keyboard
[    14.264] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    14.264] (**) Option "xkb_rules" "evdev"
[    14.264] (**) Option "xkb_model" "pc105"
[    14.264] (**) Option "xkb_layout" "us"
[    14.265] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    14.265] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.265] (**) Power Button: always reports core events
[    14.265] (**) Power Button: Device: "/dev/input/event1"
[    14.280] (II) Power Button: Found keys
[    14.280] (II) Power Button: Configuring as keyboard
[    14.280] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    14.280] (**) Option "xkb_rules" "evdev"
[    14.280] (**) Option "xkb_model" "pc105"
[    14.280] (**) Option "xkb_layout" "us"
[    14.280] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    14.280] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    14.280] (**) Sleep Button: always reports core events
[    14.280] (**) Sleep Button: Device: "/dev/input/event0"
[    14.296] (II) Sleep Button: Found keys
[    14.296] (II) Sleep Button: Configuring as keyboard
[    14.296] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    14.296] (**) Option "xkb_rules" "evdev"
[    14.296] (**) Option "xkb_model" "pc105"
[    14.296] (**) Option "xkb_layout" "us"
[    14.298] (II) config/udev: Adding input device HID 04b3:310b (/dev/input/event4)
[    14.298] (**) HID 04b3:310b: Applying InputClass "evdev pointer catchall"
[    14.298] (**) HID 04b3:310b: always reports core events
[    14.298] (**) HID 04b3:310b: Device: "/dev/input/event4"
[    14.312] (II) HID 04b3:310b: Found 3 mouse buttons
[    14.312] (II) HID 04b3:310b: Found scroll wheel(s)
[    14.312] (II) HID 04b3:310b: Found relative axes
[    14.312] (II) HID 04b3:310b: Found x and y relative axes
[    14.312] (II) HID 04b3:310b: Configuring as mouse
[    14.312] (**) HID 04b3:310b: YAxisMapping: buttons 4 and 5
[    14.312] (**) HID 04b3:310b: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    14.312] (II) XINPUT: Adding extended input device "HID 04b3:310b" (type: MOUSE)
[    14.312] (II) HID 04b3:310b: initialized for relative axes.
[    14.312] (II) config/udev: Adding input device HID 04b3:310b (/dev/input/mouse0)
[    14.312] (II) No input driver/identifier specified (ignoring)
[    14.313] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    14.313] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    14.313] (**) AT Translated Set 2 keyboard: always reports core events
[    14.313] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    14.328] (II) AT Translated Set 2 keyboard: Found keys
[    14.328] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    14.328] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    14.328] (**) Option "xkb_rules" "evdev"
[    14.328] (**) Option "xkb_model" "pc105"
[    14.328] (**) Option "xkb_layout" "us"
[    14.336] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    14.902] (II) fglrx(0): EDID vendor "HSD", prod id 17
[    14.902] (II) fglrx(0): Using EDID range info for horizontal sync
[    14.902] (II) fglrx(0): Using EDID range info for vertical refresh
[    14.910] (II) fglrx(0): EDID vendor "HSD", prod id 17
[    14.910] (II) fglrx(0): Using hsync ranges from config file
[    14.910] (II) fglrx(0): Using vrefresh ranges from config file
[    14.917] (II) fglrx(0): EDID vendor "HSD", prod id 17
[    14.917] (II) fglrx(0): Using hsync ranges from config file
[    14.917] (II) fglrx(0): Using vrefresh ranges from config file
[    15.276] (II) fglrx(0): EDID vendor "HSD", prod id 17
[    15.276] (II) fglrx(0): Using hsync ranges from config file
[    15.276] (II) fglrx(0): Using vrefresh ranges from config file
[    20.054] (II) fglrx(0): EDID vendor "HSD", prod id 17
[    20.054] (II) fglrx(0): Using hsync ranges from config file
[    20.054] (II) fglrx(0): Using vrefresh ranges from config file
[   630.420] (II) fglrx(0): EDID vendor "HSD", prod id 17
[   630.420] (II) fglrx(0): Using hsync ranges from config file
[   630.420] (II) fglrx(0): Using vrefresh ranges from config file

```

---

### Post by Insidious611 on 2010-10-03
Uhm, I'm not usually the kind of person who bumps threads, considering thats generally considered very bad forum manners, but the fact the entire forum completely ignored this thread annoys me more than a little? I mean, 10.10 is a beta, right? That means you're supposed to be looking for my feedback, right? Well, this is some feedback. 3D working is a pretty important issue to me...


I mean, I thought I provided a pretty good amount of information... So why don't I get a single reply? For 7 pages, at that?

---

### Post by jetpeach on 2010-10-13
I probably can't help much, but have you tried renaming your xorg.conf completely, then using "sudo aticonfig --initial" (or with the various options) to make a completely new one?

I'm experienced bugs with my AMD/ATI drivers in Meerkat as well - they are an early release of the Catalyst drivers and the first version to ever support Xserver 1.9, so I'm sorry to say but i think there are just a lot of bugs with these drivers...

---

### Post by alphacrucis2 on 2010-10-13
> **jetpeach said:**
> I probably can't help much, but have you tried renaming your xorg.conf completely, then using "sudo aticonfig --initial" (or with the various options) to make a completely new one?

I'm experienced bugs with my AMD/ATI drivers in Meerkat as well - they are an early release of the Catalyst drivers and the first version to ever support Xserver 1.9, so I'm sorry to say but i think there are just a lot of bugs with these drivers...

AMD should be releasing the proper release of Catalyst 10.10 before the end of the month. That might include additional bug fixes.

---

### Post by lstefek on 2010-10-15
I have ATi Radeon HD5570 too, but I'm not able to get it working with fglrx driver on ubuntu10.10 at all. Freezes when X starts. 
The same problem with 10.04. (I was using it with vesa driver only)
How did you install the driver? Different repository?

---

### Post by 0004tom on 2010-10-15
Working fine for me, I'm using the 10.10 drivers also, but have a 5450

```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: ATI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
client glx vendor string: ATI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_NV_swap_group, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_swap_barrier, GLX_SGIX_swap_group, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB, GLX_ARB_fbconfig_float, GLX_AMD_gpu_association
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
    GLX_NV_swap_group, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_swap_barrier, 
    GLX_SGIX_swap_group, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5450
OpenGL version string: 4.0.10237 Compatibility Profile Context
OpenGL shading language version string: 4.00
OpenGL extensions:
    GL_AMDX_debug_output, GL_AMDX_vertex_shader_tessellator, 
    GL_AMD_conservative_depth, GL_AMD_debug_output, GL_AMD_draw_buffers_blend, 
    GL_AMD_name_gen_delete, GL_AMD_performance_monitor, 
    GL_AMD_sample_positions, GL_AMD_seamless_cubemap_per_texture, 
    GL_AMD_shader_stencil_export, GL_AMD_texture_cube_map_array, 
    GL_AMD_texture_texture4, GL_AMD_transform_feedback3_lines_triangles, 
    GL_AMD_vertex_shader_tessellator, GL_ARB_blend_func_extended, 
    GL_ARB_color_buffer_float, GL_ARB_copy_buffer, GL_ARB_depth_buffer_float, 
    GL_ARB_depth_clamp, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_draw_buffers_blend, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_draw_indirect, GL_ARB_draw_instanced, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_framebuffer_sRGB, GL_ARB_geometry_shader4, GL_ARB_gpu_shader5, 
    GL_ARB_gpu_shader_fp64, GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_imaging, GL_ARB_instanced_arrays, GL_ARB_map_buffer_range, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_occlusion_query2, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_provoking_vertex, 
    GL_ARB_sample_shading, GL_ARB_sampler_objects, GL_ARB_seamless_cube_map, 
    GL_ARB_shader_atomic_counters, GL_ARB_shader_bit_encoding, 
    GL_ARB_shader_objects, GL_ARB_shader_subroutine, 
    GL_ARB_shader_texture_lod, GL_ARB_shading_language_100, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_sync, GL_ARB_tessellation_shader, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_buffer_object, 
    GL_ARB_texture_compression, GL_ARB_texture_compression_rgtc, 
    GL_ARB_texture_cube_map, GL_ARB_texture_cube_map_array, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_gather, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_multisample, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_query_lod, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, 
    GL_ARB_texture_snorm, GL_ARB_timer_query, GL_ARB_transform_feedback2, 
    GL_ARB_transform_feedback3, GL_ARB_transpose_matrix, 
    GL_ARB_uniform_buffer_object, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_ARB_window_pos, GL_ATI_draw_buffers, 
    GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, GL_ATI_meminfo, 
    GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_bindable_uniform, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_buffer, GL_EXT_copy_texture, GL_EXT_direct_state_access, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_sRGB, 
    GL_EXT_geometry_shader4, GL_EXT_gpu_program_parameters, 
    GL_EXT_gpu_shader4, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_float, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_provoking_vertex, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_buffer_object_rgb32, GL_EXT_texture_compression_bptc, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_integer, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_shared_exponent, GL_EXT_texture_snorm, 
    GL_EXT_texture_swizzle, GL_EXT_timer_query, GL_EXT_transform_feedback, 
    GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, GL_EXT_vertex_attrib_64bit, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, 
    GL_NV_explicit_multisample, GL_NV_float_buffer, GL_NV_half_float, 
    GL_NV_primitive_restart, GL_NV_texgen_reflection, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays, 
    GL_WIN_swap_hint, WGL_EXT_swap_control

65 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x023 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x024 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x025 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x026 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x027 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x028 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x029 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x02a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x02b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x02c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x02d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x02e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x02f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x030 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x031 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x032 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x033 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x034 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x035 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x036 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x037 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x038 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x039 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x03a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x03b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x03c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x03d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x03e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x043 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x044 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x045 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x046 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x04b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x04c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x04d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x04e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x04f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x050 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x051 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x052 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x053 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x054 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x055 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x056 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x057 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x058 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x059 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x05a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x05b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x05c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x05d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x05e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x05f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x060 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x061 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x062 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x063 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x064 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x065 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x066 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x06b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x06c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x06d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x06e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x0ac 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 Ncon

75 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x023 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x024 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x025 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x026 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x027 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x028 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x029 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x02a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x02b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x02c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x02d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x02e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x02f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x030 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x031 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x032 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x033 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x034 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x035 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x036 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x037 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x038 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x039 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x03a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x03b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x03c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x03d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x03e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x043 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x044 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x045 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x046 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x04b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x04c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x04d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x04e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x04f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x050 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x051 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x052 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x053 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x054 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x055 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x056 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x057 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x058 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x059 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x05a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x05b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x05c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x05d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x05e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x05f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x060 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x061 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x062 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x063 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x064 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x065 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x066 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x06b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x06c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x06d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x06e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x0ac 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 Ncon
0x0ac 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 Ncon
0x0ac 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 Ncon
0x0ac 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 Ncon
0x0ac 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 Ncon
0x0ac  0 tc  0 128  0    y .  32 32 32 32 .  .  0 24  0  0  0  0  0  0 0 None
0x0ac  0 tc  0 128  0    . .  32 32 32 32 .  .  0 24  0  0  0  0  0  0 0 None
0x0ac  0 tc  0  64  0    y .  16 16 16 16 .  .  0 24  0  0  0  0  0  0 0 None
0x0ac  0 tc  0  64  0    . .  16 16 16 16 .  .  0 24  0  0  0  0  0  0 0 None
0x0ac  0 tc  0  32  0    y .  11 11 10  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0ac  0 tc  0  32  0    . .  11 11 10  0 .  .  0 24  0  0  0  0  0  0 0 None
```

Altho it was a pain getting the drivers to work. They worked flawlessly in the beta, had to fight with my system to get them working with the release.

---

### Post by SeePU on 2010-10-21
> **0004tom said:**
> Working fine for me, I'm using the 10.10 drivers also, but have a 5450

Altho it was a pain getting the drivers to work. They worked flawlessly in the beta, had to fight with my system to get them working with the release.
Had to fight with them how?

You mean you had to recompile almost every video program you want to use, that kind of fighting?  Then you had to jump over hoops and do headstands until the drivers worked?   That kind of fighting?  

ATI is pure Windows.  Soon, some more changes and then they won't work again.

---

### Post by sleepingdragon on 2010-10-30
I am getting the exact same problem using a HD3450 - no fglrxinfo, glxgears all freeze up on me. Video seems to be working well enough and the computer is certainly responsive, but 3D is certainly a no-no.

> 
fglrxinfo:
-- that's as far as it gets.

Here's my xorg.conf:

> 
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
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
    BusID       "PCI:2:0:0"
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
Pretty much the same as yours, and it certainly doesn't create any problems. Since this is a new machine, it's just the final piece of the puzzle to making this a great desktop, but it is a BIG flaw.

---

### Post by 0004tom on 2010-11-07
> **SeePU said:**
> Had to fight with them how?

You mean you had to recompile almost every video program you want to use, that kind of fighting?  Then you had to jump over hoops and do headstands until the drivers worked?   That kind of fighting?  

ATI is pure Windows.  Soon, some more changes and then they won't work again.

LOL pretty much yeah, but no normally I would just install then restart, and I would have one screen running, I have 3 monitors, notmally would be the DVI port monitor running, then I would just run amdcccle, set up my "eyefinity group" it would say I reboot is required for the changes to take effect, reboot and I would be happy everything running.

With the drivers in MeerKat I had to run aticonfig --inital-dualhead and go from there. I know it's a step ATi and everyone says to use, however this was the first time I have ever needed to do this.

---

