---
title: "How do you remove MESA drivers?"
date: 2008-07-08
forum: Multimedia Software
---

### Post by DOS4dinner on 2008-07-08
I got my drivers setup thanks to envy. However, it still says that I am using the MESA drivers for OpenGL stuff. How do I change that?

My machine:
Pentium 4 @2.6 ghz
ATI Radeon 9800 pro 128mb
1 gig of RAM

Thanks in advance.

Here is my xorg.0.log, if it helps:
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(WW) fglrx(0): could not detect X server version (query_status=-3)
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xf0000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xf0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 7167
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT

---

### Post by overdrank on 2008-07-08
> **DOS4dinner said:**
> I got my drivers setup thanks to envy. However, it still says that I am using the MESA drivers for OpenGL stuff. How do I change that?

My machine:
Pentium 4 @2.6 ghz
ATI Radeon 9800 pro 128mb
1 gig of RAM

```
Thanks in advance.

Here is my xorg.0.log, if it helps:
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(WW) fglrx(0): could not detect X server version (query_status=-3)
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xf0000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xf0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 7167
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
```

Hi and I am using a ATI 9600 on Hardy and it still say mesa on the glxinfo. But the desktop effects work but I have not played any games.
Well sort of but that is another story. :)

---

### Post by zgornel on 2008-07-08
Try doing a ```
sudo modprobe fglrx
``` and then ```
sudo depmod -a
```. The 'fglrx' kernel module might not be loaded so X reverts to inderect rendering. There is no reason to remove mesa.

---

### Post by DOS4dinner on 2008-07-08
> **zgornel said:**
> Try doing a ```
sudo modprobe fglrx
``` and then ```
sudo depmod -a
```. The 'fglrx' kernel module might not be loaded so X reverts to inderect rendering. There is no reason to remove mesa.

Tried it, did not do a thing. Frets on Fire and the fancy screensavers still run at a crawl and it still says I am using mesa.

---

### Post by soxs on 2008-07-08
try method 2 if method one fails (worked for me and at least 2 more) 
[http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide)

---

### Post by DOS4dinner on 2008-07-08
> **soxs said:**
> try method 2 if method one fails (worked for me and at least 2 more) 
[http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide)

I was afraid it would come to that. I used the envy installer, and the ATI catalyst control center found my card just fine, but it just is using mesa for OpenGL instead of my ATI card. I hoped that there would be just some way of switching what openGL driver it uses.

I will wait a bit before I do that, though. Hopefully someone will have an answer.

---

### Post by soxs on 2008-07-08
post your /var/log/Xorg.0.log

---

### Post by DOS4dinner on 2008-07-08
Here is the whole thing: (sorry for being long)


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
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux jeff-desktop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul  8 13:24:47 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
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
(**) Extension "Composite" is enabled
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
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
(II) PCI: 00:00:0: chip 8086,2578 card 1028,0157 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2579 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:06:0: chip 8086,257e card 0000,0000 rev 02 class 08,80,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,24d2 card 1028,0157 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1028,0157 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 1028,0157 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1028,0157 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1028,0157 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1028,0157 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,24d1 card 1028,0157 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1028,0157 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4e48 card 1002,3002 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,4e68 card 1002,3003 rev 00 class 03,80,00 hdr 00
(II) PCI: 02:01:0: chip 1814,0301 card 1462,b834 rev 00 class 02,80,00 hdr 00
(II) PCI: 02:02:0: chip 1102,0006 card 1102,1003 rev 00 class 04,01,00 hdr 80
(II) PCI: 02:02:1: chip 1102,7004 card 1102,1003 rev 00 class 09,80,00 hdr 80
(II) PCI: 02:08:0: chip 8086,1050 card 1028,0157 rev 02 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe900000 - 0xfeafffff (0x200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xf7ffffff (0x10000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] rev 0, Mem @ 0xf0000000/27, 0xfe9e0000/16, I/O @ 0xde00/8, BIOS @ 0xfea00000/17
(--) PCI: (1:0:1) ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary) rev 0, Mem @ 0xe8000000/27, 0xfe9f0000/16
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe7ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfe8f7000 - 0xfe8f7fff (0x1000) MX[B]
	[1] -1	0	0xfe8f8000 - 0xfe8fffff (0x8000) MX[B]
	[2] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[3] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[4] -1	0	0xfecf0000 - 0xfecf0fff (0x1000) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[7] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[8] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[9] -1	0	0xfe9e0000 - 0xfe9effff (0x10000) MX[B](B)
	[10] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0x0000cf40 - 0x0000cf7f (0x40) IX[B]
	[12] -1	0	0x0000cf18 - 0x0000cf1f (0x8) IX[B]
	[13] -1	0	0x0000cf20 - 0x0000cf3f (0x20) IX[B]
	[14] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[15] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[16] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[17] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[18] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[19] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[26] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[27] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[28] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[29] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe8f7000 - 0xfe8f7fff (0x1000) MX[B]
	[1] -1	0	0xfe8f8000 - 0xfe8fffff (0x8000) MX[B]
	[2] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[3] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[4] -1	0	0xfecf0000 - 0xfecf0fff (0x1000) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[7] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[8] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[9] -1	0	0xfe9e0000 - 0xfe9effff (0x10000) MX[B](B)
	[10] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0x0000cf40 - 0x0000cf7f (0x40) IX[B]
	[12] -1	0	0x0000cf18 - 0x0000cf1f (0x8) IX[B]
	[13] -1	0	0x0000cf20 - 0x0000cf3f (0x20) IX[B]
	[14] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[15] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[16] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[17] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[18] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[19] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[26] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[27] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[28] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[29] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
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
	[4] -1	0	0xfe8f7000 - 0xfe8f7fff (0x1000) MX[B]
	[5] -1	0	0xfe8f8000 - 0xfe8fffff (0x8000) MX[B]
	[6] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfecf0000 - 0xfecf0fff (0x1000) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe9e0000 - 0xfe9effff (0x10000) MX[B](B)
	[14] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000cf40 - 0x0000cf7f (0x40) IX[B]
	[18] -1	0	0x0000cf18 - 0x0000cf1f (0x8) IX[B]
	[19] -1	0	0x0000cf20 - 0x0000cf3f (0x20) IX[B]
	[20] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[21] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[22] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[23] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[24] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[25] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[32] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[33] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[34] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[35] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
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
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.47.3
	Module class: X.Org Video Driver
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.47.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.476                    
(II) ATI Proprietary Linux Driver Build Date: Mar 29 2008 00:05:22
(--) Assigning device section with no busID to primary device
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x4E48) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8f7000 - 0xfe8f7fff (0x1000) MX[B]
	[5] -1	0	0xfe8f8000 - 0xfe8fffff (0x8000) MX[B]
	[6] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfecf0000 - 0xfecf0fff (0x1000) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe9e0000 - 0xfe9effff (0x10000) MX[B](B)
	[14] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000cf40 - 0x0000cf7f (0x40) IX[B]
	[18] -1	0	0x0000cf18 - 0x0000cf1f (0x8) IX[B]
	[19] -1	0	0x0000cf20 - 0x0000cf3f (0x20) IX[B]
	[20] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[21] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[22] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[23] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[24] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[25] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[32] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[33] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[34] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[35] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x820c768
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8f7000 - 0xfe8f7fff (0x1000) MX[B]
	[5] -1	0	0xfe8f8000 - 0xfe8fffff (0x8000) MX[B]
	[6] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfecf0000 - 0xfecf0fff (0x1000) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe9e0000 - 0xfe9effff (0x10000) MX[B](B)
	[14] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000cf40 - 0x0000cf7f (0x40) IX[B]
	[21] -1	0	0x0000cf18 - 0x0000cf1f (0x8) IX[B]
	[22] -1	0	0x0000cf20 - 0x0000cf3f (0x20) IX[B]
	[23] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[24] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[25] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[26] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[27] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[28] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[29] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[30] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[31] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[32] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[35] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[36] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[37] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[38] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): PCI bus 1 card 0 func 0
(II) fglrx(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(**) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "RADEON 9800 PRO" (Chipset = 0x4e48)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x3002)
(--) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xf0000000
(--) fglrx(0): MMIO registers at 0xfe9e0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 131072 kB
(II) fglrx(0): VESA VBE OEM: ATI R350
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: R350
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.47.3
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Using adapter: 1:0.0.
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) fglrx(0): Connected Display1: DFP on internal TMDS [tmds1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: VSC  Model: e11  Serial#: 16843009
(II) fglrx(0): Year: 2003  Week: 13
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 38  vert.: 31
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.634 redY: 0.354   greenX: 0.304 greenY: 0.581
(II) fglrx(0): blueX: 0.143 blueY: 0.102   whiteX: 0.310 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  376 x 310 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Serial No: A1W031300355
(II) fglrx(0): Ranges: V min: 50  V max: 85 Hz, H min: 30  H max: 82 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: VP191b
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff005a63110e01010101
(II) fglrx(0): 	0d0d010380261f782a6f86a25a4d9424
(II) fglrx(0): 	1a4f54bfef808180714f615945593159
(II) fglrx(0): 	310a01010101302a009851002a403070
(II) fglrx(0): 	130078361100001e000000ff00413157
(II) fglrx(0): 	3033313330303335350a000000fd0032
(II) fglrx(0): 	551e520e000a202020202020000000fc
(II) fglrx(0): 	005650313931620a20202020202000d6
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - DFP on internal TMDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay not supported on this hardware
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 34 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 0)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 (80.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync (74.6 kHz)
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1152x864": 119.7 MHz (scaled from 0.0 MHz), 77.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 +hsync (77.1 kHz)
(**) fglrx(0):  Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 (67.5 kHz)
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"x70.0   96.76  1152 1224 1344 1536  864 865 868 900 +hsync (63.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
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
(**) fglrx(0): *Mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"x60.0   38.16  1024 1048 1152 1280  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"x60.0   31.48  848 864 952 1056  480 481 484 497 +hsync (29.8 kHz)
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
(**) fglrx(0): *Mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"x60.0   32.66  720 744 816 912  576 577 580 597 +hsync (35.8 kHz)
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
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(--) fglrx(0): Display dimensions: (380, 310) mm
(--) fglrx(0): DPI set to (85, 83)
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 (80.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync (74.6 kHz)
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1152x864": 119.7 MHz (scaled from 0.0 MHz), 77.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 +hsync (77.1 kHz)
(**) fglrx(0):  Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 (67.5 kHz)
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"x70.0   96.76  1152 1224 1344 1536  864 865 868 900 +hsync (63.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
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
(**) fglrx(0): *Mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"x60.0   38.16  1024 1048 1152 1280  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"x60.0   31.48  848 864 952 1056  480 481 484 497 +hsync (29.8 kHz)
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
(**) fglrx(0): *Mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"x60.0   32.66  720 744 816 912  576 577 580 597 +hsync (35.8 kHz)
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
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(II) fglrx(0): [pci] find AGP GART
(EE) fglrx(0): [agp] unable to acquire AGP, error -1023
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfe9e0000 - 0xfe9effff (0x10000) MX[B]
	[1] 0	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfe8f7000 - 0xfe8f7fff (0x1000) MX[B]
	[7] -1	0	0xfe8f8000 - 0xfe8fffff (0x8000) MX[B]
	[8] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[9] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[10] -1	0	0xfecf0000 - 0xfecf0fff (0x1000) MX[B]
	[11] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[12] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[13] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[14] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[15] -1	0	0xfe9e0000 - 0xfe9effff (0x10000) MX[B](B)
	[16] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[20] 0	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000cf40 - 0x0000cf7f (0x40) IX[B]
	[24] -1	0	0x0000cf18 - 0x0000cf1f (0x8) IX[B]
	[25] -1	0	0x0000cf20 - 0x0000cf3f (0x20) IX[B]
	[26] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[27] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[28] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[29] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[30] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[31] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[32] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[33] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[34] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[35] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[37] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[38] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[39] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[40] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[41] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(WW) fglrx(0): could not detect X server version (query_status=-3)
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xf0000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xf0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 7167
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(II) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
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
(II) AIGLX: Screen 0 is not DRI capable
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
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
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) 3rd Button detected: disabling emulate3Button
```

---

### Post by soxs on 2008-07-08
these are the evil ones:

```
(EE) fglrx(0): [agp] unable to acquire AGP, error -1023
(EE) fglrx(0): cannot init AGP
```

plx post your /etc/X11/xorg.conf
there my lie the cause

I will have look at tomorrow (it's 11:49 PM and I am somewhat tired)

---

### Post by DOS4dinner on 2008-07-08
> **soxs said:**
> these are the evil ones:

```
(EE) fglrx(0): [agp] unable to acquire AGP, error -1023
(EE) fglrx(0): cannot init AGP
```

plx post your /etc/X11/xorg.conf
there my lie the cause

I will have look at tomorrow (it's 11:49 PM and I am somewhat tired)

Here is my xorg.conf:

```
# xorg.conf (X.Org X Window System server configuration file)
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

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

Thanks for your help. If I can get this working, I can be rid of Windows forever.

---

### Post by DOS4dinner on 2008-07-09
Bumped in name of Punching Bill Gates in the face. If bumping is not allowed, forgive me for my error.

---

### Post by soxs on 2008-07-09
Replace ```
Load		"glx"
``` with:

```
        Load            "bitmap"
        Load            "vbe"
        Load            "ddc"
        Load            "freetype"
        Load            "int10"
        Load            "glx"
        Load            "dri"
        Load            "extmod"
```

Another thing you can try is, adding these to lines to you DeviceSection:
```
        Option          "DRI"   "1"
        Option          "UseInternalAGPGART"    "1" ## tinker with 1 or 0, it won't hurt your system, just will check if the internal or the fglrx shipped agpgart works
```

---

### Post by DOS4dinner on 2008-07-09
It won't let me make the changes, as I do not have the permissions. (I do have my admin password). How do I change it?

---

### Post by DOS4dinner on 2008-07-09
Nevermind, it saved. Now checking to see if it worked...

---

### Post by DOS4dinner on 2008-07-09
Nope. Still the same. I made the change to the xorg.conf, but it still is using mesa.  I have not yet checked putting in a 0 in the option part, as I was not quite sure if you meant both of the lines or just that last one. Here is my current log:


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
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux jeff-desktop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul  9 09:16:35 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
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
(**) Extension "Composite" is enabled
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
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
(II) PCI: 00:00:0: chip 8086,2578 card 1028,0157 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2579 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:06:0: chip 8086,257e card 0000,0000 rev 02 class 08,80,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,24d2 card 1028,0157 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1028,0157 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 1028,0157 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1028,0157 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1028,0157 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1028,0157 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,24d1 card 1028,0157 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1028,0157 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4e48 card 1002,3002 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,4e68 card 1002,3003 rev 00 class 03,80,00 hdr 00
(II) PCI: 02:01:0: chip 1814,0301 card 1462,b834 rev 00 class 02,80,00 hdr 00
(II) PCI: 02:02:0: chip 1102,0006 card 1102,1003 rev 00 class 04,01,00 hdr 80
(II) PCI: 02:02:1: chip 1102,7004 card 1102,1003 rev 00 class 09,80,00 hdr 80
(II) PCI: 02:08:0: chip 8086,1050 card 1028,0157 rev 02 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe900000 - 0xfeafffff (0x200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xf7ffffff (0x10000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] rev 0, Mem @ 0xf0000000/27, 0xfe9e0000/16, I/O @ 0xde00/8, BIOS @ 0xfea00000/17
(--) PCI: (1:0:1) ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary) rev 0, Mem @ 0xe8000000/27, 0xfe9f0000/16
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe7ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfe8f7000 - 0xfe8f7fff (0x1000) MX[B]
	[1] -1	0	0xfe8f8000 - 0xfe8fffff (0x8000) MX[B]
	[2] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[3] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[4] -1	0	0xfecf0000 - 0xfecf0fff (0x1000) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[7] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[8] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[9] -1	0	0xfe9e0000 - 0xfe9effff (0x10000) MX[B](B)
	[10] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0x0000cf40 - 0x0000cf7f (0x40) IX[B]
	[12] -1	0	0x0000cf18 - 0x0000cf1f (0x8) IX[B]
	[13] -1	0	0x0000cf20 - 0x0000cf3f (0x20) IX[B]
	[14] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[15] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[16] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[17] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[18] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[19] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[26] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[27] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[28] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[29] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe8f7000 - 0xfe8f7fff (0x1000) MX[B]
	[1] -1	0	0xfe8f8000 - 0xfe8fffff (0x8000) MX[B]
	[2] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[3] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[4] -1	0	0xfecf0000 - 0xfecf0fff (0x1000) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[7] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[8] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[9] -1	0	0xfe9e0000 - 0xfe9effff (0x10000) MX[B](B)
	[10] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0x0000cf40 - 0x0000cf7f (0x40) IX[B]
	[12] -1	0	0x0000cf18 - 0x0000cf1f (0x8) IX[B]
	[13] -1	0	0x0000cf20 - 0x0000cf3f (0x20) IX[B]
	[14] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[15] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[16] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[17] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[18] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[19] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[26] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[27] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[28] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[29] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
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
	[4] -1	0	0xfe8f7000 - 0xfe8f7fff (0x1000) MX[B]
	[5] -1	0	0xfe8f8000 - 0xfe8fffff (0x8000) MX[B]
	[6] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfecf0000 - 0xfecf0fff (0x1000) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe9e0000 - 0xfe9effff (0x10000) MX[B](B)
	[14] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000cf40 - 0x0000cf7f (0x40) IX[B]
	[18] -1	0	0x0000cf18 - 0x0000cf1f (0x8) IX[B]
	[19] -1	0	0x0000cf20 - 0x0000cf3f (0x20) IX[B]
	[20] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[21] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[22] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[23] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[24] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[25] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[32] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[33] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[34] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[35] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.47.3
	Module class: X.Org Video Driver
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.47.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.476                    
(II) ATI Proprietary Linux Driver Build Date: Mar 29 2008 00:05:22
(--) Assigning device section with no busID to primary device
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x4E48) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8f7000 - 0xfe8f7fff (0x1000) MX[B]
	[5] -1	0	0xfe8f8000 - 0xfe8fffff (0x8000) MX[B]
	[6] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfecf0000 - 0xfecf0fff (0x1000) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe9e0000 - 0xfe9effff (0x10000) MX[B](B)
	[14] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000cf40 - 0x0000cf7f (0x40) IX[B]
	[18] -1	0	0x0000cf18 - 0x0000cf1f (0x8) IX[B]
	[19] -1	0	0x0000cf20 - 0x0000cf3f (0x20) IX[B]
	[20] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[21] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[22] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[23] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[24] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[25] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[32] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[33] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[34] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[35] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x820c768
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8f7000 - 0xfe8f7fff (0x1000) MX[B]
	[5] -1	0	0xfe8f8000 - 0xfe8fffff (0x8000) MX[B]
	[6] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfecf0000 - 0xfecf0fff (0x1000) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe9e0000 - 0xfe9effff (0x10000) MX[B](B)
	[14] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000cf40 - 0x0000cf7f (0x40) IX[B]
	[21] -1	0	0x0000cf18 - 0x0000cf1f (0x8) IX[B]
	[22] -1	0	0x0000cf20 - 0x0000cf3f (0x20) IX[B]
	[23] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[24] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[25] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[26] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[27] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[28] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[29] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[30] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[31] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[32] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[35] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[36] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[37] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[38] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): PCI bus 1 card 0 func 0
(II) fglrx(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "dri" "1"
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "UseInternalAGPGART" "1"
(II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(**) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "RADEON 9800 PRO" (Chipset = 0x4e48)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x3002)
(--) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xf0000000
(--) fglrx(0): MMIO registers at 0xfe9e0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 131072 kB
(II) fglrx(0): VESA VBE OEM: ATI R350
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: R350
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.47.3
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Using adapter: 1:0.0.
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) fglrx(0): Connected Display1: DFP on internal TMDS [tmds1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: VSC  Model: e11  Serial#: 16843009
(II) fglrx(0): Year: 2003  Week: 13
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 38  vert.: 31
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.634 redY: 0.354   greenX: 0.304 greenY: 0.581
(II) fglrx(0): blueX: 0.143 blueY: 0.102   whiteX: 0.310 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  376 x 310 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Serial No: A1W031300355
(II) fglrx(0): Ranges: V min: 50  V max: 85 Hz, H min: 30  H max: 82 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: VP191b
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff005a63110e01010101
(II) fglrx(0): 	0d0d010380261f782a6f86a25a4d9424
(II) fglrx(0): 	1a4f54bfef808180714f615945593159
(II) fglrx(0): 	310a01010101302a009851002a403070
(II) fglrx(0): 	130078361100001e000000ff00413157
(II) fglrx(0): 	3033313330303335350a000000fd0032
(II) fglrx(0): 	551e520e000a202020202020000000fc
(II) fglrx(0): 	005650313931620a20202020202000d6
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - DFP on internal TMDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay not supported on this hardware
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 34 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 0)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 (80.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync (74.6 kHz)
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1152x864": 119.7 MHz (scaled from 0.0 MHz), 77.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 +hsync (77.1 kHz)
(**) fglrx(0):  Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 (67.5 kHz)
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"x70.0   96.76  1152 1224 1344 1536  864 865 868 900 +hsync (63.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
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
(**) fglrx(0): *Mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"x60.0   38.16  1024 1048 1152 1280  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"x60.0   31.48  848 864 952 1056  480 481 484 497 +hsync (29.8 kHz)
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
(**) fglrx(0): *Mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"x60.0   32.66  720 744 816 912  576 577 580 597 +hsync (35.8 kHz)
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
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(--) fglrx(0): Display dimensions: (380, 310) mm
(--) fglrx(0): DPI set to (85, 83)
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 (80.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync (74.6 kHz)
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1152x864": 119.7 MHz (scaled from 0.0 MHz), 77.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 +hsync (77.1 kHz)
(**) fglrx(0):  Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 (67.5 kHz)
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"x70.0   96.76  1152 1224 1344 1536  864 865 868 900 +hsync (63.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
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
(**) fglrx(0): *Mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"x60.0   38.16  1024 1048 1152 1280  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"x60.0   31.48  848 864 952 1056  480 481 484 497 +hsync (29.8 kHz)
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
(**) fglrx(0): *Mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"x60.0   32.66  720 744 816 912  576 577 580 597 +hsync (35.8 kHz)
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
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(**) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): using built in AGPGART module: yes
(**) fglrx(0): ATI GART size: 256 MB
(II) fglrx(0): [pci] find AGP GART
(EE) fglrx(0): [agp] unable to acquire AGP, error -1023
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfe9e0000 - 0xfe9effff (0x10000) MX[B]
	[1] 0	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfe8f7000 - 0xfe8f7fff (0x1000) MX[B]
	[7] -1	0	0xfe8f8000 - 0xfe8fffff (0x8000) MX[B]
	[8] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[9] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[10] -1	0	0xfecf0000 - 0xfecf0fff (0x1000) MX[B]
	[11] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[12] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[13] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[14] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[15] -1	0	0xfe9e0000 - 0xfe9effff (0x10000) MX[B](B)
	[16] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[20] 0	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000cf40 - 0x0000cf7f (0x40) IX[B]
	[24] -1	0	0x0000cf18 - 0x0000cf1f (0x8) IX[B]
	[25] -1	0	0x0000cf20 - 0x0000cf3f (0x20) IX[B]
	[26] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[27] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[28] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[29] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[30] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[31] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[32] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[33] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[34] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[35] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[37] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[38] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[39] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[40] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[41] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(WW) fglrx(0): could not detect X server version (query_status=-3)
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xf0000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xf0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 7167
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(II) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
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
(II) AIGLX: Screen 0 is not DRI capable
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
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
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
```

---

### Post by Muffinabus on 2008-07-09
Thought I'd chime in and say that I'm experiencing the same exact problem.  No matter what I do, it seems the darned driver is stuck on Mesa.  I've tried the suggestions in this thread to no avail.

EDIT:  Though I don't have the same AGP errors that DOS4dinner has.

---

### Post by piousp on 2008-07-09
MESA is hell. 
You may want to check out [this thread]("http://ubuntuforums.org/showthread.php?t=515573&highlight=MESA+HELL") and [this one]("http://ubuntuforums.org/showthread.php?t=789641&highlight=MESA+HELL") too

Good luck!

---

### Post by DOS4dinner on 2008-07-09
> **piousp said:**
> MESA is hell. 
You may want to check out [this thread]("http://ubuntuforums.org/showthread.php?t=515573&highlight=MESA+HELL") and [this one]("http://ubuntuforums.org/showthread.php?t=789641&highlight=MESA+HELL") too

Good luck!

PIKMIN!!!!!!!!Love your avatar.

Hopefully someone can figure this out.If I do a manual method 2 install, will that hopefully set it up without those mesa drivers? Also, if I plan to do a method 2 install, do I need to uninstall envy and restore my xorg.conf to the way it was? 

On another note, why on earth isn't there a button or function in Ubuntu that says "Turn off MESA drivers".:?

---

### Post by soxs on 2008-07-09
only change the IinternalAGPGart value

keep your current adjusted xorg.conf (make a backup to your desktop with: ```
sudo cp -vf /etc/X11/xorg.conf ~/Desktop/xorg.conf.txt; sudo chmod 755 ~/Desktop/xorg.conf.txt
```)

then uninstall the current atidriver with envy. You can now remove or keep envyng, doesn't really matter, as long as you don't touch it.

-> run method 2

---

### Post by DOS4dinner on 2008-07-09
Okay. I shall begin doing method 2. Hopefully it will work.

---

### Post by DOS4dinner on 2008-07-09
Uninstalled the ATI driver with envy. Tried to use Method 2, but It stops mid-install with this error:
 Generating package: Ubuntu/hardy
Resolving build dependencies...
./packages/Ubuntu/ati-packager.sh: 347: sh -c '/usr/sbin/synaptic --set-selections --non-interactive --hide-main-window < /tmp/fileTcJZYW': not found
Unable to resolve  build-essential fakeroot.  Please manually install and try again.

What now?

---

### Post by DOS4dinner on 2008-07-09
Hmm...this does not look promising. Anyone have any other ideas?

---

### Post by zgornel on 2008-07-09
You could try using the open source driver :D . Radeon 9800 is fully supported and should work great with compiz.

---

### Post by DOS4dinner on 2008-07-09
> **zgornel said:**
> You could try using the open source driver :D . Radeon 9800 is fully supported and should work great with compiz.

How do I go about enabling that? Also, does it support 3D (as that is my main issue--2D works fine)

---

### Post by zgornel on 2008-07-09
Section Device of xorg.conf should look like this:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"radeon"
EndSection

```
Also, make sure you have xserver-xorg-video-ati installed. You can check the man page for xorg.conf options for the driver:
```
man radeon
```. It should support 3D quite well. Your problem is not only 3D, if DRI is not initialized you do not have 2D acceleration as well which means videos will be choppy and high content video will be unplayable.

---

### Post by DOS4dinner on 2008-07-09
> **zgornel said:**
> Section Device of xorg.conf should look like this:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"radeon"
EndSection

```
Also, make sure you have xserver-xorg-video-ati installed. You can check the man page for xorg.conf options for the driver:
```
man radeon
```. It should support 3D quite well. Your problem is not only 3D, if DRI is not initialized you do not have 2D acceleration as well which means videos will be choppy and high content video will be unplayable.

Do I need to use the envy installer or another form of installation, or do I just put in the code? Note: At this point, I have no driver installed that I know of. I used envy to uninstall the ATI driver.

---

### Post by DOS4dinner on 2008-07-09
Re-installed my ATI drivers with envy and edited the conf as you requested. Seems to make no difference.

---

### Post by soxs on 2008-07-10
> **DOS4dinner said:**
> Uninstalled the ATI driver with envy. Tried to use Method 2, but It stops mid-install with this error:
 Generating package: Ubuntu/hardy
Resolving build dependencies...
./packages/Ubuntu/ati-packager.sh: 347: sh -c '/usr/sbin/synaptic --set-selections --non-interactive --hide-main-window < /tmp/fileTcJZYW': not found
Unable to resolve  build-essential fakeroot.  Please manually install and try again.

What now?
sudo apt-get install fakeroot build-essential
Note: you may need some more
Note: opensource is about 30% of 3D rendering capability of the fglrx

---

### Post by zgornel on 2008-07-10
> **DOS4dinner said:**
> Do I need to use the envy installer or another form of installation, or do I just put in the code? Note: At this point, I have no driver installed that I know of. I used envy to uninstall the ATI driver.
Uninstall the official drivers and modify xorg.conf. The driver should be provided with the default install of Ubuntu.

---

### Post by soxs on 2008-07-10
Well, he should first think about which driver he finally wants, and not undoing the steps for fglrx when he has done 50%...

---

### Post by DOS4dinner on 2008-07-10
Lets see if I have this straight: 
The manual method 2 install can be fixed by that install command. Doing it this way may have the best chance of getting my 3D to work right. Do I need to uninstall my envy ATI drivers (again)? 

To do the open-source drivers, I must uninstall (again) my ATI drivers with envy. Then, I must edit the xorg.conf as previously posted. This might, however, not allow me to do full 3D. 

Which should I try first? I will probably try both in a half-hour or so, but which one is most likely to work?

Also, Thanks for helping me out. I really appreciate all the work you guys have put into this 2/3-day long multi-page thread.

---

### Post by zgornel on 2008-07-10
It does not make any difference what method you try first. More info about the open source ati driver: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) .

---

### Post by DOS4dinner on 2008-07-10
According to the link, I would have "good" acceleration (not full) with the open-source. How good is "good"? For instance, would I be able to play Frets on Fire, use any screensaver I want on full power, and be able to run most other programs with ease? I probably will not be running anything heavy, maybe just watching some movies or something. By "good", does that mean that it is just slow, or are some command/features/whatever they are called not supported?

---

### Post by DOS4dinner on 2008-07-10
Trying open-source driver now...be back in a minute.

---

### Post by DOS4dinner on 2008-07-10
Done. Still no 3D stuff. Is there something I need to remove/add to my xorg.conf?

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"radeon"
	Option		"DRI"	"1"
	Option		"UseInternalAGPGART"	"0"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Module"
	Load		"bitmap"
	Load		"vbe"
	Load		"ddc"
	Load		"freetype"
	Load		"int10"
	Load		"glx"
	Load		"dri"
	Load		"extmod"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
EndSection
```

---

### Post by soxs on 2008-07-11
> **DOS4dinner said:**
> Done. Still no 3D stuff. Is there something I need to remove/add to my xorg.conf?


How did you check that, don't expect fglrxinfo to give you any usableinfo.

---

### Post by DOS4dinner on 2008-07-11
> **soxs said:**
> How did you check that, don't expect fglrxinfo to give you any usableinfo.

I checked it two ways: One, I open Frets on fire. Currently, the main menu runs at about 4 frames per second (not measured, just telling you it runs very slow). Two, I try running one of the advanced screensavers, like euphoria. On that and almost all the screensavers my computer slows down to a crawl. Some it does okay, but few move as smoothly as they should.

Also, I noticed these lines in my xorg log:
```

(II) RADEON(0): [drm] installed DRM signal handler
(WW) RADEON(0): [agp] AGP not available
(EE) RADEON(0): [agp] AGP failed to initialize. Disabling the DRI.
(II) RADEON(0): [agp] You may want to make sure the agpgart kernel module
is loaded before the radeon kernel module.
```

---

### Post by PeterP24 on 2008-07-11
I have a similar problem but with another ATI graphic card (xpress 1150). This is strange since in Feisty and Gutsy everything was ok. It is frustrating because so far this thread is the closest I could find to my problem and still doesn't offer a viable solution (so far). 

Peter

---

### Post by DOS4dinner on 2008-07-11
> **PeterP24 said:**
> I have a similar problem but with another ATI graphic card (xpress 1150). This is strange since in Feisty and Gutsy everything was ok. It is frustrating because so far this thread is the closest I could find to my problem and still doesn't offer a viable solution (so far). 

Peter

What have you tried so far?

---

### Post by PeterP24 on 2008-07-11
Hi! I've tried everything:
- through the restricted drivers manager (the easy way);
- through envy;
- manualy with the latest driver from ATI.

Meanwhile, since the latest post, I got it fixed (many thanks to saltedlight - from the IRC channel ubuntu-ro).
The method -> use the following commands:

 sudo apt-get update
 sudo apt-get install linux-restricted-modules-generic

 sudo apt-get install xorg-driver-fglrx
 sudo depmod -a

 sudo dpkg-reconfigure -phigh xserver-xorg

 sudo nano /etc/X11/xorg.conf

Until here you probably tried already. By the way if a message is thrown that linux-restricted-modules-generic and xorg-driver-fglrx packages are already installed is ok. Just ignore and go ahead. Next in the xorg.conf, at the Device section I wrote 

 Device "vesa" 

(instead of the classical Device "fglrx")

You save and exit (Ctrl o and exit Ctrl x)and then :

 sudo aticonfig --force --initial

You must reboot the computer and after the reboot go to restricted drivers manager (hardware drivers) and install the ATI driver. After that reboot again.

As you see there are little differences from the original guide for Hardy. These steps may appear silly (installing first vesa and then the ATI driver) but they worked for me after 3 days of trials - in this time I've tried everything I could find on the internet for Hardy. I wanted to post it, maybe it will help you too.

Best regards,

Peter

---

### Post by DOS4dinner on 2008-07-11
> **PeterP24 said:**
> Hi! I've tried everything:
- through the restricted drivers manager (the easy way);
- through envy;
- manualy with the latest driver from ATI.

Meanwhile, since the latest post, I got it fixed (many thanks to saltedlight - from the IRC channel ubuntu-ro).
The method -> use the following commands:

 sudo apt-get update
 sudo apt-get install linux-restricted-modules-generic

 sudo apt-get install xorg-driver-fglrx
 sudo depmod -a

 sudo dpkg-reconfigure -phigh xserver-xorg

 sudo nano /etc/X11/xorg.conf

Until here you probably tried already. By the way if a message is thrown that linux-restricted-modules-generic and xorg-driver-fglrx packages are already installed is ok. Just ignore and go ahead. Next in the xorg.conf, at the Device section I wrote 

 Device "vesa" 

(instead of the classical Device "fglrx")

You save and exit (Ctrl o and exit Ctrl x)and then :

 sudo aticonfig --force --initial

You must reboot the computer and after the reboot go to restricted drivers manager (hardware drivers) and install the ATI driver. After that reboot again.

As you see there are little differences from the original guide for Hardy. These steps may appear silly (installing first vesa and then the ATI driver) but they worked for me after 3 days of trials - in this time I've tried everything I could find on the internet for Hardy. I wanted to post it, maybe it will help you too.

Best regards,

Peter

I may try that. Could you put the command fglrxinfo into the terminal and make sure that you are using the ATI drivers for OpenGL rendering? If it returns Mesa, we still have problems. If it returns ATI, we may have just solved a four page thread.

---

### Post by PeterP24 on 2008-07-11
> root@MartinEden:/lost+found# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7412 Release

As I pointed out this is the ATI driver from the Ubuntu repositories (not the latest).

To be sure I tested it with the Open Arena game - it works fine. On my computer Open Arena won't start with mesa.

Peter

---

