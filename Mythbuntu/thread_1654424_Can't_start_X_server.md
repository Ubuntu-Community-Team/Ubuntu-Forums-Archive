---
title: "Can't start X server"
date: 2010-12-28
forum: Mythbuntu
---

### Post by mark_b on 2010-12-28
I'm trying to install Mythbuntu on an old desktop, the specs of which are:

ABIT NF7-S motherboard
Athlon XP2600
Sapphire Radeon 8500LE graphics
1.5GB memory
Hauppauge Nova-T 500TD Freeview card

When I boot up the computer I am faced with just a terminal shell. I can enter commands ok and I can ssh in using my (Ubuntu) laptop.

When I type sudo startx I get

```
mark@minas-morgul:~$ sudo startx
[sudo] password for mark: 


X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux minas-morgul 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=1de41c7e-fd97-4286-b743-2c4d229d4a11 ro quiet splash
Build Date: 16 September 2010  05:39:22PM
xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec 28 15:22:38 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) No supported AMD display adapters were found
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
mark@minas-morgul:~$ 

```

When I check the log file I get
```
mark@minas-morgul:~$ more /var/log/Xorg.0.log
[   101.435] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   101.435] X Protocol Version 11, Revision 0
[   101.435] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[   101.435] Current Operating System: Linux minas-morgul 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686
[   101.435] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=1de41c7e-fd97-4286-b743-2c4d229d4a11 ro quiet splash
[   101.435] Build Date: 16 September 2010  05:39:22PM
[   101.435] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[   101.435] Current version of pixman: 0.18.4
[   101.435] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   101.435] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   101.436] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec 28 15:22:38 2010
[   101.436] (==) Using config file: "/etc/X11/xorg.conf"
[   101.436] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   101.437] (==) No Layout section.  Using the first Screen section.
[   101.437] (**) |-->Screen "Default Screen" (0)
[   101.437] (**) |   |-->Monitor "<default monitor>"
[   101.437] (==) No device specified for screen "Default Screen".
	Using the first device section listed.
[   101.437] (**) |   |-->Device "Default Device"
[   101.437] (==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
[   101.437] (==) Automatically adding devices
[   101.437] (==) Automatically enabling devices
[   101.437] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   101.437] 	Entry deleted from font path.
[   101.437] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   101.437] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   101.437] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   101.437] (II) Loader magic: 0x81f8e00
[   101.437] (II) Module ABI versions:
[   101.437] 	X.Org ANSI C Emulation: 0.4
[   101.437] 	X.Org Video Driver: 8.0
[   101.437] 	X.Org XInput driver : 11.0
[   101.437] 	X.Org Server Extension : 4.0
[   101.438] (--) PCI:*(0:2:0:0) 1002:514c:1681:0004 rev 0, Mem @ 0xd0000000/268435456, 0xe1000000/65536, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072
[   101.439] (II) Open ACPI successful (/var/run/acpid.socket)
[   101.439] (II) LoadModule: "extmod"
[   101.440] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   101.440] (II) Module extmod: vendor="X.Org Foundation"
[   101.440] 	compiled for 1.9.0, module version = 1.0.0
[   101.440] 	Module class: X.Org Server Extension
[   101.440] 	ABI class: X.Org Server Extension, version 4.0
[   101.440] (II) Loading extension MIT-SCREEN-SAVER
[   101.440] (II) Loading extension XFree86-VidModeExtension
[   101.440] (II) Loading extension XFree86-DGA
[   101.440] (II) Loading extension DPMS
[   101.440] (II) Loading extension XVideo
[   101.440] (II) Loading extension XVideo-MotionCompensation
[   101.440] (II) Loading extension X-Resource
[   101.441] (II) LoadModule: "dbe"
[   101.441] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   101.441] (II) Module dbe: vendor="X.Org Foundation"
[   101.441] 	compiled for 1.9.0, module version = 1.0.0
[   101.441] 	Module class: X.Org Server Extension
[   101.441] 	ABI class: X.Org Server Extension, version 4.0
[   101.441] (II) Loading extension DOUBLE-BUFFER
[   101.441] (II) LoadModule: "glx"
[   101.441] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[   101.442] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[   101.442] 	compiled for 7.6.0, module version = 1.0.0
[   101.442] (II) Loading extension GLX
[   101.442] (II) LoadModule: "record"
[   101.443] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   101.443] (II) Module record: vendor="X.Org Foundation"
[   101.443] 	compiled for 1.9.0, module version = 1.13.0
[   101.443] 	Module class: X.Org Server Extension
[   101.443] 	ABI class: X.Org Server Extension, version 4.0
[   101.443] (II) Loading extension RECORD
[   101.443] (II) LoadModule: "dri"
[   101.444] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   101.444] (II) Module dri: vendor="X.Org Foundation"
[   101.444] 	compiled for 1.9.0, module version = 1.0.0
[   101.444] 	ABI class: X.Org Server Extension, version 4.0
[   101.444] (II) Loading extension XFree86-DRI
[   101.444] (II) LoadModule: "dri2"
[   101.445] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   101.445] (II) Module dri2: vendor="X.Org Foundation"
[   101.445] 	compiled for 1.9.0, module version = 1.2.0
[   101.445] 	ABI class: X.Org Server Extension, version 4.0
[   101.445] (II) Loading extension DRI2
[   101.445] (II) LoadModule: "fglrx"
[   101.445] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[   101.470] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[   101.470] 	compiled for 1.4.99.906, module version = 8.78.30
[   101.470] 	Module class: X.Org Video Driver
[   101.471] (II) Loading sub module "fglrxdrm"
[   101.471] (II) LoadModule: "fglrxdrm"
[   101.471] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[   101.471] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[   101.471] 	compiled for 1.8.99.905, module version = 8.78.30
[   101.471] (II) ATI Proprietary Linux Driver Version Identifier:8.78.30
[   101.471] (II) ATI Proprietary Linux Driver Release Identifier: 8.78.3                               
[   101.471] (II) ATI Proprietary Linux Driver Build Date: Sep 20 2010 21:30:49
[   101.471] (--) using VT number 8

[   101.479] (WW) Falling back to old probe method for fglrx
[   101.479] (EE) No supported AMD display adapters were found
[   101.479] (EE) No devices detected.
[   101.479] 
Fatal server error:
[   101.479] no screens found
[   101.479] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[   101.479] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   101.479] 
mark@minas-morgul:~$ 

```

Can someone please help me get this working. The live CD boots to the desktop ok. I'm told that the Radeon 8500 is supported under Linux (although it is the earliest one).

the card reported by Mythbuntu is:
```
mark@minas-morgul:~$ lspci | grep VGA
02:00.0 VGA compatible controller: ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]
mark@minas-morgul:~$ 

```

---

