---
title: "Alienware m9700 SLI video issues in Ubuntu 9.04 after installing nVidia drivers"
date: 2009-05-30
forum: Multimedia Software
---

### Post by evoblade on 2009-05-30
I posted this in a another forum, but I didn't get any replies. Hopefully I will have better luck this time.

I have an Alienware Aurora m9700 laptop with dual GeForce Go 7900 GS in SLI. When I install the restricted nvidia drivers from Ubuntu 9.04's restricted drivers manager and reboot I get no graphics. I think the difficulty is that it's not configuring itself right. Here is my /var/log/Xorg.0.log

```



X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux gaspar 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed May 20 20:11:43 2009
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
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 9

(!!) More than one possible primary device found
(--) PCI: (0@6:0:0) nVidia Corporation GeForce Go 7900 GS rev 161, Mem @ 0xf9000000/16777216, 0xa0000000/268435456, 0xf8000000/16777216, I/O @ 0x0000ac00/128, BIOS @ 0x????????/131072
(--) PCI: (0@7:0:0) nVidia Corporation GeForce Go 7900 GS rev 161, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xfc000000/16777216, I/O @ 0x0000bc00/128, BIOS @ 0x????????/131072
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
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [17] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [19] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Mon Mar 23 15:29:02 PST 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
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
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Mon Mar 23 15:05:32 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: 
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log


```

also, I don't know if this will help but here is my lspci results:

```


00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:04.1 Modem: nVidia Corporation CK804 AC'97 Modem (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
01:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
01:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
01:08.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
01:0a.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
06:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7900 GS (rev a1)
07:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7900 GS (rev a1)


```

Any ideas?

---

### Post by venomgyz on 2009-06-01
Replace your 'Section "Device"' with these.
As you can see, you need to specify your BusID with the xorg server that ubuntu 9.04 uses. Something new in 9.04 broke the default SLI settings. But these will work. The other issue you may end up noticing is some pretty bad graphics performance. I don't think the nvidia drivers have caught up yet. But good luck, post here if you have any problems or questions and I'll try to help.

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BusID          "PCI:6:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BusID          "PCI:7:0:0"
EndSection

Under 'Section "Screen"' add
    Option         "SLI" "on"

---

### Post by evoblade on 2009-06-01
Well, I appreciate your reply and it seems your solution would fix my problem, but now ubuntu won't install my nvidia drivers again.  :-(

---

### Post by spyrosebastos on 2009-06-02
Same prob.

Got 9.04 all set-up and customized..add a second Nvidia card and login screen goes tty1: black.

I have had NO luck trying to install Nvidia driver(s) more than once in any Ubuntu.  You'll probably have to reinstall 9.04, hoping here that your important files are on a separate partition.

has anyone been successful using dual/tri-nvidia graphics card by editing the X conf?  Everytime I've tried editing this myself it never goes right (invalid options or parsing errors.  It seems like any one person's x.conf file is unique to their comp (obviously some options should be different cause people are using different moniters/g.cards, etc.  But if people are using the same OS or same version of Ubuntu the options should be universal.

X.conf options that are invalid:
Resolution
Horisync
Dot Clock..
Vertrefresh...?  Cant really remember all, using liveCD right now for GUI and firefox cant open tabs on the live CD so it's difficult to post the links for the info i've tried. 

trying editing the x.conf from options in post #2

---

### Post by spyrosebastos on 2009-06-02
Vemongyz:

in your first post, under BusID are the lines: "PCI 6:0:0.."-[whatever] and PCI 7:0:0.  Are those specific to your hardware setup.  That your PCI cards are in slots PCI[e] 6 and 7 or is that just to identify them?

---

### Post by evoblade on 2009-06-02
They look like they are specific to mine.  I tried to modify my Xorg.conf and it got farther than before.  New problem: since the nvidia driver failed to install correctly for some reason I have a bastardized setup where the xorg glx module is loading and causing the nvidia stuff to crash. If anyone knows how to reinstall the nvidia drivers I think it might fix my problems.  I tried purging the linux-restricted-modules package and reinstalling but that didn't appear to do anything.

---

### Post by dagrump on 2009-06-02
You need to use one of those device sections only, that is to tell the box which is the primary card. So, if the one doesn't work edit the BusID line to the other slot & you're good. You might want to try  "SLI" "SFR" in place of "SLI  "on". SFR is split frame rendering, there are other options too.
Good luck.

---

### Post by evoblade on 2009-06-02
Would it help if I disabled SLI? After I get the driver reinstalled that is. I really don't care about 3d performance so much as just getting the nvidia driver working so I can use my system again. Really dont want to reinstall.

---

### Post by blueblob11 on 2009-06-04
Hey, I have the same problem you have, I also have an aurora m9700.  I just found out that SLI for laptops on linux is not yet supported according to:

[http://us.download.nvidia.com/XFree86/Linux-x86_64/180.60/README/chapter-25.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/180.60/README/chapter-25.html)

so I think the idea of adding the pci info for just one of the devices should work, but I'm not at my pc to try it.

---

### Post by evoblade on 2009-06-04
Does anyone know how to reinstall the nvidia binary driver? Until I can get a clean driver install nothing else is going to help.

---

### Post by blueblob11 on 2009-06-04
remove all of the nvidia binaries from your computer with

sudo apt-get purge nvidia*

reconfigure x for the backup settings

sudo dpkg-reconfigure -phigh xserver-xorg

repopulate the "hardware drivers" list with

sudo apt-get install envyng-qt

and then you should be able to use the hardware drivers to install and then modify your xorg.conf file manually.

---

### Post by evoblade on 2009-06-04
ok..
for those of us that ride the short bus to school... (like me)

after the second command your laptop should boot back into xwindows the way it did before you goofed it up by installing the nvidia driver.

The third command may fail if you have any nvidia stuff left over in /var/lib (I did, and I think I know why).

so now I think my problem is that X is trying to use a non-existent CRT instead of the DFP (built in screen). Thats why I tossed in the options I did

```


bob@gaspar:~$ cat /etc/X11/xorg.conf
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    Option "IgnoreDisplayDevices" "CRT"
    Option "UseDisplayDevice" "DFP-0"
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BusID "PCI:6:0:0"
Option "SLI" "off"
EndSection

Section "Device"
Identifier "Device1"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BusID "PCI:7:0:0"
Option "SLI" "off"
EndSection


```

gives:

```


X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux gaspar 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd)
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun  4 23:57:36 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(==) No device specified for screen "Default Screen".
    Using the first device section listed.
(**) |   |-->Device "Device0"
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
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(!!) More than one possible primary device found
(--) PCI: (0@6:0:0) nVidia Corporation GeForce Go 7900 GS rev 161, Mem @ 0xf9000000/16777216, 0xa0000000/268435456, 0xf8000000/16777216, I/O @ 0x0000ac00/128, BIOS @ 0x????????/131072
(--) PCI: (0@7:0:0) nVidia Corporation GeForce Go 7900 GS rev 161, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xfc000000/16777216, I/O @ 0x0000bc00/128, BIOS @ 0x????????/131072
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
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [17] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [19] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Mon Mar 23 15:29:02 PST 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
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
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Mon Mar 23 15:05:32 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is:
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
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
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [17] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [19] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
(**) NVIDIA(0): Option "UseDisplayDevice" "DFP-0"
(**) NVIDIA(0): Option "SLI" "off"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): NVIDIA SLI disabled.
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(GPU-0): No display devices connected; falling back to: CRT-0
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce Go 7900 GS (G71) at PCI:6:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.71.22.26.11
(II) NVIDIA(0): Detected PCI Express Link width: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce Go 7900 GS at
(--) NVIDIA(0):     PCI:6:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(WW) NVIDIA(0): Unable to find any of the requested display device "DFP-0" in
(WW) NVIDIA(0):     the list of available display devices "CRT-0".
(II) NVIDIA(0): Assigned Display Device: CRT-0
(==) NVIDIA(0):
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0):
(EE) NVIDIA(0): The requested configuration of display devices (CRT-0) in
(EE) NVIDIA(0):     MetaMode "nvidia-auto-select" is not supported on this
(EE) NVIDIA(0):     GPU.
(WW) NVIDIA(0):
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0):
(EE) NVIDIA(0): The requested configuration of display devices (CRT-0) in
(EE) NVIDIA(0):     MetaMode "nvidia-auto-select" is not supported on this
(EE) NVIDIA(0):     GPU.
(EE) NVIDIA(0): Unable to use default mode "nvidia-auto-select".
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
     at http://wiki.x.org
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log


```

---

### Post by venomgyz on 2009-06-11
Hey evoblade, sorry I took forever to get back to this post. Look at my xorg.conf file.

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder62)  Wed May 27 01:58:49 PDT 2009

Section "Monitor"
	Identifier     "Monitor0"
	VendorName     "Unknown"
	ModelName      "Unknown"
	HorizSync       28.0 - 33.0
	VertRefresh     43.0 - 72.0
	Option         "DPMS"
EndSection

Section "Screen"
	Identifier     "Screen0"
	Device         "Device0"
	Monitor        "Monitor0"
	DefaultDepth    24
	Option         "SLI" "on"
	SubSection "Display"
		Depth       24
	EndSubSection
EndSection

Section "InputDevice"
	Identifier     "Mouse0"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier     "Keyboard0"
	Driver         "kbd"
	# generated from default
EndSection

Section "ServerLayout"
	Identifier     "Layout0"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
	Identifier     "Device0"
	Driver         "nvidia"
	VendorName     "NVIDIA Corporation"
        BusID          "PCI:3:0:0"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection


```

Ok first I should tell you exactly what I did, from a fresh install.

I NEVER installed the ubuntu restricted driver for nvidia. I actually downloaded the one from nvidia (version 185). After installing the driver manually (I just reboot and go into single user mode, typing init 1 in a shell may work as well), I open xorg.conf, add 	Option         "SLI" "on" to the screen section, and BusID          "PCI:3:0:0" to the device section.

Now I know initially I told you to add the 2nd device section. This is actually unnecessary, as you can see from my xorg.conf, and I would definitely recommend only having 1. Sorry about that.

You should check to see if you have an xorg.conf.backup file in your /etc/X11/ folder. If you do you should consider making it your xorg.conf, and see what happens.

---

### Post by evoblade on 2009-06-11
Venomgyz,
What hardware are you running? The documentation for NVIDIA's drivers says SLI is not supported on laptops. My original xorg.conf didn't work, so there is no point in going back to it, my current one is much closer to a solution.

---

### Post by ktmom on 2009-06-13
FWIW:

I have a desktop with a Jaunty MythTV install.  First install a week ago things seemed to work but I was struggling with sound.  Then over night (after an update?) I would get the MythTv frontend on boot, but when I backed out to the desktop the screen would be black with just a mouse cursor.  

After fussing a bit, I reinstalled Mythbuntu but used the open source driver during config.  I then downloaded the nVidia driver from their website (dated June 05, 2009) and control-alt-F1 to a prompt and followed blueblob11's post (#11) to compile and install the downloaded sriver.  I didn't need the apt-get remove line since I never installed the nVidia driver on install.

---

### Post by evoblade on 2009-06-23
So, the consensus is.. download the nvidia driver?

---

### Post by Z-Funk on 2009-07-08
> **evoblade said:**
> So, the consensus is.. download the nvidia driver?

Hey evoblade,

I just wanted to add my 2 cents plus give some closure to this issue.  I have the exact same notebook as you with pretty much the same configuration: Alienware M9700 with a dual Nvidia Geforce GO 7900 GS (256MBx2) video cards.

I had the same problem with xserver.  I just did a fresh install of Jaunty (Actually Ubuntu Ultimate 2.3 - just Jaunty with a lot of pre-added packages).

I been googling around and have seen several threads stating the same problem.  But it was actually this thread which solved mine.  After screwing around with the xorg.conf file in different ways I did a fresh install of Jaunty.

This time after loading it up for the first time, I used envyng -k to install the recommended nvidia driver 180.44.  After I rebooted, xserver crashed with the key message saying that no device was found.

My lspci showed that slot 6 and 7 contained my video cards.  Essentially, I followed venomgyz advice and edited my xorg.conf file adding the 2 essential lines:

Option "SLI" "On" and
BusID "PCI:7:0:0"

and lo and behold on reboot I saw the nvidia logo and xserver login screen thereafter.  Enable compiz and all is well.

Here is my xorg.conf file for your inspection:

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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
        Option "SLI" "on"
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	        "nvidia"
        BusID           "PCI:7:0:0"
EndSection

```

I hope this helps.

---

### Post by mango42 on 2009-09-12
@Z-Funk

Thanks so very much for your 'closure' code. It works perfectly.

A tip for others with this problem: to avoid having to deal with the Vim editor (no doubt brilliant for programmers!) at the system prompt, try 'nano' instead, eg: sudo nano -w /etc/X11/xorg.conf

Ctrl+o saves your changes
Ctrl+x quits the editor
Everything else in the editor works like you'd expect.

And to make life simple, it's well worthwhile printing out Z-Funk's xorg.conf code above - perhaps before you hit the dread system errors ;-)

---

