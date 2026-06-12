---
title: "Video card - need a simple explanation (Radeon HD3300)"
date: 2011-11-10
forum: Multimedia Software
---

### Post by zcacogp on 2011-11-10
Hello, 

I've been using Ubuntu for a number of years, and my requirements are pretty simple; word processing, surfing the internet, watching some on-line films, nothing much more. I feel that I have never managed to configure the display/video card system on my machine properly, but have always managed to live with whatever I had set up. 

I'm now trying to get to grips with this, and struggling. The computer I use most is a 64-bit AMD desktop, with an on-board ATI Radeon HD3300 graphics card. I've just tried the instructions here: 

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

(the manual install method), and my machine will now crash out of KDE if I try to open a window. (It manages to run konsole, but trying Firefox or Dolphin returns me to the login screen.) I should add that before trying the method in the link above the machine ran OK; opening windows or the sliding panel at the top of the screen was slow, and produced some interesting (temporary) screen effects, but it worked. 

I am struggling to understand quite a lot of the terminology here; Nvidia and ATI, proprietary and fglrx, and how the xorg.conf file fits into the equation. 

So, firstly does anyone have any suggestions of good things to read that will explain what is going on in simple terms (for a beginner like me), and secondly, what does anyone suggest in terms of configuration for a Radeon HD3300 card like mine? I'm running Ubuntu 11.10 Oneiric, with KDE. 

There is a thread here: 

[http://ubuntuforums.org/showthread.php?t=1203437](http://ubuntuforums.org/showthread.php?t=1203437)

.. from a guy with the same video card, and he uses the same driver as the one I tried, but seems to install it differently and I don't understand the differences. The thread is also quite old - he talks about 9.04 - and I am reluctant to try something that may break my computer even more. 

All suggestions - both of things to read, and how to make my machine work, are welcomed - thanks. 


Oli.

---

### Post by zcacogp on 2011-11-10
A bit more information - my xorg.conf file now looks like this: 

```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

```


Oli.

---

### Post by zcacogp on 2011-11-10
OK, I think I am making progress. I have used the method on this page: 

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

... (the one entitled "Problem: Need to fully remove -fglrx and reinstall -ati from scratch") and now have the machine back to where it was when I started. It seems that I can have the proprietary driver installed, which allows nicer desktop effects (fading windows, sliding windows and so on) but which makes everything run a little slower and gives some interesting artefacts when you first open a window, or have the default standard driver (I presume this is the open-source one) which makes everything run more smoothly but doesn't permit the snazzy effects. You can't have both. 

(I am also getting the impression that *buntus run much better on nvidia cards than on ATI ones. Can I buy an nvidia card to plug into my AMD motherboard or is such a thing impossible? I'd look for something second-hand, old and cheap, as long as it works better than the built-in thing.) 


Oli.

---

### Post by zcacogp on 2011-11-13
> **zcacogp said:**
> It seems that I can have the proprietary driver installed, which allows nicer desktop effects (fading windows, sliding windows and so on) but which makes everything run a little slower and gives some interesting artefacts when you first open a window, or have the default standard driver (I presume this is the open-source one) which makes everything run more smoothly but doesn't permit the snazzy effects. You can't have both. Hello, 

Further to this message (above), I am carrying on with the default standard driver for my Radeon HD3300 graphics card, but it still isn't great; the graphics performance is generally slow, and the screen shows interesting artefacts (when you open a window, or slide out a panel, you get an outline with some black-and-white lines in it at first, which re-draws with the window content within a couple of fractions of a second.) It also won't run any window effects at all, and gives you a desktop alert message if you try to turn any of them on. 

Is anyone else running this video card and, if so, can they recommend a better driver for it? I have used earlier versions of Ubuntu on this and it wasn't as much of a problem as it is now (it has never been great, but took a turn for the worst with the latest version - it liked Gnome more than Unity or KDE, it seems.) 

Thanks for any help. 


Oli.

---

### Post by 4Orbs on 2011-11-13
Look in the System menu for "Additional Drivers" and see if Kubuntu has a recommended driver for your graphics card (it's really a chip on the motherboard, in your case). If one is available, click on the "Activate" button and wait the few minutes for it to download and install automatically; then reboot as instructed. You'll then have the proprietary driver from the Kubuntu repository, which is a few months behind the driver from the ati website... but should work nicely anyway. Best thing is that you don't need to install it manually, and it updates itself automatically as you update your Kubuntu installation.

---

### Post by alphacrucis2 on 2011-11-13
"Additional drivers" is the easiest way to go. For Oneiric that will get you Catalyst 11.8. Don't whatever you do, try to install catalyst 11.9. It's a dud. On the other hand the latest Catalyst 11.10 is fine and improved versus 11.8.

---

### Post by inobe on 2011-11-13
i would ask before following a guide of any kind, it's why our forums are here.

those guides don't work for everyone and they are beyond the recommended suggestions.

i also suggest using **"additional drivers"** prior to more advanced methods.

using the advanced methods first, and not knowing how to reverse what was done, then running **"additional drivers"**, you may experience this \/

> I am carrying on with the default standard driver for my Radeon HD3300 graphics card, but it still isn't great; the graphics performance **is generally slow**

it may be broken by user, we may never know, no way to tell, it happens often.

---

### Post by MoreOrLess on 2011-11-13
Using the driver provided by Ubuntu is safest, but if you must install the latest Catalyst, use this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

---

### Post by zcacogp on 2011-11-14
Hello, 

Many thanks for your help. 

In turn: 

4Orbs and alphacrucis2 - Additional Drivers was what I had installed, and while it allowed some screen effects it didn't allow all of them and produced some screen artefacts, and caused the computer to lock up for up to 20 seconds at a time, often a couple of times an hour. Disabling this removed the lock-ups and some of the screen artefacts but also removed all the animations. 

inobe - I think you may be onto something there; I had tried to install a driver from the AMD/ATI website, without purging  beforehand, and this caused a lot of problems; the system wouldn't boot at all. I had a thread on it elsewhere and eventually managed to get it working again, with the open-source drivers. Which is where I was before I took MoreOrLess's advice and ... 

... tried installing the latest version of the drivers, using the instructions from the Installing Oneiric link MoreOrLess gave me. Everything is now installed, but it won't boot into the windows manager; it gets stuck at "Checking Battery State [OK]" and won't go any further (but does try this several times over). I can get into a TTY terminal and hence log into a command prompt, so all is not lost. (I guess I can, from there, purge all parts of the driver installation and go back to the open source driver.)

However it seems that this problem (hanging at "Checking battery state") is not uncommonly associated with updating video cards and I'm googling for a solution ... if anyone happens to know what it is then let me know - thanks! 


Oli.

---

### Post by MoreOrLess on 2011-11-14
Hanging at that point means X is trying to start, but can't. Look in /var/log/Xorg.0.log to find out why (or run the commands in the removing fglrx section of that guide and that will have you running again).

---

### Post by zcacogp on 2011-11-17
MoreOrLess, 

Thanks. I tried the trick (mentioned in the article) of removing xorg.conf altogether, without any luck. I also tried making a minimal xorg.conf, with the same result (although it was such a minimal file it probably counted for nothing.) I also tried removing the fglrx installation and re-doing it, and it hangs in the same place again. 

The error log you mention (/var/log/Xorg.0.log) looks like this (sorry, it's a long file.) 

```

[    45.379] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    45.379] X Protocol Version 11, Revision 0
[    45.379] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    45.379] Current Operating System: Linux desktop 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64
[    45.379] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=dd3dc8ab-cf01-46af-94c8-87ba002dc575 ro quiet splash nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap vt.handoff=7
[    45.379] Build Date: 19 October 2011  05:21:26AM
[    45.379] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[    45.379] Current version of pixman: 0.22.2
[    45.379] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    45.379] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    45.379] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov 17 15:08:48 2011
[    45.379] (==) Using config file: "/etc/X11/xorg.conf"
[    45.379] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    45.380] (==) No Layout section.  Using the first Screen section.
[    45.380] (==) No screen section available. Using defaults.
[    45.380] (**) |-->Screen "Default Screen Section" (0)
[    45.380] (**) |   |-->Monitor "<default monitor>"
[    45.380] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[    45.380] (**) |   |-->Device "ATI radeon HD 3300"
[    45.380] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    45.380] (==) Automatically adding devices
[    45.380] (==) Automatically enabling devices
[    45.380] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    45.380] 	Entry deleted from font path.
[    45.380] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    45.380] 	Entry deleted from font path.
[    45.380] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    45.380] 	Entry deleted from font path.
[    45.380] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    45.380] 	Entry deleted from font path.
[    45.380] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    45.380] 	Entry deleted from font path.
[    45.380] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    45.380] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    45.380] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    45.380] (II) Loader magic: 0x7e0220
[    45.380] (II) Module ABI versions:
[    45.380] 	X.Org ANSI C Emulation: 0.4
[    45.380] 	X.Org Video Driver: 10.0
[    45.380] 	X.Org XInput driver : 12.3
[    45.380] 	X.Org Server Extension : 5.0
[    45.381] (--) PCI:*(0:1:5:0) 1002:9614:1458:d000 rev 0, Mem @ 0xd0000000/268435456, 0xfdfe0000/65536, 0xfde00000/1048576, I/O @ 0x0000ee00/256
[    45.381] (II) Open ACPI successful (/var/run/acpid.socket)
[    45.381] (II) LoadModule: "extmod"
[    45.381] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    45.381] (II) Module extmod: vendor="X.Org Foundation"
[    45.381] 	compiled for 1.10.4, module version = 1.0.0
[    45.381] 	Module class: X.Org Server Extension
[    45.381] 	ABI class: X.Org Server Extension, version 5.0
[    45.381] (II) Loading extension MIT-SCREEN-SAVER
[    45.382] (II) Loading extension XFree86-VidModeExtension
[    45.382] (II) Loading extension XFree86-DGA
[    45.382] (II) Loading extension DPMS
[    45.382] (II) Loading extension XVideo
[    45.382] (II) Loading extension XVideo-MotionCompensation
[    45.382] (II) Loading extension X-Resource
[    45.382] (II) LoadModule: "dbe"
[    45.382] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    45.382] (II) Module dbe: vendor="X.Org Foundation"
[    45.382] 	compiled for 1.10.4, module version = 1.0.0
[    45.382] 	Module class: X.Org Server Extension
[    45.382] 	ABI class: X.Org Server Extension, version 5.0
[    45.382] (II) Loading extension DOUBLE-BUFFER
[    45.382] (II) LoadModule: "glx"
[    45.382] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[    45.382] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    45.382] 	compiled for 6.9.0, module version = 1.0.0
[    45.383] (II) Loading extension GLX
[    45.383] (II) LoadModule: "record"
[    45.383] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    45.383] (II) Module record: vendor="X.Org Foundation"
[    45.383] 	compiled for 1.10.4, module version = 1.13.0
[    45.383] 	Module class: X.Org Server Extension
[    45.383] 	ABI class: X.Org Server Extension, version 5.0
[    45.383] (II) Loading extension RECORD
[    45.383] (II) LoadModule: "dri"
[    45.384] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    45.384] (II) Module dri: vendor="X.Org Foundation"
[    45.384] 	compiled for 1.10.4, module version = 1.0.0
[    45.384] 	ABI class: X.Org Server Extension, version 5.0
[    45.384] (II) Loading extension XFree86-DRI
[    45.384] (II) LoadModule: "dri2"
[    45.384] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    45.384] (II) Module dri2: vendor="X.Org Foundation"
[    45.384] 	compiled for 1.10.4, module version = 1.2.0
[    45.384] 	ABI class: X.Org Server Extension, version 5.0
[    45.384] (II) Loading extension DRI2
[    45.384] (II) LoadModule: "fglrx"
[    45.384] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    45.404] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    45.404] 	compiled for 1.4.99.906, module version = 8.91.4
[    45.404] 	Module class: X.Org Video Driver
[    45.404] (II) Loading sub module "fglrxdrm"
[    45.404] (II) LoadModule: "fglrxdrm"
[    45.404] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    45.404] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    45.404] 	compiled for 1.4.99.906, module version = 8.91.4
[    45.404] (II) ATI Proprietary Linux Driver Version Identifier:8.91.4
[    45.404] (II) ATI Proprietary Linux Driver Release Identifier: 8.911                                
[    45.404] (II) ATI Proprietary Linux Driver Build Date: Oct 25 2011 21:24:13
[    45.404] (++) using VT number 8

[    45.674] (WW) Falling back to old probe method for fglrx
[    45.682] (II) Loading PCS database from /etc/ati/amdpcsdb
[    45.683] (--) Assigning device section with no busID to primary device
[    45.683] (--) Chipset Supported AMD Graphics Processor (0x9614) found
[    45.683] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[    45.683] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[    45.683] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
[    45.683] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[    45.683] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[    45.683] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
[    45.683] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[    45.683] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[    45.683] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
[    45.683] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[    45.683] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[    45.683] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[    45.683] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
[    45.683] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:5:1) found
[    45.683] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    45.683] (II) AMD Video driver is signed
[    45.683] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    45.683] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    45.683] (II) fglrx(0): pEnt->device->identifier=0xb9c360
[    45.683] (II) fglrx(0): === [xdl_xs110_atiddxPreInit] === begin
[    45.683] (II) Loading sub module "vgahw"
[    45.683] (II) LoadModule: "vgahw"
[    45.684] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    45.684] (II) Module vgahw: vendor="X.Org Foundation"
[    45.684] 	compiled for 1.10.4, module version = 0.1.0
[    45.684] 	ABI class: X.Org Video Driver, version 10.0
[    45.684] (II) fglrx(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    45.684] (==) fglrx(0): Depth 24, (==) framebuffer bpp 32
[    45.684] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    45.684] (==) fglrx(0): Default visual is TrueColor
[    45.684] (==) fglrx(0): RGB weight 888
[    45.684] (II) fglrx(0): Using 8 bits per RGB 
[    45.684] (==) fglrx(0): Buffer Tiling is ON
[    45.684] (II) Loading sub module "fglrxdrm"
[    45.684] (II) LoadModule: "fglrxdrm"
[    45.684] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    45.684] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    45.684] 	compiled for 1.4.99.906, module version = 8.91.4
[    45.686] ukiDynamicMajor: failed to open /proc/ati/major
[    45.686] ukiDynamicMajor: failed to open /proc/ati/major
[    45.686] (==) fglrx(0): NoAccel = NO
[    45.686] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    45.686] (--) fglrx(0): Chipset: "ATI Radeon HD 3300 Graphics" (Chipset = 0x9614)
[    45.686] (--) fglrx(0): (PciSubVendor = 0x1458, PciSubDevice = 0xd000)
[    45.686] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    45.686] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    45.686] (--) fglrx(0): MMIO registers at 0xfdfe0000
[    45.686] (--) fglrx(0): I/O port at 0x0000ee00
[    45.686] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    45.691] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    45.691] (II) Loading sub module "vbe"
[    45.691] (II) LoadModule: "vbe"
[    45.692] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    45.692] (II) Module vbe: vendor="X.Org Foundation"
[    45.692] 	compiled for 1.10.4, module version = 1.1.0
[    45.692] 	ABI class: X.Org Video Driver, version 10.0
[    45.692] (II) fglrx(0): VESA BIOS detected
[    45.692] (II) fglrx(0): VESA VBE Version 3.0
[    45.692] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    45.692] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    45.692] (II) fglrx(0): VESA VBE OEM Software Rev: 10.94
[    45.692] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    45.692] (II) fglrx(0): VESA VBE OEM Product: RS780
[    45.692] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    45.701] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    45.701] (II) fglrx(0): UMA/SP interleave mode is enabled in the BIOS
[    45.701] (--) fglrx(0): Video RAM: 393216 kByte, Type: DDR3
[    45.701] (II) fglrx(0): PCIE card detected
[    45.701] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    45.701] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    45.701] (WW) fglrx(0): Hasn't establisted DRM connection
[    45.701] (II) fglrx(0): [FB] MC range(MCFBBase = 0xc0000000, MCFBSize = 0x18000000)
[    45.701] (WW) fglrx(0): No DRM connection for driver fglrx.
[    45.701] (II) fglrx(0): RandR 1.2 support is enabled!
[    45.701] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    45.701] (==) fglrx(0): Center Mode is disabled 
[    45.701] (II) Loading sub module "fb"
[    45.701] (II) LoadModule: "fb"
[    45.701] (II) Loading /usr/lib/xorg/modules/libfb.so
[    45.702] (II) Module fb: vendor="X.Org Foundation"
[    45.702] 	compiled for 1.10.4, module version = 1.0.0
[    45.702] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    45.702] (II) Loading sub module "ddc"
[    45.702] (II) LoadModule: "ddc"
[    45.702] (II) Module "ddc" already built-in
[    46.083] (II) fglrx(0): Output DFP1 has no monitor section
[    46.083] (II) fglrx(0): Output CRT1 has no monitor section
[    46.083] (II) Loading sub module "ddc"
[    46.083] (II) LoadModule: "ddc"
[    46.083] (II) Module "ddc" already built-in
[    46.083] (II) fglrx(0): Connected Display0: CRT1
[    46.083] (II) fglrx(0): Display0 EDID data ---------------------------
[    46.083] (II) fglrx(0): Manufacturer: HIT  Model: 60ff  Serial#: 16843009
[    46.083] (II) fglrx(0): Year: 2007  Week: 49
[    46.083] (II) fglrx(0): EDID Version: 1.3
[    46.083] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    46.083] (II) fglrx(0): Sync:  Separate
[    46.084] (II) fglrx(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    46.084] (II) fglrx(0): Gamma: 2.20
[    46.084] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    46.084] (II) fglrx(0): First detailed timing is preferred mode
[    46.084] (II) fglrx(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
[    46.084] (II) fglrx(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
[    46.084] (II) fglrx(0): Supported established timings:
[    46.084] (II) fglrx(0): 720x400@70Hz
[    46.084] (II) fglrx(0): 640x480@60Hz
[    46.084] (II) fglrx(0): 640x480@72Hz
[    46.084] (II) fglrx(0): 640x480@75Hz
[    46.084] (II) fglrx(0): 800x600@60Hz
[    46.084] (II) fglrx(0): 800x600@72Hz
[    46.084] (II) fglrx(0): 800x600@75Hz
[    46.084] (II) fglrx(0): 1024x768@60Hz
[    46.084] (II) fglrx(0): 1024x768@70Hz
[    46.084] (II) fglrx(0): 1024x768@75Hz
[    46.084] (II) fglrx(0): 1280x1024@75Hz
[    46.084] (II) fglrx(0): Manufacturer's mask: 0
[    46.084] (II) fglrx(0): Supported standard timings:
[    46.084] (II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    46.084] (II) fglrx(0): #1: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    46.084] (II) fglrx(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    46.084] (II) fglrx(0): #3: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    46.084] (II) fglrx(0): Supported detailed timing:
[    46.084] (II) fglrx(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    46.084] (II) fglrx(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    46.084] (II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    46.084] (II) fglrx(0): Monitor name: N220W D-sub
[    46.084] (II) fglrx(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 155 MHz
[    46.084] (II) fglrx(0): Serial No: 0WAP0B7B00935
[    46.084] (II) fglrx(0): EDID (in hex):
[    46.084] (II) fglrx(0): 	00ffffffffffff002134ff6001010101
[    46.084] (II) fglrx(0): 	31110103082f1e78ead515a455499a27
[    46.084] (II) fglrx(0): 	145054adcf008180b3009500950f0101
[    46.084] (II) fglrx(0): 	01010101010121399030621a274068b0
[    46.084] (II) fglrx(0): 	3600da281100001c000000fc004e3232
[    46.084] (II) fglrx(0): 	305720442d7375620a20000000fd0038
[    46.084] (II) fglrx(0): 	4c1f500f000a202020202020000000ff
[    46.084] (II) fglrx(0): 	003057415030423742303039333500bb
[    46.084] (II) fglrx(0): End of Display0 EDID data --------------------
[    46.105] (II) fglrx(0): EDID for output DFP1
[    46.105] (II) fglrx(0): EDID for output CRT1
[    46.105] (II) fglrx(0): Manufacturer: HIT  Model: 60ff  Serial#: 16843009
[    46.105] (II) fglrx(0): Year: 2007  Week: 49
[    46.105] (II) fglrx(0): EDID Version: 1.3
[    46.105] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    46.105] (II) fglrx(0): Sync:  Separate
[    46.105] (II) fglrx(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    46.105] (II) fglrx(0): Gamma: 2.20
[    46.105] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    46.105] (II) fglrx(0): First detailed timing is preferred mode
[    46.105] (II) fglrx(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
[    46.105] (II) fglrx(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
[    46.105] (II) fglrx(0): Supported established timings:
[    46.105] (II) fglrx(0): 720x400@70Hz
[    46.105] (II) fglrx(0): 640x480@60Hz
[    46.105] (II) fglrx(0): 640x480@72Hz
[    46.105] (II) fglrx(0): 640x480@75Hz
[    46.105] (II) fglrx(0): 800x600@60Hz
[    46.105] (II) fglrx(0): 800x600@72Hz
[    46.105] (II) fglrx(0): 800x600@75Hz
[    46.105] (II) fglrx(0): 1024x768@60Hz
[    46.105] (II) fglrx(0): 1024x768@70Hz
[    46.105] (II) fglrx(0): 1024x768@75Hz
[    46.105] (II) fglrx(0): 1280x1024@75Hz
[    46.105] (II) fglrx(0): Manufacturer's mask: 0
[    46.105] (II) fglrx(0): Supported standard timings:
[    46.105] (II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    46.105] (II) fglrx(0): #1: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    46.105] (II) fglrx(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    46.105] (II) fglrx(0): #3: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    46.105] (II) fglrx(0): Supported detailed timing:
[    46.105] (II) fglrx(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    46.105] (II) fglrx(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    46.105] (II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    46.105] (II) fglrx(0): Monitor name: N220W D-sub
[    46.105] (II) fglrx(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 155 MHz
[    46.105] (II) fglrx(0): Serial No: 0WAP0B7B00935
[    46.105] (II) fglrx(0): EDID (in hex):
[    46.105] (II) fglrx(0): 	00ffffffffffff002134ff6001010101
[    46.105] (II) fglrx(0): 	31110103082f1e78ead515a455499a27
[    46.105] (II) fglrx(0): 	145054adcf008180b3009500950f0101
[    46.105] (II) fglrx(0): 	01010101010121399030621a274068b0
[    46.105] (II) fglrx(0): 	3600da281100001c000000fc004e3232
[    46.105] (II) fglrx(0): 	305720442d7375620a20000000fd0038
[    46.105] (II) fglrx(0): 	4c1f500f000a202020202020000000ff
[    46.105] (II) fglrx(0): 	003057415030423742303039333500bb
[    46.105] (II) fglrx(0): Printing probed modes for output CRT1
[    46.105] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync (65.3 kHz)
[    46.105] (II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync -vsync (65.3 kHz)
[    46.105] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 -hsync -vsync (80.0 kHz)
[    46.105] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 -hsync -vsync (64.0 kHz)
[    46.105] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync (55.9 kHz)
[    46.105] (II) fglrx(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 +hsync -vsync (75.2 kHz)
[    46.105] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 -hsync -vsync (60.0 kHz)
[    46.105] (II) fglrx(0): Modeline "1280x800"x75.0  107.21  1280 1360 1496 1712  800 801 804 835 +hsync -vsync (62.6 kHz)
[    46.105] (II) fglrx(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 +hsync -vsync (49.7 kHz)
[    46.105] (II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 -hsync -vsync (67.5 kHz)
[    46.105] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync -vsync (53.7 kHz)
[    46.105] (II) fglrx(0): Modeline "1280x768"x75.0  102.25  1280 1360 1488 1696  768 771 778 805 +hsync -vsync (60.3 kHz)
[    46.105] (II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
[    46.105] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 -hsync -vsync (45.0 kHz)
[    46.105] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[    46.105] (II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
[    46.105] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
[    46.105] (II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 -hsync -vsync (48.1 kHz)
[    46.105] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 -hsync -vsync (46.9 kHz)
[    46.105] (II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync -vsync (43.8 kHz)
[    46.106] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 -hsync -vsync (37.9 kHz)
[    46.106] (II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync -vsync (29.8 kHz)
[    46.106] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
[    46.106] (II) fglrx(0): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 +hsync +vsync (37.9 kHz)
[    46.106] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 +hsync +vsync (31.5 kHz)
[    46.106] (II) fglrx(0): Output DFP1 disconnected
[    46.106] (II) fglrx(0): Output CRT1 connected
[    46.106] (II) fglrx(0): Using exact sizes for initial modes
[    46.106] (II) fglrx(0): Output CRT1 using initial mode 1680x1050
[    46.106] (II) fglrx(0): DPI set to (96, 96)
[    46.106] (II) fglrx(0): Adapter ATI Radeon HD 3300 Graphics has 2 configurable heads and 1 displays connected.
[    46.106] (==) fglrx(0):  PseudoColor visuals disabled
[    46.106] (II) Loading sub module "ramdac"
[    46.106] (II) LoadModule: "ramdac"
[    46.106] (II) Module "ramdac" already built-in
[    46.106] (==) fglrx(0): NoDRI = NO
[    46.106] (==) fglrx(0): Capabilities: 0x00000000
[    46.106] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    46.106] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    46.106] (==) fglrx(0): UseFastTLS=0
[    46.106] (==) fglrx(0): BlockSignalsOnLock=1
[    46.106] (--) Depth 24 pixmap format is 32 bpp
[    46.106] (EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
[    46.106] (WW) fglrx(0): ***********************************************************
[    46.106] (WW) fglrx(0): * DRI initialization failed                               *
[    46.106] (WW) fglrx(0): * kernel module (fglrx.ko) may be missing or incompatible *
[    46.106] (WW) fglrx(0): * 2D and 3D acceleration disabled                         *
[    46.106] (WW) fglrx(0): ***********************************************************
[    46.106] (II) fglrx(0): FBADPhys: 0xc4900000 FBMappedSize: 0x10000000
[    46.106] (II) fglrx(0): Reserved 0x04900000 bytes of sideport memory for power saving
[    46.106] (EE) fglrx(0): Failed to map FB memory
[    46.106] (II) fglrx(0): === [xdl_xs110_atiddxScreenInit] === end
[    46.106] 
Fatal server error:
[    46.106] AddScreen/ScreenInit failed for driver 0
[    46.106] 
[    46.106] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    46.106] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    46.106] 
[    46.404] (EE) fglrx(0): firegl_SetSuspendResumeState FAILED -9.
[    47.209]  ddxSigGiveUp: Closing log

```

I'm struggling to understand what I am looking at here, but this line seems relevant: 

```
Fatal server error:
[    46.106] AddScreen/ScreenInit failed for driver 0
```

Is this so? Any ideas on how to proceed from here? (I'll do some googling, but if you know the answer then please do let me know!)

Thanks, again, for your help. 


Oli.

---

### Post by MoreOrLess on 2011-11-17
> kernel module (fglrx.ko) may be missing or incompatibleThat's the issue. Check is the module exists:
```
sudo modinfo fglrx
```
If it spits out info, then try and load it manually (Ctrl+Alt+F2)
```
sudo service lightdm stop
sudo modprobe -v fglrx
```

---

### Post by zcacogp on 2011-11-17
MoreOrLess, 

Thanks. 

$ sudo modinfo fglrx

... spat out a LOT of info. 

The next command was for lightdm, but I'm running KDE so changed it to kdm. This made it: 

$ sudo service kdm stop 

(I presume this was correct?) It told me "kdm stop/waiting".

The last one: 

$ sudo modprobe -v fglrx

.. told me that "WARNING: Not loading blacklisted module fglrx
FATAL: Module fglrx not found."

So it looks like it is looking for fglrx. (Here I'm perplexed; I thought that fglrx was the open-source driver for ATI cards, and I was trying to replace the open-source one with the proprietry one. Have I mis-understood something?) 

Oh - I'm not sure whether this is relevant (I think it isn't), but I am running the above commands from an SSH session on another machine; I have the broken machine in front of me (showing "* Checking battery state ... [OK]") but have SSH'ed to it from my laptop and it allows me to copy and paste commands, rather than using a TTY terminal which doesn't. Does this change things? 

Thanks again for your help. 


Oli.

---

### Post by MoreOrLess on 2011-11-17
Huh? fglrx is the module for the proprietary fglrx/Catalyst driver. I'm not sure why you have it blacklisted (look at files in /etc/modprobe.d).

---

### Post by zcacogp on 2011-11-17
In /etc/modprobe.d I do have a file "fglrx.conf" listed ... is this relevant? 
(The full list of everything in there is thus: 

alsa-base.conf              blacklist-local.conf
blacklist-ath_pci.conf      blacklist-modem.conf
blacklist.conf              blacklist-oss.conf
blacklist-cups-usblp.conf   blacklist-rare-network.conf
blacklist-firewire.conf     blacklist-watchdog.conf
blacklist-framebuffer.conf  fglrx.conf

)

I'll try renaming fglrx.conf and see if it makes any difference ... 


Oli.

---

### Post by zcacogp on 2011-11-17
... opening the file fglrx.conf gives the contents as being like this: 

```
# This file was installed by fglrx
# Do not edit this file manually

blacklist radeon
alias fglrx fglrx
alias radeon off
alias lbm-radeon off
```

Any help? 


Oli.

---

### Post by zcacogp on 2011-11-17
... and another update. Renaming /etc/modprobe.d/fglrx.conf to fglrx.conf.old has made no difference - it still hangs at the same point. 


Oli.

---

### Post by zcacogp on 2011-11-17
... and another update. I discovered that there was a file in that directory called "blacklist-local.conf", which has the line "blacklist fglrx" in it. I don't know how this got there, or why it was there, but I #-ed it out and re-started. And it booted! 

Typing; 

$ fglrxinfo

in gives this: 

```
ogp@desktop:/etc/modprobe.d$ fglrxinfo
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 3300 Graphics
OpenGL version string: 3.3.11251 Compatibility Profile Context

```

Does this mean I am using the latest driver? 

I have also read about the fgl_glxgears test. I've never run this before, but if I do this then I get the animated gears-in-a-box picture (new to me, but I expect you have seen it dizens of times before), and a report of a framerate of between 175 and 200fps. Interestingly, if I move the mouse between windows (sloppy focus), I can make this drop dramatically - down to 1.400fps (yes, 7 frames in 5 seconds) - every time you change the focus between windows it seems to freeze the computer for a short while. Is this normal? 

So, it's working - very many thanks for your help MoreOrLess. I guess what I need to find out now is whether this has made the computer usable. (The screen effects were making it feel very ropey; I have just used a client's 4-year-old Dell with MS Vista on it, and the screen effects on that were silky-smooth and utterly effortless - making me wonder whether I should be going back to M$; hopefully this new screen driver will change things for the better!) 

Thanks again MoreOrLess. I'll mark this thread as solved. 


Oli.

---

### Post by zcacogp on 2011-12-09
I know this thread is 'Solved', but there is perhaps a small update. 

The reason I was fussing around with drivers for my machine was because it ran badly. Someone suggested that NVidia graphics work much better on Ubuntu and ATI ones, and I have just bought a Gigabyte GeForce GV-NX66256DP card to replace the ATI Radeon HD3300 on-board graphics. 

The numbers mean nothing to me, but the machine has been transformed by the new card; it's snappier, the screen is much crisper, no nasty screen artefacts, window animations are smooth and even and it seems to have lowered the CPU effort as well. To say it is an improvement is an understatement - I just wish I had spent that £5 three years ago! 

Thanks again for your help. 


Oli.

---

### Post by aisdyg87 on 2012-04-25
> **zcacogp said:**
> ... and another update. I discovered that there was a file in that directory called "blacklist-local.conf", which has the line "blacklist fglrx" in it. I don't know how this got there, or why it was there, but I #-ed it out and re-started. And it booted! 

Typing; 

$ fglrxinfo

in gives this: 

```
ogp@desktop:/etc/modprobe.d$ fglrxinfo
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 3300 Graphics
OpenGL version string: 3.3.11251 Compatibility Profile Context

```Does this mean I am using the latest driver? 

I have also read about the fgl_glxgears test. I've never run this before, but if I do this then I get the animated gears-in-a-box picture (new to me, but I expect you have seen it dizens of times before), and a report of a framerate of between 175 and 200fps. Interestingly, if I move the mouse between windows (sloppy focus), I can make this drop dramatically - down to 1.400fps (yes, 7 frames in 5 seconds) - every time you change the focus between windows it seems to freeze the computer for a short while. Is this normal? 

So, it's working - very many thanks for your help MoreOrLess. I guess what I need to find out now is whether this has made the computer usable. (The screen effects were making it feel very ropey; I have just used a client's 4-year-old Dell with MS Vista on it, and the screen effects on that were silky-smooth and utterly effortless - making me wonder whether I should be going back to M$; hopefully this new screen driver will change things for the better!) 

Thanks again MoreOrLess. I'll mark this thread as solved. 


Oli.


Yeap. Looked into /var/log/Xorg.0.log for messages and warnings and found that fglrx was indeed blacklisted.

Removed the blacklisted line in the file your suggested and rebooted. WORKS !!!

Thanks.

---

