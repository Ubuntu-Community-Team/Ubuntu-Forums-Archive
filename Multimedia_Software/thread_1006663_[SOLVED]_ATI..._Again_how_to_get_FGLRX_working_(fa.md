---
title: "[SOLVED] ATI... Again how to get FGLRX working (fast)"
date: 2008-12-09
forum: Multimedia Software
---

### Post by sim-value on 2008-12-09
Hi !

I just got my new Computer with a HD3650 GRaphics Card and now the ATI driver doesnt want to work AGAIN ! ](*,)](*,)

With my old PC and the X1550 i needed full 6 MOnth to get it working now i want to be kinda faster as i dont have windows on it and also i want to use my TV card and Games ...

the wiki.cchtml.com guide isnt clear at all and here the ATI thread disapperead ...

BTW im using 64 Bit.

That was the result of my Last try with 8.10 Driver ...
```
Adding Module to DKMS build system
Doing initial module build

Error!  Build of fglrx.ko failed for: 2.6.27-9-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.542/build/ for more information.
Installing initial module

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.27-9-generic (x86_64) first.
Done.

```
And then after rebooting it of course complains about missing Librarys ...

Greetings /me

---

### Post by markbuntu on 2008-12-09
All you need to do is dowload the driver and run the installer. It worked for me with my HD3650:
Open a terminal,
cd to wherever the file is and then

sudo ./ati-driver-installer-8-10-x86.x86_64.run

If you did anything else then the driver is misinstalled. In your case, the driver kernel modules were not installed. If you got a kernel update and you get compliants like in the previous post, just run the installer again. Leave it on automatic.

Be sure to turn off the desktop visual effects before installing the driver or any kernel update. This will prevent any black or white screen problems if the driver is misinstalled.

---

### Post by sim-value on 2008-12-09
Gives me this error:
> Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.27-9-generic; make sure that the version is being
correctly set by --iscurrentdistro


Can it be because of low-graphics mode ?

---

### Post by markbuntu on 2008-12-10
Ohh, you are running Intrepid. In intrepid if you just go to Adminstration/Hardware Drivers you should see a lising for ATI/AMD proprietary fglrx graphics driver
 and a button marked

activate.

If you click that button the 8.10  driver will be automatically downloaded and installed. As far as I know, this is the only way to get an fglrx driver that works with Intrepid.

before you do that though, get rid of that driver that is misinstalled

sudo apt-get purge xorg-driver-fglrx

---

### Post by sim-value on 2008-12-10
> **markbuntu said:**
> Ohh, you are running Intrepid. In intrepid if you just go to Adminstration/Hardware Drivers you should see a lising for ATI/AMD proprietary fglrx graphics driver
 and a button marked

activate.

If you click that button the 8.10  driver will be automatically downloaded and installed. As far as I know, this is the only way to get an fglrx driver that works with Intrepid.

before you do that though, get rid of that driver that is misinstalled

sudo apt-get purge xorg-driver-fglrx

Well ... before when i pressed activate .. it would shortly flash around staying at 0 % and then go back ..

Now it just tells me there are no restricted drivers in use on this system ... *playswiththethoughtofHardy*

---

### Post by markbuntu on 2008-12-10
Well, I don't know what to say. It worked for me with my HD3650. Maybe there is some new bug. 
I did install Intrepid on an old sytem yesterday that has a ATI 200M integrated graphics and got the same thing as you but I was looking for another problem so paid no attention to that since I did not plan on using it much. 

I am now thinking there is maybe some new bug introduced in the Hardware Manager. Have you looked in your system logs for some message?

---

### Post by sim-value on 2008-12-11
> **markbuntu said:**
> Well, I don't know what to say. It worked for me with my HD3650. Maybe there is some new bug. 
I did install Intrepid on an old sytem yesterday that has a ATI 200M integrated graphics and got the same thing as you but I was looking for another problem so paid no attention to that since I did not plan on using it much. 

I am now thinking there is maybe some new bug introduced in the Hardware Manager. Have you looked in your system logs for some message?

I dont know where too look for thing related to this ...

---

### Post by sim-value on 2008-12-14
Im back to Hardy now cause this is the only OS where my sound works ...

With automatic installation is still doesnt work but goes to low graphic mode ... -.-

---

### Post by markbuntu on 2008-12-14
Look in the Xorg.0.log for errors (EE). You can find it in System/Adminstration/System Log.

---

### Post by sim-value on 2008-12-15
With the Ubuntu-Way install (just enabling it in Drivers manager) the error was
(WW) fglrx(0): Failed to open DRM connection

Whole Xorg.log :
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
Current Operating System: Linux sim-linux-desk 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64
Build Date: 13 June 2008  01:10:57AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 14 14:00:54 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
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
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7bd660
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
(II) PCI: 00:00:0: chip 1002,5950 card 1849,5950 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 1002,5a34 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:05:0: chip 1002,5a37 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:12:0: chip 1002,4380 card 1849,4381 rev 00 class 01,04,00 hdr 00
(II) PCI: 00:13:0: chip 1002,4387 card 1849,4387 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4388 card 1849,4388 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4389 card 1849,4389 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:3: chip 1002,438a card 1849,438a rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:4: chip 1002,438b card 1849,438b rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:5: chip 1002,4386 card 1849,4386 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4385 card 1849,4385 rev 13 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,438c card 1849,438c rev 00 class 01,01,8a hdr 00
(II) PCI: 00:14:2: chip 1002,4383 card 1849,0662 rev 00 class 04,03,00 hdr 00
(II) PCI: 00:14:3: chip 1002,438d card 1849,438d rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4384 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10ec,8168 card 1849,8168 rev 01 class 02,00,00 hdr 00
(II) PCI: 02:00:0: chip 1002,9598 card 1787,2254 rev 00 class 03,00,00 hdr 80
(II) PCI: 02:00:1: chip 1002,aa20 card 1787,aa20 rev 00 class 04,03,00 hdr 80
(II) PCI: 03:07:0: chip 14f1,8800 card 153b,117a rev 05 class 04,00,00 hdr 80
(II) PCI: 03:07:2: chip 14f1,8802 card 153b,117a rev 05 class 04,80,00 hdr 80
(II) PCI: 03:07:4: chip 14f1,8804 card 153b,117a rev 05 class 04,80,00 hdr 80
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:2:0), (0,2,2), BCTRL: 0x000b (VGA_EN is set)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfaf00000 - 0xfaffffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:5:0), (0,1,1), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfae00000 - 0xfaefffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:20:4), (0,3,3), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfb000000 - 0xfdffffff (0x3000000) MX[B]
(--) PCI:*(2:0:0) ATI Technologies Inc unknown chipset (0x9598) rev 0, Mem @ 0xd0000000/28, 0xfaff0000/16, I/O @ 0xe000/8, BIOS @ 0xfafc0000/17
(--) PCI: (3:7:0) unknown vendor (0x14f1) unknown chipset (0x8800) rev 5, Mem @ 0xfd000000/24
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
	[0] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[1] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[2] -1	0	0xfafec000 - 0xfafeffff (0x4000) MX[B]
	[3] -1	0	0xfaeff000 - 0xfaefffff (0x1000) MX[B]
	[4] -1	0	0xfadf0000 - 0xfadf3fff (0x4000) MX[B]
	[5] -1	0	0xfadff000 - 0xfadff0ff (0x100) MX[B]
	[6] -1	0	0xfadf6000 - 0xfadf6fff (0x1000) MX[B]
	[7] -1	0	0xfadf7000 - 0xfadf7fff (0x1000) MX[B]
	[8] -1	0	0xfadfc000 - 0xfadfcfff (0x1000) MX[B]
	[9] -1	0	0xfadfd000 - 0xfadfdfff (0x1000) MX[B]
	[10] -1	0	0xfadfe000 - 0xfadfefff (0x1000) MX[B]
	[11] -1	0	0xfadff800 - 0xfadffbff (0x400) MX[B]
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xfafc0000 - 0xfafdffff (0x20000) MX[B](B)
	[14] -1	0	0xfaff0000 - 0xfaffffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[17] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[23] -1	0	0x00008000 - 0x0000800f (0x10) IX[B]
	[24] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[26] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[1] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[2] -1	0	0xfafec000 - 0xfafeffff (0x4000) MX[B]
	[3] -1	0	0xfaeff000 - 0xfaefffff (0x1000) MX[B]
	[4] -1	0	0xfadf0000 - 0xfadf3fff (0x4000) MX[B]
	[5] -1	0	0xfadff000 - 0xfadff0ff (0x100) MX[B]
	[6] -1	0	0xfadf6000 - 0xfadf6fff (0x1000) MX[B]
	[7] -1	0	0xfadf7000 - 0xfadf7fff (0x1000) MX[B]
	[8] -1	0	0xfadfc000 - 0xfadfcfff (0x1000) MX[B]
	[9] -1	0	0xfadfd000 - 0xfadfdfff (0x1000) MX[B]
	[10] -1	0	0xfadfe000 - 0xfadfefff (0x1000) MX[B]
	[11] -1	0	0xfadff800 - 0xfadffbff (0x400) MX[B]
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xfafc0000 - 0xfafdffff (0x20000) MX[B](B)
	[14] -1	0	0xfaff0000 - 0xfaffffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[17] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[23] -1	0	0x00008000 - 0x0000800f (0x10) IX[B]
	[24] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[26] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
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
	[4] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[5] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[6] -1	0	0xfafec000 - 0xfafeffff (0x4000) MX[B]
	[7] -1	0	0xfaeff000 - 0xfaefffff (0x1000) MX[B]
	[8] -1	0	0xfadf0000 - 0xfadf3fff (0x4000) MX[B]
	[9] -1	0	0xfadff000 - 0xfadff0ff (0x100) MX[B]
	[10] -1	0	0xfadf6000 - 0xfadf6fff (0x1000) MX[B]
	[11] -1	0	0xfadf7000 - 0xfadf7fff (0x1000) MX[B]
	[12] -1	0	0xfadfc000 - 0xfadfcfff (0x1000) MX[B]
	[13] -1	0	0xfadfd000 - 0xfadfdfff (0x1000) MX[B]
	[14] -1	0	0xfadfe000 - 0xfadfefff (0x1000) MX[B]
	[15] -1	0	0xfadff800 - 0xfadffbff (0x400) MX[B]
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] -1	0	0xfafc0000 - 0xfafdffff (0x20000) MX[B](B)
	[18] -1	0	0xfaff0000 - 0xfaffffff (0x10000) MX[B](B)
	[19] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[23] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[29] -1	0	0x00008000 - 0x0000800f (0x10) IX[B]
	[30] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[31] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[32] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[33] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[34] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
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
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.55.2
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
(II) Primary Device is: PCI 02:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.55.2
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.552                    
(II) ATI Proprietary Linux Driver Build Date: Oct 28 2008 21:23:22
(--) Chipset Supported AMD Graphics Processor (0x9598) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[5] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[6] -1	0	0xfafec000 - 0xfafeffff (0x4000) MX[B]
	[7] -1	0	0xfaeff000 - 0xfaefffff (0x1000) MX[B]
	[8] -1	0	0xfadf0000 - 0xfadf3fff (0x4000) MX[B]
	[9] -1	0	0xfadff000 - 0xfadff0ff (0x100) MX[B]
	[10] -1	0	0xfadf6000 - 0xfadf6fff (0x1000) MX[B]
	[11] -1	0	0xfadf7000 - 0xfadf7fff (0x1000) MX[B]
	[12] -1	0	0xfadfc000 - 0xfadfcfff (0x1000) MX[B]
	[13] -1	0	0xfadfd000 - 0xfadfdfff (0x1000) MX[B]
	[14] -1	0	0xfadfe000 - 0xfadfefff (0x1000) MX[B]
	[15] -1	0	0xfadff800 - 0xfadffbff (0x400) MX[B]
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] -1	0	0xfafc0000 - 0xfafdffff (0x20000) MX[B](B)
	[18] -1	0	0xfaff0000 - 0xfaffffff (0x10000) MX[B](B)
	[19] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[23] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[29] -1	0	0x00008000 - 0x0000800f (0x10) IX[B]
	[30] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[31] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[32] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[33] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[34] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x7f80e0
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[5] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[6] -1	0	0xfafec000 - 0xfafeffff (0x4000) MX[B]
	[7] -1	0	0xfaeff000 - 0xfaefffff (0x1000) MX[B]
	[8] -1	0	0xfadf0000 - 0xfadf3fff (0x4000) MX[B]
	[9] -1	0	0xfadff000 - 0xfadff0ff (0x100) MX[B]
	[10] -1	0	0xfadf6000 - 0xfadf6fff (0x1000) MX[B]
	[11] -1	0	0xfadf7000 - 0xfadf7fff (0x1000) MX[B]
	[12] -1	0	0xfadfc000 - 0xfadfcfff (0x1000) MX[B]
	[13] -1	0	0xfadfd000 - 0xfadfdfff (0x1000) MX[B]
	[14] -1	0	0xfadfe000 - 0xfadfefff (0x1000) MX[B]
	[15] -1	0	0xfadff800 - 0xfadffbff (0x400) MX[B]
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] -1	0	0xfafc0000 - 0xfafdffff (0x20000) MX[B](B)
	[18] -1	0	0xfaff0000 - 0xfaffffff (0x10000) MX[B](B)
	[19] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[26] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[32] -1	0	0x00008000 - 0x0000800f (0x10) IX[B]
	[33] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[34] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[35] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[36] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[37] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): PCI bus 2 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "on"
(**) fglrx(0): Option "VideoOverlay" "off"
(**) fglrx(0): Option "UseFastTLS" "1"
(**) fglrx(0): Option "TexturedVideo" "off"
(**) fglrx(0): Option "DPMS" "true"
(II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb
(II) fglrx(0): 10BitPixelFormat disabled by default
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Radeon HD 3600 Series" (Chipset = 0x9598)
(--) fglrx(0): (PciSubVendor = 0x1787, PciSubDevice = 0x2254)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfaff0000
(--) fglrx(0): I/O port at 0x0000e000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 10.77
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV635
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID PCI:2:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
(WW) fglrx(0): Failed to open DRM connection
```

FOr the automated install i dont have it cause Xorg.log is always overwritten and i didnt find any error information in it so i didnt save it ..

---

### Post by sim-value on 2008-12-15
Just did the Following :

```
sudo apt-get purge fglrx*
```

i rebooted

then i run the Installer from ati on automatic

-reboot-

then
```
aticonfig --initial -f
```

-reboot-

Result :
Black screen at start

Log file
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
Current Operating System: Linux sim-linux-desk 2.6.24-22-generic #1 SMP Mon Nov 24 19:35:06 UTC 2008 x86_64
Build Date: 13 June 2008  01:10:57AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Dec 15 09:42:19 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
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
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7bd660
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
(II) PCI: 00:00:0: chip 1002,5950 card 1849,5950 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 1002,5a34 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:05:0: chip 1002,5a37 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:12:0: chip 1002,4380 card 1849,4380 rev 00 class 01,06,01 hdr 00
(II) PCI: 00:13:0: chip 1002,4387 card 1849,4387 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4388 card 1849,4388 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4389 card 1849,4389 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:3: chip 1002,438a card 1849,438a rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:4: chip 1002,438b card 1849,438b rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:5: chip 1002,4386 card 1849,4386 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4385 card 1849,4385 rev 13 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,438c card 1849,438c rev 00 class 01,01,8a hdr 00
(II) PCI: 00:14:2: chip 1002,4383 card 1849,0662 rev 00 class 04,03,00 hdr 00
(II) PCI: 00:14:3: chip 1002,438d card 1849,438d rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4384 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10ec,8168 card 1849,8168 rev 01 class 02,00,00 hdr 00
(II) PCI: 02:00:0: chip 1002,9598 card 1787,2254 rev 00 class 03,00,00 hdr 80
(II) PCI: 02:00:1: chip 1002,aa20 card 1787,aa20 rev 00 class 04,03,00 hdr 80
(II) PCI: 03:07:0: chip 14f1,8800 card 153b,117a rev 05 class 04,00,00 hdr 80
(II) PCI: 03:07:2: chip 14f1,8802 card 153b,117a rev 05 class 04,80,00 hdr 80
(II) PCI: 03:07:4: chip 14f1,8804 card 153b,117a rev 05 class 04,80,00 hdr 80
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:2:0), (0,2,2), BCTRL: 0x000b (VGA_EN is set)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfaf00000 - 0xfaffffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:5:0), (0,1,1), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfae00000 - 0xfaefffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:20:4), (0,3,3), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfb000000 - 0xfdffffff (0x3000000) MX[B]
(--) PCI:*(2:0:0) ATI Technologies Inc unknown chipset (0x9598) rev 0, Mem @ 0xd0000000/28, 0xfaff0000/16, I/O @ 0xe000/8, BIOS @ 0xfafc0000/17
(--) PCI: (3:7:0) unknown vendor (0x14f1) unknown chipset (0x8800) rev 5, Mem @ 0xfd000000/24
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
	[0] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[1] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[2] -1	0	0xfafec000 - 0xfafeffff (0x4000) MX[B]
	[3] -1	0	0xfaeff000 - 0xfaefffff (0x1000) MX[B]
	[4] -1	0	0xfadf4000 - 0xfadf7fff (0x4000) MX[B]
	[5] -1	0	0xfadff000 - 0xfadff0ff (0x100) MX[B]
	[6] -1	0	0xfadfa000 - 0xfadfafff (0x1000) MX[B]
	[7] -1	0	0xfadfb000 - 0xfadfbfff (0x1000) MX[B]
	[8] -1	0	0xfadfc000 - 0xfadfcfff (0x1000) MX[B]
	[9] -1	0	0xfadfd000 - 0xfadfdfff (0x1000) MX[B]
	[10] -1	0	0xfadfe000 - 0xfadfefff (0x1000) MX[B]
	[11] -1	0	0xfadff800 - 0xfadffbff (0x400) MX[B]
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xfafc0000 - 0xfafdffff (0x20000) MX[B](B)
	[14] -1	0	0xfaff0000 - 0xfaffffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[17] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[23] -1	0	0x00008000 - 0x0000800f (0x10) IX[B]
	[24] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[26] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[1] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[2] -1	0	0xfafec000 - 0xfafeffff (0x4000) MX[B]
	[3] -1	0	0xfaeff000 - 0xfaefffff (0x1000) MX[B]
	[4] -1	0	0xfadf4000 - 0xfadf7fff (0x4000) MX[B]
	[5] -1	0	0xfadff000 - 0xfadff0ff (0x100) MX[B]
	[6] -1	0	0xfadfa000 - 0xfadfafff (0x1000) MX[B]
	[7] -1	0	0xfadfb000 - 0xfadfbfff (0x1000) MX[B]
	[8] -1	0	0xfadfc000 - 0xfadfcfff (0x1000) MX[B]
	[9] -1	0	0xfadfd000 - 0xfadfdfff (0x1000) MX[B]
	[10] -1	0	0xfadfe000 - 0xfadfefff (0x1000) MX[B]
	[11] -1	0	0xfadff800 - 0xfadffbff (0x400) MX[B]
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xfafc0000 - 0xfafdffff (0x20000) MX[B](B)
	[14] -1	0	0xfaff0000 - 0xfaffffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[17] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[23] -1	0	0x00008000 - 0x0000800f (0x10) IX[B]
	[24] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[26] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
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
	[4] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[5] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[6] -1	0	0xfafec000 - 0xfafeffff (0x4000) MX[B]
	[7] -1	0	0xfaeff000 - 0xfaefffff (0x1000) MX[B]
	[8] -1	0	0xfadf4000 - 0xfadf7fff (0x4000) MX[B]
	[9] -1	0	0xfadff000 - 0xfadff0ff (0x100) MX[B]
	[10] -1	0	0xfadfa000 - 0xfadfafff (0x1000) MX[B]
	[11] -1	0	0xfadfb000 - 0xfadfbfff (0x1000) MX[B]
	[12] -1	0	0xfadfc000 - 0xfadfcfff (0x1000) MX[B]
	[13] -1	0	0xfadfd000 - 0xfadfdfff (0x1000) MX[B]
	[14] -1	0	0xfadfe000 - 0xfadfefff (0x1000) MX[B]
	[15] -1	0	0xfadff800 - 0xfadffbff (0x400) MX[B]
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] -1	0	0xfafc0000 - 0xfafdffff (0x20000) MX[B](B)
	[18] -1	0	0xfaff0000 - 0xfaffffff (0x10000) MX[B](B)
	[19] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[23] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[29] -1	0	0x00008000 - 0x0000800f (0x10) IX[B]
	[30] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[31] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[32] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[33] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[34] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
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
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.55.2
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
(II) Primary Device is: PCI 02:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.55.2
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.552                    
(II) ATI Proprietary Linux Driver Build Date: Oct 28 2008 21:23:22
(--) Chipset Supported AMD Graphics Processor (0x9598) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[5] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[6] -1	0	0xfafec000 - 0xfafeffff (0x4000) MX[B]
	[7] -1	0	0xfaeff000 - 0xfaefffff (0x1000) MX[B]
	[8] -1	0	0xfadf4000 - 0xfadf7fff (0x4000) MX[B]
	[9] -1	0	0xfadff000 - 0xfadff0ff (0x100) MX[B]
	[10] -1	0	0xfadfa000 - 0xfadfafff (0x1000) MX[B]
	[11] -1	0	0xfadfb000 - 0xfadfbfff (0x1000) MX[B]
	[12] -1	0	0xfadfc000 - 0xfadfcfff (0x1000) MX[B]
	[13] -1	0	0xfadfd000 - 0xfadfdfff (0x1000) MX[B]
	[14] -1	0	0xfadfe000 - 0xfadfefff (0x1000) MX[B]
	[15] -1	0	0xfadff800 - 0xfadffbff (0x400) MX[B]
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] -1	0	0xfafc0000 - 0xfafdffff (0x20000) MX[B](B)
	[18] -1	0	0xfaff0000 - 0xfaffffff (0x10000) MX[B](B)
	[19] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[23] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[29] -1	0	0x00008000 - 0x0000800f (0x10) IX[B]
	[30] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[31] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[32] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[33] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[34] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x7f80e0
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[5] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[6] -1	0	0xfafec000 - 0xfafeffff (0x4000) MX[B]
	[7] -1	0	0xfaeff000 - 0xfaefffff (0x1000) MX[B]
	[8] -1	0	0xfadf4000 - 0xfadf7fff (0x4000) MX[B]
	[9] -1	0	0xfadff000 - 0xfadff0ff (0x100) MX[B]
	[10] -1	0	0xfadfa000 - 0xfadfafff (0x1000) MX[B]
	[11] -1	0	0xfadfb000 - 0xfadfbfff (0x1000) MX[B]
	[12] -1	0	0xfadfc000 - 0xfadfcfff (0x1000) MX[B]
	[13] -1	0	0xfadfd000 - 0xfadfdfff (0x1000) MX[B]
	[14] -1	0	0xfadfe000 - 0xfadfefff (0x1000) MX[B]
	[15] -1	0	0xfadff800 - 0xfadffbff (0x400) MX[B]
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] -1	0	0xfafc0000 - 0xfafdffff (0x20000) MX[B](B)
	[18] -1	0	0xfaff0000 - 0xfaffffff (0x10000) MX[B](B)
	[19] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[26] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[32] -1	0	0x00008000 - 0x0000800f (0x10) IX[B]
	[33] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[34] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[35] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[36] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[37] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): PCI bus 2 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "true"
(II) fglrx(0): PCS database file /etc/ati/amdpcsdb not found
(II) fglrx(0):   Creating PCS database from initial defaults instead
(II) fglrx(0): 10BitPixelFormat disabled by default
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Radeon HD 3600 Series" (Chipset = 0x9598)
(--) fglrx(0): (PciSubVendor = 0x1787, PciSubDevice = 0x2254)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfaff0000
(--) fglrx(0): I/O port at 0x0000e000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 10.77
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV635
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:2:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports PCI:2:0:0
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.55.2
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Using adapter: 2:0.0.
(II) fglrx(0): [FB] MC range(MCFBBase = 0xc0000000, MCFBSize = 0x20000000)
(--) fglrx(0): Video RAM: 524288 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) fglrx(0): ***Display: ConnectedDisplayTypes=0x00000001, disabled=0x00000000
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SAM  Model: 428  Serial#: 1297691186
(II) fglrx(0): Year: 2008  Week: 37
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:  Separate  Composite  SyncOnGreen
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 46  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.655 redY: 0.329   greenX: 0.276 greenY: 0.617
(II) fglrx(0): blueX: 0.144 blueY: 0.088   whiteX: 0.312 whiteY: 0.329
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
(II) fglrx(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 119.0 MHz   Image Size:  459 x 296 mm
(II) fglrx(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) fglrx(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: SyncMaster
(II) fglrx(0): Serial No: HMAQ905419
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff004c2d28043232594d
(II) fglrx(0): 	251201030e2e1e782adce1a754469e24
(II) fglrx(0): 	165054bfef80b30081808140714f0101
(II) fglrx(0): 	0101010101017c2e90a0601a1e403020
(II) fglrx(0): 	3600cb281100001a000000fd00384b1e
(II) fglrx(0): 	510e000a202020202020000000fc0053
(II) fglrx(0): 	796e634d61737465720a2020000000ff
(II) fglrx(0): 	00484d41513930353431390a20200023
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(==) fglrx(0): QBS disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 35 modes found for primary display.
(--) fglrx(0): Virtual size is 1680x1050 (pitch 0)
(**) fglrx(0): *Mode "1680x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"x60.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +vsync (64.7 kHz)
(**) fglrx(0): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +vsync (55.9 kHz)
(**) fglrx(0): *Mode "1400x1050": 121.8 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync (65.3 kHz)
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
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 (67.5 kHz)
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"x70.0   96.76  1152 1224 1344 1536  864 865 868 900 +hsync (63.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 (60.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 +hsync (57.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 (46.9 kHz)
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 (48.1 kHz)
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync (43.8 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 +hsync +vsync (37.9 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
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
(--) fglrx(0): Display dimensions: (460, 300) mm
(--) fglrx(0): DPI set to (92, 88)
(--) fglrx(0): Virtual size is 1680x1050 (pitch 1728)
(**) fglrx(0): *Mode "1680x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"x60.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +vsync (64.7 kHz)
(**) fglrx(0): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +vsync (55.9 kHz)
(**) fglrx(0): *Mode "1400x1050": 121.8 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync (65.3 kHz)
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
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 (67.5 kHz)
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"x70.0   96.76  1152 1224 1344 1536  864 865 868 900 +hsync (63.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 (60.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 +hsync (57.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 (46.9 kHz)
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 (48.1 kHz)
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync (43.8 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 +hsync +vsync (37.9 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
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
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 255 MB
(II) fglrx(0): [pcie] 261120 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(II) fglrx(0): Direct rendering enabled
(II) fglrx(0): AC Adapter is used
(II) fglrx(0): Interrupt handler installed at IRQ 18.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): Finished Initialize PPLIB!
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfaff0000 - 0xfaffffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[7] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[8] -1	0	0xfafec000 - 0xfafeffff (0x4000) MX[B]
	[9] -1	0	0xfaeff000 - 0xfaefffff (0x1000) MX[B]
	[10] -1	0	0xfadf4000 - 0xfadf7fff (0x4000) MX[B]
	[11] -1	0	0xfadff000 - 0xfadff0ff (0x100) MX[B]
	[12] -1	0	0xfadfa000 - 0xfadfafff (0x1000) MX[B]
	[13] -1	0	0xfadfb000 - 0xfadfbfff (0x1000) MX[B]
	[14] -1	0	0xfadfc000 - 0xfadfcfff (0x1000) MX[B]
	[15] -1	0	0xfadfd000 - 0xfadfdfff (0x1000) MX[B]
	[16] -1	0	0xfadfe000 - 0xfadfefff (0x1000) MX[B]
	[17] -1	0	0xfadff800 - 0xfadffbff (0x400) MX[B]
	[18] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[19] -1	0	0xfafc0000 - 0xfafdffff (0x20000) MX[B](B)
	[20] -1	0	0xfaff0000 - 0xfaffffff (0x10000) MX[B](B)
	[21] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[22] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[23] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[24] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[25] 0	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[28] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[29] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[35] -1	0	0x00008000 - 0x0000800f (0x10) IX[B]
	[36] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[37] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[38] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[39] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[40] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
	[41] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[42] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
[B](II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(WW) fglrx(0): could not detect X server version (query_status=-1)[/B]
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): DRIScreenInit for fglrx driver
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:2:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:2:0:0
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:2:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0x7fc556ee2000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.55.2
(II) fglrx(0):     Date: Oct 28 2008
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.24-22-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
```
xorg.conf :
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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
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

```

I cant see any error from the Log file that the ****
Any ideas ?
/me

---

### Post by sim-value on 2008-12-27
ABLE ABLE ABLE !!! UBUNTU TEAM IS GREAT !!!!!!!

Today i talked to a friend whom i preached Ubuntu who had installed ubuntu just clicked the restriced driver restarted and was done that made me so jealous cause hes a complete Linux newb that i as sone as i was home DLed 32 Bit ubuntu (8.04) did the same AND IT WORKED!!! FIRST TIME IN MY LIFE IT WORKED !!!

Im so happy !!

YOu cant imagine ...

/me

---

