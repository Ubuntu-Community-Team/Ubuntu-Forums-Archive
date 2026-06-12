---
title: "Cannot get open source ATI driver working ACER AL1916w &amp; Radeon 9000. Ubuntu 7.10"
date: 2008-04-25
forum: Multimedia Software
---

### Post by samborona on 2008-04-25
Hi All, 

I posted on here a couple of weeks ago, and have been tearing my hair out for a solution, even trying different distros. I have read thread after thread and am absolutely clueless as to why I cannot get it working. 

Basically, the problem is that when the ATI ubuntu open source driver is selected the monitor will display "no signal" or "input not supported" after the bootsplash (log-in screen). I have tried dpkg-reconfigure xserver-xorg, edited the xorg.conf manually trying different things to no avail.

I can only get ubuntu working with the "vesa" driver, which wouldn't bother me but the only resolution I can get is 1280xsomething rather than the 1440x900 which my monitor needs. The monitor is an aceral1916w - I don't think that is the cause of the problem but it may contribute to it?

I really don't know what else to try - somebody suggested this may be the problem on another forum:

> well, I hauled my 8500 back out of storage and hooked it up to the computer that is still up for sale... and um... yeah, something odd with the ATi driver, screen just goes black.

The problem seems to be that the X.org Core and kernel received and update, but the existing X.org ATi driver did not.

The difference in X.org also means that the 8.28 driver won't load... it throws a hissy fit.

So... anybody with the talent to package a more recent version of the X.org ATi driver?

Do you think this could be the case? But then surely more people would be experiencing this problem. I remember a while back trying ubuntu 5.(something) and I definitely had beryl working and 3d effects. All I want for now is my 1440x900 resolution!

Any help/suggestions appreciated - I just want to get it working so I can tweak everything how I would like it because I am literally tearing my hair out.

---

### Post by samborona on 2008-04-25
Also while I remember, would upgrading be a bad idea at the moment until I get this sorted as I have heard that the editing of the xorg file isn't possible/harder so I could end up not being able to boot into ubuntu at all. 

I tried the beta and the above happened if I remember correctly.

---

### Post by Kubunteando on 2008-04-25
My first suggestion would be to upgrade to 8.04.
The main reason is because it has the new X.org 7.3 which is much more stable.
Also you have a "safe mode" for X.org.
You can try the 8.04 liveCD and see how it works.

If you want to still try 7.10 I would post the following info executing the commands from a console:

1- the output of "lspci"
2- the file /var/log/Xorg.0.log

The file 2 is needed when you have been using the driver radeon, not the vesa. So you can try to login, and when you get the "no signal", press Ctrl+Ald+Del to restart X.org and then copy the file.

---

### Post by Kubunteando on 2008-04-25
By the way, how do you connect the graphic card with the monitor, is it just a normal VGA port?

---

### Post by samborona on 2008-04-25
I think I will more than likely try and upgrade it - hopefully that will do the trick. I will still post the information below just out of interest in case it helps anybody else.

Output of lspci:

> 
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
**01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)**
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 82)
02:09.0 Modem: ALi Corporation SmartLink SmartPCI561 56K Modem


(Will need to edit xorg file and post back for #2)

I connect with a normal vga port, nothing too fancy :)

Thanks for the reply.

---

### Post by samborona on 2008-04-25
Actually forget that - cannot seem to get it to do anything when the monitor goes so will just upgrade and report back how I get on.

---

### Post by samborona on 2008-04-26
Well I've upgraded to 8.04 and it has hindered things rather than helped if anything...

I cannot find the "safe mode" for X :S and the "GUI" to edit xserver-xorg I am also struggling to find - searched google but only details about them.

I changed "vesa" to "ati" on the xorg.conf and rebooted, hoping it would work. It now loads up the log-in screen @ 1440x900, but there are white boxes all over it sometimes, or other times it just looks odd. It wont let me click on the log-in boxes or anything for that matter so I am unable to log-in. I think in 7.10 this occasionaly happened. Again, I'm not sure why it's doing this...

On a side-note, its a real shame that dpkg-reconfigure xserver-xorg doesn't work "in full" as in 7.10 as it would have saved me a lot of bother when my install was effectively useless seen as though I couldn't log in. At least before I could be back up and running in five minutes because I could select the vesa driver. I had to manually edit the xorg.conf in terminal which wasn't really great. It's a shame this is no longer available. I'm all for making ubuntu easier for people if it works out of the box - but when things go wrong and you are left with CLI it does complicate things!

---

### Post by Kubunteando on 2008-04-26
This case is funny indeed, the ATI Radeon 9000 has been supported for years. The laptop I use has the Mobility version of it.

The "safe mode" is selectable in the login screen, just where you select your session tyoe: Gnome, KDE,... I think the name is "failsafe".

How about now, are you able to get the Xorg.0.log file?

Do you see anything when you login, still a black screen?

---

### Post by samborona on 2008-04-26
Thanks for the reply - unfortunately when it gets to the login screen I cannot even select that since (if the cursor responds) if I click something it just doesn't respond, so I can't even log-in.

The log-in "screen" displays but is usually messed up or unresponsive as outlined above.

The problem I am having getting the Xorg.0.log is that when the log-in screen is displayed the system appears to "lock up" - I cannot drop to terminal or restart or anything, so have to turn off and on via the power button...

I cannot understand why either - everybody else at least seems to be able to get it working straight away and are worried about 3d effects! Could it be something to do with the monitor?

---

### Post by Kubunteando on 2008-04-26
I don't think it is related to the monitor.

Can you login and work normally if you use the vesa driver?

I would give a try to edit the boot entry in GRUB and append in the kernel line booting option "acpi=off", and check the result.
No need to edit any file, just in grub press "e" for editing the option you want to boot, and then add at the end of all other options: "acpi=off"

Just to know a bit more about your system:
- what is yor processor?
- are there any tweaks in the xorg.conf file?

Without the Xorg.0.log it is difficult to say anything. So the first step is to be able to login. If the system hangs (not even the light of the Caps Lock are working), a look to the file /var/log/kernel.log will help, for example if you can get it when booting with the vesa driver, or even in recovery mode with no graphical session.

---

### Post by samborona on 2008-04-26
I'm in ubuntu now with the vesa driver - that has always worked fine and to be honest if it was at 1440x900 resolution it wouldn't bother me, but it is stuck at 1280xsomething...

The processor is a pentium 4 2.4ghz, and no tweaks to the xorg.conf file at all.

From what your saying even the XOrg.0.log for the vesa driver will be of some use? If so I can post that :) 

I will try the rest and report back later.

Appreciate the help!

---

### Post by Kubunteando on 2008-04-26
If it works with vesa, seems that the problem would be with the radeon driver (ati driver).

How about:
configuring the ati driver, and booting to the login screen. And when it hangs reboot and start in recovery mode and copy the Xorg.0.log file. If you boot in recovery mode from grub the Xorg.0.log should not be overwritten...
That can be one try. The Xorg.0.lof plus the kernel.log should say something.

---

### Post by Rocket2DMn on 2008-04-26
Found this threa while searching to help people with open source drivers in Hardy, but I have a solution to both.  I have a Mobility Radeon 9000 on my laptop with Compiz Fusio working.

In Gutsy, follow this guide to reconfigure X: [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
-you want the "ati" driver and your monitor's correct resolution.  You should then be able to enable desktop effects with
```
compiz --replace
```
or to fallback to Metacity
```
metacity --replace
```

In Hardy, Compiz Fusion blacklisted cards using the open source "ati" drivers because of a bug in the driver, but there is a quick workaround here - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by samborona on 2008-04-27
Have managed to grab a copy of the Xorg.0.log for the ATI driver I think. I booted into the "ATI" driver, and can confirm that the system locks up (Caps lock does nothing) and the monitor either switches off (displays no signal) or shows the log-in screen which I cannot do anything with.

Have attached it below (tried adding as a text file but was too big) - sorry theres a lot there but I didn't want to cut anything out in case it was important.

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
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux dan-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 27 20:34:38 2008
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
(II) PCI: 00:00:0: chip 8086,2560 card 1734,1003 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2561 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 1734,1004 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 1734,1004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 1734,1004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 1734,1004 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 82 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24c0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24cb card 1734,1004 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 1734,1004 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 1734,1023 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4966 card 1458,4010 rev 01 class 03,00,00 hdr 00
(II) PCI: 02:08:0: chip 8086,1039 card 1734,1001 rev 82 class 02,00,00 hdr 00
(II) PCI: 02:09:0: chip 10b9,5459 card 16be,1003 rev 00 class 07,03,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd0100000 - 0xd01fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xd0200000 - 0xd02fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon RV250 If [Radeon 9000] rev 1, Mem @ 0xd8000000/27, 0xd0100000/16, I/O @ 0x3000/8
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xd0201000 - 0xd0201fff (0x1000) MX[B]
	[1] -1	0	0xd0200000 - 0xd0200fff (0x1000) MX[B]
	[2] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[3] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[4] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[5] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[8] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[9] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[10] -1	0	0x00004000 - 0x0000403f (0x40) IX[B]
	[11] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[12] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[13] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[14] -1	0	0x00002800 - 0x0000280f (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[20] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[21] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[22] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd0201000 - 0xd0201fff (0x1000) MX[B]
	[1] -1	0	0xd0200000 - 0xd0200fff (0x1000) MX[B]
	[2] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[3] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[4] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[5] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[8] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[9] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[10] -1	0	0x00004000 - 0x0000403f (0x40) IX[B]
	[11] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[12] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[13] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[14] -1	0	0x00002800 - 0x0000280f (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[20] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[21] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[22] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0201000 - 0xd0201fff (0x1000) MX[B]
	[5] -1	0	0xd0200000 - 0xd0200fff (0x1000) MX[B]
	[6] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[7] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[8] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[9] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[12] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[16] -1	0	0x00004000 - 0x0000403f (0x40) IX[B]
	[17] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[18] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[19] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[20] -1	0	0x00002800 - 0x0000280f (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[26] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[27] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[28] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
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
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
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
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
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
	ATI Mobility Radeon X700 (M26) (PCIE), ATI Radeon 9100 IGP (A5) 5834,
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
	ATI Radeon X550XTX (RV370) 5657 (PCIE),
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
	ATI Mobility Radeon X1700, ATI  Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600, ATI RV610,
	ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
	ATI ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI RV610,
	ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI ATI RADEON E2400, ATI RV610,
	ATI RV670, ATI Radeon HD3870, ATI Radeon HD3850, ATI RV670,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI ATI Radeon HD 2600 XT AGP, ATI ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini ATI Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI ATI Radeon HD 2600 LE
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset ATI Radeon 9000/PRO If (AGP/PCI) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0201000 - 0xd0201fff (0x1000) MX[B]
	[5] -1	0	0xd0200000 - 0xd0200fff (0x1000) MX[B]
	[6] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[7] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[8] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[9] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[12] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[16] -1	0	0x00004000 - 0x0000403f (0x40) IX[B]
	[17] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[18] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[19] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[20] -1	0	0x00002800 - 0x0000280f (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[26] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[27] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[28] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0201000 - 0xd0201fff (0x1000) MX[B]
	[5] -1	0	0xd0200000 - 0xd0200fff (0x1000) MX[B]
	[6] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[7] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[8] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[9] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[12] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[19] -1	0	0x00004000 - 0x0000403f (0x40) IX[B]
	[20] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[21] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[22] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[23] -1	0	0x00002800 - 0x0000280f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[29] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[30] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[31] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0x00000000d0100000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (==) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): initializing int10
(WW) RADEON(0): Bad V_BIOS checksum
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon 9000/PRO If (AGP/PCI)" (ChipID = 0x4966)
(--) RADEON(0): Linear framebuffer at 0x00000000d8000000
(II) RADEON(0): AGP card detected
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.28.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video RAM=65536K, accessible=65536K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 65536 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 2048x1200
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 35000, min_in_pll: 40, max_in_pll: 3000, xclk: 20000, sclk: 200.000000, mclk: 250.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=35000; xclk=20000
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-0x60, DACType-1, TMDSType-1, ConnectorType-1
(II) RADEON(0): Port1: DDCType-0x64, DACType-2, TMDSType-1, ConnectorType-2
(II) RADEON(0): Port5: DDCType-0x0, DACType-2, TMDSType-0, ConnectorType-5
(II) RADEON(0): Output VGA-0 using monitor section Configured Monitor
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): DFP table revision: 3
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: PAL
(II) RADEON(0): TV standards supported by chip: NTSC PAL 
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- 0x60
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- 0x64
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): EDID vendor "ACR", prod id 44370
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: ACR  Model: ad52  Serial#: 1417678716
(II) RADEON(0): Year: 2005  Week: 48
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.642 redY: 0.348   greenX: 0.288 greenY: 0.601
(II) RADEON(0): blueX: 0.143 blueY: 0.072   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 82 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: Acer AL1916W
(II) RADEON(0): Serial No: ETL5209015
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00047252ad7c0f8054
(II) RADEON(0): 	300f010368291a782e4fa5a459499924
(II) RADEON(0): 	125054bfef0081808140714f95000101
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	360098ff1000001c000000fd00384c1e
(II) RADEON(0): 	520e000a202020202020000000fc0041
(II) RADEON(0): 	63657220414c31393136570a000000ff
(II) RADEON(0): 	0045544c353230393031352020200020
finished output detect: 0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
finished output detect: 1
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): EDID vendor "ACR", prod id 44370
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: ACR  Model: ad52  Serial#: 1417678716
(II) RADEON(0): Year: 2005  Week: 48
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.642 redY: 0.348   greenX: 0.288 greenY: 0.601
(II) RADEON(0): blueX: 0.143 blueY: 0.072   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 82 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: Acer AL1916W
(II) RADEON(0): Serial No: ETL5209015
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00047252ad7c0f8054
(II) RADEON(0): 	300f010368291a782e4fa5a459499924
(II) RADEON(0): 	125054bfef0081808140714f95000101
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	360098ff1000001c000000fd00384c1e
(II) RADEON(0): 	520e000a202020202020000000fc0041
(II) RADEON(0): 	63657220414c31393136570a000000ff
(II) RADEON(0): 	0045544c353230393031352020200020
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "ACR", prod id 44370
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Output VGA-0 using initial mode 1440x900
after xf86InitialConfiguration
(**) RADEON(0): Display dimensions: (410, 260) mm
(**) RADEON(0): DPI set to (89, 117)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): MM_TABLE: 01-0c-00-1f-06-00-00-66-02-00-00-06-00-07
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd0100000 - 0xd010ffff (0x10000) MX[B]
	[1] 0	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xd0201000 - 0xd0201fff (0x1000) MX[B]
	[7] -1	0	0xd0200000 - 0xd0200fff (0x1000) MX[B]
	[8] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[9] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[10] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[11] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[14] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[18] 0	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[22] -1	0	0x00004000 - 0x0000403f (0x40) IX[B]
	[23] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[24] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[25] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[26] -1	0	0x00002800 - 0x0000280f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[32] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[33] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[34] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit d8000000 0 0
(==) RADEON(0): Write-combining range (0xd8000000,0x4000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable montype: 1
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x04000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xdbffd800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1472,8191)
(II) RADEON(0): Reserved area from (0,1200) to (1472,1202)
(II) RADEON(0): Largest offscreen area available: 1472 x 6989
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0xd7a000
(II) RADEON(0): Will use depth buffer at offset 0x1437000
(II) RADEON(0): Will use 37888 kb for textures at offset 0x1af4000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0xd8000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(==) RADEON(0): Using AGP 4x
(II) RADEON(0): [agp] Mode 0x1f000207 [AGP 0x8086/0x2560; Card 0x1002/0x4966]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xe0000000
(II) RADEON(0): [agp] Ring mapped at 0xb7997000
(II) RADEON(0): [agp] ring read ptr handle = 0xe0101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb7996000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xe0102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xb36d4000
(II) RADEON(0): [agp] GART texture map handle = 0xe0302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xb31f4000
(II) RADEON(0): [drm] register handle = 0xd0100000
(II) RADEON(0): [dri] Visual configs initialized
disable montype: 1
init memmap
init common
init crtc1
init pll1
freq: 106500000
best_freq: 106500000
best_feedback_div: 142
best_ref_div: 18
best_post_div: 2
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xdbffd800 0x1fff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 1
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 17
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xdbffd800 is: 0xdbffd800
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xe07fe000
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xdbffd800 0xdbffd800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xe07fe000
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor 0 (scanline 1202)
(II) RADEON(0): Using hardware cursor 1 (scanline 1204)
(II) RADEON(0): Largest offscreen area available: 1472 x 6983
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEON(0): Using R200 i2c bus access method
(II) RADEON(0): I2C bus "Radeon multimedia bus" initialized.
(II) Loading sub module "fi1236"
(II) LoadModule: "fi1236"
(II) Loading /usr/lib/xorg/modules/multimedia//fi1236_drv.so
(II) Module fi1236: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "uda1380"
(II) LoadModule: "uda1380"
(II) Loading /usr/lib/xorg/modules/multimedia//uda1380_drv.so
(II) Module uda1380: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "msp3430"
(II) LoadModule: "msp3430"
(II) Loading /usr/lib/xorg/modules/multimedia//msp3430_drv.so
(II) Module msp3430: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): No response from device 0 on VIP bus
(II) RADEON(0): Device 1 on VIP bus ids as 0x4d541002
(II) RADEON(0): No response from device 2 on VIP bus
(II) RADEON(0): No response from device 3 on VIP bus
(II) RADEON(0): Detected Rage Theatre as device 1 on VIP bus with id 0x4d541002
(II) RADEON(0): Detected Rage Theatre revision 00000003
(II) RADEON(0): video decoder type is 0x4e20 (BIOS value) versus 0x4e20 (current PLL setting)
(II) RADEON(0): Composite connector is port 2
(II) RADEON(0): SVideo connector is port 6
(II) RADEON(0): Rage Theatre: Connectors (detected): tuner=0, composite=2, svideo=6
(II) RADEON(0): RageTheatre: Connectors (using): tuner=0, composite=2, svideo=6
(II) RADEON(0): video decoder type used: 0x0006
(II) RADEON(0): Going to load the corresponding theatre module
(II) Loading sub module "theatre"
(II) LoadModule: "theatre"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_drv.so
(II) Module theatre: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): Rage Theatre setting standard 0x0000
(II) RADEON(0): Rage Theatre setting standard 0x0000
(II) RADEON(0): Rage Theatre setting standard 0x0000
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
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
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
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
(II) AIGLX: Loaded and initialized /usr/lib/dri/r200_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 408 x 255
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
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
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
enable montype: 1
(II) RADEON(0): EDID vendor "ACR", prod id 44370
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: ACR  Model: ad52  Serial#: 1417678716
(II) RADEON(0): Year: 2005  Week: 48
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.642 redY: 0.348   greenX: 0.288 greenY: 0.601
(II) RADEON(0): blueX: 0.143 blueY: 0.072   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 82 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: Acer AL1916W
(II) RADEON(0): Serial No: ETL5209015
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00047252ad7c0f8054
(II) RADEON(0): 	300f010368291a782e4fa5a459499924
(II) RADEON(0): 	125054bfef0081808140714f95000101
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	360098ff1000001c000000fd00384c1e
(II) RADEON(0): 	520e000a202020202020000000fc0041
(II) RADEON(0): 	63657220414c31393136570a000000ff
(II) RADEON(0): 	0045544c353230393031352020200020
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "ACR", prod id 44370
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0

```

Rocket2Dmn - that will be useful for setting up compiz but unfortunately I cannot even get the ATI driver to work at all!

- Again appreciate the help and contributions!

---

### Post by Rocket2DMn on 2008-04-27
I'm assuming you're on Hardy now?  If you have ever fiddled with restricted drivers, even though you should not have, run
```
sudo apt-get remove --purge xorg-driver-fglrx
```
Now we're going to try to reconfigure X again
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Restart X with CTRL+ALT+BACKSPACE
Then post
```
lspci | grep VGA
cat /etc/X11/xorg.conf
compiz --replace
```

---

### Post by samborona on 2008-04-27
Yes have upgraded to 8.04 Hardy now. Followed the instructions above here are the outputs:

**lspci | grep VGA**

```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)
```

**cat /etc/X11/xorg.conf**

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

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

(Have now edited this back to the "vesa" driver to allow me to boot)

**compiz --replace**

```
Checking for Xgl: xvinfo: Unable to open display not present.

xset@ unable to open display ""

xset q doesn't reveal the location of the logfile. Using fallback /var/log/Xorg.0.log

Detected PCI ID for VGA: 01:00.0 0300: 1002:4966 (rev/01) (prog if 00 [vga controller])

Checking for texture_from pixmap: not present.

Trying again with indirect rendering:

Checking for texture_from pixmap: not present.

aborting and using fallback: /usr/bin/metacity

Window Manager error: Unable to open X display/
```

Sorry if that isn't 100% correct - I had to write down "compiz --replace" and type it up because I was stuck in terminal and didn't know if there was a way to output it to the file.

Hope that is of some help :)

---

### Post by Rocket2DMn on 2008-04-27
When I run, I get
```
Checking for XGL: not present.
```
Perhaps you need to uninstall xserver-xgl
```
sudo apt-get remove --purge xserver-xgl
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
```
I don't know about this texture_from_pixmap, it's supposed to be present.
Do CTRL+ALT+BACKSPACE again and try to load up compiz when you're logged back in.  Post output.

A search revealed some other threads with this problem, with misc. solutions or absence of solutions.  You didn't by any chance accidentally install nvidia drivers at any point, did you?

---

### Post by samborona on 2008-04-27
Hmm... I'm in vesa now and typed in compiz --replace and got the following:

```
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```

It only displayed the above with the ATI driver selected... Is it still worth trying the above? Because I executed the command at the command line (recovery mode)would  that would be the reason for the error? Just thought I'd check.

I didn't install nvidia drivers, or any fglrx drivers etc. at all. All I have done is a clean install of 7.10, updated everything to the latest and updated to 8.04.

---

### Post by Rocket2DMn on 2008-04-27
You're not going to be able to run Compiz with the vesa driver.  You need to autoreconfigure X again with
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
then restart it with CTRL+ALT+BACKSPACE.  Hopefully this should put you back with the "ati" drivers.
Now try starting compiz again
```
compiz --replace
```
You should be good to go assuming you followed the guide I posted before about enabling compiz with the "ati" drivers in Hardy - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by samborona on 2008-04-28
I tried uninstalling xserver-xgl with:

```
sudo apt-get remove --purge xserver-xgl
```

and it said: "Package xserver-xgl is not installed, so not removed" - so it definately isn't there.

I then ran: 

```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
```

- this did install something.

I then restarted X which brought up a funny looking screen, so rebooted for the monitor to display "no signal" at login prompt, so rebooted again into command line prompt and tried

```
compiz --replace
```

This spitted out the same errors as before (I should point out that I enabled skip_checks=yes) but with the following new ones:

```
Checking for FBconfig: Error: Unable to open display.
```

```
Checking for nVidia: xdpyinfo: Unable to open display "".
```

```
/usr/bin/compiz.real (core) - Fatal: Couldn't open display.
```

Have now reverted back to vesa driver in order for system to boot.

Appreciate the help.

---

### Post by samborona on 2008-04-29
Do you think it would be worth posting a bug report if nobody else has any suggestions because I'm really stumped. Short of buying a new video card I'm not sure what else to try - but other people have reported this card working...

---

### Post by Rocket2DMn on 2008-04-29
You should search for existing bug reports on launchpad first, then if you don't find one, you can create one yourself.  Include as much information as you can regarding your problem - what works, what doesn't, what you've tried, etc.

---

### Post by Kubunteando on 2008-04-29
I had a look at your Xorg.0.log.
And it looks quite normal, except by two things:
- (WW) RADEON(0): Bad V_BIOS checksum
- I don't find any mode selected for the monitor (resolution and refresh rate)

I don't think that the checksum is a big issue, since the card is detected well. But not finding a monitor resolution can be the issue...

So I have one last advice if you haven't tried already: in the monitor settings in Ubuntu, do you have the monitor set as "PlugnPlay"?
I would try to set it up as AL1916w, it is actually an available monitor selection. And I have seen that then it will list the possible resolutions in the xorg.conf file. Maybe you can do it with the vesa driver, and then try again the radeon driver.

I this does not help I am running out of ideas, so a bug report sounds fair.

But if the capslock shows that the computer hangs completely I would then check the file /var/log/kernel.log, and see if there are any error messages...

---

### Post by samborona on 2008-04-29
I went into the screen/graphics preferences and it was already set to AL1916w, but wasn't set to widescreen I don't think, so I checked that and changed the driver to "radeon".

This gave the following:

Xorg.conf:

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

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"ATI Radeon"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Acer"
	Modelname	"Acer AL1916Wc"
	Horizsync	30.0-82.0
	Vertrefresh	56.0-76.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1920	1200
		Modes		"1440x900@75"	"1440x900@60"	"1280x800@60"	"1600x1024@60"	"1280x768@75"	"1680x1050@60"	"1280x800@75"	"1680x1050@75"	"1280x720@60"	"1920x1200@60"	"1280x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection
```

Grabbed Xorg.0.log again:

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
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux dan-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr 29 22:42:58 2008
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
(II) PCI: 00:00:0: chip 8086,2560 card 1734,1003 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2561 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 1734,1004 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 1734,1004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 1734,1004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 1734,1004 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 82 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24c0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24cb card 1734,1004 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 1734,1004 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 1734,1023 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4966 card 1458,4010 rev 01 class 03,00,00 hdr 00
(II) PCI: 02:08:0: chip 8086,1039 card 1734,1001 rev 82 class 02,00,00 hdr 00
(II) PCI: 02:09:0: chip 10b9,5459 card 16be,1003 rev 00 class 07,03,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd0100000 - 0xd01fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xd0200000 - 0xd02fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon RV250 If [Radeon 9000] rev 1, Mem @ 0xd8000000/27, 0xd0100000/16, I/O @ 0x3000/8
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xd0201000 - 0xd0201fff (0x1000) MX[B]
	[1] -1	0	0xd0200000 - 0xd0200fff (0x1000) MX[B]
	[2] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[3] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[4] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[5] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[8] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[9] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[10] -1	0	0x00004000 - 0x0000403f (0x40) IX[B]
	[11] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[12] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[13] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[14] -1	0	0x00002800 - 0x0000280f (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[20] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[21] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[22] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd0201000 - 0xd0201fff (0x1000) MX[B]
	[1] -1	0	0xd0200000 - 0xd0200fff (0x1000) MX[B]
	[2] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[3] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[4] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[5] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[8] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[9] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[10] -1	0	0x00004000 - 0x0000403f (0x40) IX[B]
	[11] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[12] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[13] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[14] -1	0	0x00002800 - 0x0000280f (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[20] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[21] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[22] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0201000 - 0xd0201fff (0x1000) MX[B]
	[5] -1	0	0xd0200000 - 0xd0200fff (0x1000) MX[B]
	[6] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[7] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[8] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[9] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[12] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[16] -1	0	0x00004000 - 0x0000403f (0x40) IX[B]
	[17] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[18] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[19] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[20] -1	0	0x00002800 - 0x0000280f (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[26] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[27] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[28] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
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
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 2.0
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
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
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
(II) v4l driver for Video4Linux
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
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
	ATI Mobility Radeon X700 (M26) (PCIE), ATI Radeon 9100 IGP (A5) 5834,
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
	ATI Radeon X550XTX (RV370) 5657 (PCIE),
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
	ATI Mobility Radeon X1700, ATI  Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600, ATI RV610,
	ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
	ATI ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI RV610,
	ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI ATI RADEON E2400, ATI RV610,
	ATI RV670, ATI Radeon HD3870, ATI Radeon HD3850, ATI RV670,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI ATI Radeon HD 2600 XT AGP, ATI ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini ATI Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI ATI Radeon HD 2600 LE
(II) Primary Device is: PCI 01:00:0
(--) Chipset ATI Radeon 9000/PRO If (AGP/PCI) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0201000 - 0xd0201fff (0x1000) MX[B]
	[5] -1	0	0xd0200000 - 0xd0200fff (0x1000) MX[B]
	[6] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[7] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[8] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[9] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[12] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[16] -1	0	0x00004000 - 0x0000403f (0x40) IX[B]
	[17] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[18] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[19] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[20] -1	0	0x00002800 - 0x0000280f (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[26] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[27] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[28] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0201000 - 0xd0201fff (0x1000) MX[B]
	[5] -1	0	0xd0200000 - 0xd0200fff (0x1000) MX[B]
	[6] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[7] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[8] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[9] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[12] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[19] -1	0	0x00004000 - 0x0000403f (0x40) IX[B]
	[20] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[21] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[22] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[23] -1	0	0x00002800 - 0x0000280f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[29] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[30] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[31] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0x00000000d0100000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): initializing int10
(WW) RADEON(0): Bad V_BIOS checksum
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon 9000/PRO If (AGP/PCI)" (ChipID = 0x4966)
(--) RADEON(0): Linear framebuffer at 0x00000000d8000000
(II) RADEON(0): AGP card detected
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.28.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video RAM=65536K, accessible=65536K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 65536 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 1920x1200
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 35000, min_in_pll: 40, max_in_pll: 3000, xclk: 20000, sclk: 200.000000, mclk: 250.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=35000; xclk=20000
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-0x60, DACType-1, TMDSType-1, ConnectorType-1
(II) RADEON(0): Port1: DDCType-0x64, DACType-2, TMDSType-1, ConnectorType-2
(II) RADEON(0): Port5: DDCType-0x0, DACType-2, TMDSType-0, ConnectorType-5
(II) RADEON(0): Output VGA-0 using monitor section Configured Monitor
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): DFP table revision: 3
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: PAL
(II) RADEON(0): TV standards supported by chip: NTSC PAL 
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- 0x60
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- 0x64
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): EDID vendor "ACR", prod id 44370
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: ACR  Model: ad52  Serial#: 1417678716
(II) RADEON(0): Year: 2005  Week: 48
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.642 redY: 0.348   greenX: 0.288 greenY: 0.601
(II) RADEON(0): blueX: 0.143 blueY: 0.072   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 82 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: Acer AL1916W
(II) RADEON(0): Serial No: ETL5209015
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00047252ad7c0f8054
(II) RADEON(0): 	300f010368291a782e4fa5a459499924
(II) RADEON(0): 	125054bfef0081808140714f95000101
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	360098ff1000001c000000fd00384c1e
(II) RADEON(0): 	520e000a202020202020000000fc0041
(II) RADEON(0): 	63657220414c31393136570a000000ff
(II) RADEON(0): 	0045544c353230393031352020200020
finished output detect: 0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
finished output detect: 1
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): EDID vendor "ACR", prod id 44370
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: ACR  Model: ad52  Serial#: 1417678716
(II) RADEON(0): Year: 2005  Week: 48
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.642 redY: 0.348   greenX: 0.288 greenY: 0.601
(II) RADEON(0): blueX: 0.143 blueY: 0.072   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 82 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: Acer AL1916W
(II) RADEON(0): Serial No: ETL5209015
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00047252ad7c0f8054
(II) RADEON(0): 	300f010368291a782e4fa5a459499924
(II) RADEON(0): 	125054bfef0081808140714f95000101
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	360098ff1000001c000000fd00384c1e
(II) RADEON(0): 	520e000a202020202020000000fc0041
(II) RADEON(0): 	63657220414c31393136570a000000ff
(II) RADEON(0): 	0045544c353230393031352020200020
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "ACR", prod id 44370
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Output VGA-0 using initial mode 1440x900
after xf86InitialConfiguration
(**) RADEON(0): Display dimensions: (410, 260) mm
(**) RADEON(0): DPI set to (118, 117)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(**) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): MM_TABLE: 01-0c-00-1f-06-00-00-66-02-00-00-06-00-07
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd0100000 - 0xd010ffff (0x10000) MX[B]
	[1] 0	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xd0201000 - 0xd0201fff (0x1000) MX[B]
	[7] -1	0	0xd0200000 - 0xd0200fff (0x1000) MX[B]
	[8] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[9] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[10] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[11] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[14] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[18] 0	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[22] -1	0	0x00004000 - 0x0000403f (0x40) IX[B]
	[23] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[24] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[25] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[26] -1	0	0x00002800 - 0x0000280f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[32] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[33] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[34] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit d8000000 0 0
(==) RADEON(0): Write-combining range (0xd8000000,0x4000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable montype: 1
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x04000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xdbffd800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1920,8191)
(II) RADEON(0): Reserved area from (0,1200) to (1920,1202)
(II) RADEON(0): Largest offscreen area available: 1920 x 6989
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0x11d0000
(II) RADEON(0): Will use depth buffer at offset 0x1a9a000
(II) RADEON(0): Will use 29184 kb for textures at offset 0x2364000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0xd8000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(==) RADEON(0): Using AGP 4x
(II) RADEON(0): [agp] Mode 0x1f000207 [AGP 0x8086/0x2560; Card 0x1002/0x4966]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xe0000000
(II) RADEON(0): [agp] Ring mapped at 0xb7990000
(II) RADEON(0): [agp] ring read ptr handle = 0xe0101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb798f000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xe0102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xb36cd000
(II) RADEON(0): [agp] GART texture map handle = 0xe0302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xb31ed000
(II) RADEON(0): [drm] register handle = 0xd0100000
(II) RADEON(0): [dri] Visual configs initialized
disable montype: 1
init memmap
init common
init crtc1
init pll1
freq: 106500000
best_freq: 106500000
best_feedback_div: 142
best_ref_div: 18
best_post_div: 2
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xdbffd800 0x1fff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 1
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 17
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xdbffd800 is: 0xdbffd800
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xe07fe000
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xdbffd800 0xdbffd800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xe07fe000
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor 0 (scanline 1202)
(II) RADEON(0): Using hardware cursor 1 (scanline 1204)
(II) RADEON(0): Largest offscreen area available: 1920 x 6984
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEON(0): Using R200 i2c bus access method
(II) RADEON(0): I2C bus "Radeon multimedia bus" initialized.
(II) Loading sub module "fi1236"
(II) LoadModule: "fi1236"
(II) Loading /usr/lib/xorg/modules/multimedia//fi1236_drv.so
(II) Module fi1236: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "uda1380"
(II) LoadModule: "uda1380"
(II) Loading /usr/lib/xorg/modules/multimedia//uda1380_drv.so
(II) Module uda1380: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "msp3430"
(II) LoadModule: "msp3430"
(II) Loading /usr/lib/xorg/modules/multimedia//msp3430_drv.so
(II) Module msp3430: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): No response from device 0 on VIP bus
(II) RADEON(0): Device 1 on VIP bus ids as 0x4d541002
(II) RADEON(0): No response from device 2 on VIP bus
(II) RADEON(0): No response from device 3 on VIP bus
(II) RADEON(0): Detected Rage Theatre as device 1 on VIP bus with id 0x4d541002
(II) RADEON(0): Detected Rage Theatre revision 00000003
(II) RADEON(0): video decoder type is 0x4e20 (BIOS value) versus 0x4e20 (current PLL setting)
(II) RADEON(0): Composite connector is port 2
(II) RADEON(0): SVideo connector is port 6
(II) RADEON(0): Rage Theatre: Connectors (detected): tuner=0, composite=2, svideo=6
(II) RADEON(0): RageTheatre: Connectors (using): tuner=0, composite=2, svideo=6
(II) RADEON(0): video decoder type used: 0x0006
(II) RADEON(0): Going to load the corresponding theatre module
(II) Loading sub module "theatre"
(II) LoadModule: "theatre"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_drv.so
(II) Module theatre: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): Rage Theatre setting standard 0x0000
(II) RADEON(0): Rage Theatre setting standard 0x0000
(II) RADEON(0): Rage Theatre setting standard 0x0000
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(WW) RADEON(0): Option "MergedFB" is not used
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
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
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
(II) AIGLX: Loaded and initialized /usr/lib/dri/r200_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 408 x 255
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
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
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
enable montype: 1
(II) RADEON(0): EDID vendor "ACR", prod id 44370
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: ACR  Model: ad52  Serial#: 1417678716
(II) RADEON(0): Year: 2005  Week: 48
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.642 redY: 0.348   greenX: 0.288 greenY: 0.601
(II) RADEON(0): blueX: 0.143 blueY: 0.072   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 82 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: Acer AL1916W
(II) RADEON(0): Serial No: ETL5209015
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00047252ad7c0f8054
(II) RADEON(0): 	300f010368291a782e4fa5a459499924
(II) RADEON(0): 	125054bfef0081808140714f95000101
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	360098ff1000001c000000fd00384c1e
(II) RADEON(0): 	520e000a202020202020000000fc0041
(II) RADEON(0): 	63657220414c31393136570a000000ff
(II) RADEON(0): 	0045544c353230393031352020200020
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "ACR", prod id 44370
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
```

Grabbed ATIXorg.0.log as well, not sure if its useful (might be for the vesa driver not sure):

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
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux dan-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 27 20:34:38 2008
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
(II) PCI: 00:00:0: chip 8086,2560 card 1734,1003 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2561 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 1734,1004 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 1734,1004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 1734,1004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 1734,1004 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 82 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24c0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24cb card 1734,1004 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 1734,1004 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 1734,1023 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4966 card 1458,4010 rev 01 class 03,00,00 hdr 00
(II) PCI: 02:08:0: chip 8086,1039 card 1734,1001 rev 82 class 02,00,00 hdr 00
(II) PCI: 02:09:0: chip 10b9,5459 card 16be,1003 rev 00 class 07,03,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd0100000 - 0xd01fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xd0200000 - 0xd02fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon RV250 If [Radeon 9000] rev 1, Mem @ 0xd8000000/27, 0xd0100000/16, I/O @ 0x3000/8
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xd0201000 - 0xd0201fff (0x1000) MX[B]
	[1] -1	0	0xd0200000 - 0xd0200fff (0x1000) MX[B]
	[2] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[3] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[4] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[5] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[8] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[9] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[10] -1	0	0x00004000 - 0x0000403f (0x40) IX[B]
	[11] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[12] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[13] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[14] -1	0	0x00002800 - 0x0000280f (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[20] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[21] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[22] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd0201000 - 0xd0201fff (0x1000) MX[B]
	[1] -1	0	0xd0200000 - 0xd0200fff (0x1000) MX[B]
	[2] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[3] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[4] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[5] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[8] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[9] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[10] -1	0	0x00004000 - 0x0000403f (0x40) IX[B]
	[11] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[12] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[13] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[14] -1	0	0x00002800 - 0x0000280f (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[20] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[21] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[22] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0201000 - 0xd0201fff (0x1000) MX[B]
	[5] -1	0	0xd0200000 - 0xd0200fff (0x1000) MX[B]
	[6] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[7] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[8] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[9] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[12] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[16] -1	0	0x00004000 - 0x0000403f (0x40) IX[B]
	[17] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[18] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[19] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[20] -1	0	0x00002800 - 0x0000280f (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[26] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[27] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[28] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
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
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
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
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
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
	ATI Mobility Radeon X700 (M26) (PCIE), ATI Radeon 9100 IGP (A5) 5834,
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
	ATI Radeon X550XTX (RV370) 5657 (PCIE),
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
	ATI Mobility Radeon X1700, ATI  Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600, ATI RV610,
	ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
	ATI ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI RV610,
	ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI ATI RADEON E2400, ATI RV610,
	ATI RV670, ATI Radeon HD3870, ATI Radeon HD3850, ATI RV670,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI ATI Radeon HD 2600 XT AGP, ATI ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini ATI Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI ATI Radeon HD 2600 LE
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset ATI Radeon 9000/PRO If (AGP/PCI) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0201000 - 0xd0201fff (0x1000) MX[B]
	[5] -1	0	0xd0200000 - 0xd0200fff (0x1000) MX[B]
	[6] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[7] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[8] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[9] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[12] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[16] -1	0	0x00004000 - 0x0000403f (0x40) IX[B]
	[17] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[18] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[19] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[20] -1	0	0x00002800 - 0x0000280f (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[26] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[27] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[28] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0201000 - 0xd0201fff (0x1000) MX[B]
	[5] -1	0	0xd0200000 - 0xd0200fff (0x1000) MX[B]
	[6] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[7] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[8] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[9] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[12] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[19] -1	0	0x00004000 - 0x0000403f (0x40) IX[B]
	[20] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[21] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[22] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[23] -1	0	0x00002800 - 0x0000280f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[29] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[30] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[31] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0x00000000d0100000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (==) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): initializing int10
(WW) RADEON(0): Bad V_BIOS checksum
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon 9000/PRO If (AGP/PCI)" (ChipID = 0x4966)
(--) RADEON(0): Linear framebuffer at 0x00000000d8000000
(II) RADEON(0): AGP card detected
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.28.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video RAM=65536K, accessible=65536K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 65536 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 2048x1200
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 35000, min_in_pll: 40, max_in_pll: 3000, xclk: 20000, sclk: 200.000000, mclk: 250.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=35000; xclk=20000
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-0x60, DACType-1, TMDSType-1, ConnectorType-1
(II) RADEON(0): Port1: DDCType-0x64, DACType-2, TMDSType-1, ConnectorType-2
(II) RADEON(0): Port5: DDCType-0x0, DACType-2, TMDSType-0, ConnectorType-5
(II) RADEON(0): Output VGA-0 using monitor section Configured Monitor
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): DFP table revision: 3
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: PAL
(II) RADEON(0): TV standards supported by chip: NTSC PAL 
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- 0x60
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- 0x64
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): EDID vendor "ACR", prod id 44370
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: ACR  Model: ad52  Serial#: 1417678716
(II) RADEON(0): Year: 2005  Week: 48
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.642 redY: 0.348   greenX: 0.288 greenY: 0.601
(II) RADEON(0): blueX: 0.143 blueY: 0.072   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 82 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: Acer AL1916W
(II) RADEON(0): Serial No: ETL5209015
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00047252ad7c0f8054
(II) RADEON(0): 	300f010368291a782e4fa5a459499924
(II) RADEON(0): 	125054bfef0081808140714f95000101
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	360098ff1000001c000000fd00384c1e
(II) RADEON(0): 	520e000a202020202020000000fc0041
(II) RADEON(0): 	63657220414c31393136570a000000ff
(II) RADEON(0): 	0045544c353230393031352020200020
finished output detect: 0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
finished output detect: 1
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): EDID vendor "ACR", prod id 44370
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: ACR  Model: ad52  Serial#: 1417678716
(II) RADEON(0): Year: 2005  Week: 48
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.642 redY: 0.348   greenX: 0.288 greenY: 0.601
(II) RADEON(0): blueX: 0.143 blueY: 0.072   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 82 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: Acer AL1916W
(II) RADEON(0): Serial No: ETL5209015
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00047252ad7c0f8054
(II) RADEON(0): 	300f010368291a782e4fa5a459499924
(II) RADEON(0): 	125054bfef0081808140714f95000101
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	360098ff1000001c000000fd00384c1e
(II) RADEON(0): 	520e000a202020202020000000fc0041
(II) RADEON(0): 	63657220414c31393136570a000000ff
(II) RADEON(0): 	0045544c353230393031352020200020
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "ACR", prod id 44370
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Output VGA-0 using initial mode 1440x900
after xf86InitialConfiguration
(**) RADEON(0): Display dimensions: (410, 260) mm
(**) RADEON(0): DPI set to (89, 117)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): MM_TABLE: 01-0c-00-1f-06-00-00-66-02-00-00-06-00-07
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd0100000 - 0xd010ffff (0x10000) MX[B]
	[1] 0	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xd0201000 - 0xd0201fff (0x1000) MX[B]
	[7] -1	0	0xd0200000 - 0xd0200fff (0x1000) MX[B]
	[8] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[9] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[10] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[11] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[14] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[18] 0	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[22] -1	0	0x00004000 - 0x0000403f (0x40) IX[B]
	[23] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[24] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[25] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[26] -1	0	0x00002800 - 0x0000280f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[32] -1	0	0x00001400 - 0x0000141f (0x20) IX[B]
	[33] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[34] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit d8000000 0 0
(==) RADEON(0): Write-combining range (0xd8000000,0x4000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable montype: 1
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x04000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xdbffd800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1472,8191)
(II) RADEON(0): Reserved area from (0,1200) to (1472,1202)
(II) RADEON(0): Largest offscreen area available: 1472 x 6989
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0xd7a000
(II) RADEON(0): Will use depth buffer at offset 0x1437000
(II) RADEON(0): Will use 37888 kb for textures at offset 0x1af4000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0xd8000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(==) RADEON(0): Using AGP 4x
(II) RADEON(0): [agp] Mode 0x1f000207 [AGP 0x8086/0x2560; Card 0x1002/0x4966]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xe0000000
(II) RADEON(0): [agp] Ring mapped at 0xb7997000
(II) RADEON(0): [agp] ring read ptr handle = 0xe0101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb7996000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xe0102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xb36d4000
(II) RADEON(0): [agp] GART texture map handle = 0xe0302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xb31f4000
(II) RADEON(0): [drm] register handle = 0xd0100000
(II) RADEON(0): [dri] Visual configs initialized
disable montype: 1
init memmap
init common
init crtc1
init pll1
freq: 106500000
best_freq: 106500000
best_feedback_div: 142
best_ref_div: 18
best_post_div: 2
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xdbffd800 0x1fff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 1
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 17
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xdbffd800 is: 0xdbffd800
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xe07fe000
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xdbffd800 0xdbffd800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xe07fe000
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor 0 (scanline 1202)
(II) RADEON(0): Using hardware cursor 1 (scanline 1204)
(II) RADEON(0): Largest offscreen area available: 1472 x 6983
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEON(0): Using R200 i2c bus access method
(II) RADEON(0): I2C bus "Radeon multimedia bus" initialized.
(II) Loading sub module "fi1236"
(II) LoadModule: "fi1236"
(II) Loading /usr/lib/xorg/modules/multimedia//fi1236_drv.so
(II) Module fi1236: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "uda1380"
(II) LoadModule: "uda1380"
(II) Loading /usr/lib/xorg/modules/multimedia//uda1380_drv.so
(II) Module uda1380: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "msp3430"
(II) LoadModule: "msp3430"
(II) Loading /usr/lib/xorg/modules/multimedia//msp3430_drv.so
(II) Module msp3430: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): No response from device 0 on VIP bus
(II) RADEON(0): Device 1 on VIP bus ids as 0x4d541002
(II) RADEON(0): No response from device 2 on VIP bus
(II) RADEON(0): No response from device 3 on VIP bus
(II) RADEON(0): Detected Rage Theatre as device 1 on VIP bus with id 0x4d541002
(II) RADEON(0): Detected Rage Theatre revision 00000003
(II) RADEON(0): video decoder type is 0x4e20 (BIOS value) versus 0x4e20 (current PLL setting)
(II) RADEON(0): Composite connector is port 2
(II) RADEON(0): SVideo connector is port 6
(II) RADEON(0): Rage Theatre: Connectors (detected): tuner=0, composite=2, svideo=6
(II) RADEON(0): RageTheatre: Connectors (using): tuner=0, composite=2, svideo=6
(II) RADEON(0): video decoder type used: 0x0006
(II) RADEON(0): Going to load the corresponding theatre module
(II) Loading sub module "theatre"
(II) LoadModule: "theatre"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_drv.so
(II) Module theatre: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): Rage Theatre setting standard 0x0000
(II) RADEON(0): Rage Theatre setting standard 0x0000
(II) RADEON(0): Rage Theatre setting standard 0x0000
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
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
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
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
(II) AIGLX: Loaded and initialized /usr/lib/dri/r200_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 408 x 255
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
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
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
enable montype: 1
(II) RADEON(0): EDID vendor "ACR", prod id 44370
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: ACR  Model: ad52  Serial#: 1417678716
(II) RADEON(0): Year: 2005  Week: 48
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.642 redY: 0.348   greenX: 0.288 greenY: 0.601
(II) RADEON(0): blueX: 0.143 blueY: 0.072   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 82 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: Acer AL1916W
(II) RADEON(0): Serial No: ETL5209015
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00047252ad7c0f8054
(II) RADEON(0): 	300f010368291a782e4fa5a459499924
(II) RADEON(0): 	125054bfef0081808140714f95000101
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	360098ff1000001c000000fd00384c1e
(II) RADEON(0): 	520e000a202020202020000000fc0041
(II) RADEON(0): 	63657220414c31393136570a000000ff
(II) RADEON(0): 	0045544c353230393031352020200020
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "ACR", prod id 44370
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
```

kern.log attached here (I'm sorry it is so big - I have tried to attach the bit that had the error) Wherever the power button goes off it is usually because the system has locked up due to the driver.

```
Apr 29 22:42:58 dan-desktop kernel: [ 2541.773247] [drm] Initialized drm 1.1.0 20060810
Apr 29 22:42:58 dan-desktop kernel: [ 2541.805886] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 17
Apr 29 22:42:58 dan-desktop kernel: [ 2541.806125] [drm] Initialized radeon 1.28.0 20060524 on minor 0
Apr 29 22:43:00 dan-desktop kernel: [ 2543.369946] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Apr 29 22:43:00 dan-desktop kernel: [ 2543.370822] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Apr 29 22:43:00 dan-desktop kernel: [ 2543.371583] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Apr 29 22:43:00 dan-desktop kernel: [ 2543.724491] [drm] Setting GART location based on new memory map
Apr 29 22:43:00 dan-desktop kernel: [ 2543.724503] [drm] Loading R200 Microcode
Apr 29 22:43:00 dan-desktop kernel: [ 2543.724556] [drm] writeback test succeeded in 1 usecs
Apr 29 22:55:36 dan-desktop kernel: Inspecting /boot/System.map-2.6.24-16-generic
Apr 29 22:55:36 dan-desktop kernel: Loaded 27704 symbols from /boot/System.map-2.6.24-16-generic.
Apr 29 22:55:36 dan-desktop kernel: Symbols match kernel version 2.6.24.
Apr 29 22:55:36 dan-desktop kernel: Loaded 15297 symbols from 80 modules.
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 29 22:55:36 dan-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000000fef0000 (usable)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000]  BIOS-e820: 000000000fef0000 - 000000000fefc000 (ACPI data)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000]  BIOS-e820: 000000000fefc000 - 000000000ff00000 (ACPI NVS)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000]  BIOS-e820: 000000000ff00000 - 000000000ff80000 (usable)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000]  BIOS-e820: 000000000ff80000 - 0000000010000000 (reserved)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] 0MB HIGHMEM available.
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] 255MB LOWMEM available.
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 65408) 0 entries of 256 used
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] Zone PFN ranges:
Apr 29 22:55:36 dan-desktop kernel: [    0.000000]   DMA             0 ->     4096
Apr 29 22:55:36 dan-desktop kernel: [    0.000000]   Normal       4096 ->    65408
Apr 29 22:55:36 dan-desktop kernel: [    0.000000]   HighMem     65408 ->    65408
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] Movable zone start PFN for each node
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 29 22:55:36 dan-desktop kernel: [    0.000000]     0:        0 ->    65408
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] On node 0 totalpages: 65408
Apr 29 22:55:36 dan-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 29 22:55:36 dan-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 29 22:55:36 dan-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr 29 22:55:36 dan-desktop kernel: [    0.000000]   Normal zone: 479 pages used for memmap
Apr 29 22:55:36 dan-desktop kernel: [    0.000000]   Normal zone: 60833 pages, LIFO batch:15
Apr 29 22:55:36 dan-desktop kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Apr 29 22:55:36 dan-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] DMI present.
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7CE0 checksum 0
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] ACPI: RSDP 000F7CE0, 0014 (r0 PTLTD )
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] ACPI: RSDT 0FEF90BC, 0030 (r1 PTLTD    RSDT    6040001  LTP        0)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] ACPI: FACP 0FEF90EC, 0074 (r1 FSC    D152X     6040001         F4240)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] ACPI: DSDT 0FEF9160, 2E1E (r1 FSC    D152X     6040001 MSFT  100000E)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] ACPI: FACS 0FEFCFC0, 0040
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] ACPI: APIC 0FEFBF7E, 005A (r1 FSC    ^I APIC    6040001  CSF        0)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] ACPI: BOOT 0FEFBFD8, 0028 (r1 PTLTD  $SBFTBL$  6040001  LTP        1)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] ACPI: DMI detected: Fujitsu Siemens
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xf008
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] Processor #0 15:2 APIC version 20
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:eec00000)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000ce000
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000ce000 - 00000000000d0000
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000d0000 - 00000000000dc000
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 00000000000e0000
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 00000000000e4000
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000fef0000 - 000000000fefc000
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000fefc000 - 000000000ff00000
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64897
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] Kernel command line: root=UUID=0bfca241-5f24-4fea-a85e-4e3bff4ee371 ro quiet splash
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] Initializing CPU#0
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
Apr 29 22:55:36 dan-desktop kernel: [    0.000000] Detected 2525.288 MHz processor.
Apr 29 22:55:36 dan-desktop kernel: [   20.907730] Console: colour VGA+ 80x25
Apr 29 22:55:36 dan-desktop kernel: [   20.907736] console [tty0] enabled
Apr 29 22:55:36 dan-desktop kernel: [   20.907935] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 29 22:55:36 dan-desktop kernel: [   20.908104] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Apr 29 22:55:36 dan-desktop kernel: [   20.913690] Memory: 247460k/261632k available (2157k kernel code, 13620k reserved, 998k data, 364k init, 0k highmem)
Apr 29 22:55:36 dan-desktop kernel: [   20.913699] virtual kernel memory layout:
Apr 29 22:55:36 dan-desktop kernel: [   20.913700]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Apr 29 22:55:36 dan-desktop kernel: [   20.913701]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr 29 22:55:36 dan-desktop kernel: [   20.913703]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB)
Apr 29 22:55:36 dan-desktop kernel: [   20.913704]     lowmem  : 0xc0000000 - 0xcff80000   ( 255 MB)
Apr 29 22:55:36 dan-desktop kernel: [   20.913705]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
Apr 29 22:55:36 dan-desktop kernel: [   20.913706]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
Apr 29 22:55:36 dan-desktop kernel: [   20.913707]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
Apr 29 22:55:36 dan-desktop kernel: [   20.913711] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 29 22:55:36 dan-desktop kernel: [   20.913746] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Apr 29 22:55:36 dan-desktop kernel: [   20.993671] Calibrating delay using timer specific routine.. 5055.04 BogoMIPS (lpj=10110082)
Apr 29 22:55:36 dan-desktop kernel: [   20.993698] Security Framework initialized
Apr 29 22:55:36 dan-desktop kernel: [   20.993705] SELinux:  Disabled at boot.
Apr 29 22:55:36 dan-desktop kernel: [   20.993720] AppArmor: AppArmor initialized
Apr 29 22:55:36 dan-desktop kernel: [   20.993725] Failure registering capabilities with primary security module.
Apr 29 22:55:36 dan-desktop kernel: [   20.993734] Mount-cache hash table entries: 512
Apr 29 22:55:36 dan-desktop kernel: [   20.993871] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
Apr 29 22:55:36 dan-desktop kernel: [   20.993885] CPU: Trace cache: 12K uops, L1 D cache: 8K
Apr 29 22:55:36 dan-desktop kernel: [   20.993888] CPU: L2 cache: 512K
Apr 29 22:55:36 dan-desktop kernel: [   20.993891] CPU: Hyper-Threading is disabled
Apr 29 22:55:36 dan-desktop kernel: [   20.993893] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
Apr 29 22:55:36 dan-desktop kernel: [   20.993906] Compat vDSO mapped to ffffe000.
Apr 29 22:55:36 dan-desktop kernel: [   20.993920] Checking 'hlt' instruction... OK.
Apr 29 22:55:36 dan-desktop kernel: [   21.010042] SMP alternatives: switching to UP code
Apr 29 22:55:36 dan-desktop kernel: [   21.011706] Freeing SMP alternatives: 11k freed
Apr 29 22:55:36 dan-desktop kernel: [   21.011856] Early unpacking initramfs... done
Apr 29 22:55:36 dan-desktop kernel: [   21.341151] ACPI: Core revision 20070126
Apr 29 22:55:36 dan-desktop kernel: [   21.341213] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Apr 29 22:55:36 dan-desktop kernel: [   21.343399] CPU0: Intel(R) Pentium(R) 4 CPU 2.53GHz stepping 07
Apr 29 22:55:36 dan-desktop kernel: [   21.343443] Total of 1 processors activated (5055.04 BogoMIPS).
Apr 29 22:55:36 dan-desktop kernel: [   21.343580] ENABLING IO-APIC IRQs
Apr 29 22:55:36 dan-desktop kernel: [   21.343768] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 29 22:55:36 dan-desktop kernel: [   21.489135] Brought up 1 CPUs
Apr 29 22:55:36 dan-desktop kernel: [   21.489161] CPU0 attaching sched-domain:
Apr 29 22:55:36 dan-desktop kernel: [   21.489164]  domain 0: span 01
Apr 29 22:55:36 dan-desktop kernel: [   21.489166]   groups: 01
Apr 29 22:55:36 dan-desktop kernel: [   21.489372] net_namespace: 64 bytes
Apr 29 22:55:36 dan-desktop kernel: [   21.489382] Booting paravirtualized kernel on bare hardware
Apr 29 22:55:36 dan-desktop kernel: [   21.490024] Time: 22:55:14  Date: 04/29/08
Apr 29 22:55:36 dan-desktop kernel: [   21.490054] NET: Registered protocol family 16
Apr 29 22:55:36 dan-desktop kernel: [   21.490297] EISA bus registered
Apr 29 22:55:36 dan-desktop kernel: [   21.490325] ACPI: bus type pci registered
Apr 29 22:55:36 dan-desktop kernel: [   21.515322] PCI: PCI BIOS revision 2.10 entry at 0xfd987, last bus=2
Apr 29 22:55:36 dan-desktop kernel: [   21.515325] PCI: Using configuration type 1
Apr 29 22:55:36 dan-desktop kernel: [   21.515327] Setting up standard PCI resources
Apr 29 22:55:36 dan-desktop kernel: [   21.524019] ACPI: EC: Look up EC in DSDT
Apr 29 22:55:36 dan-desktop kernel: [   21.525778] ACPI: Interpreter enabled
Apr 29 22:55:36 dan-desktop kernel: [   21.525782] ACPI: (supports S0 S1 S3 S4 S5)
Apr 29 22:55:36 dan-desktop kernel: [   21.525800] ACPI: Using IOAPIC for interrupt routing
Apr 29 22:55:36 dan-desktop kernel: [   21.528952] ACPI: Device [ECP] status [00000008]: functional but not present; setting present
Apr 29 22:55:36 dan-desktop kernel: [   21.529356] ACPI: Device [COM2] status [00000008]: functional but not present; setting present
Apr 29 22:55:36 dan-desktop kernel: [   21.529625] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 29 22:55:36 dan-desktop kernel: [   21.530058] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Apr 29 22:55:36 dan-desktop kernel: [   21.530059] * this clock source is slow. If you are sure your timer does not have
Apr 29 22:55:36 dan-desktop kernel: [   21.530061] * this bug, please use "acpi_pm_good" to disable the workaround
Apr 29 22:55:36 dan-desktop kernel: [   21.530107] PCI quirk: region f000-f07f claimed by ICH4 ACPI/GPIO/TCO
Apr 29 22:55:36 dan-desktop kernel: [   21.530111] PCI quirk: region f180-f1bf claimed by ICH4 GPIO
Apr 29 22:55:36 dan-desktop kernel: [   21.530593] PCI: Transparent bridge - 0000:00:1e.0
Apr 29 22:55:36 dan-desktop kernel: [   21.530619] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 29 22:55:36 dan-desktop kernel: [   21.530805] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
Apr 29 22:55:36 dan-desktop kernel: [   21.530890] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIH._PRT]
Apr 29 22:55:36 dan-desktop kernel: [   21.532954] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Apr 29 22:55:36 dan-desktop kernel: [   21.533061] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Apr 29 22:55:36 dan-desktop kernel: [   21.533152] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Apr 29 22:55:36 dan-desktop kernel: [   21.533245] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Apr 29 22:55:36 dan-desktop kernel: [   21.533337] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Apr 29 22:55:36 dan-desktop kernel: [   21.533420] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Apr 29 22:55:36 dan-desktop kernel: [   21.533504] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Apr 29 22:55:36 dan-desktop kernel: [   21.533597] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Apr 29 22:55:36 dan-desktop kernel: [   21.533732] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 29 22:55:36 dan-desktop kernel: [   21.533772] pnp: PnP ACPI init
Apr 29 22:55:36 dan-desktop kernel: [   21.533784] ACPI: bus type pnp registered
Apr 29 22:55:36 dan-desktop kernel: [   21.535481] pnp: PnP ACPI: found 12 devices
Apr 29 22:55:36 dan-desktop kernel: [   21.535484] ACPI: ACPI bus type pnp unregistered
Apr 29 22:55:36 dan-desktop kernel: [   21.535490] PnPBIOS: Disabled by ACPI PNP
Apr 29 22:55:36 dan-desktop kernel: [   21.535770] PCI: Using ACPI for IRQ routing
Apr 29 22:55:36 dan-desktop kernel: [   21.535775] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 29 22:55:36 dan-desktop kernel: [   21.549021] NET: Registered protocol family 8
Apr 29 22:55:36 dan-desktop kernel: [   21.549024] NET: Registered protocol family 20
Apr 29 22:55:36 dan-desktop kernel: [   21.549103] AppArmor: AppArmor Filesystem Enabled
Apr 29 22:55:36 dan-desktop kernel: [   21.553005] Time: tsc clocksource has been installed.
Apr 29 22:55:36 dan-desktop kernel: [   21.561046] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Apr 29 22:55:36 dan-desktop kernel: [   21.561049] system 00:02: ioport range 0xf000-0xf07f has been reserved
Apr 29 22:55:36 dan-desktop kernel: [   21.561052] system 00:02: ioport range 0xf100-0xf10f has been reserved
Apr 29 22:55:36 dan-desktop kernel: [   21.561055] system 00:02: ioport range 0xf180-0xf1bf has been reserved
Apr 29 22:55:36 dan-desktop kernel: [   21.561057] system 00:02: ioport range 0x800-0x87f has been reserved
Apr 29 22:55:36 dan-desktop kernel: [   21.561060] system 00:02: ioport range 0xf820-0xf82f has been reserved
Apr 29 22:55:36 dan-desktop kernel: [   21.561063] system 00:02: ioport range 0xfe00-0xfe00 has been reserved
Apr 29 22:55:36 dan-desktop kernel: [   21.591540] PCI: Bridge: 0000:00:01.0
Apr 29 22:55:36 dan-desktop kernel: [   21.591544]   IO window: 3000-3fff
Apr 29 22:55:36 dan-desktop kernel: [   21.591549]   MEM window: d0100000-d01fffff
Apr 29 22:55:36 dan-desktop kernel: [   21.591554]   PREFETCH window: d8000000-dfffffff
Apr 29 22:55:36 dan-desktop kernel: [   21.591559] PCI: Bridge: 0000:00:1e.0
Apr 29 22:55:36 dan-desktop kernel: [   21.591563]   IO window: 4000-4fff
Apr 29 22:55:36 dan-desktop kernel: [   21.591568]   MEM window: d0200000-d02fffff
Apr 29 22:55:36 dan-desktop kernel: [   21.591572]   PREFETCH window: disabled.
Apr 29 22:55:36 dan-desktop kernel: [   21.591591] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Apr 29 22:55:36 dan-desktop kernel: [   21.591605] NET: Registered protocol family 2
Apr 29 22:55:36 dan-desktop kernel: [   21.629005] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
Apr 29 22:55:36 dan-desktop kernel: [   21.629260] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
Apr 29 22:55:36 dan-desktop kernel: [   21.629309] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Apr 29 22:55:36 dan-desktop kernel: [   21.629357] TCP: Hash tables configured (established 8192 bind 8192)
Apr 29 22:55:36 dan-desktop kernel: [   21.629360] TCP reno registered
Apr 29 22:55:36 dan-desktop kernel: [   21.641042] checking if image is initramfs... it is
Apr 29 22:55:36 dan-desktop kernel: [   22.092349] Switched to high resolution mode on CPU 0
Apr 29 22:55:36 dan-desktop kernel: [   22.291555] Freeing initrd memory: 7260k freed
Apr 29 22:55:36 dan-desktop kernel: [   22.291787] Simple Boot Flag at 0x69 set to 0x1
Apr 29 22:55:36 dan-desktop kernel: [   22.292288] audit: initializing netlink socket (disabled)
Apr 29 22:55:36 dan-desktop kernel: [   22.292309] audit(1209509714.276:1): initialized
Apr 29 22:55:36 dan-desktop kernel: [   22.294658] VFS: Disk quotas dquot_6.5.1
Apr 29 22:55:36 dan-desktop kernel: [   22.294747] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 29 22:55:36 dan-desktop kernel: [   22.294920] io scheduler noop registered
Apr 29 22:55:36 dan-desktop kernel: [   22.294922] io scheduler anticipatory registered
Apr 29 22:55:36 dan-desktop kernel: [   22.294924] io scheduler deadline registered
Apr 29 22:55:36 dan-desktop kernel: [   22.294938] io scheduler cfq registered (default)
Apr 29 22:55:36 dan-desktop kernel: [   22.295013] Boot video device is 0000:01:00.0
Apr 29 22:55:36 dan-desktop kernel: [   22.295019] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
Apr 29 22:55:36 dan-desktop kernel: [   22.295347] isapnp: Scanning for PnP cards...
Apr 29 22:55:36 dan-desktop kernel: [   22.648992] isapnp: No Plug & Play device found
Apr 29 22:55:36 dan-desktop kernel: [   22.682884] Real Time Clock Driver v1.12ac
Apr 29 22:55:36 dan-desktop kernel: [   22.683007] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 29 22:55:36 dan-desktop kernel: [   22.683139] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 29 22:55:36 dan-desktop kernel: [   22.684398] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 29 22:55:36 dan-desktop kernel: [   22.684596] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 19 (level, low) -> IRQ 16
Apr 29 22:55:36 dan-desktop kernel: [   22.686007] 0000:02:09.0: ttyS1 at I/O 0x4428 (irq = 16) is a 8250
Apr 29 22:55:36 dan-desktop kernel: [   22.686712] 0000:02:09.0: ttyS2 at I/O 0x4440 (irq = 16) is a 8250
Apr 29 22:55:36 dan-desktop kernel: [   22.687197] 0000:02:09.0: ttyS3 at I/O 0x4450 (irq = 16) is a 8250
Apr 29 22:55:36 dan-desktop kernel: [   22.687281] Couldn't register serial port 0000:02:09.0: -28
Apr 29 22:55:36 dan-desktop kernel: [   22.688047] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 29 22:55:36 dan-desktop kernel: [   22.688126] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Apr 29 22:55:36 dan-desktop kernel: [   22.688255] PNP: PS/2 Controller [PNP0303:KEYB,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr 29 22:55:36 dan-desktop kernel: [   22.690907] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 29 22:55:36 dan-desktop kernel: [   22.690912] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 29 22:55:36 dan-desktop kernel: [   22.695695] mice: PS/2 mouse device common for all mice
Apr 29 22:55:36 dan-desktop kernel: [   22.695838] EISA: Probing bus 0 at eisa.0
Apr 29 22:55:36 dan-desktop kernel: [   22.695846] Cannot allocate resource for EISA slot 1
Apr 29 22:55:36 dan-desktop kernel: [   22.695848] Cannot allocate resource for EISA slot 2
Apr 29 22:55:36 dan-desktop kernel: [   22.695850] Cannot allocate resource for EISA slot 3
Apr 29 22:55:36 dan-desktop kernel: [   22.695852] Cannot allocate resource for EISA slot 4
Apr 29 22:55:36 dan-desktop kernel: [   22.695869] EISA: Detected 0 cards.
Apr 29 22:55:36 dan-desktop kernel: [   22.695872] cpuidle: using governor ladder
Apr 29 22:55:36 dan-desktop kernel: [   22.695874] cpuidle: using governor menu
Apr 29 22:55:36 dan-desktop kernel: [   22.695983] NET: Registered protocol family 1
Apr 29 22:55:36 dan-desktop kernel: [   22.696018] Using IPI No-Shortcut mode
Apr 29 22:55:36 dan-desktop kernel: [   22.696054] registered taskstats version 1
Apr 29 22:55:36 dan-desktop kernel: [   22.696153]   Magic number: 4:393:958
Apr 29 22:55:36 dan-desktop kernel: [   22.696218]   hash matches device ptyzf
Apr 29 22:55:36 dan-desktop kernel: [   22.696264]   hash matches device oldmem
Apr 29 22:55:36 dan-desktop kernel: [   22.696284] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr 29 22:55:36 dan-desktop kernel: [   22.696286] EDD information not available.
Apr 29 22:55:36 dan-desktop kernel: [   22.696744] Freeing unused kernel memory: 364k freed
Apr 29 22:55:36 dan-desktop kernel: [   22.723529] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Apr 29 22:55:36 dan-desktop kernel: [   23.941084] fuse init (API version 7.9)
Apr 29 22:55:36 dan-desktop kernel: [   24.564260] usbcore: registered new interface driver usbfs
Apr 29 22:55:36 dan-desktop kernel: [   24.564290] usbcore: registered new interface driver hub
Apr 29 22:55:36 dan-desktop kernel: [   24.581191] usbcore: registered new device driver usb
Apr 29 22:55:36 dan-desktop kernel: [   24.591013] USB Universal Host Controller Interface driver v3.0
Apr 29 22:55:36 dan-desktop kernel: [   24.591096] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 17
Apr 29 22:55:36 dan-desktop kernel: [   24.591109] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Apr 29 22:55:36 dan-desktop kernel: [   24.591114] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr 29 22:55:36 dan-desktop kernel: [   24.591463] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Apr 29 22:55:36 dan-desktop kernel: [   24.591493] uhci_hcd 0000:00:1d.0: irq 17, io base 0x00001000
Apr 29 22:55:36 dan-desktop kernel: [   24.591656] usb usb1: configuration #1 chosen from 1 choice
Apr 29 22:55:36 dan-desktop kernel: [   24.591683] hub 1-0:1.0: USB hub found
Apr 29 22:55:36 dan-desktop kernel: [   24.591690] hub 1-0:1.0: 2 ports detected
Apr 29 22:55:36 dan-desktop kernel: [   24.625121] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
Apr 29 22:55:36 dan-desktop kernel: [   24.625125] e100: Copyright(c) 1999-2006 Intel Corporation
Apr 29 22:55:36 dan-desktop kernel: [   24.642299] SCSI subsystem initialized
Apr 29 22:55:36 dan-desktop kernel: [   24.670901] libata version 3.00 loaded.
Apr 29 22:55:36 dan-desktop kernel: [   24.693078] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 16
Apr 29 22:55:36 dan-desktop kernel: [   24.693092] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Apr 29 22:55:36 dan-desktop kernel: [   24.693096] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr 29 22:55:36 dan-desktop kernel: [   24.693124] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Apr 29 22:55:36 dan-desktop kernel: [   24.693154] uhci_hcd 0000:00:1d.1: irq 16, io base 0x00001400
Apr 29 22:55:36 dan-desktop kernel: [   24.693280] usb usb2: configuration #1 chosen from 1 choice
Apr 29 22:55:36 dan-desktop kernel: [   24.693308] hub 2-0:1.0: USB hub found
Apr 29 22:55:36 dan-desktop kernel: [   24.693314] hub 2-0:1.0: 2 ports detected
Apr 29 22:55:36 dan-desktop kernel: [   24.796988] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Apr 29 22:55:36 dan-desktop kernel: [   24.797002] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Apr 29 22:55:36 dan-desktop kernel: [   24.797006] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr 29 22:55:36 dan-desktop kernel: [   24.797034] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Apr 29 22:55:36 dan-desktop kernel: [   24.797063] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001800
Apr 29 22:55:36 dan-desktop kernel: [   24.797204] usb usb3: configuration #1 chosen from 1 choice
Apr 29 22:55:36 dan-desktop kernel: [   24.797231] hub 3-0:1.0: USB hub found
Apr 29 22:55:36 dan-desktop kernel: [   24.797237] hub 3-0:1.0: 2 ports detected
Apr 29 22:55:36 dan-desktop kernel: [   24.837329] Floppy drive(s): fd0 is 1.44M
Apr 29 22:55:36 dan-desktop kernel: [   24.857339] FDC 0 is a post-1991 82077
Apr 29 22:55:36 dan-desktop kernel: [   24.901062] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
Apr 29 22:55:36 dan-desktop kernel: [   24.901081] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Apr 29 22:55:36 dan-desktop kernel: [   24.901085] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr 29 22:55:36 dan-desktop kernel: [   24.901118] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Apr 29 22:55:36 dan-desktop kernel: [   24.905032] ehci_hcd 0000:00:1d.7: debug port 1
Apr 29 22:55:36 dan-desktop kernel: [   24.905039] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
Apr 29 22:55:36 dan-desktop kernel: [   24.905051] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xd0000000
Apr 29 22:55:36 dan-desktop kernel: [   24.932688] usb 1-2: new full speed USB device using uhci_hcd and address 2
Apr 29 22:55:36 dan-desktop kernel: [   24.944663] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr 29 22:55:36 dan-desktop kernel: [   24.944832] usb usb4: configuration #1 chosen from 1 choice
Apr 29 22:55:36 dan-desktop kernel: [   24.944862] hub 4-0:1.0: USB hub found
Apr 29 22:55:36 dan-desktop kernel: [   24.944870] hub 4-0:1.0: 6 ports detected
Apr 29 22:55:36 dan-desktop kernel: [   25.048900] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 20
Apr 29 22:55:36 dan-desktop kernel: [   25.072916] e100: eth0: e100_probe: addr 0xd0200000, irq 20, MAC addr 00:30:05:3c:4d:7c
Apr 29 22:55:36 dan-desktop kernel: [   25.072940] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
Apr 29 22:55:36 dan-desktop kernel: [   25.072947] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Apr 29 22:55:36 dan-desktop kernel: [   25.072997] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Apr 29 22:55:36 dan-desktop kernel: [   25.073012] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
Apr 29 22:55:36 dan-desktop kernel: [   25.077694] ata_piix 0000:00:1f.1: version 2.12
Apr 29 22:55:36 dan-desktop kernel: [   25.077716] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Apr 29 22:55:36 dan-desktop kernel: [   25.077772] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Apr 29 22:55:36 dan-desktop kernel: [   25.079088] scsi0 : ata_piix
Apr 29 22:55:36 dan-desktop kernel: [   25.080049] scsi1 : ata_piix
Apr 29 22:55:36 dan-desktop kernel: [   25.080752] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x2800 irq 14
Apr 29 22:55:36 dan-desktop kernel: [   25.080755] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x2808 irq 15
Apr 29 22:55:36 dan-desktop kernel: [   25.300713] ata1.00: ATA-6: ST380022A, 3.33, max UDMA/100
Apr 29 22:55:36 dan-desktop kernel: [   25.300718] ata1.00: 156301488 sectors, multi 16: LBA 
Apr 29 22:55:36 dan-desktop kernel: [   25.316613] ata1.00: configured for UDMA/100
Apr 29 22:55:36 dan-desktop kernel: [   25.619863] usb 1-2: new full speed USB device using uhci_hcd and address 3
Apr 29 22:55:36 dan-desktop kernel: [   25.799850] ata2.00: ATAPI: HL-DT-STDVD-ROM GDR8161B, 0042, max UDMA/33
Apr 29 22:55:36 dan-desktop kernel: [   25.799878] ata2.01: ATAPI: HL-DT-ST GCE-8481B, 1.00, max UDMA/33
Apr 29 22:55:36 dan-desktop kernel: [   25.812886] usb 1-2: configuration #1 chosen from 1 choice
Apr 29 22:55:36 dan-desktop kernel: [   25.971556] ata2.00: configured for UDMA/33
Apr 29 22:55:36 dan-desktop kernel: [   26.143337] ata2.01: configured for UDMA/33
Apr 29 22:55:36 dan-desktop kernel: [   26.143488] scsi 0:0:0:0: Direct-Access     ATA      ST380022A        3.33 PQ: 0 ANSI: 5
Apr 29 22:55:36 dan-desktop kernel: [   26.154548] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDR8161B 0042 PQ: 0 ANSI: 5
Apr 29 22:55:36 dan-desktop kernel: [   26.155062] scsi 1:0:1:0: CD-ROM            HL-DT-ST CD-RW GCE-8481B  1.00 PQ: 0 ANSI: 5
Apr 29 22:55:36 dan-desktop kernel: [   26.170972] Driver 'sd' needs updating - please use bus_type methods
Apr 29 22:55:36 dan-desktop kernel: [   26.171136] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 29 22:55:36 dan-desktop kernel: [   26.171152] sd 0:0:0:0: [sda] Write Protect is off
Apr 29 22:55:36 dan-desktop kernel: [   26.171155] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 29 22:55:36 dan-desktop kernel: [   26.171181] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 29 22:55:36 dan-desktop kernel: [   26.171239] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 29 22:55:36 dan-desktop kernel: [   26.171253] sd 0:0:0:0: [sda] Write Protect is off
Apr 29 22:55:36 dan-desktop kernel: [   26.171256] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 29 22:55:36 dan-desktop kernel: [   26.171279] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 29 22:55:36 dan-desktop kernel: [   26.171283]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Apr 29 22:55:36 dan-desktop kernel: [   26.189724]  sda1 sda2 sda3
Apr 29 22:55:36 dan-desktop kernel: [   26.206130] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 29 22:55:36 dan-desktop kernel: [   26.213334] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 29 22:55:36 dan-desktop kernel: [   26.213359] sr 1:0:0:0: Attached scsi generic sg1 type 5
Apr 29 22:55:36 dan-desktop kernel: [   26.213380] scsi 1:0:1:0: Attached scsi generic sg2 type 5
Apr 29 22:55:36 dan-desktop kernel: [   26.230936] sr0: scsi3-mmc drive: 20x/48x cd/rw xa/form2 cdda tray
Apr 29 22:55:36 dan-desktop kernel: [   26.230943] Uniform CD-ROM driver Revision: 3.20
Apr 29 22:55:36 dan-desktop kernel: [   26.231026] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr 29 22:55:36 dan-desktop kernel: [   26.234570] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Apr 29 22:55:36 dan-desktop kernel: [   26.234646] sr 1:0:1:0: Attached scsi CD-ROM sr1
Apr 29 22:55:36 dan-desktop kernel: [   26.928143] Attempting manual resume
Apr 29 22:55:36 dan-desktop kernel: [   26.928148] swsusp: Resume From Partition 8:3
Apr 29 22:55:36 dan-desktop kernel: [   26.928150] PM: Checking swsusp image.
Apr 29 22:55:36 dan-desktop kernel: [   26.936862] PM: Resume from disk failed.
Apr 29 22:55:36 dan-desktop kernel: [   26.977842] kjournald starting.  Commit interval 5 seconds
Apr 29 22:55:36 dan-desktop kernel: [   26.977856] EXT3-fs: mounted filesystem with ordered data mode.
Apr 29 22:55:36 dan-desktop kernel: [   35.375402] input: PC Speaker as /devices/platform/pcspkr/input/input2
Apr 29 22:55:36 dan-desktop kernel: [   35.542264] iTCO_vendor_support: vendor-support=0
Apr 29 22:55:36 dan-desktop kernel: [   35.586449] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Apr 29 22:55:36 dan-desktop kernel: [   35.635137] Linux agpgart interface v0.102
Apr 29 22:55:36 dan-desktop kernel: [   35.696200] agpgart: Detected an Intel 830M Chipset.
Apr 29 22:55:36 dan-desktop kernel: [   35.699306] agpgart: AGP aperture is 64M @ 0xe0000000
Apr 29 22:55:36 dan-desktop kernel: [   35.730873] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 29 22:55:36 dan-desktop kernel: [   35.771855] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr 29 22:55:36 dan-desktop kernel: [   36.018235] input: Power Button (FF) as /devices/virtual/input/input3
Apr 29 22:55:36 dan-desktop kernel: [   36.042529] ACPI: Power Button (FF) [PWRF]
Apr 29 22:55:36 dan-desktop kernel: [   36.042618] input: Power Button (CM) as /devices/virtual/input/input4
Apr 29 22:55:36 dan-desktop kernel: [   36.070422] ACPI: Power Button (CM) [PWRB]
Apr 29 22:55:36 dan-desktop kernel: [   36.235987] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Apr 29 22:55:36 dan-desktop kernel: [   36.264812] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0xf060)
Apr 29 22:55:36 dan-desktop kernel: [   36.264942] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Apr 29 22:55:36 dan-desktop kernel: [   36.264990] parport_pc 00:0a: reported by Plug and Play ACPI
Apr 29 22:55:36 dan-desktop kernel: [   36.265015] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
Apr 29 22:55:36 dan-desktop kernel: [   36.592045] intel_rng: FWH not detected
Apr 29 22:55:36 dan-desktop kernel: [   38.039371] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
Apr 29 22:55:36 dan-desktop kernel: [   38.039401] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Apr 29 22:55:36 dan-desktop kernel: [   38.140818] Linux video capture interface: v2.00
Apr 29 22:55:36 dan-desktop kernel: [   38.171447] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found.(SPCA561A)
Apr 29 22:55:36 dan-desktop kernel: [   38.177136] usbcore: registered new interface driver gspca
Apr 29 22:55:36 dan-desktop kernel: [   38.177142] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
Apr 29 22:55:36 dan-desktop kernel: [   38.459303] intel8x0_measure_ac97_clock: measured 52092 usecs
Apr 29 22:55:36 dan-desktop kernel: [   38.459307] intel8x0: clocking to 48000
Apr 29 22:55:36 dan-desktop kernel: [   40.032922] lp0: using parport0 (interrupt-driven).
Apr 29 22:55:36 dan-desktop kernel: [   40.111752] Adding 522104k swap on /dev/sda3.  Priority:-1 extents:1 across:522104k
Apr 29 22:55:36 dan-desktop kernel: [   40.661143] EXT3 FS on sda2, internal journal
Apr 29 22:55:36 dan-desktop kernel: [   42.080034] ip_tables: (C) 2000-2006 Netfilter Core Team
Apr 29 22:55:36 dan-desktop kernel: [   42.600078] No dock devices found.
Apr 29 22:55:38 dan-desktop kernel: [   45.138758] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Apr 29 22:55:38 dan-desktop kernel: [   45.290732] ppdev: user-space parallel port driver
Apr 29 22:55:38 dan-desktop kernel: [   45.486309] audit(1209506138.549:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4910 profile="/usr/sbin/cupsd" namespace="default"
Apr 29 22:55:38 dan-desktop kernel: [   45.524322] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Apr 29 22:55:38 dan-desktop kernel: [   45.524328] apm: overridden by ACPI.
Apr 29 22:55:38 dan-desktop kernel: [   45.785978] Bluetooth: Core ver 2.11
Apr 29 22:55:38 dan-desktop kernel: [   45.787046] NET: Registered protocol family 31
Apr 29 22:55:38 dan-desktop kernel: [   45.787051] Bluetooth: HCI device and connection manager initialized
Apr 29 22:55:38 dan-desktop kernel: [   45.787056] Bluetooth: HCI socket layer initialized
Apr 29 22:55:38 dan-desktop kernel: [   45.919612] Bluetooth: L2CAP ver 2.9
Apr 29 22:55:38 dan-desktop kernel: [   45.919618] Bluetooth: L2CAP socket layer initialized
Apr 29 22:55:39 dan-desktop kernel: [   46.005053] Bluetooth: RFCOMM socket layer initialized
Apr 29 22:55:39 dan-desktop kernel: [   46.005077] Bluetooth: RFCOMM TTY layer initialized
Apr 29 22:55:39 dan-desktop kernel: [   46.005079] Bluetooth: RFCOMM ver 1.8
Apr 29 22:55:43 dan-desktop kernel: [   49.965482] NET: Registered protocol family 17
Apr 29 22:55:45 dan-desktop kernel: [   52.589598] NET: Registered protocol family 10
Apr 29 22:55:45 dan-desktop kernel: [   52.590537] lo: Disabled Privacy Extensions
Apr 29 22:55:55 dan-desktop kernel: [   62.892734] eth0: no IPv6 routers present
Apr 29 22:58:40 dan-desktop kernel: Inspecting /boot/System.map-2.6.24-16-generic
Apr 29 22:58:40 dan-desktop kernel: Loaded 27704 symbols from /boot/System.map-2.6.24-16-generic.
Apr 29 22:58:40 dan-desktop kernel: Symbols match kernel version 2.6.24.
Apr 29 22:58:40 dan-desktop kernel: Loaded 15297 symbols from 80 modules.
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 29 22:58:40 dan-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000000fef0000 (usable)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000]  BIOS-e820: 000000000fef0000 - 000000000fefc000 (ACPI data)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000]  BIOS-e820: 000000000fefc000 - 000000000ff00000 (ACPI NVS)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000]  BIOS-e820: 000000000ff00000 - 000000000ff80000 (usable)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000]  BIOS-e820: 000000000ff80000 - 0000000010000000 (reserved)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] 0MB HIGHMEM available.
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] 255MB LOWMEM available.
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 65408) 0 entries of 256 used
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] Zone PFN ranges:
Apr 29 22:58:40 dan-desktop kernel: [    0.000000]   DMA             0 ->     4096
Apr 29 22:58:40 dan-desktop kernel: [    0.000000]   Normal       4096 ->    65408
Apr 29 22:58:40 dan-desktop kernel: [    0.000000]   HighMem     65408 ->    65408
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] Movable zone start PFN for each node
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 29 22:58:40 dan-desktop kernel: [    0.000000]     0:        0 ->    65408
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] On node 0 totalpages: 65408
Apr 29 22:58:40 dan-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 29 22:58:40 dan-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 29 22:58:40 dan-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr 29 22:58:40 dan-desktop kernel: [    0.000000]   Normal zone: 479 pages used for memmap
Apr 29 22:58:40 dan-desktop kernel: [    0.000000]   Normal zone: 60833 pages, LIFO batch:15
Apr 29 22:58:40 dan-desktop kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Apr 29 22:58:40 dan-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] DMI present.
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7CE0 checksum 0
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] ACPI: RSDP 000F7CE0, 0014 (r0 PTLTD )
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] ACPI: RSDT 0FEF90BC, 0030 (r1 PTLTD    RSDT    6040001  LTP        0)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] ACPI: FACP 0FEF90EC, 0074 (r1 FSC    D152X     6040001         F4240)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] ACPI: DSDT 0FEF9160, 2E1E (r1 FSC    D152X     6040001 MSFT  100000E)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] ACPI: FACS 0FEFCFC0, 0040
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] ACPI: APIC 0FEFBF7E, 005A (r1 FSC    ^I APIC    6040001  CSF        0)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] ACPI: BOOT 0FEFBFD8, 0028 (r1 PTLTD  $SBFTBL$  6040001  LTP        1)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] ACPI: DMI detected: Fujitsu Siemens
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xf008
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] Processor #0 15:2 APIC version 20
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:eec00000)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000ce000
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000ce000 - 00000000000d0000
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000d0000 - 00000000000dc000
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 00000000000e0000
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 00000000000e4000
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000fef0000 - 000000000fefc000
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000fefc000 - 000000000ff00000
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64897
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] Kernel command line: root=UUID=0bfca241-5f24-4fea-a85e-4e3bff4ee371 ro quiet splash
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] Initializing CPU#0
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
Apr 29 22:58:40 dan-desktop kernel: [    0.000000] Detected 2525.267 MHz processor.
Apr 29 22:58:40 dan-desktop kernel: [   21.880948] Console: colour VGA+ 80x25
Apr 29 22:58:40 dan-desktop kernel: [   21.880953] console [tty0] enabled
Apr 29 22:58:40 dan-desktop kernel: [   21.881155] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 29 22:58:40 dan-desktop kernel: [   21.881317] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Apr 29 22:58:40 dan-desktop kernel: [   21.886917] Memory: 247460k/261632k available (2157k kernel code, 13620k reserved, 998k data, 364k init, 0k highmem)
Apr 29 22:58:40 dan-desktop kernel: [   21.886926] virtual kernel memory layout:
Apr 29 22:58:40 dan-desktop kernel: [   21.886927]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Apr 29 22:58:40 dan-desktop kernel: [   21.886928]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr 29 22:58:40 dan-desktop kernel: [   21.886929]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB)
Apr 29 22:58:40 dan-desktop kernel: [   21.886930]     lowmem  : 0xc0000000 - 0xcff80000   ( 255 MB)
Apr 29 22:58:40 dan-desktop kernel: [   21.886931]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
Apr 29 22:58:40 dan-desktop kernel: [   21.886933]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
Apr 29 22:58:40 dan-desktop kernel: [   21.886934]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
Apr 29 22:58:40 dan-desktop kernel: [   21.886937] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 29 22:58:40 dan-desktop kernel: [   21.886972] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Apr 29 22:58:40 dan-desktop kernel: [   21.966898] Calibrating delay using timer specific routine.. 5055.03 BogoMIPS (lpj=10110072)
Apr 29 22:58:40 dan-desktop kernel: [   21.966925] Security Framework initialized
Apr 29 22:58:40 dan-desktop kernel: [   21.966932] SELinux:  Disabled at boot.
Apr 29 22:58:40 dan-desktop kernel: [   21.966947] AppArmor: AppArmor initialized
Apr 29 22:58:40 dan-desktop kernel: [   21.966952] Failure registering capabilities with primary security module.
Apr 29 22:58:40 dan-desktop kernel: [   21.966961] Mount-cache hash table entries: 512
Apr 29 22:58:40 dan-desktop kernel: [   21.967099] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
Apr 29 22:58:40 dan-desktop kernel: [   21.967113] CPU: Trace cache: 12K uops, L1 D cache: 8K
Apr 29 22:58:40 dan-desktop kernel: [   21.967116] CPU: L2 cache: 512K
Apr 29 22:58:40 dan-desktop kernel: [   21.967119] CPU: Hyper-Threading is disabled
Apr 29 22:58:40 dan-desktop kernel: [   21.967121] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
Apr 29 22:58:40 dan-desktop kernel: [   21.967133] Compat vDSO mapped to ffffe000.
Apr 29 22:58:40 dan-desktop kernel: [   21.967147] Checking 'hlt' instruction... OK.
Apr 29 22:58:40 dan-desktop kernel: [   21.983268] SMP alternatives: switching to UP code
Apr 29 22:58:40 dan-desktop kernel: [   21.984933] Freeing SMP alternatives: 11k freed
Apr 29 22:58:40 dan-desktop kernel: [   21.985083] Early unpacking initramfs... done
Apr 29 22:58:40 dan-desktop kernel: [   22.314050] ACPI: Core revision 20070126
Apr 29 22:58:40 dan-desktop kernel: [   22.314111] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Apr 29 22:58:40 dan-desktop kernel: [   22.316315] CPU0: Intel(R) Pentium(R) 4 CPU 2.53GHz stepping 07
Apr 29 22:58:40 dan-desktop kernel: [   22.316360] Total of 1 processors activated (5055.03 BogoMIPS).
Apr 29 22:58:40 dan-desktop kernel: [   22.316496] ENABLING IO-APIC IRQs
Apr 29 22:58:40 dan-desktop kernel: [   22.316684] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 29 22:58:40 dan-desktop kernel: [   22.462361] Brought up 1 CPUs
Apr 29 22:58:40 dan-desktop kernel: [   22.462387] CPU0 attaching sched-domain:
Apr 29 22:58:40 dan-desktop kernel: [   22.462390]  domain 0: span 01
Apr 29 22:58:40 dan-desktop kernel: [   22.462393]   groups: 01
Apr 29 22:58:40 dan-desktop kernel: [   22.462599] net_namespace: 64 bytes
Apr 29 22:58:40 dan-desktop kernel: [   22.462609] Booting paravirtualized kernel on bare hardware
Apr 29 22:58:40 dan-desktop kernel: [   22.463250] Time: 22:58:18  Date: 04/29/08
Apr 29 22:58:40 dan-desktop kernel: [   22.463280] NET: Registered protocol family 16
Apr 29 22:58:40 dan-desktop kernel: [   22.463521] EISA bus registered
Apr 29 22:58:40 dan-desktop kernel: [   22.463548] ACPI: bus type pci registered
Apr 29 22:58:40 dan-desktop kernel: [   22.488543] PCI: PCI BIOS revision 2.10 entry at 0xfd987, last bus=2
Apr 29 22:58:40 dan-desktop kernel: [   22.488546] PCI: Using configuration type 1
Apr 29 22:58:40 dan-desktop kernel: [   22.488548] Setting up standard PCI resources
Apr 29 22:58:40 dan-desktop kernel: [   22.497157] ACPI: EC: Look up EC in DSDT
Apr 29 22:58:40 dan-desktop kernel: [   22.498924] ACPI: Interpreter enabled
Apr 29 22:58:40 dan-desktop kernel: [   22.498928] ACPI: (supports S0 S1 S3 S4 S5)
Apr 29 22:58:40 dan-desktop kernel: [   22.498945] ACPI: Using IOAPIC for interrupt routing
Apr 29 22:58:40 dan-desktop kernel: [   22.502101] ACPI: Device [ECP] status [00000008]: functional but not present; setting present
Apr 29 22:58:40 dan-desktop kernel: [   22.502508] ACPI: Device [COM2] status [00000008]: functional but not present; setting present
Apr 29 22:58:40 dan-desktop kernel: [   22.502775] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 29 22:58:40 dan-desktop kernel: [   22.503208] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Apr 29 22:58:40 dan-desktop kernel: [   22.503210] * this clock source is slow. If you are sure your timer does not have
Apr 29 22:58:40 dan-desktop kernel: [   22.503211] * this bug, please use "acpi_pm_good" to disable the workaround
Apr 29 22:58:40 dan-desktop kernel: [   22.503257] PCI quirk: region f000-f07f claimed by ICH4 ACPI/GPIO/TCO
Apr 29 22:58:40 dan-desktop kernel: [   22.503261] PCI quirk: region f180-f1bf claimed by ICH4 GPIO
Apr 29 22:58:40 dan-desktop kernel: [   22.503744] PCI: Transparent bridge - 0000:00:1e.0
Apr 29 22:58:40 dan-desktop kernel: [   22.503770] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 29 22:58:40 dan-desktop kernel: [   22.503955] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
Apr 29 22:58:40 dan-desktop kernel: [   22.504040] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIH._PRT]
Apr 29 22:58:40 dan-desktop kernel: [   22.506101] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Apr 29 22:58:40 dan-desktop kernel: [   22.506195] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Apr 29 22:58:40 dan-desktop kernel: [   22.506299] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Apr 29 22:58:40 dan-desktop kernel: [   22.506392] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Apr 29 22:58:40 dan-desktop kernel: [   22.506483] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Apr 29 22:58:40 dan-desktop kernel: [   22.506565] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Apr 29 22:58:40 dan-desktop kernel: [   22.506649] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Apr 29 22:58:40 dan-desktop kernel: [   22.506743] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Apr 29 22:58:40 dan-desktop kernel: [   22.506876] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 29 22:58:40 dan-desktop kernel: [   22.506917] pnp: PnP ACPI init
Apr 29 22:58:40 dan-desktop kernel: [   22.506928] ACPI: bus type pnp registered
Apr 29 22:58:40 dan-desktop kernel: [   22.508616] pnp: PnP ACPI: found 12 devices
Apr 29 22:58:40 dan-desktop kernel: [   22.508619] ACPI: ACPI bus type pnp unregistered
Apr 29 22:58:40 dan-desktop kernel: [   22.508625] PnPBIOS: Disabled by ACPI PNP
Apr 29 22:58:40 dan-desktop kernel: [   22.508904] PCI: Using ACPI for IRQ routing
Apr 29 22:58:40 dan-desktop kernel: [   22.508908] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 29 22:58:40 dan-desktop kernel: [   22.522249] NET: Registered protocol family 8
Apr 29 22:58:40 dan-desktop kernel: [   22.522252] NET: Registered protocol family 20
Apr 29 22:58:40 dan-desktop kernel: [   22.522332] AppArmor: AppArmor Filesystem Enabled
Apr 29 22:58:40 dan-desktop kernel: [   22.526234] Time: tsc clocksource has been installed.
Apr 29 22:58:40 dan-desktop kernel: [   22.534273] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Apr 29 22:58:40 dan-desktop kernel: [   22.534277] system 00:02: ioport range 0xf000-0xf07f has been reserved
Apr 29 22:58:40 dan-desktop kernel: [   22.534280] system 00:02: ioport range 0xf100-0xf10f has been reserved
Apr 29 22:58:40 dan-desktop kernel: [   22.534283] system 00:02: ioport range 0xf180-0xf1bf has been reserved
Apr 29 22:58:40 dan-desktop kernel: [   22.534285] system 00:02: ioport range 0x800-0x87f has been reserved
Apr 29 22:58:40 dan-desktop kernel: [   22.534288] system 00:02: ioport range 0xf820-0xf82f has been reserved
Apr 29 22:58:40 dan-desktop kernel: [   22.534291] system 00:02: ioport range 0xfe00-0xfe00 has been reserved
Apr 29 22:58:40 dan-desktop kernel: [   22.564766] PCI: Bridge: 0000:00:01.0
Apr 29 22:58:40 dan-desktop kernel: [   22.564770]   IO window: 3000-3fff
Apr 29 22:58:40 dan-desktop kernel: [   22.564776]   MEM window: d0100000-d01fffff
Apr 29 22:58:40 dan-desktop kernel: [   22.564780]   PREFETCH window: d8000000-dfffffff
Apr 29 22:58:40 dan-desktop kernel: [   22.564786] PCI: Bridge: 0000:00:1e.0
Apr 29 22:58:40 dan-desktop kernel: [   22.564789]   IO window: 4000-4fff
Apr 29 22:58:40 dan-desktop kernel: [   22.564795]   MEM window: d0200000-d02fffff
Apr 29 22:58:40 dan-desktop kernel: [   22.564799]   PREFETCH window: disabled.
Apr 29 22:58:40 dan-desktop kernel: [   22.564817] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Apr 29 22:58:40 dan-desktop kernel: [   22.564830] NET: Registered protocol family 2
Apr 29 22:58:40 dan-desktop kernel: [   22.602236] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
Apr 29 22:58:40 dan-desktop kernel: [   22.602493] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
Apr 29 22:58:40 dan-desktop kernel: [   22.602543] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Apr 29 22:58:40 dan-desktop kernel: [   22.602590] TCP: Hash tables configured (established 8192 bind 8192)
Apr 29 22:58:40 dan-desktop kernel: [   22.602592] TCP reno registered
Apr 29 22:58:40 dan-desktop kernel: [   22.614271] checking if image is initramfs... it is
Apr 29 22:58:40 dan-desktop kernel: [   23.065595] Switched to high resolution mode on CPU 0
Apr 29 22:58:40 dan-desktop kernel: [   23.264896] Freeing initrd memory: 7260k freed
Apr 29 22:58:40 dan-desktop kernel: [   23.265130] Simple Boot Flag at 0x69 set to 0x1
Apr 29 22:58:40 dan-desktop kernel: [   23.265629] audit: initializing netlink socket (disabled)
Apr 29 22:58:40 dan-desktop kernel: [   23.265649] audit(1209509898.276:1): initialized
Apr 29 22:58:40 dan-desktop kernel: [   23.267995] VFS: Disk quotas dquot_6.5.1
Apr 29 22:58:40 dan-desktop kernel: [   23.268085] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 29 22:58:40 dan-desktop kernel: [   23.268258] io scheduler noop registered
Apr 29 22:58:40 dan-desktop kernel: [   23.268260] io scheduler anticipatory registered
Apr 29 22:58:40 dan-desktop kernel: [   23.268262] io scheduler deadline registered
Apr 29 22:58:40 dan-desktop kernel: [   23.268275] io scheduler cfq registered (default)
Apr 29 22:58:40 dan-desktop kernel: [   23.268351] Boot video device is 0000:01:00.0
Apr 29 22:58:40 dan-desktop kernel: [   23.268356] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
Apr 29 22:58:40 dan-desktop kernel: [   23.268684] isapnp: Scanning for PnP cards...
Apr 29 22:58:40 dan-desktop kernel: [   23.622326] isapnp: No Plug & Play device found
Apr 29 22:58:40 dan-desktop kernel: [   23.657139] Real Time Clock Driver v1.12ac
Apr 29 22:58:40 dan-desktop kernel: [   23.657258] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 29 22:58:40 dan-desktop kernel: [   23.657391] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 29 22:58:40 dan-desktop kernel: [   23.658350] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 29 22:58:40 dan-desktop kernel: [   23.658520] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 19 (level, low) -> IRQ 16
Apr 29 22:58:40 dan-desktop kernel: [   23.659917] 0000:02:09.0: ttyS1 at I/O 0x4428 (irq = 16) is a 8250
Apr 29 22:58:40 dan-desktop kernel: [   23.660636] 0000:02:09.0: ttyS2 at I/O 0x4440 (irq = 16) is a 8250
Apr 29 22:58:40 dan-desktop kernel: [   23.661152] 0000:02:09.0: ttyS3 at I/O 0x4450 (irq = 16) is a 8250
Apr 29 22:58:40 dan-desktop kernel: [   23.661237] Couldn't register serial port 0000:02:09.0: -28
Apr 29 22:58:40 dan-desktop kernel: [   23.661995] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 29 22:58:40 dan-desktop kernel: [   23.662076] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Apr 29 22:58:40 dan-desktop kernel: [   23.662209] PNP: PS/2 Controller [PNP0303:KEYB,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr 29 22:58:40 dan-desktop kernel: [   23.664716] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 29 22:58:40 dan-desktop kernel: [   23.664721] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 29 22:58:40 dan-desktop kernel: [   23.676828] mice: PS/2 mouse device common for all mice
Apr 29 22:58:40 dan-desktop kernel: [   23.676973] EISA: Probing bus 0 at eisa.0
Apr 29 22:58:40 dan-desktop kernel: [   23.676981] Cannot allocate resource for EISA slot 1
Apr 29 22:58:40 dan-desktop kernel: [   23.676984] Cannot allocate resource for EISA slot 2
Apr 29 22:58:40 dan-desktop kernel: [   23.676986] Cannot allocate resource for EISA slot 3
Apr 29 22:58:40 dan-desktop kernel: [   23.676988] Cannot allocate resource for EISA slot 4
Apr 29 22:58:40 dan-desktop kernel: [   23.677005] EISA: Detected 0 cards.
Apr 29 22:58:40 dan-desktop kernel: [   23.677009] cpuidle: using governor ladder
Apr 29 22:58:40 dan-desktop kernel: [   23.677011] cpuidle: using governor menu
Apr 29 22:58:40 dan-desktop kernel: [   23.677121] NET: Registered protocol family 1
Apr 29 22:58:40 dan-desktop kernel: [   23.677157] Using IPI No-Shortcut mode
Apr 29 22:58:40 dan-desktop kernel: [   23.677193] registered taskstats version 1
Apr 29 22:58:40 dan-desktop kernel: [   23.677290]   Magic number: 4:943:1008
Apr 29 22:58:40 dan-desktop kernel: [   23.677298]   hash matches device ttye7
Apr 29 22:58:40 dan-desktop kernel: [   23.677307]   hash matches device ttyba
Apr 29 22:58:40 dan-desktop kernel: [   23.677422] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr 29 22:58:40 dan-desktop kernel: [   23.677424] EDD information not available.
Apr 29 22:58:40 dan-desktop kernel: [   23.677877] Freeing unused kernel memory: 364k freed
Apr 29 22:58:40 dan-desktop kernel: [   23.704739] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Apr 29 22:58:40 dan-desktop kernel: [   24.921325] fuse init (API version 7.9)
Apr 29 22:58:40 dan-desktop kernel: [   25.558389] usbcore: registered new interface driver usbfs
Apr 29 22:58:40 dan-desktop kernel: [   25.558417] usbcore: registered new interface driver hub
Apr 29 22:58:40 dan-desktop kernel: [   25.566374] usbcore: registered new device driver usb
Apr 29 22:58:40 dan-desktop kernel: [   25.575950] USB Universal Host Controller Interface driver v3.0
Apr 29 22:58:40 dan-desktop kernel: [   25.576032] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 17
Apr 29 22:58:40 dan-desktop kernel: [   25.576048] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Apr 29 22:58:40 dan-desktop kernel: [   25.576055] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr 29 22:58:40 dan-desktop kernel: [   25.576394] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Apr 29 22:58:40 dan-desktop kernel: [   25.576428] uhci_hcd 0000:00:1d.0: irq 17, io base 0x00001000
Apr 29 22:58:40 dan-desktop kernel: [   25.576592] usb usb1: configuration #1 chosen from 1 choice
Apr 29 22:58:40 dan-desktop kernel: [   25.576619] hub 1-0:1.0: USB hub found
Apr 29 22:58:40 dan-desktop kernel: [   25.576626] hub 1-0:1.0: 2 ports detected
Apr 29 22:58:40 dan-desktop kernel: [   25.627410] SCSI subsystem initialized
Apr 29 22:58:40 dan-desktop kernel: [   25.674029] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
Apr 29 22:58:40 dan-desktop kernel: [   25.674033] e100: Copyright(c) 1999-2006 Intel Corporation
Apr 29 22:58:40 dan-desktop kernel: [   25.678275] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 16
Apr 29 22:58:40 dan-desktop kernel: [   25.678290] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Apr 29 22:58:40 dan-desktop kernel: [   25.678297] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr 29 22:58:40 dan-desktop kernel: [   25.678324] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Apr 29 22:58:40 dan-desktop kernel: [   25.678356] uhci_hcd 0000:00:1d.1: irq 16, io base 0x00001400
Apr 29 22:58:40 dan-desktop kernel: [   25.678486] usb usb2: configuration #1 chosen from 1 choice
Apr 29 22:58:40 dan-desktop kernel: [   25.678518] hub 2-0:1.0: USB hub found
Apr 29 22:58:40 dan-desktop kernel: [   25.678524] hub 2-0:1.0: 2 ports detected
Apr 29 22:58:40 dan-desktop kernel: [   25.686182] libata version 3.00 loaded.
Apr 29 22:58:40 dan-desktop kernel: [   25.782175] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Apr 29 22:58:40 dan-desktop kernel: [   25.782192] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Apr 29 22:58:40 dan-desktop kernel: [   25.782199] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr 29 22:58:40 dan-desktop kernel: [   25.782228] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Apr 29 22:58:40 dan-desktop kernel: [   25.782259] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001800
Apr 29 22:58:40 dan-desktop kernel: [   25.782397] usb usb3: configuration #1 chosen from 1 choice
Apr 29 22:58:40 dan-desktop kernel: [   25.782426] hub 3-0:1.0: USB hub found
Apr 29 22:58:40 dan-desktop kernel: [   25.782433] hub 3-0:1.0: 2 ports detected
Apr 29 22:58:40 dan-desktop kernel: [   25.823339] Floppy drive(s): fd0 is 1.44M
Apr 29 22:58:40 dan-desktop kernel: [   25.841686] FDC 0 is a post-1991 82077
Apr 29 22:58:40 dan-desktop kernel: [   25.886158] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
Apr 29 22:58:40 dan-desktop kernel: [   25.886176] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Apr 29 22:58:40 dan-desktop kernel: [   25.886180] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr 29 22:58:40 dan-desktop kernel: [   25.886212] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Apr 29 22:58:40 dan-desktop kernel: [   25.890113] ehci_hcd 0000:00:1d.7: debug port 1
Apr 29 22:58:40 dan-desktop kernel: [   25.890120] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
Apr 29 22:58:40 dan-desktop kernel: [   25.890131] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xd0000000
Apr 29 22:58:40 dan-desktop kernel: [   25.917877] usb 1-2: new full speed USB device using uhci_hcd and address 2
Apr 29 22:58:40 dan-desktop kernel: [   25.929884] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr 29 22:58:40 dan-desktop kernel: [   25.930072] usb usb4: configuration #1 chosen from 1 choice
Apr 29 22:58:40 dan-desktop kernel: [   25.930102] hub 4-0:1.0: USB hub found
Apr 29 22:58:40 dan-desktop kernel: [   25.930110] hub 4-0:1.0: 6 ports detected
Apr 29 22:58:40 dan-desktop kernel: [   26.033984] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 20
Apr 29 22:58:40 dan-desktop kernel: [   26.058026] e100: eth0: e100_probe: addr 0xd0200000, irq 20, MAC addr 00:30:05:3c:4d:7c
Apr 29 22:58:40 dan-desktop kernel: [   26.058052] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
Apr 29 22:58:40 dan-desktop kernel: [   26.058058] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Apr 29 22:58:40 dan-desktop kernel: [   26.058107] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Apr 29 22:58:40 dan-desktop kernel: [   26.058122] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
Apr 29 22:58:40 dan-desktop kernel: [   26.062984] ata_piix 0000:00:1f.1: version 2.12
Apr 29 22:58:40 dan-desktop kernel: [   26.063006] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Apr 29 22:58:40 dan-desktop kernel: [   26.063066] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Apr 29 22:58:40 dan-desktop kernel: [   26.064377] scsi0 : ata_piix
Apr 29 22:58:40 dan-desktop kernel: [   26.065337] scsi1 : ata_piix
Apr 29 22:58:40 dan-desktop kernel: [   26.066039] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x2800 irq 14
Apr 29 22:58:40 dan-desktop kernel: [   26.066043] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x2808 irq 15
Apr 29 22:58:40 dan-desktop kernel: [   26.285912] ata1.00: ATA-6: ST380022A, 3.33, max UDMA/100
Apr 29 22:58:40 dan-desktop kernel: [   26.285917] ata1.00: 156301488 sectors, multi 16: LBA 
Apr 29 22:58:40 dan-desktop kernel: [   26.301809] ata1.00: configured for UDMA/100
Apr 29 22:58:40 dan-desktop kernel: [   26.592973] usb 1-2: new full speed USB device using uhci_hcd and address 3
Apr 29 22:58:40 dan-desktop kernel: [   26.785013] ata2.00: ATAPI: HL-DT-STDVD-ROM GDR8161B, 0042, max UDMA/33
Apr 29 22:58:40 dan-desktop kernel: [   26.785041] ata2.01: ATAPI: HL-DT-ST GCE-8481B, 1.00, max UDMA/33
Apr 29 22:58:40 dan-desktop kernel: [   26.842762] usb 1-2: configuration #1 chosen from 1 choice
Apr 29 22:58:40 dan-desktop kernel: [   26.956731] ata2.00: configured for UDMA/33
Apr 29 22:58:40 dan-desktop kernel: [   27.128505] ata2.01: configured for UDMA/33
Apr 29 22:58:40 dan-desktop kernel: [   27.128659] scsi 0:0:0:0: Direct-Access     ATA      ST380022A        3.33 PQ: 0 ANSI: 5
Apr 29 22:58:40 dan-desktop kernel: [   27.139711] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDR8161B 0042 PQ: 0 ANSI: 5
Apr 29 22:58:40 dan-desktop kernel: [   27.140233] scsi 1:0:1:0: CD-ROM            HL-DT-ST CD-RW GCE-8481B  1.00 PQ: 0 ANSI: 5
Apr 29 22:58:40 dan-desktop kernel: [   27.156219] Driver 'sd' needs updating - please use bus_type methods
Apr 29 22:58:40 dan-desktop kernel: [   27.156396] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 29 22:58:40 dan-desktop kernel: [   27.156413] sd 0:0:0:0: [sda] Write Protect is off
Apr 29 22:58:40 dan-desktop kernel: [   27.156416] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 29 22:58:40 dan-desktop kernel: [   27.156441] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 29 22:58:40 dan-desktop kernel: [   27.156499] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Apr 29 22:58:40 dan-desktop kernel: [   27.156513] sd 0:0:0:0: [sda] Write Protect is off
Apr 29 22:58:40 dan-desktop kernel: [   27.156516] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 29 22:58:40 dan-desktop kernel: [   27.156539] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 29 22:58:40 dan-desktop kernel: [   27.156543]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Apr 29 22:58:40 dan-desktop kernel: [   27.171962]  sda1 sda2 sda3
Apr 29 22:58:40 dan-desktop kernel: [   27.188366] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 29 22:58:40 dan-desktop kernel: [   27.195585] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 29 22:58:40 dan-desktop kernel: [   27.195610] sr 1:0:0:0: Attached scsi generic sg1 type 5
Apr 29 22:58:40 dan-desktop kernel: [   27.195631] scsi 1:0:1:0: Attached scsi generic sg2 type 5
Apr 29 22:58:40 dan-desktop kernel: [   27.218041] sr0: scsi3-mmc drive: 20x/48x cd/rw xa/form2 cdda tray
Apr 29 22:58:40 dan-desktop kernel: [   27.218048] Uniform CD-ROM driver Revision: 3.20
Apr 29 22:58:40 dan-desktop kernel: [   27.218118] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr 29 22:58:40 dan-desktop kernel: [   27.221660] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Apr 29 22:58:40 dan-desktop kernel: [   27.221731] sr 1:0:1:0: Attached scsi CD-ROM sr1
Apr 29 22:58:40 dan-desktop kernel: [   27.885452] Attempting manual resume
Apr 29 22:58:40 dan-desktop kernel: [   27.885457] swsusp: Resume From Partition 8:3
Apr 29 22:58:40 dan-desktop kernel: [   27.885459] PM: Checking swsusp image.
Apr 29 22:58:40 dan-desktop kernel: [   27.894175] PM: Resume from disk failed.
Apr 29 22:58:40 dan-desktop kernel: [   27.935156] kjournald starting.  Commit interval 5 seconds
Apr 29 22:58:40 dan-desktop kernel: [   27.935171] EXT3-fs: mounted filesystem with ordered data mode.
Apr 29 22:58:40 dan-desktop kernel: [   36.372437] input: PC Speaker as /devices/platform/pcspkr/input/input2
Apr 29 22:58:40 dan-desktop kernel: [   36.554816] iTCO_vendor_support: vendor-support=0
Apr 29 22:58:40 dan-desktop kernel: [   36.626588] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Apr 29 22:58:40 dan-desktop kernel: [   36.666905] Linux agpgart interface v0.102
Apr 29 22:58:40 dan-desktop kernel: [   36.703601] agpgart: Detected an Intel 830M Chipset.
Apr 29 22:58:40 dan-desktop kernel: [   36.706995] agpgart: AGP aperture is 64M @ 0xe0000000
Apr 29 22:58:40 dan-desktop kernel: [   36.735390] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 29 22:58:40 dan-desktop kernel: [   36.776475] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr 29 22:58:40 dan-desktop kernel: [   36.975036] input: Power Button (FF) as /devices/virtual/input/input3
Apr 29 22:58:40 dan-desktop kernel: [   37.023557] ACPI: Power Button (FF) [PWRF]
Apr 29 22:58:40 dan-desktop kernel: [   37.023647] input: Power Button (CM) as /devices/virtual/input/input4
Apr 29 22:58:40 dan-desktop kernel: [   37.051484] ACPI: Power Button (CM) [PWRB]
Apr 29 22:58:40 dan-desktop kernel: [   37.248554] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Apr 29 22:58:40 dan-desktop kernel: [   37.281885] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0xf060)
Apr 29 22:58:40 dan-desktop kernel: [   37.281921] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Apr 29 22:58:40 dan-desktop kernel: [   37.281968] parport_pc 00:0a: reported by Plug and Play ACPI
Apr 29 22:58:40 dan-desktop kernel: [   37.281991] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
Apr 29 22:58:40 dan-desktop kernel: [   37.470757] intel_rng: FWH not detected
Apr 29 22:58:40 dan-desktop kernel: [   39.039391] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
Apr 29 22:58:40 dan-desktop kernel: [   39.039422] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Apr 29 22:58:40 dan-desktop kernel: [   39.173082] Linux video capture interface: v2.00
Apr 29 22:58:40 dan-desktop kernel: [   39.203845] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found.(SPCA561A)
Apr 29 22:58:40 dan-desktop kernel: [   39.208963] usbcore: registered new interface driver gspca
Apr 29 22:58:40 dan-desktop kernel: [   39.208970] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
Apr 29 22:58:40 dan-desktop kernel: [   39.464313] intel8x0_measure_ac97_clock: measured 55880 usecs
Apr 29 22:58:40 dan-desktop kernel: [   39.464317] intel8x0: clocking to 48000
Apr 29 22:58:40 dan-desktop kernel: [   41.039912] lp0: using parport0 (interrupt-driven).
Apr 29 22:58:40 dan-desktop kernel: [   41.110373] Adding 522104k swap on /dev/sda3.  Priority:-1 extents:1 across:522104k
Apr 29 22:58:40 dan-desktop kernel: [   41.659155] EXT3 FS on sda2, internal journal
Apr 29 22:58:40 dan-desktop kernel: [   43.078625] ip_tables: (C) 2000-2006 Netfilter Core Team
Apr 29 22:58:40 dan-desktop kernel: [   43.590424] No dock devices found.
Apr 29 22:58:42 dan-desktop kernel: [   46.067857] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Apr 29 22:58:42 dan-desktop kernel: [   46.222887] ppdev: user-space parallel port driver
Apr 29 22:58:42 dan-desktop kernel: [   46.410204] audit(1209506322.460:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4910 profile="/usr/sbin/cupsd" namespace="default"
Apr 29 22:58:42 dan-desktop kernel: [   46.448234] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Apr 29 22:58:42 dan-desktop kernel: [   46.448241] apm: overridden by ACPI.
Apr 29 22:58:42 dan-desktop kernel: [   46.695115] Bluetooth: Core ver 2.11
Apr 29 22:58:42 dan-desktop kernel: [   46.696600] NET: Registered protocol family 31
Apr 29 22:58:42 dan-desktop kernel: [   46.696605] Bluetooth: HCI device and connection manager initialized
Apr 29 22:58:42 dan-desktop kernel: [   46.696610] Bluetooth: HCI socket layer initialized
Apr 29 22:58:42 dan-desktop kernel: [   46.768825] Bluetooth: L2CAP ver 2.9
Apr 29 22:58:42 dan-desktop kernel: [   46.768830] Bluetooth: L2CAP socket layer initialized
Apr 29 22:58:42 dan-desktop kernel: [   46.920899] Bluetooth: RFCOMM socket layer initialized
Apr 29 22:58:42 dan-desktop kernel: [   46.920920] Bluetooth: RFCOMM TTY layer initialized
Apr 29 22:58:42 dan-desktop kernel: [   46.920922] Bluetooth: RFCOMM ver 1.8
Apr 29 22:58:46 dan-desktop kernel: [   50.914313] NET: Registered protocol family 17
Apr 29 22:58:50 dan-desktop kernel: [   54.484938] NET: Registered protocol family 10
Apr 29 22:58:50 dan-desktop kernel: [   54.485898] lo: Disabled Privacy Extensions
Apr 29 22:59:01 dan-desktop kernel: [   65.080155] eth0: no IPv6 routers present
```

Really appreciate the help - if there is nothing else to try I will take a look at filing a bug.

There are one or two similar cases, ([https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/206845](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/206845) - suggests installing older drivers, something to try?)

Also, I'm guessing installing the ATI proprietary driver is a bad idea?

---

### Post by samborona on 2008-04-30
Thinking of giving the ATI drivers a go before I file a bug report - heard people saying this is a bad idea? 

I think I've run out of options really!

---

### Post by thumper_e on 2008-04-30
Hi,

Have you tried changing the virtual 1920 1200 in the screen section to 1440 900?

[HTML]https://help.ubuntu.com/community/RadeonDriver[/HTML]

helped when i tried to use the radeon driver, yet I now use the ati drivers with the 9600 card on hardy and everything (except a minor problem with a version of wine!!)  seems to work just fine.

[HTML]http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html[/HTML] -- is the new driver for your card

follow the instructions. Or try installing the driver with envy.

I hope this is of some help.



Ian

---

### Post by steefjeqv on 2008-05-01
Hi,

It may be just a small detail, but in the last xorg.conf mentioned the driver is "ati".

Try changing this to "radeon" (if you haven't tried this already).

I had a similar issue with a Sidux installation : no go using "ati", works perfectly with "radeon". 

Greetings,
Steven

---

### Post by samborona on 2008-05-01
Appreciate the replies.

Tried changing the "ati" reference to "radeon" and no luck unfortunately.

Also changed the size of the virtual screen but again no luck.

Think I might give the propietary drivers ago or post bug report now.

---

### Post by samborona on 2008-05-02
I get the following error when trying to install the ati.com driver:

```
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: unable to detect
Removing temporary directory: fglrx-install

```

I'm guessing this is because I'm using the newest version of X which is unsupported by the old driver? I think its a dependancy issue. 

Have posted a bug report here: [https://bugs.launchpad.net/ubuntu/+bug/225863](https://bugs.launchpad.net/ubuntu/+bug/225863)

If nothing comes of it I guess I will be forced to buy a new graphics card or give up on linux which would be a shame.

---

### Post by samborona on 2008-05-11
Sorry to bump the thread, but no joy at all on this so far.

Seems there are several similar bugs now:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/222544](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/222544)

Does this mean it will get fixed soon?

Just wondering if anybody had anymore suggestions as I have tried all sorts, and posted on a few linux/distro forums. 

Would it be worth posting a bug report on x.org? I really don't want to give up on this!

Could the proprietary driver be repackaged?

Thanks in advance!

---

### Post by Rocket2DMn on 2008-05-11
Posting on bug reports and/or creating your own is a good step.  You can help confirm already existing bugs.  It seems like that bug report has already been confirmed, triaged, and assigned a high priority which means a fix will probably be released in the next few months upstream, so you will have to download the updated driver manually or from another repository (debian or ubuntu intrepid ibex repos when they go online).  You can check back on that report or subscribe to changes in it so you will know when a fix has been released.  I wouldn't bank on the driver being released under the Hardy repos, except maybe through hardy-backports.

The proprietary driver will never be written and packaged to work for cards this old.  They drew the line at Radeon 9500 or so, which means support will never be implemented for older cards.

---

### Post by showgun22 on 2008-05-12
Ubuntu Hardy 
Is there a link to that bug?
I have the same type of problem Radeon 8500LE Acer x193w connected VGA
Afetr the boot up screen I get the floating box input not supported than no signal than a green screen and finally Ubuntu loads very nicely. At shut down I get the same annoying floating box Input not supported.

I did try I did install the Proprietary drivers as per the Howto seems to be working fine but still have the same problem....

According to Acer website the "Input not supported" is cause bu to hight resolution but my setting is exactly as per the specification. 1440 X 900 @ 60Hz.

It sure would be nice to have a link to this bug report they might need more info?

This seems to be happening to more than just a couple persons...

Thanks

---

### Post by frandy on 2008-05-13
Radeon 9000 Pro here

Same issue with installing ATI drivers

Saw this :

[http://www.phoronix.com/forums/showthread.php?p=29844](http://www.phoronix.com/forums/showthread.php?p=29844)

Says you need PURE etch install - :confused:

I'm off to find out what etch is and try it. Any help appreciated.

---

### Post by showgun22 on 2008-05-13
Etch is a version of Debian an other flavor of Linux which Ubuntu is base on.

---

### Post by steefjeqv on 2008-05-13
Hi,

As showgun22 says, Etch is the stable version of Debian.

Debian Etch = stable, which means that this version is frozen. No new versions of programs are uploaded to this version. Therefore this version is rocksolid stable. There are of course security updates.

Debian Lenny = testing. This version is used for further testing before these program versions are "ready" to be used in the next stable version.

Debian Sid = experimental. This version contains the newest version of all programs. Cutting edge, but may be somehow buggy. Ubuntu is partially based on this version (with a lot of work from Ubuntu to gain stability).

If you want the xorg version of Etch, you'll have to change your Ubuntu repositories to the Etch repos (temporarily). This may result in a working ATI card, but can give you other incompatability problems.

In terminal :

sudo gedit /etc/apt/sources.list

Put a comment(#) in front of all the ubuntu repos.

Now add the following repos to this file :

deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) etch main
deb [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib

Save the file.

Start up synaptic and remove xorg-core.

Then in terminal :

sudo apt-get update

Back to synaptic again to install the etch version of xorg. Don't forget to freeze this xorg version in synaptic.

Uncomment the ubuntu repos in the sources.list file and comment the Etch repos.

Ctr-alt-backspace should give you an Ubuntu OS with an Etch version of xorg.

Greetings,
Steven

---

### Post by Rocket2DMn on 2008-05-13
If you decide to use steefjeqv's method, PLEASE be sure to remove the Debian Etch repositories as soon as you get what you need, and make sure you run
```
sudo apt-get update
```
afterward to refresh your repositories.  DO NOT run upgrade or install anything else with these repositories enabled or you will put your system at risk for instability.
I just wanted to reinforce this for you as it is rather important.

---

