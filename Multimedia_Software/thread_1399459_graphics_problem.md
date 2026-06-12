---
title: "graphics problem"
date: 2010-02-05
forum: Multimedia Software
---

### Post by arunpkd on 2010-02-05
i have newly installed ubuntu 9.1 but it is not able to play any movies also don't show mouse pointer,
i have installed all players and neccesory files for multimedia. when i play the file media player opens and starts playing but i am able to see only a screen full of colored pixels
my system: AMD Athlon , Asus Mother board dual core 3600+,VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller [1106:5336], resolution 1280 X 1024, lg 17" LCD

---

### Post by lavinog on 2010-02-06
looks like a driver issue.
please post the contents of /var/log/Xorg.0.log

post the output of lspci

---

### Post by arunpkd on 2010-02-06
lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. Device 6290
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M890CE/K8N890CE [Chrome 9] (rev 11)
03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 03)
03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 03)
04:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
05:07.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
05:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by arunpkd on 2010-02-06
content of xorg.log is

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux Sudha 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=71c7b16c-6198-419f-9432-f08ded47fb8c ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Feb  6 15:27:37 2010
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 1106:3230:1043:81b5 VIA Technologies, Inc. K8M890CE/K8N890CE [Chrome 9] rev 17, Mem @ 0xd0000000/268435456, 0xfa000000/16777216, BIOS @ 0x????????/65536
(==) Using default built-in configuration (30 lines)
(==) --- Start of built-in configuration ---
    Section "Device"
        Identifier    "Builtin Default openchrome Device 0"
        Driver    "openchrome"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default openchrome Screen 0"
        Device    "Builtin Default openchrome Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default vesa Device 0"
        Driver    "vesa"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default vesa Screen 0"
        Device    "Builtin Default vesa Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default fbdev Device 0"
        Driver    "fbdev"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default fbdev Screen 0"
        Device    "Builtin Default fbdev Device 0"
    EndSection
    Section "ServerLayout"
        Identifier    "Builtin Default Layout"
        Screen    "Builtin Default openchrome Screen 0"
        Screen    "Builtin Default vesa Screen 0"
        Screen    "Builtin Default fbdev Screen 0"
    EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default openchrome Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default openchrome Device 0"
(==) No monitor specified for screen "Builtin Default openchrome Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (2)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default fbdev Device 0"
(==) No monitor specified for screen "Builtin Default fbdev Screen 0".
    Using a default monitor configuration.
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
(II) Open ACPI successful (/var/run/acpid.socket)
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
    [24] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [25] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [26] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [27] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [28] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [29] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [30] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [31] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [32] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [33] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [34] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [35] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [36] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [37] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [38] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [39] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [40] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [41] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [42] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [43] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [44] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [45] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [46] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [47] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [48] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [49] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [50] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [51] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [52] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [53] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [54] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [55] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [56] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [57] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [58] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [59] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [60] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [61] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [62] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [63] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [64] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [65] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [66] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [67] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [68] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [69] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [70] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [71] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
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
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "openchrome"
(II) Loading /usr/lib/xorg/modules/drivers//openchrome_drv.so
(II) Module openchrome: vendor="http://openchrome.org/"
    compiled for 1.6.1.901, module version = 0.2.903
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 2.2.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.4.0
    ABI class: X.Org Video Driver, version 5.0
(II) OPENCHROME: Driver for VIA Chrome chipsets: CLE266, KM400/KN400,
    K8M800/K8N800, PM800/PM880/CN400, P4M800Pro/VN800/CN700,
    K8M890/K8N890, P4M900/VN896/CN896, CX700/VX700, P4M890, VX800, VX855
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
(!!) VIA Technologies does not support this driver in any way.
(!!) For support, please refer to [http://www.openchrome.org/](http://www.openchrome.org/).
(!!) (development build, compiled on Mon Jul 27 22:18:45 2009)
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 0.0.2
    ABI class: X.Org Video Driver, version 5.0
(EE) open /dev/fb0: No such file or directory
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
    [24] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [25] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [26] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [27] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [28] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [29] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [30] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [31] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [32] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [33] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [34] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [35] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [36] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [37] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [38] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [39] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [40] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [41] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [42] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [43] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [44] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [45] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [46] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [47] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [48] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [49] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [50] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [51] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [52] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [53] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [54] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [55] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [56] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [57] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [58] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [59] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [60] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [61] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [62] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [63] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [64] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [65] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [66] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [67] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [68] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [69] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [70] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [71] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) CHROME(0): VIAPreInit
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) CHROME(0): VIAGetRec
(II) CHROME(0): Creating default Display subsection in Screen section
    "Builtin Default openchrome Screen 0" for depth/fbbpp 24/32
(==) CHROME(0): Depth 24, (--) framebuffer bpp 32
(==) CHROME(0): RGB weight 888
(==) CHROME(0): Default visual is TrueColor
(--) CHROME(0): Chipset: K8M890/K8N890
(--) CHROME(0): Chipset revision: 0
(--) CHROME(0): Probed amount of VideoRAM = 65536 kB
(II) CHROME(0): Setting up default chipset options.
(II) CHROME(0): VIASetupDefaultOptions
(II) CHROME(0): Reading config file...
(II) CHROME(0): Starting to parse config file options...
(==) CHROME(0): Shadow framebuffer is disabled.
(==) CHROME(0): Hardware acceleration is enabled.
(==) CHROME(0): Using XAA acceleration architecture.
(==) CHROME(0): Using hardware two-color cursors and software full-color cursors.
(==) CHROME(0): GPU virtual command queue will be enabled.
(==) CHROME(0): DRI IRQ will be enabled if DRI is enabled.
(==) CHROME(0): AGP DMA will be disabled if DRI is enabled.
(==) CHROME(0): PCI DMA will not be used for XV image transfer if DRI is enabled.
(==) CHROME(0): Will not enable VBE modes.
(==) CHROME(0): VBE VGA register save & restore will not be used
    if VBE modes are enabled.
(==) CHROME(0): Xv Bandwidth check is enabled.
(==) CHROME(0): Will not impose a limit on video RAM reserved for DRI.
(==) CHROME(0): Will try to allocate 32768 kB of AGP memory.
(==) CHROME(0): Digital output bus width is 12 bits.
(==) CHROME(0): DVI Center is disabled.
(==) CHROME(0): Panel size is not selected from config file.
(==) CHROME(0): Panel will not be forced.
(==) CHROME(0): TV dotCrawl is disabled.
(==) CHROME(0): TV deflicker is set to 0.
(==) CHROME(0): No default TV type is set.
(==) CHROME(0): No default TV output signal type is set.
(II) CHROME(0): VIAMapMMIO
(--) CHROME(0): mapping MMIO @ 0xfa000000 with size 0x9000
(--) CHROME(0): mapping BitBlt MMIO @ 0xfa200000 with size 0x200000
(II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) CHROME(0): Will not print VGA registers.
(==) CHROME(0): Will not scan I2C buses.
(II) CHROME(0): ...Finished parsing config file options.
(--) CHROME(0): Detected Asustek A8V-VM.
(II) CHROME(0): Detected MemClk 6
(II) CHROME(0): ViaGetMemoryBandwidth
(II) CHROME(0): Detected TV standard: NTSC.
(==) CHROME(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) CHROME(0): ViaI2CInit
(II) CHROME(0): ViaI2CBus1Init
(II) CHROME(0): I2C bus "I2C bus 1" initialized.
(II) CHROME(0): ViaI2cBus2Init
(II) CHROME(0): I2C bus "I2C bus 2" initialized.
(II) CHROME(0): ViaI2CBus3Init
(II) CHROME(0): I2C bus "I2C bus 3" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) CHROME(0): I2C device "I2C bus 1:E-EDID segment register" registered at address 0x60.
(II) CHROME(0): I2C device "I2C bus 1:ddc2" registered at address 0xA0.
(II) CHROME(0): Manufacturer: GSM  Model: 4432  Serial#: 16529
(II) CHROME(0): Year: 2007  Week: 30
(II) CHROME(0): EDID Version: 1.1
(II) CHROME(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) CHROME(0): Sync:  Separate  Composite  SyncOnGreen
(II) CHROME(0): Max Image Size [cm]: horiz.: 34  vert.: 27
(II) CHROME(0): Gamma: 2.20
(II) CHROME(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) CHROME(0): First detailed timing is preferred mode
(II) CHROME(0): redX: 0.641 redY: 0.342   greenX: 0.292 greenY: 0.611
(II) CHROME(0): blueX: 0.147 blueY: 0.068   whiteX: 0.313 whiteY: 0.329
(II) CHROME(0): Supported established timings:
(II) CHROME(0): 720x400@70Hz
(II) CHROME(0): 640x480@60Hz
(II) CHROME(0): 640x480@75Hz
(II) CHROME(0): 800x600@60Hz
(II) CHROME(0): 800x600@75Hz
(II) CHROME(0): 832x624@75Hz
(II) CHROME(0): 1024x768@60Hz
(II) CHROME(0): 1024x768@75Hz
(II) CHROME(0): 1280x1024@75Hz
(II) CHROME(0): 1152x870@75Hz
(II) CHROME(0): Manufacturer's mask: 0
(II) CHROME(0): Supported standard timings:
(II) CHROME(0): #0: hsize: 640  vsize 480  refresh: 75  vid: 20273
(II) CHROME(0): #1: hsize: 800  vsize 600  refresh: 75  vid: 20293
(II) CHROME(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) CHROME(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) CHROME(0): Supported detailed timing:
(II) CHROME(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) CHROME(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) CHROME(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) CHROME(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 140 MHz
(II) CHROME(0): Monitor name: L1752S
(II) CHROME(0): Monitor name: 
(II) CHROME(0): EDID (in hex):
(II) CHROME(0):     00ffffffffffff001e6d324491400000
(II) CHROME(0):     1e1101016e221b78ea2ee5a4574a9c25
(II) CHROME(0):     115054a56b80314f454f614f81800101
(II) CHROME(0):     010101010101302a009851002a403070
(II) CHROME(0):     1300520e1100001e000000fd00384b1e
(II) CHROME(0):     530e000a202020202020000000fc004c
(II) CHROME(0):     31373532530a202020202020000000fc
(II) CHROME(0):     00200a20202020202020202020200059
(II) CHROME(0): EDID vendor "GSM", prod id 17458
(II) CHROME(0): Using EDID range info for horizontal sync
(II) CHROME(0): Using EDID range info for vertical refresh
(II) CHROME(0): Printing DDC gathered Modelines:
(II) CHROME(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) CHROME(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) CHROME(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) CHROME(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) CHROME(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) CHROME(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) CHROME(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) CHROME(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) CHROME(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) CHROME(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) CHROME(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) CHROME(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) CHROME(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) CHROME(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) CHROME(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) CHROME(0): ViaOutputsDetect
(II) CHROME(0): VIATVDetect
(II) CHROME(0): ViaOutputsSelect
(II) CHROME(0): ViaOutputsSelect: X Configuration: 0x00
(II) CHROME(0): ViaOutputsSelect: BIOS Initialised register: 0x00
(II) CHROME(0): ViaOutputsSelect: CRT.
(II) CHROME(0): ViaModesAttach
(II) CHROME(0): <default monitor>: Using hsync range of 30.00-83.00 kHz
(II) CHROME(0): <default monitor>: Using vrefresh range of 56.00-75.00 Hz
(II) CHROME(0): <default monitor>: Using maximum pixel clock of 140.00 MHz
(II) CHROME(0): Estimated virtual size for aspect ratio 1.2593 is 1280x1024
(II) CHROME(0): Clock range:  20.00 to 230.00 MHz
(II) CHROME(0): ViaValidMode: Validating 640x350 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "640x350" (vrefresh out of range)
(II) CHROME(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x400 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "640x400" (vrefresh out of range)
(II) CHROME(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 720x400 (35500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "720x400" (vrefresh out of range)
(II) CHROME(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (25175)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (36000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "640x480" (vrefresh out of range)
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (36000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (40000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (50000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (49500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (56300)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "800x600" (vrefresh out of range)
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (44900)
(II) CHROME(0): Not using default mode "1024x768" (interlace mode not supported)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (65000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (75000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (78750)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (94500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1024x768" (vrefresh out of range)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x960 (108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x960 (148500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1280x960" (hsync out of range)
(II) CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (135000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (157500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1280x1024" (hsync out of range)
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 832x624 (57284)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (81620)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (96770)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (104990)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (119650)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1152x864" (vrefresh out of range)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (121500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1152x864" (vrefresh out of range)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (143470)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1360x768" (width too large for virtual size)
(II) CHROME(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1360x768" (width too large for virtual size)
(II) CHROME(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1440x900" (width too large for virtual size)
(II) CHROME(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) CHROME(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) CHROME(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) CHROME(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (40000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (25175)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 720x400 (28320)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (135000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (78750)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (65000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 832x624 (57284)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (49500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1152x864 (108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (49500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (78750)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (135000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (135000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1280x960 (108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1152x864 (108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1152x864 (108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1152x864 (104990)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1152x864 (96770)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1152x864 (81620)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (78750)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (78750)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (65000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (78750)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (75000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (65000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 832x624 (57284)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 832x624 (57284)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (49500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (49500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (40000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (49500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (50000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (40000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (36000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (25175)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (25175)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 720x400 (28320)
(II) CHROME(0): ViaFirstCRTCModeValid
(--) CHROME(0): Virtual size is 1280x1024 (pitch 1280)
(**) CHROME(0): *Driver mode "1280x1024": 108.0 MHz (scaled from -0.0 MHz), 64.0 kHz, 60.0 Hz
(II) CHROME(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) CHROME(0): *Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) CHROME(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) CHROME(0): *Driver mode "1280x1024": 108.0 MHz (scaled from -0.0 MHz), 64.0 kHz, 60.0 Hz
(II) CHROME(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) CHROME(0): *Default mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) CHROME(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) CHROME(0): *Default mode "1280x1024": 108.0 MHz (scaled from -0.0 MHz), 64.0 kHz, 60.0 Hz
(II) CHROME(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) CHROME(0): *Default mode "1280x960": 108.0 MHz (scaled from -0.0 MHz), 60.0 kHz, 60.0 Hz
(II) CHROME(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(**) CHROME(0): *Driver mode "1152x864": 108.0 MHz (scaled from -0.0 MHz), 67.5 kHz, 75.0 Hz
(II) CHROME(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) CHROME(0): *Default mode "1152x864": 108.0 MHz (scaled from -0.0 MHz), 67.5 kHz, 75.0 Hz
(II) CHROME(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) CHROME(0): *Default mode "1152x864": 105.0 MHz (scaled from -0.0 MHz), 67.6 kHz, 75.0 Hz
(II) CHROME(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(**) CHROME(0): *Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) CHROME(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(**) CHROME(0): *Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) CHROME(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(**) CHROME(0): *Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) CHROME(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) CHROME(0): *Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) CHROME(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) CHROME(0): *Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) CHROME(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) CHROME(0): *Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) CHROME(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) CHROME(0): *Default mode "1024x768": 75.0 MHz (scaled from -0.0 MHz), 56.5 kHz, 70.1 Hz
(II) CHROME(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) CHROME(0): *Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) CHROME(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) CHROME(0): *Driver mode "832x624": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.6 Hz
(II) CHROME(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) CHROME(0): *Default mode "832x624": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.6 Hz
(II) CHROME(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) CHROME(0): *Driver mode "800x600": 49.5 MHz (scaled from -0.0 MHz), 46.9 kHz, 75.0 Hz
(II) CHROME(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) CHROME(0): *Driver mode "800x600": 49.5 MHz (scaled from -0.0 MHz), 46.9 kHz, 75.0 Hz
(II) CHROME(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) CHROME(0): *Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
(II) CHROME(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) CHROME(0): *Default mode "800x600": 49.5 MHz (scaled from -0.0 MHz), 46.9 kHz, 75.0 Hz
(II) CHROME(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) CHROME(0): *Default mode "800x600": 50.0 MHz (scaled from -0.0 MHz), 48.1 kHz, 72.2 Hz
(II) CHROME(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) CHROME(0): *Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
(II) CHROME(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) CHROME(0): *Default mode "800x600": 36.0 MHz (scaled from -0.0 MHz), 35.2 kHz, 56.2 Hz
(II) CHROME(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) CHROME(0): *Driver mode "640x480": 31.5 MHz (scaled from -0.0 MHz), 37.5 kHz, 75.0 Hz
(II) CHROME(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) CHROME(0): *Driver mode "640x480": 31.5 MHz (scaled from -0.0 MHz), 37.5 kHz, 75.0 Hz
(II) CHROME(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) CHROME(0): *Driver mode "640x480": 25.2 MHz (scaled from -0.0 MHz), 31.5 kHz, 59.9 Hz
(II) CHROME(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) CHROME(0): *Default mode "640x480": 31.5 MHz (scaled from -0.0 MHz), 37.5 kHz, 75.0 Hz
(II) CHROME(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) CHROME(0): *Default mode "640x480": 31.5 MHz (scaled from -0.0 MHz), 37.9 kHz, 72.8 Hz
(II) CHROME(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) CHROME(0): *Default mode "640x480": 25.2 MHz (scaled from -0.0 MHz), 31.5 kHz, 59.9 Hz
(II) CHROME(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) CHROME(0): *Driver mode "720x400": 28.3 MHz (scaled from -0.0 MHz), 31.5 kHz, 70.1 Hz
(II) CHROME(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) CHROME(0): Display dimensions: (340, 270) mm
(**) CHROME(0): DPI set to (95, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.2.1
    ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) CHROME(0): VIAUnmapMem
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
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
    [24] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [25] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [26] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [27] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [28] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [29] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [30] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [31] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [32] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [33] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [34] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [35] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [36] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [37] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [38] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [39] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [40] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [41] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [42] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [43] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [44] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [45] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [46] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [47] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [48] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [49] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [50] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [51] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [52] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [53] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [54] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [55] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [56] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [57] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [58] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [59] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [60] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [61] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [62] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [63] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [64] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [65] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [66] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [67] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [68] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [69] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [70] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [71] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) CHROME(0): VIAScreenInit
(II) CHROME(0): VIAMapFB
(--) CHROME(0): mapping framebuffer @ 0xd0000000 with size 0x4000000
(--) CHROME(0): Frame buffer start: 0xb387d000, free start: 0x500000 end: 0x4000000
(II) CHROME(0): VIAMapMMIO
(--) CHROME(0): mapping MMIO @ 0xfa000000 with size 0x9000
(--) CHROME(0): mapping BitBlt MMIO @ 0xfa200000 with size 0x200000
(II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) CHROME(0): VIASave
(II) CHROME(0): Primary
(II) CHROME(0): Crtc...
(II) CHROME(0): TVSave...
(II) CHROME(0): VIAWriteMode
(II) CHROME(0): ViaModeSet
(II) CHROME(0): Name: 1280x1024
(II) CHROME(0): Clock: 108000
(II) CHROME(0): VRefresh: 60.019741
(II) CHROME(0): HSync: 63.981041
(II) CHROME(0): HDisplay: 1280
(II) CHROME(0): HSyncStart: 1328
(II) CHROME(0): HSyncEnd: 1440
(II) CHROME(0): HTotal: 1688
(II) CHROME(0): HSkew: 0
(II) CHROME(0): VDisplay: 1024
(II) CHROME(0): VSyncStart: 1025
(II) CHROME(0): VSyncEnd: 1028
(II) CHROME(0): VTotal: 1066
(II) CHROME(0): VScan: 0
(II) CHROME(0): Flags: 5
(II) CHROME(0): CrtcHDisplay: 0x500
(II) CHROME(0): CrtcHBlankStart: 0x500
(II) CHROME(0): CrtcHSyncStart: 0x530
(II) CHROME(0): CrtcHSyncEnd: 0x5a0
(II) CHROME(0): CrtcHBlankEnd: 0x698
(II) CHROME(0): CrtcHTotal: 0x698
(II) CHROME(0): CrtcHSkew: 0x0
(II) CHROME(0): CrtcVDisplay: 0x400
(II) CHROME(0): CrtcVBlankStart: 0x400
(II) CHROME(0): CrtcVSyncStart: 0x401
(II) CHROME(0): CrtcVSyncEnd: 0x404
(II) CHROME(0): CrtcVBlankEnd: 0x42a
(II) CHROME(0): CrtcVTotal: 0x42a
(II) CHROME(0): ViaDisplaySetStreamOnCRT
(II) CHROME(0): ViaDisplayEnableCRT
(II) CHROME(0): ViaModeFirstCRTC
(II) CHROME(0): ViaFirstCRTCSetMode
(II) CHROME(0): Setting up 1280x1024
(II) CHROME(0): ViaSetPrimaryFIFO
(II) CHROME(0): ViaSetDotclock to 0x079089
(II) CHROME(0): ViaSetUseExternalClock
(II) CHROME(0): ViaDisplayDisableSimultaneous
(II) CHROME(0): VIAAdjustFrame
(II) CHROME(0): VIAAdjustFrame
(II) CHROME(0): - Blanked
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] loaded kernel module for "via" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) CHROME(0): [drm] Using the DRM lock SAREA also for drawables.
(II) CHROME(0): [drm] framebuffer handle = 0xd0000000
(II) CHROME(0): [drm] added 1 reserved context for kernel
(II) CHROME(0): X context handle = 0x1
(II) CHROME(0): [drm] installed DRM signal handler
(II) CHROME(0): [dri] visual configs initialized.
(II) CHROME(0): [drm] register handle = 0xfa000000
(II) CHROME(0): [drm] framebuffer handle = 0xd0000000
(II) CHROME(0): [drm] mmio Registers = 0xfa000000
(II) CHROME(0): [dri] mmio mapped.
(II) CHROME(0): - Visuals set up
(II) CHROME(0): VIAInternalScreenInit
(II) CHROME(0): - B & W
(II) CHROME(0): CursorStart: 0x3fc0000
(II) CHROME(0): Using 3072 lines for offscreen memory.
(II) CHROME(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    8x8 color pattern filled rectangles
    Solid Lines
    Dashed Lines
    Image Writes
    Setting up tile and stipple cache:
        31 128x128 slots
        24 256x256 slots
        7 512x512 slots
        32 8x8 color pattern slots
(==) CHROME(0): Backing store disabled
(II) CHROME(0): - Backing store set up
(II) CHROME(0): - SW cursor set up
(II) CHROME(0): VIAHWCursorInit
(II) CHROME(0): - Def Color map set up
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): - Palette loaded
(II) CHROME(0): DPMS enabled
(II) CHROME(0): - DPMS set up
(II) CHROME(0): - Color maps etc. set up
(II) CHROME(0): [drm] Detected AGP vendor 0x1106, device 0x0336
(II) CHROME(0): [drm] Found AGP v3 compatible device. Trying AGP 8X mode.
(II) CHROME(0): [drm] Trying to enable AGP fast writes.
(II) CHROME(0): [drm] drmAgpEnabled succeeded
(II) CHROME(0): [drm] agpAddr = 0xd0000000
(II) CHROME(0): [drm] agpBase = (nil)
(II) CHROME(0): [drm] agpAddr = 0xd0000000
(II) CHROME(0): [drm] agpSize = 0x02000000
(II) CHROME(0): [drm] agp physical addr = 0x00000000
(II) CHROME(0): [dri] Using AGP.
(II) CHROME(0): [drm] Using 45864928 bytes for DRM memory heap.
(II) CHROME(0): [dri] Frame buffer initialized.
(II) CHROME(0): [DRI] installation complete
(II) CHROME(0): [dri] Kernel data initialized.
(II) CHROME(0): [drm] IRQ handler installed, using IRQ 16.
(II) CHROME(0): direct rendering enabled
Fulfilled via DRI at 20976640
(II) CHROME(0): Benchmarking video copy.  Less time is better.
(--) CHROME(0): Timed   libc YUV420 copy... 1150275. Throughput: 979.9 MiB/s.
(--) CHROME(0): Timed kernel YUV420 copy... 1150709. Throughput: 979.6 MiB/s.
(--) CHROME(0): Timed    SSE YUV420 copy... 752799. Throughput: 1497.3 MiB/s.
(--) CHROME(0): Timed    MMX YUV420 copy... 955776. Throughput: 1179.4 MiB/s.
(--) CHROME(0): Timed 3DNow! YUV420 copy... 1017273. Throughput: 1108.1 MiB/s.
(--) CHROME(0): Timed   MMX2 YUV420 copy... 748333. Throughput: 1506.3 MiB/s.
Freed 20976640 (pool 2)
(--) CHROME(0): Using MMX2 YUV42X copy for video.
(WW) CHROME(0): [XvMC] XvMC is not supported on this chipset.
(II) CHROME(0): - Done
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(EE) AIGLX error: swrast does not export required DRI extension
(EE) AIGLX: reverting to software rendering
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device ImExPS/2 Logitech Explorer Mouse
(**) ImExPS/2 Logitech Explorer Mouse: always reports core events
(**) ImExPS/2 Logitech Explorer Mouse: Device: "/dev/input/event5"
(II) ImExPS/2 Logitech Explorer Mouse: Found 9 mouse buttons
(II) ImExPS/2 Logitech Explorer Mouse: Found x and y relative axes
(II) ImExPS/2 Logitech Explorer Mouse: Found scroll wheel(s)
(II) ImExPS/2 Logitech Explorer Mouse: Configuring as mouse
(**) ImExPS/2 Logitech Explorer Mouse: YAxisMapping: buttons 4 and 5
(**) ImExPS/2 Logitech Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImExPS/2 Logitech Explorer Mouse" (type: MOUSE)
(**) ImExPS/2 Logitech Explorer Mouse: (accel) keeping acceleration scheme 1
(**) ImExPS/2 Logitech Explorer Mouse: (accel) filter chain progression: 2.00
(**) ImExPS/2 Logitech Explorer Mouse: (accel) filter stage 0: 20.00 ms
(**) ImExPS/2 Logitech Explorer Mouse: (accel) set acceleration profile 0
(II) ImExPS/2 Logitech Explorer Mouse: initialized for relative axes.
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.

---

### Post by lavinog on 2010-02-06
How much memory is dedicated to the video card?  The open chrome website says you should have at least 64M.

Also have you tried disabling desktop effects? System>preferences>apperance>visual effects>none

---

### Post by arunpkd on 2010-02-06
the visual effects is in "none"
how can i know how much memory allocated to video card

---

### Post by lavinog on 2010-02-06
It should be set in bios.
It looks like support for your video card is flaky.  You might want to consider upgrading it to a card that has better support.

---

### Post by arunpkd on 2010-02-07
yesterday i tried with live cd of 7.1, in that everything works well only in 9.1 it is not working.what should i do to install the drivers for VIA Chrome9

---

