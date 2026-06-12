---
title: "Ubuntu 8.10 don't show screen after installing ATI 10.1 drivers"
date: 2010-02-05
forum: Multimedia Software
---

### Post by aviramof on 2010-02-05
i want to install this drivers but it dones't want to show screen after installing them what can i do solve this problem other then uninstalling them in recovery mode the point is to fix the problem not just to go back to ubuntu without driver.
 
my card is hd3650 512mb ddr 2 shappire agp card with crt screen
 
thanks in advance.

---

### Post by markbuntu on 2010-02-05
Did you do

aticonfig -f

after installing the driver?
You really need to do that. If you have not then you can do it from the recovery terminal and then reboot.

---

### Post by aviramof on 2010-02-05
and what exceclly this will do?
i have already install ubuntu several times in the past few days i do not want to have 
to do it again especily after that now everything is finaly fine i even discoverd the source
of the problem with movies i had it's because of compiz so i switch to metacity when i 
want to see movies but i got to say i really don't like this catalyst version she's very basic
and the full version might be better but i need to know exceclly what to do before i risk 
destoring ubuntu graphics again because of this driver.

thanks in advance.

---

### Post by markbuntu on 2010-02-05
That command will initalize the driver. If you do not do it the driver will not work.
It is in the installer instructions which are at the ati site where you got the driver from. You should read them and the release notes which are also there.

---

### Post by aviramof on 2010-02-05
i have read them here is a link to what is see:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat101-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat101-inst.pdf)

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)

the problem is this:
[http://ubuntuforums.org/showthread.php?t=1399422](http://ubuntuforums.org/showthread.php?t=1399422)

this is the driver i'm trying to install:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)

the installer said install driver 8.69 on x.org 7.4 and later releases and as far as i know 

8.10 don't have x.org 7.4 it got 6 something 

and i don't see any aticonfig -f option in the installion instruction i see "For versions of X.Org older than 7, /usr/X11R6/bin/aticonfig --initial" 

so what should i do now?

can i press install driver 8.69 on x.org 7.4 and later releases and then /usr/X11R6/bin/aticonfig --initial or should i choose 

Generate Distribution Specific Driver Package and in this case i need a solution to the problem i'v describe here:

[http://ubuntuforums.org/showthread.php?t=1399422](http://ubuntuforums.org/showthread.php?t=1399422)

thanks in advance.

---

### Post by mushwars on 2010-02-06
pastebin your /var/log/Xorg.0.log please. Then we can see what is causing the problem. Otherwise it is a shot in the dark, it could be anything.

---

### Post by aviramof on 2010-02-06
you want see the problem now because i have not yet installed the ati driver i don't want to install it again and ruin something for the third time but here is the file any way.

thanks in advance.

```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux ofir-desktop 2.6.27-17-generic #1 SMP Wed Jan 27 23:14:44 UTC 2010 i686
Build Date: 09 March 2009  10:48:54AM
xorg-server 2:1.5.2-2ubuntu3.1 (buildd@rothera.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Feb  6 07:22:03 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 4.1
    X.Org XInput driver : 2.1
    X.Org Server Extension : 1.1
    X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) ATI Technologies Inc RV635 PRO AGP [Radeon HD 3650] rev 0, Mem @ 0xe0000000/0, 0xfdef0000/0, I/O @ 0x0000bc00/0, BIOS @ 0x????????/131072
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [30] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [31] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [32] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [33] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [34] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [35] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 7.4.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 1.1
(**) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 1.5.2, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 7.4.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "fglrx"

(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.4.99.906, module version = 8.54.3
    Module class: X.Org Video Driver
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for fglrx
(II) ATI Proprietary Linux Driver Version Identifier:8.54.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.543.2                  
(II) ATI Proprietary Linux Driver Build Date: Oct 10 2008 21:37:39
(WW) This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0
(WW) Video driver ABI version of the X server is 4.1
(--) Assigning device section with no busID to primary device
(--) Chipset Supported AMD Graphics Processor (0x9596) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [30] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [31] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [32] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [33] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [34] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [35] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) fglrx(0): pEnt->device->identifier=0x9098a58
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [24] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [25] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [26] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [27] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [28] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [29] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [30] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [31] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [32] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [33] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [34] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [35] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [36] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [37] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [38] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [39] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [40] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 0.1.0
    ABI class: X.Org Video Driver, version 4.1
(II) fglrx(0): PCI bus 1 card 0 func 0
(II) fglrx(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb
(II) fglrx(0): 10BitPixelFormat disabled by default
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(**) fglrx(0): Gamma Correction for I is 0x06419064
(**) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Radeon HD 3650 AGP" (Chipset = 0x9596)
(--) fglrx(0): (PciSubVendor = 0x1787, PciSubDevice = 0x0028)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
(--) fglrx(0): MMIO registers at 0xfdef0000
(--) fglrx(0): I/O port at 0x0000bc00
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    ABI class: X.Org Video Driver, version 4.1
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.1.0
    ABI class: X.Org Video Driver, version 4.1
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 10.78
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: 
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"

(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.4.99.906, module version = 8.54.3
    ABI class: X.Org Server Extension, version 1.1
(II) fglrx(0): Using adapter: 1:0.0.
(II) fglrx(0): [FB] Find the MC FB aperturs range(MCFBBase = 0xe0000000, MCFBSize = 0x20000000)
(--) fglrx(0): Video RAM: 524288 kByte, Type: DDR2
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): ***Display: ConnectedDisplayTypes=0x00000001, disabled=0x00000000
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: AOC  Model: f700  Serial#: 16135
(II) fglrx(0): Year: 2006  Week: 17
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate
(II) fglrx(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.631 redY: 0.329   greenX: 0.276 greenY: 0.600
(II) fglrx(0): blueX: 0.143 blueY: 0.057   whiteX: 0.283 whiteY: 0.297
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 94.5 MHz   Image Size:  310 x 230 mm
(II) fglrx(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) fglrx(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) fglrx(0): Monitor name: AOC FT7x0
(II) fglrx(0): Monitor name:  Series
(II) fglrx(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 72 kHz, PixClock max 110 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0):     00ffffffffffff0005e300f7073f0000
(II) fglrx(0):     11100103682018782a9ea8a154469924
(II) fglrx(0):     0e484ca4420031594559615981800101
(II) fglrx(0):     010101010101ea240060410028303060
(II) fglrx(0):     130036e61000001e000000fc00414f43
(II) fglrx(0):     2046543778300a202020000000fc0020
(II) fglrx(0):     5365726965730a2020202020000000fd
(II) fglrx(0):     0032a01e480b000a20202020202000c8
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000020
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 40 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 0)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync (50.9 kHz)
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync (46.3 kHz)
(**) fglrx(0): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync (39.2 kHz)
(**) fglrx(0): *Mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 (68.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 (60.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 +hsync (57.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace (35.5 kHz)
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"x85.0   56.25  800 832 896 1048  600 601 604 631 (53.7 kHz)
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 (46.9 kHz)
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 (48.1 kHz)
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync (43.8 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0):  Default mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
(II) fglrx(0): Modeline "800x600"x100.0   68.17  800 848 936 1072  600 601 604 636 +hsync (63.6 kHz)
(**) fglrx(0):  Default mode "800x600": 60.1 MHz (scaled from 0.0 MHz), 56.9 kHz, 90.0 Hz
(II) fglrx(0): Modeline "800x600"x90.0   60.06  800 840 928 1056  600 601 604 632 +hsync (56.9 kHz)
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 +hsync +vsync (43.3 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 +hsync +vsync (37.9 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "640x480"x120.0   52.40  640 680 744 848  480 481 484 515 +hsync (61.8 kHz)
(**) fglrx(0):  Default mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 50.9 kHz, 100.0 Hz
(II) fglrx(0): Modeline "640x480"x100.0   43.16  640 680 744 848  480 481 484 509 +hsync (50.9 kHz)
(**) fglrx(0):  Default mode "640x480": 37.9 MHz (scaled from 0.0 MHz), 45.5 kHz, 90.0 Hz
(II) fglrx(0): Modeline "640x480"x90.0   37.89  640 672 736 832  480 481 484 506 +hsync (45.5 kHz)
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 (31.1 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan (46.9 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan (37.9 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(--) fglrx(0): Display dimensions: (320, 240) mm
(--) fglrx(0): DPI set to (101, 108)
(--) fglrx(0): Virtual size is 2560x1024 (pitch 2560)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync (50.9 kHz)
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync (46.3 kHz)
(**) fglrx(0): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync (39.2 kHz)
(**) fglrx(0): *Mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 (68.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 (60.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 +hsync (57.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace (35.5 kHz)
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"x85.0   56.25  800 832 896 1048  600 601 604 631 (53.7 kHz)
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 (46.9 kHz)
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 (48.1 kHz)
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync (43.8 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0):  Default mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
(II) fglrx(0): Modeline "800x600"x100.0   68.17  800 848 936 1072  600 601 604 636 +hsync (63.6 kHz)
(**) fglrx(0):  Default mode "800x600": 60.1 MHz (scaled from 0.0 MHz), 56.9 kHz, 90.0 Hz
(II) fglrx(0): Modeline "800x600"x90.0   60.06  800 840 928 1056  600 601 604 632 +hsync (56.9 kHz)
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 +hsync +vsync (43.3 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 +hsync +vsync (37.9 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "640x480"x120.0   52.40  640 680 744 848  480 481 484 515 +hsync (61.8 kHz)
(**) fglrx(0):  Default mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 50.9 kHz, 100.0 Hz
(II) fglrx(0): Modeline "640x480"x100.0   43.16  640 680 744 848  480 481 484 509 +hsync (50.9 kHz)
(**) fglrx(0):  Default mode "640x480": 37.9 MHz (scaled from 0.0 MHz), 45.5 kHz, 90.0 Hz
(II) fglrx(0): Modeline "640x480"x90.0   37.89  640 672 736 832  480 481 484 506 +hsync (45.5 kHz)
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 (31.1 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan (46.9 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan (37.9 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(--) fglrx(0): Virtual size is 2560x1024 (pitch 2560)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync (50.9 kHz)
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync (46.3 kHz)
(**) fglrx(0): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync (39.2 kHz)
(**) fglrx(0): *Mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 (68.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 (60.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 +hsync (57.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace (35.5 kHz)
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"x85.0   56.25  800 832 896 1048  600 601 604 631 (53.7 kHz)
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 (46.9 kHz)
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 (48.1 kHz)
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync (43.8 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0):  Default mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
(II) fglrx(0): Modeline "800x600"x100.0   68.17  800 848 936 1072  600 601 604 636 +hsync (63.6 kHz)
(**) fglrx(0):  Default mode "800x600": 60.1 MHz (scaled from 0.0 MHz), 56.9 kHz, 90.0 Hz
(II) fglrx(0): Modeline "800x600"x90.0   60.06  800 840 928 1056  600 601 604 632 +hsync (56.9 kHz)
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 +hsync +vsync (43.3 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 +hsync +vsync (37.9 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "640x480"x120.0   52.40  640 680 744 848  480 481 484 515 +hsync (61.8 kHz)
(**) fglrx(0):  Default mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 50.9 kHz, 100.0 Hz
(II) fglrx(0): Modeline "640x480"x100.0   43.16  640 680 744 848  480 481 484 509 +hsync (50.9 kHz)
(**) fglrx(0):  Default mode "640x480": 37.9 MHz (scaled from 0.0 MHz), 45.5 kHz, 90.0 Hz
(II) fglrx(0): Modeline "640x480"x90.0   37.89  640 672 736 832  480 481 484 506 +hsync (45.5 kHz)
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 (31.1 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan (46.9 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan (37.9 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(--) fglrx(0): Virtual size is 2560x1024 (pitch 2560)
(--) fglrx(0): *Mode 2560x1024 (unnamed)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync (50.9 kHz)
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync (46.3 kHz)
(**) fglrx(0): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync (39.2 kHz)
(**) fglrx(0): *Mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 (68.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 (60.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 +hsync (57.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace (35.5 kHz)
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"x85.0   56.25  800 832 896 1048  600 601 604 631 (53.7 kHz)
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 (46.9 kHz)
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 (48.1 kHz)
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync (43.8 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0):  Default mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
(II) fglrx(0): Modeline "800x600"x100.0   68.17  800 848 936 1072  600 601 604 636 +hsync (63.6 kHz)
(**) fglrx(0):  Default mode "800x600": 60.1 MHz (scaled from 0.0 MHz), 56.9 kHz, 90.0 Hz
(II) fglrx(0): Modeline "800x600"x90.0   60.06  800 840 928 1056  600 601 604 632 +hsync (56.9 kHz)
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 +hsync +vsync (43.3 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 +hsync +vsync (37.9 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "640x480"x120.0   52.40  640 680 744 848  480 481 484 515 +hsync (61.8 kHz)
(**) fglrx(0):  Default mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 50.9 kHz, 100.0 Hz
(II) fglrx(0): Modeline "640x480"x100.0   43.16  640 680 744 848  480 481 484 509 +hsync (50.9 kHz)
(**) fglrx(0):  Default mode "640x480": 37.9 MHz (scaled from 0.0 MHz), 45.5 kHz, 90.0 Hz
(II) fglrx(0): Modeline "640x480"x90.0   37.89  640 672 736 832  480 481 484 506 +hsync (45.5 kHz)
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 (31.1 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan (46.9 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan (37.9 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.2.0
    ABI class: X.Org Video Driver, version 4.1
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"

(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 255 MB
(II) fglrx(0): [pci] find AGP GART
(II) fglrx(0): [agp] Mode=0x07000a1b bridge: 0x1106/0x0314
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x07000b1a
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x07000312)
(II) fglrx(0): [agp] graphics chipset has AGP v3.0 (native mode)
(II) fglrx(0): [pcie] 261120 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(II) fglrx(0): Direct rendering enabled
(II) fglrx(0): Interrupt handler installed at IRQ 16.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): Finished Initialize PPLIB!
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [24] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
    [25] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
    [26] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
    [27] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [28] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [29] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [30] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [31] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [32] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [33] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [34] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [35] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [36] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [37] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [38] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [39] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
    [40] 0    0    0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 1.4.x.y with x.y >= 99.906
(II) fglrx(0): detected X.org 7.4.2.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): DRIScreenInit for fglrx driver
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x1e92000
(II) fglrx(0): [drm] mapped SAREA 0x1e92000 to 0xb80a8000
(II) fglrx(0): [drm] framebuffer handle = 0x1e93000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.54.3
(II) fglrx(0):     Date: Oct 10 2008
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.27-17-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x01e94000
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x01040000
(II) fglrx(0): FBMM initialized for area (0,0)-(2560,1664)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(2560,1024) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 2560 x 640
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(II) fglrx(0): DPMS enabled
(II) fglrx(0): Initialized in-driver Xinerama extension
(**) fglrx(0): Textured Video is enabled.
(II) LoadModule: "glesx"

(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
    compiled for 1.4.99.906, module version = 1.0.0
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 26
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    Solid Horizontal and Vertical Lines
    Driver provided ScreenToScreenBitBlt replacement
    Driver provided FillSolidRects replacement
(II) fglrx(0): GLESX is enabled
(II) LoadModule: "amdxmm"

(II) Loading /usr/lib/xorg/modules//amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
    compiled for 1.4.99.906, module version = 1.0.0
    ABI class: X.Org Server Extension, version 1.1
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) fglrx(0): Enable the clock gating!
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 2.0.99
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device ImExPS/2 Generic Explorer Mouse
(**) ImExPS/2 Generic Explorer Mouse: always reports core events
(**) ImExPS/2 Generic Explorer Mouse: Device: "/dev/input/event7"
(II) ImExPS/2 Generic Explorer Mouse: Found x and y relative axes
(II) ImExPS/2 Generic Explorer Mouse: Found 5 mouse buttons
(II) ImExPS/2 Generic Explorer Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "ImExPS/2 Generic Explorer Mouse" (type: MOUSE)
(**) ImExPS/2 Generic Explorer Mouse: YAxisMapping: buttons 4 and 5
(**) ImExPS/2 Generic Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us,il"
(**) AT Translated Set 2 keyboard: xkb_layout: "us,il"
(**) Option "xkb_variant" ","
(**) AT Translated Set 2 keyboard: xkb_variant: ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(**) AT Translated Set 2 keyboard: xkb_options: "grp:alt_shift_toggle,grp_led:scroll"
(II) config/hal: Adding input device USB Optical Mouse
(**) USB Optical Mouse: always reports core events
(**) USB Optical Mouse: Device: "/dev/input/event2"
(II) USB Optical Mouse: Found x and y relative axes
(II) USB Optical Mouse: Found 3 mouse buttons
(II) USB Optical Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
(**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
AUDIT: Sat Feb  6 07:22:07 2010: 10999 X: client 4 rejected from local host ( uid=0 gid=0 pid=11019 )
AUDIT: Sat Feb  6 07:22:12 2010: 10999 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=11023 )
AUDIT: Sat Feb  6 07:22:12 2010: 10999 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=11024 )
AUDIT: Sat Feb  6 07:22:12 2010: 10999 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=11025 )
```

---

### Post by mushwars on 2010-02-06
I dont see a single problem in that log, not even a warning that could keep it from working, you already ARE using the non-free driver, which is the best it can be, the xf86-ati-drivers is the open source driver.

Can you tell me again what the problem you are having is, because based on that log it appears that X was working perfectly, and that it looks to be impossible that its "not working"

so what is "not working" 

perhaps a dmesg would help.

EDIT: X probably didnt start when you installed the free driver because it probably uninstalls the non-free and then doesnt change your xorg.conf
if you must use these drivers you would have to 
```
sudo X -configure
```


EDIT 2: **you dont have to reinstall everytime you have a problem** that is why we are here, you have a live cd for a reason, you can boot it and then chroot into your system and do all the configureation required to fix your problem then boot back into it, there is no such thing as a broken linux system that cant be repaired.

I never advocate reinstallation.

---

### Post by aviramof on 2010-02-06
i'm currently using the non-free driver the os itself gave me but it's old 8.54.3 as opposed to 8.69 and it uses old catalyst and not very good one version 2.1 i want to install the new one but when i do the system goes up and u get the sound but no screen just black screen

the problem is the new drivers said it's for x.org 7.4 and ubuntu 8.10 it's 6.8 or 6.9 so what
should i do to install it install as is then For versions of X.Org older than 7, /usr/X11R6/bin/aticonfig --initial and then aticonfig -f or 
sudo X -configure?

---

### Post by mushwars on 2010-02-06
> **aviramof said:**
> the problem is the new drivers said it's for x.org 7.4 and ubuntu 8.10 it's 6.8 or 6.9 so what
should i do to install it install as is then For versions of X.Org older than 7, /usr/X11R6/bin/aticonfig --initial and then aticonfig -f or 
sudo X -configure?

well it appears to be working now, so copy your config
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
```

then you should install your newest driver that you need then you need to run the aticonfig on your xorg.conf, yes.

---

