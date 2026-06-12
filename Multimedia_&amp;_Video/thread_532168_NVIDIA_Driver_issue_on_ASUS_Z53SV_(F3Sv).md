---
title: "NVIDIA Driver issue on ASUS Z53SV (F3Sv)"
date: 2007-08-22
forum: Multimedia &amp; Video
---

### Post by lubosz on 2007-08-22
[SIZE="4"]**My System**[/SIZE]

[IMG]http://geizhals.at/img/pix/261048.jpg[/IMG] 

**ASUS Z53SV-AS103G** ([Same model as F3Sv]("http://vip.asus.com/forum/view.aspx?id=20070621074216484")) 

**CPU:** Core 2 Duo T7500 2x 2.20GHz
**RAM:** 2048MB (2x 1024MB)
**HDD:** 200GB 
**GFX:** NVidia GeForce Go 8600M GS 256MB max.1024MB shared memory

**BIOS:** 206 (Current)
**nvidia driver:** 100.14.11
**Kernel:** 2.6.22-9-generic (Gutsy Gibbon 7.10)


[SIZE="4"]**My Problem**[/SIZE] ](*,)

My Gutsy installation runs very nice, the only problem is the xserver runs with the vesa driver.
I managed to get the nvidia driver to start on feisty with envy. The nvidia.com installer's setup only worked until reboot.
Now i had to upgrade to gutsy because the new kernel supports my wifi chip. No envy until october.

i tried some stuff on **gutsy:**
* nvidia.com driver => worked unsable until reboot, after reboot the xserver crashed
* nvidia-glx-new => xserver crashed, with other configs hardware reboot
* uninstalled all nvidia packages and restricted-common with apt, ran the envy uninstall script

Now after nvidia.com setup (NVIDIA-Linux-x86-100.14.11-pkg1.run) the server doesn't run after all, not even until reboot.

[SIZE="4"]**Xorg.conf**[/SIZE]

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "de"
    Option         "XkbVariant" "nodeadkeys"
    Option         "XkbOptions" "lv3:ralt_switch"
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

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    VendorName     "Asus"
    ModelName      "CMO"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "GeForce 8600M"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600M GS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "GeForce 8600M"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

[SIZE="4"]**Xorg.log**[/SIZE]

```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu
Current Operating System: Linux burning-studio 2.6.22-9-generic #1 SMP Fri Aug 3 00:50:37 GMT 2007 i686
Build Date: 26 July 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 22 16:55:43 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "GeForce 8600M"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
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
(**) RgbPath set to "/usr/lib/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81e5980
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
(II) PCI: 00:00:0: chip 8086,2a00 card 1043,14e7 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2a01 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1a:0: chip 8086,2834 card 1043,14e7 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card 1043,14e7 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card 1043,14e7 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,284b card 1043,1339 rev 03 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,283f card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,2841 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,2843 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,2845 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,2847 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:5: chip 8086,2849 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2830 card 1043,14e7 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card 1043,14e7 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card 1043,14e7 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card 1043,14e7 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev f3 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2815 card 1043,14e7 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,2850 card 1043,14e7 rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,2829 card 1043,14e7 rev 03 class 01,06,01 hdr 00
(II) PCI: 01:00:0: chip 10de,0425 card 1043,1514 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 1969,1048 card 1043,14e5 rev b0 class 02,00,00 hdr 00
(II) PCI: 03:00:0: chip 8086,4229 card 8086,1101 rev 61 class 02,80,00 hdr 00
(II) PCI: 09:01:0: chip 1180,0832 card 1043,14e7 rev 05 class 0c,00,10 hdr 80
(II) PCI: 09:01:1: chip 1180,0822 card 1043,14e7 rev 22 class 08,05,00 hdr 80
(II) PCI: 09:01:2: chip 1180,0843 card 1043,14e7 rev 12 class 08,80,00 hdr 80
(II) PCI: 09:01:3: chip 1180,0592 card 1043,14e7 rev 12 class 08,80,00 hdr 80
(II) PCI: 09:01:4: chip 1180,0852 card 1043,14e7 rev 12 class 08,80,00 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,9), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf7f00000 - 0xfdffffff (0x6100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xbdf00000 - 0xddefffff (0x20000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfe000000 - 0xfe0fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfe100000 - 0xfe1fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:2), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:28:3), (0,5,5), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:28:4), (0,6,7), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0xfe200000 - 0xfe9fffff (0x800000) MX[B]
(II) Bus 6 prefetchable memory range:
	[0] -1	0	0xddf00000 - 0xdfefffff (0x2000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 8: bridge is at (0:28:5), (0,8,8), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 9: bridge is at (0:30:0), (0,9,9), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 9 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x0425) rev 161, Mem @ 0xfc000000/24, 0xc0000000/28, 0xfa000000/25, I/O @ 0xbc00/7, BIOS @ 0xfdfe0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xfeafe800 - 0xfeafe8ff (0x100) MX[B]
	[1] -1	0	0xfeafec00 - 0xfeafecff (0x100) MX[B]
	[2] -1	0	0xfeaff000 - 0xfeaff0ff (0x100) MX[B]
	[3] -1	0	0xfeaff400 - 0xfeaff4ff (0x100) MX[B]
	[4] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[5] -1	0	0xfe1fe000 - 0xfe1fffff (0x2000) MX[B]
	[6] -1	0	0xfe0c0000 - 0xfe0fffff (0x40000) MX[B]
	[7] -1	0	0xfebff800 - 0xfebfffff (0x800) MX[B]
	[8] -1	0	0xfebff000 - 0xfebff3ff (0x400) MX[B]
	[9] -1	0	0xfebf8000 - 0xfebfbfff (0x4000) MX[B]
	[10] -1	0	0xfebff400 - 0xfebff7ff (0x400) MX[B]
	[11] -1	0	0xfdfe0000 - 0xfdffffff (0x20000) MX[B](B)
	[12] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[16] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[18] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[19] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[26] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[27] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[29] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
	[30] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeafe800 - 0xfeafe8ff (0x100) MX[B]
	[1] -1	0	0xfeafec00 - 0xfeafecff (0x100) MX[B]
	[2] -1	0	0xfeaff000 - 0xfeaff0ff (0x100) MX[B]
	[3] -1	0	0xfeaff400 - 0xfeaff4ff (0x100) MX[B]
	[4] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[5] -1	0	0xfe1fe000 - 0xfe1fffff (0x2000) MX[B]
	[6] -1	0	0xfe0c0000 - 0xfe0fffff (0x40000) MX[B]
	[7] -1	0	0xfebff800 - 0xfebfffff (0x800) MX[B]
	[8] -1	0	0xfebff000 - 0xfebff3ff (0x400) MX[B]
	[9] -1	0	0xfebf8000 - 0xfebfbfff (0x4000) MX[B]
	[10] -1	0	0xfebff400 - 0xfebff7ff (0x400) MX[B]
	[11] -1	0	0xfdfe0000 - 0xfdffffff (0x20000) MX[B](B)
	[12] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[16] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[18] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[19] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[26] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[27] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[29] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
	[30] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B](B)
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
	[4] -1	0	0xfeafe800 - 0xfeafe8ff (0x100) MX[B]
	[5] -1	0	0xfeafec00 - 0xfeafecff (0x100) MX[B]
	[6] -1	0	0xfeaff000 - 0xfeaff0ff (0x100) MX[B]
	[7] -1	0	0xfeaff400 - 0xfeaff4ff (0x100) MX[B]
	[8] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[9] -1	0	0xfe1fe000 - 0xfe1fffff (0x2000) MX[B]
	[10] -1	0	0xfe0c0000 - 0xfe0fffff (0x40000) MX[B]
	[11] -1	0	0xfebff800 - 0xfebfffff (0x800) MX[B]
	[12] -1	0	0xfebff000 - 0xfebff3ff (0x400) MX[B]
	[13] -1	0	0xfebf8000 - 0xfebfbfff (0x4000) MX[B]
	[14] -1	0	0xfebff400 - 0xfebff7ff (0x400) MX[B]
	[15] -1	0	0xfdfe0000 - 0xfdffffff (0x20000) MX[B](B)
	[16] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[17] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[22] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[24] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[25] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[32] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[33] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[34] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[35] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
	[36] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B](B)
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
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.11  Wed Jun 13 18:58:58 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
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
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) NVIDIA dlloader X Driver  100.14.11  Wed Jun 13 18:23:34 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeafe800 - 0xfeafe8ff (0x100) MX[B]
	[5] -1	0	0xfeafec00 - 0xfeafecff (0x100) MX[B]
	[6] -1	0	0xfeaff000 - 0xfeaff0ff (0x100) MX[B]
	[7] -1	0	0xfeaff400 - 0xfeaff4ff (0x100) MX[B]
	[8] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[9] -1	0	0xfe1fe000 - 0xfe1fffff (0x2000) MX[B]
	[10] -1	0	0xfe0c0000 - 0xfe0fffff (0x40000) MX[B]
	[11] -1	0	0xfebff800 - 0xfebfffff (0x800) MX[B]
	[12] -1	0	0xfebff000 - 0xfebff3ff (0x400) MX[B]
	[13] -1	0	0xfebf8000 - 0xfebfbfff (0x4000) MX[B]
	[14] -1	0	0xfebff400 - 0xfebff7ff (0x400) MX[B]
	[15] -1	0	0xfdfe0000 - 0xfdffffff (0x20000) MX[B](B)
	[16] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[17] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[22] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[24] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[25] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[32] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[33] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[34] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[35] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
	[36] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeafe800 - 0xfeafe8ff (0x100) MX[B]
	[5] -1	0	0xfeafec00 - 0xfeafecff (0x100) MX[B]
	[6] -1	0	0xfeaff000 - 0xfeaff0ff (0x100) MX[B]
	[7] -1	0	0xfeaff400 - 0xfeaff4ff (0x100) MX[B]
	[8] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[9] -1	0	0xfe1fe000 - 0xfe1fffff (0x2000) MX[B]
	[10] -1	0	0xfe0c0000 - 0xfe0fffff (0x40000) MX[B]
	[11] -1	0	0xfebff800 - 0xfebfffff (0x800) MX[B]
	[12] -1	0	0xfebff000 - 0xfebff3ff (0x400) MX[B]
	[13] -1	0	0xfebf8000 - 0xfebfbfff (0x4000) MX[B]
	[14] -1	0	0xfebff400 - 0xfebff7ff (0x400) MX[B]
	[15] -1	0	0xfdfe0000 - 0xfdffffff (0x20000) MX[B](B)
	[16] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[17] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[25] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[27] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[28] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[29] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[30] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[31] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[35] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[37] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[38] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
	[39] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B](B)
	[40] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[41] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
[COLOR="Red"](EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***[/COLOR]
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

---

### Post by tseliot on 2007-08-22
> **lubosz said:**
> Now i had to upgrade to gutsy because the new kernel supports my wifi chip. No envy until october.
I think that for one you'll be happy to be wrong:
[http://albertomilone.com/wordpress/?p=107](http://albertomilone.com/wordpress/?p=107)

---

### Post by A3sthetix on 2007-08-22
Damn your good! I would not be using Linux if you were not around.

---

### Post by lubosz on 2007-08-22
wow!!!!! it works :D
tseliot your script rocks! it's like magic.

---

### Post by dreadlord_chris on 2007-08-22
> **tseliot said:**
> I think that for one you'll be happy to be wrong:
[http://albertomilone.com/wordpress/?p=107](http://albertomilone.com/wordpress/?p=107)

I too thank you for the little work-around
and for continued Envy post to your blog - which is where I first read about this....

---

