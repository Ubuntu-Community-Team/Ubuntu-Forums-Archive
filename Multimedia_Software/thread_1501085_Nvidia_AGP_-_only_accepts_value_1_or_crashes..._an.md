---
title: "Nvidia AGP - only accepts value 1 or crashes... and AGP does not work with value 1"
date: 2010-06-03
forum: Multimedia Software
---

### Post by davis.peixoto on 2010-06-03
Hi all.

Yes, I am new here. It's my first post, but I am not a complete novice on Linux. I am here because I didn't find any solution so far after days - yes, days - of trial and error, tons of reading (including this same forum), and no success so far. So I think it is time for asking help.

My machine is as:
- mobo: asus A7N8X-E Deluxe, with an AMD Athlon XP 3200 Black Edition
- chipset is nvidia nforce2
- vga: Nvidia geforce xfx 6200 ( core 44a ), AGP 8x.
- display: Samsung SyncMaster 2232BW plus (yes, 22 inches)

I can use it normally with a few inconvenients as I am not a gammer. Any GLX application have high chances to crash my machine. Youtube videos are 100% certain will crash in less than 30 seconds. Using compiz don't crash (but I do not make any features showdown to friends).

I'm running upon Ubuntu 8.04 LTS. Nvidia drivers installed through synaptic (currently using nvidia-glx-new).

- Yes, I removed Load "dri" and "glcore" from xorg.conf
- yes, I added Load "glx" to xorg.conf
- yes, I changed device driver from nv to nvidia on xorg.conf
- yes, I added NvAGP 1 to xorg.conf.

Let's start with odd things that are driving me crazy now:

Output from $cat /proc/driver/nvidia/agp/status gives me

```
Status: Disabled
```and tells me to look into dmesg, where I can find the expected:

```
NVRM: not using NVAGP, an AGPGART backend is loaded!
```If I try to set any value other than "1" for NvAGP option into xorg.conf, system crashes right after gdm login.

I can log into security terminal, and the cat /proc/driver/nvidia/agp/status gives me AGPGART loaded, but if I log into gdm, it crashes. Always. No matter if I put 0, 2,3 or even remove NvAGP line. It crashes.

Trying blacklist agpgart into /etc/modprobe.d/blacklist does not work. And I do not see any reason to do that, because nvidia and nvidia_agp modules depends on agpgart module.

I also tryed putting the option agp=off into grub line that call linux image. No success.

I also even tryed after a lot of research use the option mem=nopentium, as nvidia driver manual tells that this can be a source of agp errors on AMD machines. No success, too.

So, what should I do in order to get Nvidia driver being used and showing up into /proc/driver/nvidia/agp/status ?

I am clueless at this point.

Of course, I would be very glad if beyond getting this feature working, I could also activate Fast Writes feature on my card - yes, it already did the homework on this one also, and files already contains the string to activate them (AGP does not work with or without these lines, so I keep them on).

Any ideas, guys?

Thanks in advance.

---

### Post by BoneKracker on 2010-06-03
I don't know, but I have a few thoughts that might give you some ideas.

1. You might learn something from perusing /var/log/Xorg.0.log (or whatever it's called on your system).

2. If your kernel is hightly modular (which I would expect Ubuntu's is), then the agpgart stuff may have been built as modules, and you may be able to force the system to use the external module(s) from NVIDIA by blacklisting the regular kernel modules.  They modules provided by the kernel (as opposed to the ones from NVIDIA) would be called AGPGART and AGP_NVIDIA.  To see what AGP-related kernel modules you have loaded:
```
lsmod | grep AGP
```
You might try blacklisting one or both of those (if they exist) and see what happens.

3. NVIDIA provides a utility that will build what it thinks is a good Xorg.conf for you.  You might want to move your xorg.conf to xorg.conf.mine or something, run that, and see if anything is different that jumps out at you.
```
nvidia-xconfig
```

---

### Post by davis.peixoto on 2010-06-04
Hi BoneKraker,

yes, I already look into Xorg log, and learned a lot about kernel modules. However, let me paste those as a whole here, if that help.

Xorg.0.log

```


This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.3)
Current Operating System: Linux theBox 2.6.24-28-generic #1 SMP Thu May 27 00:16:49 UTC 2010 i686
Build Date: 06 May 2010  09:30:24PM
 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun  4 08:06:54 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "SyncMaster"
(**) |   |-->Device "nVidia Corporation NV44A [GeForce 6200]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/cyrillic,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(**) RgbPath set to "/usr/share/X11/rgb.txt"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.3
    X.Org Video Driver: 2.0
    X.Org XInput driver : 2.0
    X.Org Server Extension : 0.3
    X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,01e0 card 1043,80ac rev c1 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01eb card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ee card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01ed card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,01ec card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:5: chip 10de,01ef card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,0060 card 1043,80ad rev a4 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0064 card 1043,0c11 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,0067 card 1043,0c11 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,0067 card 1043,0c11 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,0068 card 1043,0c11 rev a4 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0066 card 1043,80a7 rev a1 class 02,00,00 hdr 00
(II) PCI: 00:05:0: chip 10de,006b card 1043,0c11 rev a2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,006a card 1043,8095 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,006c card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0065 card f043,0c11 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:0d:0: chip 10de,006e card 1043,809a rev a3 class 0c,00,10 hdr 00
(II) PCI: 00:1e:0: chip 10de,01e8 card 0000,0000 rev c1 class 06,04,00 hdr 01
(II) PCI: 01:04:0: chip 11ab,4320 card 1043,811a rev 13 class 02,00,00 hdr 00
(II) PCI: 01:08:0: chip 2003,8800 card 1801,2800 rev 02 class 07,03,00 hdr 00
(II) PCI: 01:0b:0: chip 1095,3112 card 1095,6112 rev 02 class 01,04,00 hdr 00
(II) PCI: 03:00:0: chip 10de,0221 card 1682,2152 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 I/O range:
    [0] -1    0    0x0000a000 - 0x0000bfff (0x2000) IX[B]
(II) Bus 1 non-prefetchable memory range:
    [0] -1    0    0xd5000000 - 0xd6ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
    [0] -1    0    0xd0000000 - 0xd0ffffff (0x1000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 3 non-prefetchable memory range:
    [0] -1    0    0xd2000000 - 0xd4ffffff (0x3000000) MX[B]
(II) Bus 3 prefetchable memory range:
    [0] -1    0    0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(--) PCI:*(3:0:0) nVidia Corporation NV44A [GeForce 6200] rev 161, Mem @ 0xd2000000/24, 0xc0000000/28, 0xd3000000/24
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xb0000000 from 0xbfffffff to 0xafffffff
(II) Active PCI resource ranges:
    [0] -1    0    0xd6004000 - 0xd60041ff (0x200) MX[B]
    [1] -1    0    0xd0000000 - 0xd0ffffff (0x1000000) MX[B]
    [2] -1    0    0xd6000000 - 0xd6003fff (0x4000) MX[B]
    [3] -1    0    0xd7085000 - 0xd708503f (0x40) MX[B]
    [4] -1    0    0xd7084000 - 0xd70847ff (0x800) MX[B]
    [5] -1    0    0xd7087000 - 0xd7087fff (0x1000) MX[B]
    [6] -1    0    0xd7000000 - 0xd707ffff (0x80000) MX[B]
    [7] -1    0    0xd7083000 - 0xd7083fff (0x1000) MX[B]
    [8] -1    0    0xd7082000 - 0xd70820ff (0x100) MX[B]
    [9] -1    0    0xd7081000 - 0xd7081fff (0x1000) MX[B]
    [10] -1    0    0xd7086000 - 0xd7086fff (0x1000) MX[B]
    [11] -1    0    0xb0000000 - 0xafffffff (0x0) MX[B]O
    [12] -1    0    0xd3000000 - 0xd3ffffff (0x1000000) MX[B](B)
    [13] -1    0    0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
    [14] -1    0    0xd2000000 - 0xd2ffffff (0x1000000) MX[B](B)
    [15] -1    0    0x0000b400 - 0x0000b40f (0x10) IX[B]
    [16] -1    0    0x0000b000 - 0x0000b003 (0x4) IX[B]
    [17] -1    0    0x0000ac00 - 0x0000ac07 (0x8) IX[B]
    [18] -1    0    0x0000a800 - 0x0000a803 (0x4) IX[B]
    [19] -1    0    0x0000a400 - 0x0000a407 (0x8) IX[B]
    [20] -1    0    0x0000a000 - 0x0000a0ff (0x100) IX[B]
    [21] -1    0    0x0000f000 - 0x0000f00f (0x10) IX[B]
    [22] -1    0    0x0000d400 - 0x0000d47f (0x80) IX[B]
    [23] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[B]
    [24] -1    0    0x0000e400 - 0x0000e407 (0x8) IX[B]
    [25] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xd6004000 - 0xd60041ff (0x200) MX[B]
    [1] -1    0    0xd0000000 - 0xd0ffffff (0x1000000) MX[B]
    [2] -1    0    0xd6000000 - 0xd6003fff (0x4000) MX[B]
    [3] -1    0    0xd7085000 - 0xd708503f (0x40) MX[B]
    [4] -1    0    0xd7084000 - 0xd70847ff (0x800) MX[B]
    [5] -1    0    0xd7087000 - 0xd7087fff (0x1000) MX[B]
    [6] -1    0    0xd7000000 - 0xd707ffff (0x80000) MX[B]
    [7] -1    0    0xd7083000 - 0xd7083fff (0x1000) MX[B]
    [8] -1    0    0xd7082000 - 0xd70820ff (0x100) MX[B]
    [9] -1    0    0xd7081000 - 0xd7081fff (0x1000) MX[B]
    [10] -1    0    0xd7086000 - 0xd7086fff (0x1000) MX[B]
    [11] -1    0    0xb0000000 - 0xafffffff (0x0) MX[B]O
    [12] -1    0    0xd3000000 - 0xd3ffffff (0x1000000) MX[B](B)
    [13] -1    0    0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
    [14] -1    0    0xd2000000 - 0xd2ffffff (0x1000000) MX[B](B)
    [15] -1    0    0x0000b400 - 0x0000b40f (0x10) IX[B]
    [16] -1    0    0x0000b000 - 0x0000b003 (0x4) IX[B]
    [17] -1    0    0x0000ac00 - 0x0000ac07 (0x8) IX[B]
    [18] -1    0    0x0000a800 - 0x0000a803 (0x4) IX[B]
    [19] -1    0    0x0000a400 - 0x0000a407 (0x8) IX[B]
    [20] -1    0    0x0000a000 - 0x0000a0ff (0x100) IX[B]
    [21] -1    0    0x0000f000 - 0x0000f00f (0x10) IX[B]
    [22] -1    0    0x0000d400 - 0x0000d47f (0x80) IX[B]
    [23] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[B]
    [24] -1    0    0x0000e400 - 0x0000e407 (0x8) IX[B]
    [25] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xd6004000 - 0xd60041ff (0x200) MX[B]
    [5] -1    0    0xd0000000 - 0xd0ffffff (0x1000000) MX[B]
    [6] -1    0    0xd6000000 - 0xd6003fff (0x4000) MX[B]
    [7] -1    0    0xd7085000 - 0xd708503f (0x40) MX[B]
    [8] -1    0    0xd7084000 - 0xd70847ff (0x800) MX[B]
    [9] -1    0    0xd7087000 - 0xd7087fff (0x1000) MX[B]
    [10] -1    0    0xd7000000 - 0xd707ffff (0x80000) MX[B]
    [11] -1    0    0xd7083000 - 0xd7083fff (0x1000) MX[B]
    [12] -1    0    0xd7082000 - 0xd70820ff (0x100) MX[B]
    [13] -1    0    0xd7081000 - 0xd7081fff (0x1000) MX[B]
    [14] -1    0    0xd7086000 - 0xd7086fff (0x1000) MX[B]
    [15] -1    0    0xb0000000 - 0xafffffff (0x0) MX[B]O
    [16] -1    0    0xd3000000 - 0xd3ffffff (0x1000000) MX[B](B)
    [17] -1    0    0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
    [18] -1    0    0xd2000000 - 0xd2ffffff (0x1000000) MX[B](B)
    [19] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [20] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [21] -1    0    0x0000b400 - 0x0000b40f (0x10) IX[B]
    [22] -1    0    0x0000b000 - 0x0000b003 (0x4) IX[B]
    [23] -1    0    0x0000ac00 - 0x0000ac07 (0x8) IX[B]
    [24] -1    0    0x0000a800 - 0x0000a803 (0x4) IX[B]
    [25] -1    0    0x0000a400 - 0x0000a407 (0x8) IX[B]
    [26] -1    0    0x0000a000 - 0x0000a0ff (0x100) IX[B]
    [27] -1    0    0x0000f000 - 0x0000f00f (0x10) IX[B]
    [28] -1    0    0x0000d400 - 0x0000d47f (0x80) IX[B]
    [29] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[B]
    [30] -1    0    0x0000e400 - 0x0000e407 (0x8) IX[B]
    [31] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 1.4.0.90, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.12  Thu Feb 14 18:45:56 PST 2008
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.1.0
    ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
    compiled for 1.4.0, module version = 0.1.1
    ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
    compiled for 1.4.0, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
    compiled for 1.4.0, module version = 1.2.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.0
(II) v4l driver for Video4Linux
(II) NVIDIA dlloader X Driver  169.12  Thu Feb 14 17:55:38 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 03:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xd6004000 - 0xd60041ff (0x200) MX[B]
    [5] -1    0    0xd0000000 - 0xd0ffffff (0x1000000) MX[B]
    [6] -1    0    0xd6000000 - 0xd6003fff (0x4000) MX[B]
    [7] -1    0    0xd7085000 - 0xd708503f (0x40) MX[B]
    [8] -1    0    0xd7084000 - 0xd70847ff (0x800) MX[B]
    [9] -1    0    0xd7087000 - 0xd7087fff (0x1000) MX[B]
    [10] -1    0    0xd7000000 - 0xd707ffff (0x80000) MX[B]
    [11] -1    0    0xd7083000 - 0xd7083fff (0x1000) MX[B]
    [12] -1    0    0xd7082000 - 0xd70820ff (0x100) MX[B]
    [13] -1    0    0xd7081000 - 0xd7081fff (0x1000) MX[B]
    [14] -1    0    0xd7086000 - 0xd7086fff (0x1000) MX[B]
    [15] -1    0    0xb0000000 - 0xafffffff (0x0) MX[B]O
    [16] -1    0    0xd3000000 - 0xd3ffffff (0x1000000) MX[B](B)
    [17] -1    0    0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
    [18] -1    0    0xd2000000 - 0xd2ffffff (0x1000000) MX[B](B)
    [19] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [20] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [21] -1    0    0x0000b400 - 0x0000b40f (0x10) IX[B]
    [22] -1    0    0x0000b000 - 0x0000b003 (0x4) IX[B]
    [23] -1    0    0x0000ac00 - 0x0000ac07 (0x8) IX[B]
    [24] -1    0    0x0000a800 - 0x0000a803 (0x4) IX[B]
    [25] -1    0    0x0000a400 - 0x0000a407 (0x8) IX[B]
    [26] -1    0    0x0000a000 - 0x0000a0ff (0x100) IX[B]
    [27] -1    0    0x0000f000 - 0x0000f00f (0x10) IX[B]
    [28] -1    0    0x0000d400 - 0x0000d47f (0x80) IX[B]
    [29] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[B]
    [30] -1    0    0x0000e400 - 0x0000e407 (0x8) IX[B]
    [31] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[B]
(II) resource ranges after probing:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xd6004000 - 0xd60041ff (0x200) MX[B]
    [5] -1    0    0xd0000000 - 0xd0ffffff (0x1000000) MX[B]
    [6] -1    0    0xd6000000 - 0xd6003fff (0x4000) MX[B]
    [7] -1    0    0xd7085000 - 0xd708503f (0x40) MX[B]
    [8] -1    0    0xd7084000 - 0xd70847ff (0x800) MX[B]
    [9] -1    0    0xd7087000 - 0xd7087fff (0x1000) MX[B]
    [10] -1    0    0xd7000000 - 0xd707ffff (0x80000) MX[B]
    [11] -1    0    0xd7083000 - 0xd7083fff (0x1000) MX[B]
    [12] -1    0    0xd7082000 - 0xd70820ff (0x100) MX[B]
    [13] -1    0    0xd7081000 - 0xd7081fff (0x1000) MX[B]
    [14] -1    0    0xd7086000 - 0xd7086fff (0x1000) MX[B]
    [15] -1    0    0xb0000000 - 0xafffffff (0x0) MX[B]O
    [16] -1    0    0xd3000000 - 0xd3ffffff (0x1000000) MX[B](B)
    [17] -1    0    0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
    [18] -1    0    0xd2000000 - 0xd2ffffff (0x1000000) MX[B](B)
    [19] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [20] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [21] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [23] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [24] -1    0    0x0000b400 - 0x0000b40f (0x10) IX[B]
    [25] -1    0    0x0000b000 - 0x0000b003 (0x4) IX[B]
    [26] -1    0    0x0000ac00 - 0x0000ac07 (0x8) IX[B]
    [27] -1    0    0x0000a800 - 0x0000a803 (0x4) IX[B]
    [28] -1    0    0x0000a400 - 0x0000a407 (0x8) IX[B]
    [29] -1    0    0x0000a000 - 0x0000a0ff (0x100) IX[B]
    [30] -1    0    0x0000f000 - 0x0000f00f (0x10) IX[B]
    [31] -1    0    0x0000d400 - 0x0000d47f (0x80) IX[B]
    [32] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[B]
    [33] -1    0    0x0000e400 - 0x0000e407 (0x8) IX[B]
    [34] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[B]
    [35] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [36] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "NvAGP" "1"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Option "DynamicTwinView" "False"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Use of NVIDIA internal AGP requested
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 (NV44) at PCI:3:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.a2.10.81
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 at PCI:3:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (DFP-0)
(--) NVIDIA(0): Samsung SyncMaster (DFP-0): 155.0 MHz maximum pixel clock
(--) NVIDIA(0): Samsung SyncMaster (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1680x1050@60"
(**) NVIDIA(0): Virtual screen size configured to be 1680 x 1050
(--) NVIDIA(0): DPI set to (87, 83); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xd6004000 - 0xd60041ff (0x200) MX[B]
    [5] -1    0    0xd0000000 - 0xd0ffffff (0x1000000) MX[B]
    [6] -1    0    0xd6000000 - 0xd6003fff (0x4000) MX[B]
    [7] -1    0    0xd7085000 - 0xd708503f (0x40) MX[B]
    [8] -1    0    0xd7084000 - 0xd70847ff (0x800) MX[B]
    [9] -1    0    0xd7087000 - 0xd7087fff (0x1000) MX[B]
    [10] -1    0    0xd7000000 - 0xd707ffff (0x80000) MX[B]
    [11] -1    0    0xd7083000 - 0xd7083fff (0x1000) MX[B]
    [12] -1    0    0xd7082000 - 0xd70820ff (0x100) MX[B]
    [13] -1    0    0xd7081000 - 0xd7081fff (0x1000) MX[B]
    [14] -1    0    0xd7086000 - 0xd7086fff (0x1000) MX[B]
    [15] -1    0    0xb0000000 - 0xafffffff (0x0) MX[B]O
    [16] -1    0    0xd3000000 - 0xd3ffffff (0x1000000) MX[B](B)
    [17] -1    0    0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
    [18] -1    0    0xd2000000 - 0xd2ffffff (0x1000000) MX[B](B)
    [19] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [20] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [21] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [23] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [24] -1    0    0x0000b400 - 0x0000b40f (0x10) IX[B]
    [25] -1    0    0x0000b000 - 0x0000b003 (0x4) IX[B]
    [26] -1    0    0x0000ac00 - 0x0000ac07 (0x8) IX[B]
    [27] -1    0    0x0000a800 - 0x0000a803 (0x4) IX[B]
    [28] -1    0    0x0000a400 - 0x0000a407 (0x8) IX[B]
    [29] -1    0    0x0000a000 - 0x0000a0ff (0x100) IX[B]
    [30] -1    0    0x0000f000 - 0x0000f00f (0x10) IX[B]
    [31] -1    0    0x0000d400 - 0x0000d47f (0x80) IX[B]
    [32] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[B]
    [33] -1    0    0x0000e400 - 0x0000e407 (0x8) IX[B]
    [34] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[B]
    [35] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [36] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "1680x1050@60"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "abnt2"
(**) Generic Keyboard: XkbModel: "abnt2"
(**) Option "XkbLayout" "br"
(**) Generic Keyboard: XkbLayout: "br"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
SetClientVersion: 0 9

```

```
lsmod | grep -i agp
```

```

nvidia_agp              9628  1 
agpgart                34760  2 nvidia_agp,nvidia

```

Also worth, in my opinion, to take a look into:
```
lsmod | grep -i nv
```
and
```
grep -i AGP /boot/config-2.6.24-28-generic
```

Outputs:

```

nvidia_agp              9628  1 
nvidia               7825536  34 
agpgart                34760  2 nvidia_agp,nvidia
i2c_core               24832  2 nvidia,i2c_nforce2

```

```

CONFIG_AGP=m
CONFIG_AGP_INTEL=m
CONFIG_AGP_ALI=m
CONFIG_AGP_AMD=m
CONFIG_AGP_AMD64=m
CONFIG_AGP_ATI=m
CONFIG_AGP_EFFICEON=m
CONFIG_AGP_NVIDIA=m
CONFIG_AGP_SIS=m
CONFIG_AGP_SWORKS=m
CONFIG_AGP_VIA=m

```

From all above, what I got is:

[LIST]
[*]All agp modules are kernel loadable, and not compiled
[*]nvidia and nvidia_agp depends on agpgart
[/LIST]
I also spotted something interesting on Xorg log, a little before:

```

...
(II) LoadModule: "dri"
...
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
...
```

This shows up, even removing Load dri from xorg.conf. I actually searched for how to explicitly disable, but I really don't think this is necessary anymore, and probably has nothing related to AGP issue.

Will try nvidia-xconfig. Update you soon.

---

### Post by davis.peixoto on 2010-06-04
Just tried running nvidia-xconfig

Nothing relevant on xorg.conf. It stripped device section moving all Option lines to screen section, and reformatted comment lines, putting all comments on each sections start.

just for information:

My xorg.conf:
```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
    FontPath    "/usr/share/fonts/X11/misc"
    FontPath    "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/Type1"
    FontPath    "/usr/share/fonts/X11/100dpi"
    FontPath    "/usr/share/fonts/X11/75dpi"
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    RgbPath        "/usr/share/X11/rgb.txt"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "abnt2"
    Option        "XkbLayout"    "br"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"    "/dev/input/mice"
    Option        "Protocol"    "ImPS/2"
    Option        "ZAxisMapping"    "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "Device"
    Identifier    "nVidia Corporation NV44A [GeForce 6200]"
    Boardname    "NVIDIA GeForce 6 Series"
    Driver        "nvidia"
    VideoRam    262144
    Busid        "PCI:3:0:0"
    #Option        "AddARGBVisuals"    "True"
    Option        "AddARGBGLXVisuals"    "True"
    #Option        "NoAccel"        "False"
    #Option        "AccelMethod"    "EXA"
    Option        "NoLogo"    "True"
    Option        "NvAGP"        "1"    #changed from 1 to 3 to enforce any AGP available use
    Option        "DynamicTwinView" "False"
    #Option        "UseEvents"    "False"
EndSection

Section "Monitor"
    Identifier    "SyncMaster"
    Vendorname    "Samsung"
    Modelname    "2232BW"
    Horizsync    30-81
    Vertrefresh    56.0 - 75.0
    modeline    "1680x1050@60" 140.76 1680 1712 2240 2272 1050 1071 1081 1103 -hsync +vsync
    Gamma        1.0
    #Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "nVidia Corporation NV44A [GeForce 6200]"
    Monitor        "SyncMaster"
    Defaultdepth    24
    Option        "DynamicTwinView" "False"
    SubSection "Display"
        Depth    24
        Virtual 1680 1050
        Modes    "1680x1050@60" # "1024x768"    "800x600"    "720x400"    "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen "Default Screen"
    Inputdevice    "Generic Keyboard"
    Inputdevice    "Configured Mouse"
EndSection

Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "dbe"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "vbe"
    Load    "v4l"
EndSection

```

nvidia-xconfig xorg.conf:
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
    RgbPath         "/usr/share/X11/rgb.txt"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "dbe"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
    Load           "v4l"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "abnt2"
    Option         "XkbLayout" "br"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"

    #Option        "DPMS"
    Identifier     "SyncMaster"
    VendorName     "Samsung"
    ModelName      "2232BW"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Gamma           1
    ModeLine       "1680x1050@60" 140.8 1680 1712 2240 2272 1050 1071 1081 1103 -hsync +vsync
EndSection

Section "Device"

    #Option        "AddARGBVisuals"    "True"
    #Option        "AccelMethod"    "EXA"
    Identifier     "nVidia Corporation NV44A [GeForce 6200]"
    Driver         "nvidia"
    BoardName      "NVIDIA GeForce 6 Series"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV44A [GeForce 6200]"
    Monitor        "SyncMaster"
    DefaultDepth    24
    Option         "DynamicTwinView" "False"
    #Option        "UseEvents"    "False"
    Option         "AddARGBGLXVisuals" "True"
    #Option        "NoAccel"        "False"
    Option         "NoLogo" "True"
    Option         "NvAGP" "1"    #changed from 1 to 3 to enforce any AGP available use
    SubSection     "Display"
 # "1024x768"    "800x600"    "720x400"    "640x480"
        Virtual     1680 1050
        Depth       24
        Modes      "1680x1050@60"
    EndSubSection
EndSection

```

I am starting to think nvidia_agp kernel module is not compatible with my Asus A7N8X-E chipset, or something like that...

Any further ideas guys?

---

### Post by davis.peixoto on 2010-06-04
Ok, some more news...

I blacklisted two modules in /etc/modprobe.d/blacklist

```

blacklist nvidia_agp #this is just an alias to module below
blacklist nvidia-agp

```

So I figured out how to avoid nvidia_agp module to get loaded. Fine.

Restarted, and got a crash right after login. A real bad one. Reset button did't work. Alt+ctrl+f1-12, didn't work either. Ctrl+alt+backspace... not work.

Ok, I restarted on hard way, then selected terminal session in the login screen. Secure terminal opened. And I could see at proc/.../agp/status that Nvidia driver was loaded and working. But I cannot login normally into gnome without getting a bad crash.

Other stuff I also tried:

use noapic option in the kernel selection line. No effects.

But I am really not intending to give up (almost all threads I read finishes with person giving up, and a few getting a solution that doesn't work for me).

So... anyone have any idea?

---

### Post by Despotic on 2010-06-04
I feel your pain.
I have a very similar configuration, but I had very few problems with 8.04, my problems have begun with 10.04. Perhaps your problem is similar? Do you have your Monitor plugged in via Analog or Digital connector?

I just upgraded to 10.04 the other day and I still haven't got it working. The problem for me seems to be getting the nVidia 6200 or 6800 (not sure which I have anymore) to output to the DVI by default. If I plug in via the analog connector it boots into X just fine, but when I disconnect, it craps out and I'm left at a terminal login screen.

Anything in your journey suggest how I can force the default video card output to the DVI connector?

---

### Post by davis.peixoto on 2010-06-04
Hello Despotic,

when I bought my monitor I made a post in my blog about configuring it. But it is written in brazilian portuguese, so I think I can shoot some quick tips on how I figured out here.

Currently I use DVI cable to connect my video card to my display, but first time I used the analog cable.

I could log in, but resolution was 1024 x 768 - which I used with my old LG CRT 15".

Ok, I edited xorg.conf as I posted above. Look carefully into sections monitor and screen (in the second xorg.conf I posted). Depending on your display device, some googling maybe required to find correct values.

After xorg.conf edit, go to 

```
/home/yourUser/.gconf/desktop/gnome/screen/default/0/%gconf.xml
```

This file contains the lastest sucessful used options for gnome session. You need to reset this file, otherwise you can get errors and a very very ugly screen.

Make a backup of this file first, then put this inside:

```

<?xml version="1.0"?>
<gconf>
    <entry  name="rate" mtime="1214273641" type="int" value="**56**">
    </entry>
    <entry name="resolution" mtime="1204383760"  type="string">
       <stringvalue>**1680x1050**</stringvalue>
    </entry>
</gconf>

```

Adjust the highlighted values if necessary. Restart.

You should be able to see a very strange configuration when you boot. Probably a huge black strip, as if the screen is out of center. If you see this, relax. Shutdown, change analog cable to DVI, and start again.

For me this worked like a charm.

But... pay attention to other configuration sources. Gnome display settings mostly. Try to make all confs be the same, and avoid as a hell using any intermediate discovering or adapting layers. More intermediate layers or misaligned software configs, more sources to be error prone.

If you are still getting stucked, try find out about a Xorg's extension/module named DDC.

Try use a Option "NoDDC" on device, monitor or screen section. Can't remeber where it goes now. But DDC stands for Display Data Channel, and is an extension used for detecting configurations, and almost always override your confs to what the machine understands as "better" as detected. Disabling this can put some light (keep an eye on the logs).

Well... that's it. Ah, I used nvidia drivers since before I bought this display here.

Cheers.

---

### Post by davis.peixoto on 2010-06-04
Now about my odyssey...

I tested changing the focus. Instead of nvidia drivers and agp, I focused where it hangs, ie, when gdm logs me in a gnome session. No success either.

But, after a bunch of crashing and restarting, I realized that sometimes it works* in the following configuration:


[LIST]
[*]blacklist nvidia**-**agp AND nvidia**_**agp
[*]add "mem=nopentium noapic" to boot loader line
[/LIST]

Sometimes crash in the login, sometimes log in, stays some minutes, and then crashes (starting glxgears or watching a video on youtube is enough to crash in less than 3 seconds).

I will find out - if someone help would be better, of course - but I am really sad about this. I mean, this machine was a jetset 5 years ago.

Nice mobo, nice cpu, nice gpu, nice chipset (nvidia on vga card and mobo chipset)... and linux running upon. It should be fast. Really fast. Even compared to nowadays cheap PCs, it should be a nice one.

But I have cool stuff, and can't extract one tenth of it because, it sounds funny, Linux does not allow. I am used to live with some software restrictions, but at this level is new for me.

So, once again: any ideas? Thx guys.

---

### Post by Despotic on 2010-06-04
Thanks for the info.

The only thing I'm not clear on is if 10.04 will check the xorg.conf file? I read elsewhere that it was built into the Kernel now, so is there any benefit to setting values in the xorg.conf file anymore?

-Jesse

---

### Post by BoneKracker on 2010-06-04
> **davis.peixoto said:**
> Now about my odyssey...

I tested changing the focus. Instead of nvidia drivers and agp, I focused where it hangs, ie, when gdm logs me in a gnome session. No success either.

But, after a bunch of crashing and restarting, I realized that sometimes it works* in the following configuration:


[LIST]
[*]blacklist nvidia**-**agp AND nvidia**_**agp
[*]add "mem=nopentium noapic" to boot loader line
[/LIST]

Sometimes crash in the login, sometimes log in, stays some minutes, and then crashes (starting glxgears or watching a video on youtube is enough to crash in less than 3 seconds).

I will find out - if someone help would be better, of course - but I am really sad about this. I mean, this machine was a jetset 5 years ago.

Nice mobo, nice cpu, nice gpu, nice chipset (nvidia on vga card and mobo chipset)... and linux running upon. It should be fast. Really fast. Even compared to nowadays cheap PCs, it should be a nice one.

But I have cool stuff, and can't extract one tenth of it because, it sounds funny, Linux does not allow. I am used to live with some software restrictions, but at this level is new for me.

So, once again: any ideas? Thx guys.
That's what I meant.  Blacklist both the internal modules.  Not sure what your second line is about.

Everything I see in your xorg log file looks good, like it should be working.  This may be a problem outside of X.

This is beyond me, but I think my first step, personally, would be to try to bring up just plain old X (without GDM, without Gnome, etc.).  I'm not familiar with Ubuntu's X configuration, but you might be able to do that with a simple "startx" command.  If that works, and you can run glxgears, etc., then the problem may lie elsewhere (like in some facet of the Gnome environment).

Another form of similar fault isolation would be to try a livecd that offers hardware accelerated graphics options, or a different Linux distro.

Other thoughts:

In your xorg, since you are trying to force use of nvidia agp, maybe your "NvAGP" should reflect that to prevent X from even checking for the in-kernel agpgart stuff (although the xorg log output looks fine, so I'm not sure if this will make any difference).

Other nivdia-related settings may be relevant ("AddARGBGLXVisuals", "AccelMethod", etc.).  It may be there are settings unique to that board that are required, although I would have expected nvidia's xorg.conf configurator to produce the correct settings).  I imagine you have already googled for information specific to your board pertaining to configuration on linux.

There is documentation, and reading it might spark some ideas.  Some of it contains information about idiosyncrasies of particular boards.  There is probably documenation on your system (maybe in /usr/share/docs), and there is documenation available on the web, e.g.:
[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/index.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/index.html)
(Try to find the one that corresponds to the version of the driver you are using.)

I wonder if using the nouveau driver would make a difference (you'd lose some capability compared to the proprietary nvidia drivers, but have more than the xorg nv driver).

Sorry I can't be of more help.

---

### Post by davis.peixoto on 2010-06-05
@Despotic

Dude, I am running upon 8.04, not 10.04. And I am completely out of 10.04 world as of now. I'm cannot confirm if xorg.conf is not being read and loaded. Sorry. But I think creating a thread may worth.

****

@Bonekracker

Blacklisting nvidia_agp modules makes my system hang. A lot. When it does not crash right after login, it crashes quickly. Less than 2 minutes. No pattern that could be observed so far other than crashing seems unavoidable.

I really do not consider myself as an specilist of anything on Unix world. I never compiled a kernel. I do not understand what is the flow and chain of responsability in almost any process. I am a simple user, but not lazy as usual to chase down more info about the problem I want to solve. That said, I can tell you I do not understand what is the correct flow in the graphic startup process.

I tried what you said (about trying startx from the command line). I follow these steps:

- in the ubuntu login screen I hit ctrl+alt+F2.
- logged in by terminal screen
- ran a $ps aux | grep -i gdm and $ps aux | grep -i X
- killed all gdm and X processes.
- typed "startx" and hit enter.

It started a usual session for me. With gnome panels, bars, sound, and even with compiz enabled. All this with nvidia_agp modules blacklisted. Everything fine until I open a xterm and type glxgears. Then my machine crashed again.

I am starting to think all this started when I upgraded from Ubuntu 7.10 to 8.04 using Synaptic way. All my files and configuration were saved from the need of a backup and restore process.

But... I think this solution was/is not mature enough. Even more on packed distributions. So I start thinking maybe some old file were kept, and it is still being referenced, and does not pops out on the logs. Some library or anything like that.

Well, it is sad after all, the need to try with a live CD or even changing distro. But it maybe necessary. I am not sure if I will head to lastest Ubuntu LTS, 10.04, or will come to Arch world - I like speed dudes.

About noveau, nv, I can't use compiz, and performance is not as bright as I would like. It is stable, but watching a youtube video is full os lags, even with at lowest resolution.

And about Nvidia options, yes, I read ALL manuals and options. Everytime I try a new driver I go after options to ensure the proper setting and behavior.

The second line, the one about mem=nopentium, noapic... This was all extracted from Nvidia official documentation (common problems, known issues...).

So, that's it. I will do a fresh installation (for me this sounds really BAD, and should sound same way for anyone who cares about software quality and responsability) from a new distro. See you guys.

Thanks for all, but I really do not want to waste my vacation's time with a thing that simply does not work. My wife deserves me better than behind a screen restarting PC over and over.

---

### Post by BoneKracker on 2010-06-05
> **davis.peixoto said:**
> I tried what you said (about trying startx from the command line). I follow these steps:

- in the ubuntu login screen I hit ctrl+alt+F2.
- logged in by terminal screen
- ran a $ps aux | grep -i gdm and $ps aux | grep -i X
- killed all gdm and X processes.
- typed "startx" and hit enter.

It started a usual session for me. With gnome panels, bars, sound, and even with compiz enabled. All this with nvidia_agp modules blacklisted. Everything fine until I open a xterm and type glxgears. Then my machine crashed again.

I am starting to think all this started when I upgraded from Ubuntu 7.10 to 8.04 using Synaptic way. All my files and configuration were saved from the need of a backup and restore process.

But... I think this solution was/is not mature enough. Even more on packed distributions. So I start thinking maybe some old file were kept, and it is still being referenced, and does not pops out on the logs. Some library or anything like that.

Well, it is sad after all, the need to try with a live CD or even changing distro. But it maybe necessary. I am not sure if I will head to lastest Ubuntu LTS, 10.04, or will come to Arch world - I like speed dudes.

About noveau, nv, I can't use compiz, and performance is not as bright as I would like. It is stable, but watching a youtube video is full os lags, even with at lowest resolution.

And about Nvidia options, yes, I read ALL manuals and options. Everytime I try a new driver I go after options to ensure the proper setting and behavior.

The second line, the one about mem=nopentium, noapic... This was all extracted from Nvidia official documentation (common problems, known issues...).

So, that's it. I will do a fresh installation (for me this sounds really BAD, and should sound same way for anyone who cares about software quality and responsability) from a new distro. See you guys.

Thanks for all, but I really do not want to waste my vacation's time with a thing that simply does not work. My wife deserves me better than behind a screen restarting PC over and over.

Like I said before, I'm not an Ubuntu user.  But it sounds to me like you've done pretty much all the same sorts of troubleshooting that I would have done.  You may well be right about the update process being the culprit.

Barring some additional insight from an advanced Ubuntu user here, what I would probably do is back up my important files somewhere, and install 10.04 from scratch (if you want to continue with Ubuntu).  Maybe you want to try a lighter version while you're at it.

If not, (and I'm not trying to steer you away from Ubuntu, which really is a very good distro) something like Arch, which use rolling releases, might be right for you.  No matter what distro you use, you're going to have an occasional problem and some frustration.  Also, keep in mind that a distro that uses rolling releases doesn't take less time to administer -- it just spreads that time out.  You can even end up having more problems overall, with rolling releases, although they tend to be more isolated and therefore easier to fix.  Some distros that use rolling releases are:
Arch Linux
PCLinuxOS
Foresight Linux
Gentoo Linux
Sabayon Linux (easier-to-install Gentoo derivative)

The only one of those I've used is Gentoo, but if I had to bet, I'd say the one that takes the least amount of time to administer (i.e., best for the wife) would be PCLinusOS.  If I were to pick the most interesting, I'd say they would be Foresight, Arch, and Gentoo.

---

### Post by davis.peixoto on 2010-06-07
Hello Bonekracker,

yeah, I had exactly that in mind - backing up my files and making a fresh installation of Ubuntu 10.04, or trying Arch Linux.

I agree Ubuntu is a great distro. But I also always had an eye on Arch, which is rolling releases distro, minimalist, and performance oriented (no i386 backwards compatibility, and I must say this attracts me a lot).

Thanks for the tips, dude.

But to be true, I guess I found a work around here. Let me share.

I am using nvidia-glx-new from Ubuntu official repos, what gives me version 169.12 of nvidia driver. After reading nvidia's driver manual over and over, even the less used options, and xorg's log, I realized that just - in my case at least - just commenting out GLcore and DRI modules just don't work.

Xorg's log brings those modules as loaded by default all times. So, instead of commenting out or removing those lines from xorg.conf, I need to appeal to another directive.

My xorg.conf looks like:
```

...
Section "Module"
    [B]Disable "dri"
    Disable "GLcore"
    Disable "Composite"[/B]
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "vbe"
    Load    "v4l"
EndSection

```

I explicitely disabled the conflicting modules. Composite seems to be conflicting with nvidia GLX extension as per driver manual. And let nvidia section without any options other than NoLogo and NvAGP.

With this, I still can't see the driver being correct used for AGP status, and I really believe the performance can be far way better with an AGP driver loaded and properly working. But removing those conflicting modules brought an user acceptable performance. Now I can, at least, watch a movie on youtube, and use firefox for navigating javascript intensive sites without loosing too much performance.

I will try later removing nvidia_agp modules and test stability. If this works, I think I will be done. Otherwise, I don't care too much. I intend to buy a new, powerful, x86_64, PC in the next months and install Arch.

I will keep this thread posted about stability findings. See you guys, and thanks for all patience and support.

---

### Post by BoneKracker on 2010-06-07
I'm glad you got it working.

Now that you mention this conflict, this brings something to mind.  Instead of disabling those modules, I have a fuzzy memory of some option like "enable composite with glx" or something like that.

I'm one of the few people who doesn't like composite, so almost anybody else could probably help you better with that, but you might want to research that and see if it's relevant.

This may be outdated, but backup your xorg.conf and see what this produces (check nvidia-xconfig to see that these options are correct and what the syntax is):
```
nvidia-xconfig --composite --allow-glx-with-composite --render-accel --add-argb-glx-visuals

```
Like I say, check syntax -- you may need to do those in sequence; I'm not sure how it works.

nvidia xconfig
nvidia-xconfig --composite
nvidia-xconfig --alloow-glx-with-composite
nvidia-xconfig --render-acccel
nvidia-xconfig --add-argb-glx-visuals

---

