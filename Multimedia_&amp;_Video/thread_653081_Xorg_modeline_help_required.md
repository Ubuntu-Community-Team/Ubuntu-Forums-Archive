---
title: "Xorg modeline help required"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by gunja99 on 2007-12-29
Dear all.
   Well have now spent a good 12 hours trying to get my MiniPC DUo to output to my Samsung 40inch LCD 1080 TV (LE40M86BD) reliably. It DOES work some of the time, but the egdes are cut off in both 1080 and 720 resolutions. I have installed the latest Gusty (7.10 ubuntu), with all the latest updates installed (all standard sources, no, non standards yet). It is connected to the TV via HDMI through a DVI-HDMI adaptor.

The problems I am having is as follows:
   It unreliably starts into either 720 or 1080, and both resolutions you cannot see the footer or the top menu bars (have to guess where they are). Now I did have Vista installed on this PC, and had exactly the same problem, though the intel drivers had a tool that allowed me to shrink the screen to fit.
   Sometimes the screen is blank on the TV and it is NOT showing Mode is not supported it's stating the mode is supported, but the screen is blank. If I switch between console (CTL-ALT-F3 and then CTL-ALT-F7), it sometimes comes back, and sometimes doesn't.

I want to run this in 1920x1080. I have been playing with the xorg.conf files, and using utilities off the net to try and work out how to get this working. I know there are some problems with the 965 chipset, but I believe I can get this working with the correct xorg settings! I just have no idea what the modelines mean (well I have a very very small understanding).  Below I have posted the output from lspci, the xorg.conf I am trying, the xorg log file, the version of the intel driver I am using, as well as the output from xresprobe and ddcprobe.

When using the modeline, is the part in double quotes ("1080i" for example), just any name I can use, and then refer to this in the modes part of the screen section?

It also seems that xorg is ignoring these modelines and getting it's own from EDID? and DDC? (not sure if this is correct). I read somewhere about an IgnoreEDID option (can't remember the exact line, but along those lines), which apparently the intel driver does not support. Although there is a NoDDC or something, but this made no difference under the device section.

What I need to be able to do is firstly get x to start with always the same modeline settings for a 1920x1080 resolution, and then know what changes I could make to the modeline to make it shrink (overscan playing).

Any help would be greatly appreciated. If I get it working I will let everyone know the modeline for this fantastic TV!

Oh and one last thing, is the parts out of the manual for TV at 1920x1080 (DVI/HDMI output):

VESA 1920x1080: H Freq (kHz): 66.587, V Freq (Hz): 59.934, Pixel Clock (Mhz): 138.500 Sync Polatiry (H/V) +/-


```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
```

I am using the intel driver as follows:

```
root@tv-pc:~# apt-show-versions | grep intel
xserver-xorg-video-intel/gutsy uptodate 2:2.1.1-0ubuntu9
```

The /etc/X11/xorg.conf (only the screen parts have been copied here):

```
Section "Device"
        Identifier      "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option          "AddARGBXVisuals" "True"
        Option "DisableGLXRootClipping" "True"
        Option "XAANoOffscreenPixmaps"
        Option "UseFBDev"
        Option "TripleBuffer" "true"
EndSection

Section "Monitor"
        Identifier      "SAMSUNG"
        Option          "DPMS" "true"
        HorizSync       15 - 68
        VertRefresh     49 - 61
        #Modeline "1920x1080" 176.92  1920 2008 2224 2632  1080 1080 1083 1120
        Modeline "1080" 182.01 1920 1952 2640 2672 1080 1102 1113 1135
        Modeline "1080i" 148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync -vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Monitor         "SAMSUNG"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1080i"
        EndSubSection
EndSection
```

"xresprobe intel" output:
```
id: SAMSUNG
res: 1920x1080 1280x720 640x480
freq: 15-68 49-61
disptype:
```

"ddcprobe" output:
```
vbe: VESA 3.0 detected.
oem: Intel(r)GM965/PM965/GL960 Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)GM965/PM965/GL960 Graphics Controller Hardware Version 0.0
memory: 7616kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid:
edid: 1 3
id: 029f
eisa: SAM029f
serial: 00000000
manufacture: 45 2006
input: analog signal.
screensize: 16 9
gamma: 2.200000
dpms: RGB, no active off, no suspend, no standby
timing: 640x480@75 Hz (VESA)
dtiming: 1920x1080@67
dtiming: 1280x720@71
monitorname: SAMSUNG
monitorrange: 15-68, 49-61
```

Last boot xorg log:

```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux tv-pc 2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007 x86_64
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec 29 18:44:06 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "SAMSUNG"
(**) |   |-->Device "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7cd8a0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2a00 card a0a0,062d rev 03 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2a02 card a0a0,062d rev 03 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,2a03 card a0a0,062d rev 03 class 03,80,00 hdr 80
(II) PCI: 00:19:0: chip 8086,1049 card a0a0,062d rev 03 class 02,00,00 hdr 00
(II) PCI: 00:1a:0: chip 8086,2834 card a0a0,062d rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card a0a0,062d rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card a0a0,062d rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,284b card a0a0,062d rev 03 class 04,03,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,2830 card a0a0,062d rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card a0a0,062d rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card a0a0,062d rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card a0a0,062d rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev f3 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2815 card a0a0,062d rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,2850 card a0a0,062d rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,2828 card a0a0,062d rev 03 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,283e card a0a0,062d rev 03 class 0c,05,00 hdr 00
(II) PCI: 01:03:0: chip 11c1,5811 card a0a0,030a rev 70 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xfdc00000 - 0xfdcfffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation Mobile Integrated Graphics Controller rev 3, Mem @ 0xfdb00000/20, 0xd0000000/28, I/O @ 0xff00/3
(--) PCI: (0:2:1) Intel Corporation Mobile Integrated Graphics Controller rev 3, Mem @ 0xfde00000/20
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xfddff000 - 0xfddfffff (0x1000) MX[B]
	[1] -1	0	0xfdffc000 - 0xfdffc0ff (0x100) MX[B]
	[2] -1	0	0xfdffd000 - 0xfdffd3ff (0x400) MX[B]
	[3] -1	0	0xfdff4000 - 0xfdff7fff (0x4000) MX[B]
	[4] -1	0	0xfdffe000 - 0xfdffe3ff (0x400) MX[B]
	[5] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B]
	[6] -1	0	0xfdfc0000 - 0xfdfdffff (0x20000) MX[B]
	[7] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xfdb00000 - 0xfdbfffff (0x100000) MX[B](B)
	[10] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[11] -1	0	0x0000f200 - 0x0000f20f (0x10) IX[B]
	[12] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[13] -1	0	0x0000f400 - 0x0000f403 (0x4) IX[B]
	[14] -1	0	0x0000f500 - 0x0000f507 (0x8) IX[B]
	[15] -1	0	0x0000f600 - 0x0000f603 (0x4) IX[B]
	[16] -1	0	0x0000f700 - 0x0000f707 (0x8) IX[B]
	[17] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x0000f900 - 0x0000f91f (0x20) IX[B]
	[23] -1	0	0x0000fa00 - 0x0000fa1f (0x20) IX[B]
	[24] -1	0	0x0000fb00 - 0x0000fb1f (0x20) IX[B]
	[25] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[26] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]
	[27] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]
	[28] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfddff000 - 0xfddfffff (0x1000) MX[B]
	[1] -1	0	0xfdffc000 - 0xfdffc0ff (0x100) MX[B]
	[2] -1	0	0xfdffd000 - 0xfdffd3ff (0x400) MX[B]
	[3] -1	0	0xfdff4000 - 0xfdff7fff (0x4000) MX[B]
	[4] -1	0	0xfdffe000 - 0xfdffe3ff (0x400) MX[B]
	[5] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B]
	[6] -1	0	0xfdfc0000 - 0xfdfdffff (0x20000) MX[B]
	[7] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xfdb00000 - 0xfdbfffff (0x100000) MX[B](B)
	[10] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[11] -1	0	0x0000f200 - 0x0000f20f (0x10) IX[B]
	[12] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[13] -1	0	0x0000f400 - 0x0000f403 (0x4) IX[B]
	[14] -1	0	0x0000f500 - 0x0000f507 (0x8) IX[B]
	[15] -1	0	0x0000f600 - 0x0000f603 (0x4) IX[B]
	[16] -1	0	0x0000f700 - 0x0000f707 (0x8) IX[B]
	[17] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x0000f900 - 0x0000f91f (0x20) IX[B]
	[23] -1	0	0x0000fa00 - 0x0000fa1f (0x20) IX[B]
	[24] -1	0	0x0000fb00 - 0x0000fb1f (0x20) IX[B]
	[25] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[26] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]
	[27] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]
	[28] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfddff000 - 0xfddfffff (0x1000) MX[B]
	[5] -1	0	0xfdffc000 - 0xfdffc0ff (0x100) MX[B]
	[6] -1	0	0xfdffd000 - 0xfdffd3ff (0x400) MX[B]
	[7] -1	0	0xfdff4000 - 0xfdff7fff (0x4000) MX[B]
	[8] -1	0	0xfdffe000 - 0xfdffe3ff (0x400) MX[B]
	[9] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B]
	[10] -1	0	0xfdfc0000 - 0xfdfdffff (0x20000) MX[B]
	[11] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfdb00000 - 0xfdbfffff (0x100000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[17] -1	0	0x0000f200 - 0x0000f20f (0x10) IX[B]
	[18] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[19] -1	0	0x0000f400 - 0x0000f403 (0x4) IX[B]
	[20] -1	0	0x0000f500 - 0x0000f507 (0x8) IX[B]
	[21] -1	0	0x0000f600 - 0x0000f603 (0x4) IX[B]
	[22] -1	0	0x0000f700 - 0x0000f707 (0x8) IX[B]
	[23] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x0000f900 - 0x0000f91f (0x20) IX[B]
	[29] -1	0	0x0000fa00 - 0x0000fa1f (0x20) IX[B]
	[30] -1	0	0x0000fb00 - 0x0000fb1f (0x20) IX[B]
	[31] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[32] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]
	[33] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]
	[34] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 2.1.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, 965G, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33
(II) Primary Device is: PCI 00:02:0
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset 965GM found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfddff000 - 0xfddfffff (0x1000) MX[B]
	[5] -1	0	0xfdffc000 - 0xfdffc0ff (0x100) MX[B]
	[6] -1	0	0xfdffd000 - 0xfdffd3ff (0x400) MX[B]
	[7] -1	0	0xfdff4000 - 0xfdff7fff (0x4000) MX[B]
	[8] -1	0	0xfdffe000 - 0xfdffe3ff (0x400) MX[B]
	[9] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B]
	[10] -1	0	0xfdfc0000 - 0xfdfdffff (0x20000) MX[B]
	[11] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfdb00000 - 0xfdbfffff (0x100000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[17] -1	0	0x0000f200 - 0x0000f20f (0x10) IX[B]
	[18] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[19] -1	0	0x0000f400 - 0x0000f403 (0x4) IX[B]
	[20] -1	0	0x0000f500 - 0x0000f507 (0x8) IX[B]
	[21] -1	0	0x0000f600 - 0x0000f603 (0x4) IX[B]
	[22] -1	0	0x0000f700 - 0x0000f707 (0x8) IX[B]
	[23] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x0000f900 - 0x0000f91f (0x20) IX[B]
	[29] -1	0	0x0000fa00 - 0x0000fa1f (0x20) IX[B]
	[30] -1	0	0x0000fb00 - 0x0000fb1f (0x20) IX[B]
	[31] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[32] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]
	[33] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]
	[34] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfddff000 - 0xfddfffff (0x1000) MX[B]
	[5] -1	0	0xfdffc000 - 0xfdffc0ff (0x100) MX[B]
	[6] -1	0	0xfdffd000 - 0xfdffd3ff (0x400) MX[B]
	[7] -1	0	0xfdff4000 - 0xfdff7fff (0x4000) MX[B]
	[8] -1	0	0xfdffe000 - 0xfdffe3ff (0x400) MX[B]
	[9] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B]
	[10] -1	0	0xfdfc0000 - 0xfdfdffff (0x20000) MX[B]
	[11] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfdb00000 - 0xfdbfffff (0x100000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[20] -1	0	0x0000f200 - 0x0000f20f (0x10) IX[B]
	[21] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[22] -1	0	0x0000f400 - 0x0000f403 (0x4) IX[B]
	[23] -1	0	0x0000f500 - 0x0000f507 (0x8) IX[B]
	[24] -1	0	0x0000f600 - 0x0000f603 (0x4) IX[B]
	[25] -1	0	0x0000f700 - 0x0000f707 (0x8) IX[B]
	[26] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000f900 - 0x0000f91f (0x20) IX[B]
	[32] -1	0	0x0000fa00 - 0x0000fa1f (0x20) IX[B]
	[33] -1	0	0x0000fb00 - 0x0000fb1f (0x20) IX[B]
	[34] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[35] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]
	[36] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]
	[37] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(**) intel(0): Option "TripleBuffer" "true"
(II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
(--) intel(0): Chipset: "965GM"
(--) intel(0): Linear framebuffer at 0xD0000000
(--) intel(0): IO registers at addr 0xFDB00000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using XAA for acceleration
(--) intel(0): Will try to allocate texture pool for old Mesa 3D driver.
(II) intel(0): Will try to reserve 32768 kiB of AGP aperture space
	for the DRM memory manager.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) intel(0): Output VGA using monitor section SAMSUNG
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID for output LVDS
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 7616 kB
(II) intel(0): VESA VBE OEM: Intel(r)GM965/PM965/GL960 Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r)GM965/PM965/GL960 Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): I2C bus "SDVOB DDC Bus" initialized.
(II) intel(0): Output TMDS-1 has no monitor section
(II) intel(0): SDVO device VID/DID: 02:3C.06, clock range 25.0MHz - 200.0MHz, input 1: Y, input 2: N, output 1: Y, output 2: N
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): Output TV has no monitor section
(II) intel(0): Current clock rate multiplier: 8
(II) intel(0): Output VGA disconnected
(II) intel(0): EDID for output VGA
(II) intel(0): Output LVDS connected
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID for output LVDS
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x800" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 (48.4 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): Output TMDS-1 connected
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" removed.
(II) intel(0): EDID for output TMDS-1
(II) intel(0): Manufacturer: SAM  Model: 29f  Serial#: 0
(II) intel(0): Year: 2006  Week: 45
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max H-Image Size [cm]: horiz.: 16  vert.: 9
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.650 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported VESA Video Modes:
(II) intel(0): 640x480@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 148.5 MHz   Image Size:  160 x 90 mm
(II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 74.2 MHz   Image Size:  160 x 90 mm
(II) intel(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
(II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
(II) intel(0): Monitor name: SAMSUNG
(II) intel(0): Ranges: V min: 49  V max: 61 Hz, H min: 15  H max: 68 kHz, PixClock max 230 MHz
(II) intel(0): Number of EDID sections to follow: 1
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004c2d9f0200000000
(II) intel(0): 	2d100103801009780aaea5a6544c9926
(II) intel(0): 	14505420000001010101010101010101
(II) intel(0): 	010101010101023a801871382d40582c
(II) intel(0): 	4500a05a0000001e011d007251d01e20
(II) intel(0): 	6e285500a05a0000001e000000fc0053
(II) intel(0): 	414d53554e470a2020202020000000fd
(II) intel(0): 	00313d0f4417000a202020202020012f
(II) intel(0): EDID vendor "SAM", prod id 671
(II) intel(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1440x900" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Printing probed modes for output TMDS-1
(II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output TV disconnected
(II) intel(0): EDID for output TV
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output TMDS-1 connected
(II) intel(0): Output TV disconnected
(II) intel(0): Output LVDS using initial mode 1024x768
(II) intel(0): Output TMDS-1 using initial mode 1280x720
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 512 kB GTT.
(II) intel(0): detected 7676 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(**) intel(0): Triple buffering enabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x68000 (TV_CTL) changed from 0x100000c0 to 0x000c0000
(WW) intel(0): Register 0x68010 (TV_CSC_Y) changed from 0x00000000 to 0x0332012d
(WW) intel(0): Register 0x68014 (TV_CSC_Y2) changed from 0x00000000 to 0x07d30104
(WW) intel(0): Register 0x68018 (TV_CSC_U) changed from 0x00000000 to 0x0733052d
(WW) intel(0): Register 0x6801c (TV_CSC_U2) changed from 0x00000000 to 0x05c70200
(WW) intel(0): Register 0x68020 (TV_CSC_V) changed from 0x00000000 to 0x0340030c
(WW) intel(0): Register 0x68024 (TV_CSC_V2) changed from 0x00000000 to 0x06d00200
(WW) intel(0): Register 0x68028 (TV_CLR_KNOBS) changed from 0x00000000 to 0x10606000
(WW) intel(0): Register 0x6802c (TV_CLR_LEVEL) changed from 0x00000000 to 0x010b00e1
(WW) intel(0): Register 0x68030 (TV_H_CTL_1) changed from 0x00000000 to 0x00400359
(WW) intel(0): Register 0x68034 (TV_H_CTL_2) changed from 0x00000000 to 0x80480022
(WW) intel(0): Register 0x68038 (TV_H_CTL_3) changed from 0x00000000 to 0x007c0344
(WW) intel(0): Register 0x6803c (TV_V_CTL_1) changed from 0x00000000 to 0x00f01415
(WW) intel(0): Register 0x68040 (TV_V_CTL_2) changed from 0x00000000 to 0x00060607
(WW) intel(0): Register 0x68044 (TV_V_CTL_3) changed from 0x00000000 to 0x80120001
(WW) intel(0): Register 0x68048 (TV_V_CTL_4) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x6804c (TV_V_CTL_5) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68050 (TV_V_CTL_6) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x68054 (TV_V_CTL_7) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68060 (TV_SC_CTL_1) changed from 0x00000000 to 0xc1710088
(WW) intel(0): Register 0x68064 (TV_SC_CTL_2) changed from 0x00000000 to 0x4e2d1dc8
(WW) intel(0): Register 0x68070 (TV_WIN_POS) changed from 0x00000000 to 0x00360024
(WW) intel(0): Register 0x68074 (TV_WIN_SIZE) changed from 0x00000000 to 0x02640198
(WW) intel(0): Register 0x68080 (TV_FILTER_CTL_1) changed from 0x00000000 to 0x8000085e
(WW) intel(0): Register 0x68084 (TV_FILTER_CTL_2) changed from 0x00000000 to 0x0000fafb
(WW) intel(0): Register 0x68088 (TV_FILTER_CTL_3) changed from 0x00000000 to 0x00007d7d
(WW) intel(0): Register 0x68100 (TV_H_LUMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x681ec (TV_H_LUMA_59) changed from 0x00000000 to 0x0000b060
(WW) intel(0): Register 0x68200 (TV_H_CHROMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x682ec (TV_H_CHROMA_59) changed from 0x00000000 to 0x0000b060
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MS[B]
	[1] 0	0	0xfdb00000 - 0xfdbfffff (0x100000) MS[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfddff000 - 0xfddfffff (0x1000) MX[B]
	[7] -1	0	0xfdffc000 - 0xfdffc0ff (0x100) MX[B]
	[8] -1	0	0xfdffd000 - 0xfdffd3ff (0x400) MX[B]
	[9] -1	0	0xfdff4000 - 0xfdff7fff (0x4000) MX[B]
	[10] -1	0	0xfdffe000 - 0xfdffe3ff (0x400) MX[B]
	[11] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B]
	[12] -1	0	0xfdfc0000 - 0xfdfdffff (0x20000) MX[B]
	[13] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfdb00000 - 0xfdbfffff (0x100000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[19] 0	0	0x0000ff00 - 0x0000ff07 (0x8) IS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[23] -1	0	0x0000f200 - 0x0000f20f (0x10) IX[B]
	[24] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[25] -1	0	0x0000f400 - 0x0000f403 (0x4) IX[B]
	[26] -1	0	0x0000f500 - 0x0000f507 (0x8) IX[B]
	[27] -1	0	0x0000f600 - 0x0000f603 (0x4) IX[B]
	[28] -1	0	0x0000f700 - 0x0000f707 (0x8) IX[B]
	[29] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000f900 - 0x0000f91f (0x20) IX[B]
	[35] -1	0	0x0000fa00 - 0x0000fa1f (0x20) IX[B]
	[36] -1	0	0x0000fb00 - 0x0000fb1f (0x20) IX[B]
	[37] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[38] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]
	[39] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]
	[40] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B](B)
	[41] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[42] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 488960 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 1955836 kB available
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers and 
	       large DRI memory manager reservation:
(II) intel(0): Allocating 6848 scanlines for pixmap cache
(II) intel(0): Success.
(II) intel(0): Memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00029fff: HW cursors (40 kB)
(II) intel(0): 0x0002a000-0x00031fff: logical 3D context (32 kB)
(II) intel(0): 0x00032000-0x00041fff: exa G965 state buffer (64 kB)
(II) intel(0): 0x00050000-0x04087fff: front buffer (65760 kB)
(II) intel(0): 0x0077f000:            end of stolen memory
(II) intel(0): 0x04088000-0x04097fff: xaa scratch (64 kB)
(II) intel(0): 0x04098000-0x04ea7fff: back buffer (14400 kB)
(II) intel(0): 0x04ea8000-0x05cb7fff: third buffer (14400 kB)
(II) intel(0): 0x05cb8000-0x06ac7fff: depth buffer (14400 kB)
(II) intel(0): 0x06ac8000-0x08ac7fff: textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): front buffer is not tiled
(II) intel(0): back buffer is tiled
(II) intel(0): third buffer is tiled
(II) intel(0): depth buffer is tiled
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): [drm] loaded kernel module for "i915" driver
(II) intel(0): [drm] DRM interface version 1.3
(II) intel(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) intel(0): [drm] added 8192 byte SAREA at 0x1efff000
(II) intel(0): [drm] mapped SAREA 0x1efff000 to 0x2b0767505000
(II) intel(0): [drm] framebuffer handle = 0xd0050000
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): [drm] Registers = 0xfdb00000
(II) intel(0): [drm] ring buffer = 0xd0000000
(II) intel(0): [drm] init sarea width,height = 1920 x 1920 (pitch 1920)
(II) intel(0): [drm] Back Buffer = 0xd4098000
(II) intel(0): [drm] Third Buffer = 0xd4ea8000
(II) intel(0): [drm] Depth Buffer = 0xd5cb8000
(II) intel(0): [drm] textures = 0xd6ac8000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xd0000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(**) intel(0): Option "XaaNoOffscreenPixmaps"
(II) intel(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): Current clock rate multiplier: 8
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x0077f000 (pgoffset 1919)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x04088000 (pgoffset 16520)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x04098000 (pgoffset 16536)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x04ea8000 (pgoffset 20136)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x05cb8000 (pgoffset 23736)
(II) intel(0): xf86BindGARTMemory: bind key 5 at 0x06ac8000 (pgoffset 27336)
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TMDS-1 is connected to pipe A
(II) intel(0):   Output TV is connected to pipe none
(**) Option "dpms" "true"
(**) intel(0): DPMS enabled
(II) intel(0): Set up textured video
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(II) intel(0): [DRI] installation complete
(II) intel(0): [drm] dma control initialized, using IRQ 16
(II) intel(0): direct rendering: Enabled
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(WW) intel(0): Option "AddARGBXVisuals" is not used
(WW) intel(0): Option "DisableGLXRootClipping" is not used
(WW) intel(0): Option "UseFBDev" is not used
(--) RandR disabled
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
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
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 338 x 203
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) intel(0): Output VGA disconnected
(II) intel(0): EDID for output VGA
(II) intel(0): Output LVDS connected
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID for output LVDS
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x800" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) intel(0): Printing probed modes for output LVDS
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 (48.4 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): Output TMDS-1 connected
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" removed.
(II) intel(0): EDID for output TMDS-1
(II) intel(0): Manufacturer: SAM  Model: 29f  Serial#: 0
(II) intel(0): Year: 2006  Week: 45
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max H-Image Size [cm]: horiz.: 16  vert.: 9
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.650 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported VESA Video Modes:
(II) intel(0): 640x480@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 148.5 MHz   Image Size:  160 x 90 mm
(II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 74.2 MHz   Image Size:  160 x 90 mm
(II) intel(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
(II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
(II) intel(0): Monitor name: SAMSUNG
(II) intel(0): Ranges: V min: 49  V max: 61 Hz, H min: 15  H max: 68 kHz, PixClock max 230 MHz
(II) intel(0): Number of EDID sections to follow: 1
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004c2d9f0200000000
(II) intel(0): 	2d100103801009780aaea5a6544c9926
(II) intel(0): 	14505420000001010101010101010101
(II) intel(0): 	010101010101023a801871382d40582c
(II) intel(0): 	4500a05a0000001e011d007251d01e20
(II) intel(0): 	6e285500a05a0000001e000000fc0053
(II) intel(0): 	414d53554e470a2020202020000000fd
(II) intel(0): 	00313d0f4417000a202020202020012f
(II) intel(0): EDID vendor "SAM", prod id 671
(II) intel(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1440x900" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) intel(0): Printing probed modes for output TMDS-1
(II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output TV disconnected
(II) intel(0): EDID for output TV
SetGrabKeysState - disabled

```

---

### Post by jwatsonoz on 2008-01-06
Hi there,

I'm new to Linux... and I don't have a full answer for you. Type in "overscan" as a search and you will see my situation by reading "How do I correct overscan on my HDTV?".

I notice that nobody has answered you (or me) yet... so I thought I would like to share what I do know so far.

As you know you can set x to ignore the EDID from the monitor. I had to do this because my tv was insisting on stating it was 1024x768 when it is actually widescreen and 1280x720.

I did this by adding the following to my xorg.conf

is section "screen" add this line:
Option "UseEdidFreqs" "false"

After i did this and added "1280x720" like so "again in the screen section":
SubSection "Display"
		Modes		"1280x720" "1024x768"
EndSubSection

I obtained the proper aspect ratio when I logged in. My TV does state that it supports higher resolutions but I wasn't able to get anything higher working. It looks pretty good at 1280x720 except for the overscan option (I miss about 3/4 inch around the screen - it is fine for watching tv but a bit rubbish for moving windows about.

If you read my other post you will see that I have been attempting different modelines without success so far.

Have read of:
[http://en.wikipedia.org/wiki/XFree86_Modeline](http://en.wikipedia.org/wiki/XFree86_Modeline)
(interesting info on modelines - try some of the modeline creator sites - I havent been able to get any modelines to work on mine though)

best of luck,
Jason

PS. Be forgiving if my advice is not the best as this is my first venture into linux and my first attempt to help somebody else - thanks!

---

### Post by gunja99 on 2008-01-06
Well I've done it! All that was required was change the p.size (zoom) on the TV settings to Just Scan, and it works. OK I have a couple of pixels missing at the top, but everythings there now! Can't believe how simple it was.

Well a total success story today. I ended up installing Windows XP to try and get the correct modelines, and then back to Ubuntu64, and obviously I had worked out the zoom problem by then. The sound problem through SPDIF very very simple, and instaleld XBMC. After a little while trying to compile I discovered that XBMC does NOT work with the 64bit version, so I shoved on the 32bit version of Gutsy (7.10), tried again, and it's fantastic! I can't believe I have XBMC back after all this time. It's in Alpha at the moment, but boy o boy what an alpha! Pictures seems to crash it, but I'm sure that'll be resolved in a little while, and it's 1080p content I want anyways, and it's back, and they run perfect.

Happy to help anyone who wants to get the great XBMC working on Linux, it's awesome!

---

