---
title: "ATi Catalyst 9.6 released"
date: 2009-06-15
forum: Multimedia Software
---

### Post by DangerIsGo on 2009-06-15
I just saw that ATi released Catalyst 9.6.  Anyone give this a try and see if it works with a 4870x2?  I might try it later depending on time.

According to the release notes:

> [Ubuntu 9.04] Xserver now starts properly with ATI Radeon HD 4870 GPU configurations 

EDIT: I just installed a fresh copy of Jaunty, then installed 9.6 with my 4870x2 and upon reboot, everything works!  Anyone else get this success?  It only took ATi 3 months, but hey, better late than never!

---

### Post by UnicycleBloke on 2009-06-16
I installed it this morning for my ATI Radeon HD 3650 AGP. It seems to work OK. Compiz eye candy fine, and I gave Nexuiz a spin. Early days though.

I got nowhere with the Xorg drivers last night. Not that I was expecting to: 2D support works, but 3D is still WIP. I also got in a tizzy when trying to install fglrx through the Synaptic Package Manager. And the restricted drivers thing seems to conflict with the downloaded installer.

So I downloaded the driver from [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English) and followed the instructions provided there. Installation was a breeze, and Control Centre seemed simple enough. So far so good.

This card is a compromise upgrade for me: I needed AGP and didn't need cutting edge. It's fantastic compared to the Radeon 8500 I had before, but I haven't done any frame rate tests or anything yet.


Unicycle Bloke

---

### Post by Pitboss on 2009-06-16
I just tried the new driver and it totally sucks. The problem with maximizing windows is still present.

Damn.

---

### Post by sanumala on 2009-06-16
> **Pitboss said:**
> I just tried the new driver and it totally sucks. The problem with maximizing windows is still present.
 
Damn.
 
 
Good to see ur response. I thogught of trying this one. Now i dont install this new one ;)

---

### Post by nicobeukes on 2009-06-16
Can this be !

I also have a sapphire 4870x2 gpu and wanted to try 9.04 for so long but had to go back to 8.10, I needed fglrx to work to get the gpu temp down

Did you have to do a aticonfig --initial -f to set it up or did you just reboot, with 8.10 i did not have to do the aticonfig --initial -f and all was ok after the reboot.

In case you do not know this,"thought I give you a hint"

If you do a aticonfig --pplib-cmd "set fanspeed 0 50" it will let your fanspeed run at 50% and your card runs nice and cool, 40 is a lot less noisy

Please advise on above, I realy want to try 9.04

---

### Post by csaw on 2009-06-16
Well for me it's a partial success - 4870X2 boots up & I can login but no compiz :-(. fglrxinfo says all ok but xorg.0.logs says 

[FONT="Courier New"](WW) AIGLX: 3D driver claims to not support visual xxxx[/FONT]

where xxx starts at 0x23 & goes up to 0x72

compiz-check states [FONT="Courier New"]'Error: No rendering method in use (AIGLX, Xgl or Nvidia)[/FONT]'

I can at least play 'World Of Goo' which is a major result!

---

### Post by markbuntu on 2009-06-16
Try this, in the ServerLayout section of xorg.conf add 

Options "AIGLX" "on"

---

### Post by cartman_ on 2009-06-16
It is still a no go for the Asus M51Ta laptop (integrated HD 3200 & Mobility HD 3650) - got a garbled screen after the boot progress bar.

Xorg.0.log says:
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux cartman-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun 16 23:21:49 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "aticonfig Layout"
(**) |-->Screen "aticonfig-Screen[0]-0" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]-0"
(**) |   |-->Device "aticonfig-Device[0]-0"
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0xb40
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:5:0) ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] rev 0, Mem @ 0xb0000000/268435456, 0xfdcf0000/65536, 0xfdb00000/1048576, I/O @ 0x0000b000/256
(--) PCI: (0@2:0:0) ATI Technologies Inc Mobility Radeon HD 3650 rev 0, Mem @ 0xc0000000/536870912, 0xfddf0000/65536, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [30] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [31] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [32] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [33] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [34] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [35] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 7.4.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 7.4.0, module version = 1.0.0
(II) Loading extension XFree86-DRI
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.4.99.906, module version = 8.62.4
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.4.99.906, module version = 8.62.4
    Module class: X.Org Video Driver
(II) Primary Device is: PCI 01@00:05:0
(WW) Falling back to old probe method for fglrx
(II) ATI Proprietary Linux Driver Version Identifier:8.62.4
(II) ATI Proprietary Linux Driver Release Identifier: 8.62                                 
(II) ATI Proprietary Linux Driver Build Date: May 20 2009 16:46:48
(II) Loading PCS database from /etc/ati/amdpcsdb
(WW) This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0
(WW) Video driver ABI version of the X server is 5.0
(WW) fglrx: No matching Device section for instance (BusID PCI:0@2:0:0) found
(--) Chipset Supported AMD Graphics Processor (0x9612) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@2:0:1) found
(**) ChipID override: 0x9591
(**) Chipset Supported AMD Graphics Processor (0x9591) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [30] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [31] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [32] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [33] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [34] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [35] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) fglrx(0): pEnt->device->identifier=0x180a270
(II) pEnt->device->identifier=(nil)
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [24] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [25] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [26] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [27] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [28] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [29] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [30] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [31] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [32] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [33] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [34] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [35] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [36] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [37] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [38] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [39] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [40] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) fglrx(0): PCI bus 1 card 5 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "true"
(II) fglrx(0): 10BitPixelFormat disabled by default
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID PCI:2:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports PCI:2:0:0
(--) fglrx(0): Chipset: "ATI Radeon HD 3200 Graphics " (Chipset = 0x9612)
(--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x1062)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xb0000000
(--) fglrx(0): MMIO registers at 0xfdcf0000
(--) fglrx(0): I/O port at 0x0000b000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): AC Adapter is used
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 10.94
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RS780M
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(--) fglrx(0): Video RAM: 262144 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): PCI bus 2 card 0 func 0
(**) fglrx(0): Chipset: "ATI Mobility Radeon HD 3650" (Chipset = 0x9591)
(**) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x1872)
(**) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xfddf0000
(--) fglrx(0): I/O port at 0x0000c000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): AC Adapter is used
(EE) fglrx(0): Invalid video BIOS signature!
(EE) fglrx(0): GetBIOSParameter failed
(EE) fglrx(0): PreInitAdapter for slave 0 failed
(II) fglrx(0): RandR 1.2 support is enabled!
(II) fglrx(0): RandR 1.2 rotation support is enabled!
(==) fglrx(0): Center Mode is disabled 
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
```I guess this is the problem:
```
(EE) fglrx(0): Invalid video BIOS signature!
(EE) fglrx(0): GetBIOSParameter failed
(EE) fglrx(0): PreInitAdapter for slave 0 failed
```:(

---

### Post by DangerIsGo on 2009-06-16
I just rebooted after installing.  I have noticed, after enabling compiz, that windows resizing or maximizing really suck.  It's very sluggish.

---

### Post by Mattaus on 2009-06-17
Hope this fixes my MythTV playback issue. But I have a funny feeling it wont.

---

### Post by wty on 2009-06-17
I have HD4850 x 2 and downloaded the drivers from ati.com. After installing the driver, I configured my screenoptions trough amdccle with dualscreens and xinerama. And after a reboot it don't work. Same as in 9.5. If I turn off xinerama it works, displays on both monitors. But yeah, to different screens. And I guess clone works as well, I haven't tried that in 9.6. 

So it's totally useless for me, as I want xinerama to work.

-wty

---

### Post by reference2myself on 2009-06-17
How do you tell what version driver you have installed.  The fglrx version doesn't seem to match the catalyst version, is there a way to tell?

---

### Post by markbuntu on 2009-06-17
> **wty said:**
> I have HD4850 x 2 and downloaded the drivers from ati.com. After installing the driver, I configured my screenoptions trough amdccle with dualscreens and xinerama. And after a reboot it don't work. Same as in 9.5. If I turn off xinerama it works, displays on both monitors. But yeah, to different screens. And I guess clone works as well, I haven't tried that in 9.6. 

So it's totally useless for me, as I want xinerama to work.

-wty

If you want to use  dual screens and xinerama with amdcccle you need to turn off xrandr. Just add this line to the "Device" section of xorg.conf.


Option	    "EnableRandR12" "false"

---

### Post by wty on 2009-06-18
> **markbuntu said:**
> If you want to use  dual screens and xinerama with amdcccle you need to turn off xrandr. Just add this line to the "Device" section of xorg.conf.


Option	    "EnableRandR12" "false"

Okei, I'll try that as soon as I'm home from work. I assume that will work on three monitors as well?

---

### Post by nicobeukes on 2009-06-18
> **nicobeukes said:**
> Can this be !

I also have a sapphire 4870x2 gpu and wanted to try 9.04 for so long but had to go back to 8.10, I needed fglrx to work to get the gpu temp down

Did you have to do a aticonfig --initial -f to set it up or did you just reboot, with 8.10 i did not have to do the aticonfig --initial -f and all was ok after the reboot.

In case you do not know this,"thought I give you a hint"

If you do a aticonfig --pplib-cmd "set fanspeed 0 50" it will let your fanspeed run at 50% and your card runs nice and cool, 40 is a lot less noisy

Please advise on above, I realy want to try 9.04

I just loaded the new 9.04 amd64bit and installed the 9.6 driver
I did not do a aticonfig --initial -f and all was well after the reboot
with compiz working straight away, now I can set my fanspeed again
U buntu 9.04 is the best, and very fast with ext4

Good luck to all out there with a 4870x2, it is the best card out there and so mutch easier to load drivers unlike nvidia

regards

---

### Post by markbuntu on 2009-06-18
> **wty said:**
> Okei, I'll try that as soon as I'm home from work. I assume that will work on three monitors as well?

I am not so sure about that but the 9.6 driver claims to be able to do that according to the release notes. I have a HD3650 PCIe and before disabling randr I was completely unable to set a big desktop with aticonfig or CCC. I am suspecting that randr and xinerama are mutually incompatible. 

Someday I would  like to add another monitor or four using my mobo's HD3300 or the 3300 and the HD3450 I also have lying around but so far I have had zero luck with that the few times I have tried it.

---

### Post by mr_raider on 2009-06-18
Anyone use it on mobility radeon 3400 series? The stock 9.04 drivers cause a crash is a fullscreen video playback with compiz enabled. Will 9.6 solve the problem? If not I'll wait until July.

Intrepid didn't really get sorted out until 9.4.

---

### Post by V!&gt;&lt;0N on 2009-06-18
Allright, I have a 4870 hd (x2?) by Diamond.  I think its the black edition maybe? 512 mb ram.  Ill give it a go and report back.   This better work or its back to my old Nvidia 6600.;)

---

### Post by V!&gt;&lt;0N on 2009-06-18
Well, first I removed my Nvidia drivers and installed xorg-driver-fglrx.  The first restart failed, but then I entered recovery and netroot, and did aticonfig --initial -f.  After that, I could get to the desktop.  However, after a few seconds or after Avant Window Navigator started, the computer froze.  So, I removed all compiz things.  Now, everything works mostly untill you move or maximize a window.  I have solved this problem in the past (8.10) by slightly underclockin the card, and to my suprize stability increased greatly.  But now, I cant find where you underclock in the amdcccle, even if I launch it as root.  So next I installed the .run file from Ati directly to see if it had the overdrive(?) section, but its the same. (I still dont see the place where you can over and underclock.)   Does anyone know how I can underclock with the Catalyst Control Center?

---

### Post by markbuntu on 2009-06-18
Well, I just had an adventure getting the 9.6 driver to run with my Hardy 64 bit UbuntuStudio and the rt kernel which has not worked since the 8.7 driver. So, it seems that the rt patch is finally in /patches instead of /patches/patches. Good news for rt kernel users! yay!

But the DKMS module build failed with the automatic installer so I had to install manually which worked. Then I had to do the Option "EnableRandR12" "false" trick to get my big desktop.

Now I can use my ubuntustudio again. For me the rt kernel will not even boot in Intrepid or Jaunty and the radeon driver is just crap in hardy.

Uh Oh, kernel updates, stand by......

If you are using fglrx it is always a good idea to watch the terminal when you get kernel updates...

UPDATE: good thing I was watching. Some drama but all is well. Compiz seems a little slow with the effects but I usually have that off anyway.

---

### Post by wty on 2009-06-19
I did some testing last night, and my problem was that I haven't added Option "EnableRandR12" "false" to one of my device inputs. After that it worked well. Even with three monitors. I have not tried with more than three, but I can't see the problem with adding more monitors.

Though compiz ain't working. But that doesn't bother me.

---

### Post by V!&gt;&lt;0N on 2009-06-19
Well, I'm still not having luck with my 4870.  With or without compiz, the computer freezes if I move anything...window, icon, etc.  Any suggestions?

Btw what is the command to safely restart ubuntu?

something like ctrl alt  and then "Raising skinny elephants isnt always boring"
does anyone know what I'm talking about? I cant remember the command.

---

### Post by jespo on 2009-06-19
I just downloaded binary from link from this thread. I had the jaunty repo drivers.
I just uninstalled with synaptic all fglrx references, and ati and radeon drivers and execute the binary with --buildpkg Ubuntu/jaunty
It generate next packages:

7646632 2009-06-19 17:37 fglrx-amdcccle_8.620-0ubuntu1_i386.deb
1605960 2009-06-19 17:37 fglrx-kernel-source_8.620-0ubuntu1_i386.deb
11250 2009-06-19 17:37 fglrx-modaliases_8.620-0ubuntu1_i386.deb
728398 2009-06-19 17:38 libamdxvba1_8.620-0ubuntu1_i386.deb
16024402 2009-06-19 17:37 xorg-driver-fglrx_8.620-0ubuntu1_i386.deb
86174 2009-06-19 17:37 xorg-driver-fglrx-dev_8.620-0ubuntu1_i386.deb

just dpkg --install all this debs, reboot and the problem of flickering videos with vlc windowed and compiz has gone :p

Now I can view videos in jaunty with my ATI HD3450 card.

---

### Post by raymondvillain on 2009-06-19
> **UnicycleBloke said:**
> I installed it this morning for my ATI Radeon HD 3650 AGP. It seems to work OK. Compiz eye candy fine, and I gave Nexuiz a spin. Early days though.

I got nowhere with the Xorg drivers last night. Not that I was expecting to: 2D support works, but 3D is still WIP. I also got in a tizzy when trying to install fglrx through the Synaptic Package Manager. And the restricted drivers thing seems to conflict with the downloaded installer.

So I downloaded the driver from [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English) and followed the instructions provided there. Installation was a breeze, and Control Centre seemed simple enough. So far so good.

This card is a compromise upgrade for me: I needed AGP and didn't need cutting edge. It's fantastic compared to the Radeon 8500 I had before, but I haven't done any frame rate tests or anything yet.


Unicycle Bloke

I too went to the ATI website, downloaded the drivers, but when I click on the "installer instructions" link it gives me a document that shows only instructions for installing on windows!

How does one install the drivers?

---

### Post by sanumala on 2009-06-19
> **nicobeukes said:**
> I just loaded the new 9.04 amd64bit and installed the 9.6 driver
I did not do a aticonfig --initial -f and all was well after the reboot
with compiz working straight away, now I can set my fanspeed again
U buntu 9.04 is the best, and very fast with ext4
 
Good luck to all out there with a 4870x2, it is the best card out there and so mutch easier to load drivers unlike nvidia
 
regards
 
 
Did you tried playing DVD's and Blu-Ray rips (.mkv) files in vlc 9.04 64bit with ur ati card???

---

### Post by wty on 2009-06-19
> **raymondvillain said:**
> I too went to the ATI website, downloaded the drivers, but when I click on the "installer instructions" link it gives me a document that shows only instructions for installing on windows!

How does one install the drivers?

Here download this one:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat96-inst.pdf]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat96-inst.pdf")

---

### Post by randyklein99 on 2009-06-19
My 4770 is working (with Extra Features turned on) with the 9.6 drivers, huge improvement.  I no longer have logout/switch users hanging problems, like I did with 9.5.

However, the initial login and initial switch, after entering the password, you get a blue background with quickly flashing black bar randomly on the screen for about 15 seconds and then you get the desktop. Switching back to a user though does not experience this flashing. Any clues on how to fix that? Or is wait until 9.7???

---

### Post by mr_raider on 2009-06-19
> **jespo said:**
> I just downloaded binary from link from this thread. I had the jaunty repo drivers.
I just uninstalled with synaptic all fglrx references, and ati and radeon drivers and execute the binary with --buildpkg Ubuntu/jaunty
It generate next packages:

7646632 2009-06-19 17:37 fglrx-amdcccle_8.620-0ubuntu1_i386.deb
1605960 2009-06-19 17:37 fglrx-kernel-source_8.620-0ubuntu1_i386.deb
11250 2009-06-19 17:37 fglrx-modaliases_8.620-0ubuntu1_i386.deb
728398 2009-06-19 17:38 libamdxvba1_8.620-0ubuntu1_i386.deb
16024402 2009-06-19 17:37 xorg-driver-fglrx_8.620-0ubuntu1_i386.deb
86174 2009-06-19 17:37 xorg-driver-fglrx-dev_8.620-0ubuntu1_i386.deb

just dpkg --install all this debs, reboot and the problem of flickering videos with vlc windowed and compiz has gone :p

Now I can view videos in jaunty with my ATI HD3450 card.

Excellent. Good to hear. What rendering method are you using for videos? x11, xv or GL?

---

### Post by raymondvillain on 2009-06-19
Many thanks, wty, for providing the correct link to the download instructions!

Finally I have graphics.

---

### Post by jespo on 2009-06-20
> **mr_raider said:**
> Excellent. Good to hear. What rendering method are you using for videos? x11, xv or GL?

I'm using OpenGL Video Output.
Just upgraded the kernel with new version and installed this morning.
I have to rebuild the .deb's but all goes ok after it.

---

### Post by mr_raider on 2009-06-20
> **jespo said:**
> I'm using OpenGL Video Output.
Just upgraded the kernel with new version and installed this morning.
I have to rebuild the .deb's but all goes ok after it.

I'm still getting flicker with Open GL in VLC or or SMplayer. XV just slows the video to a slideshow. X11 works fine though my CPU stays pegged at 100%.

Using a mobility 3410 on a AMD neo 1.6GHZ CPU.

---

### Post by DhulKarnain on 2009-06-21
is the ATI driver in Ubuntu's Hardware drivers updated to 9.6 and, if not, how will I know when it is? There really ought to be a version number in that window.

---

### Post by mr_raider on 2009-06-21
> **DhulKarnain said:**
> is the ATI driver in Ubuntu's Hardware drivers updated to 9.6 and, if not, how will I know when it is? There really ought to be a version number in that window.

Open catalyst control center and check the info tap.

9.6 is version 2d driver 8.62.4

---

### Post by markbuntu on 2009-06-21
Ubuntu does not generally update the repository driver.

---

### Post by notoriousdbp on 2009-06-21
I've got an HD3200.  Does fast user switching and logging out now work with this driver?

---

### Post by miket3115 on 2009-06-21
I installed 9.04 in safe graphical mode then downloaded the ATI driver from their web site, followed the install instructions and now all I get is a blank screen after the boot screen.  Using an HD2400 PCI card.  I can see It's trying to load but all I get is and "Out Of Range" message on my monitor. Monitor is a view sonic VA902b.  I haven't tried to roll back the driver yet in safemode.

---

### Post by markbuntu on 2009-06-21
Did you do 

aticonfig --initial

If you did not do that the driver may not work properly.

---

### Post by sroland81 on 2009-06-25
I installed Jaunty for amd64 in my HP 6735s and because "hardware drivers" thing didn't worked at all for me, i downloaded ATI Catalyst binary driver for my ATI HD 3200 card. I followed instructions and installed, now i have compiz working... BUT when i watch a video, or movie in totem it slows the PC, and the video is not continous and smooth. if i change to metacity or openbox, everything is fine... other thing is when i run compiz-check, it says that it does not have any render mechanism (AIGLX, glx, bla bla) and read that adding the Option "AIGLX" on in the device section would do something but it didn't... then i ran "sudo aticonfig --initial" and rebooted and nothing changed.... any ideas? when i installed the binary i didn't generated the .deb file... just installed the driver... but i think that it should work anyway...

thanks in advance!
Cheers!

---

### Post by markbuntu on 2009-06-25
Option "AIGLX" "on" should be placed in Section "ServerLayout"

---

### Post by sroland81 on 2009-06-25
Yes, mi mistake.... that were i added the line... and didn't worked.... now i'm generating distribution specific .deb with ATI binary installer... hope it works...!

Hey, found this place that says lot of things... can i apply some of this to a radeon HD3200?

take a look!

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

Cheers

---

### Post by sroland81 on 2009-06-25
No... i just generated distribution specific .deb packages drom the ATI driver installer and installed them with GDebi and rebooted... the machine hangs up in the login showing distorted ubuntu echoes on top with strange line patterns... what's going on?

installed the driver (but not generating debs) and now it is ok, compiz wroks... still have the same issue with video and compiz-check says no render method AIGLX, .... etc.

any ideas?
thanks.

---

### Post by xzero1 on 2009-07-22
> **mr_raider said:**
> I'm still getting flicker with Open GL in VLC or or SMplayer. XV just slows the video to a slideshow. X11 works fine though my CPU stays pegged at 100%.

Using a mobility 3410 on a AMD neo 1.6GHZ CPU.

Are you running xv *full screen* with the latest mplayer? Using xv with  3300IGP video, mplayer ( SVN-r29317-4.3.3) plays 1920x1080x24p video *with* compiz smoothly even with my cpu locked at 800Mhz speed! Apparently, the video is accelerated by the gpu, but only for full screen playback. The only issues I have noticed is compiz must be disabled to play flash videos (hulu) full screen.

Edit::D
Fixed flash fullscreen support by enabling 'Legacy Fullscreen Support under compiz workarounds and disabling and 'Unredirect Fullscreen Windows' compiz general tab . See [URL="http://www.linuxinsight.com/full-screen-flash-not-working-under-compiz.html"]http://www.linuxinsight.com/full-screen-flash-not-working-under-compiz.html.
[/URL]

---

### Post by leandromartinez98 on 2009-07-22
I have exactly the same behavior. Installation from the .run works perfectly (actually really well), but trying to install the driver
any other way results in a broken X.

---

### Post by mr_raider on 2009-08-07
> **xzero1 said:**
> Are you running xv *full screen* with the latest mplayer? Using xv with  3300IGP video, mplayer ( SVN-r29317-4.3.3) plays 1920x1080x24p video *with* compiz smoothly even with my cpu locked at 800Mhz speed! Apparently, the video is accelerated by the gpu, but only for full screen playback. The only issues I have noticed is compiz must be disabled to play flash videos (hulu) full screen.

Edit::D
Fixed flash fullscreen support by enabling 'Legacy Fullscreen Support under compiz workarounds and disabling and 'Unredirect Fullscreen Windows' compiz general tab . See [URL="http://www.linuxinsight.com/full-screen-flash-not-working-under-compiz.html"]http://www.linuxinsight.com/full-screen-flash-not-working-under-compiz.html.
[/URL]

Fullscreen is indeed OK. My issues are with windowed mode. For now, I'm getting best results with XBNC and compiz off.

---

