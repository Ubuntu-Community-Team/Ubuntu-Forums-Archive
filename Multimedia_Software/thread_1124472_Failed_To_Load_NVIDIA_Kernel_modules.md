---
title: "Failed To Load NVIDIA Kernel modules"
date: 2009-04-13
forum: Multimedia Software
---

### Post by xx.canes.rites on 2009-04-13
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux rob-desktop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686
Build Date: 24 October 2008 08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd)
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan 30 13:17:00 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) | |-->Monitor "Monitor0"
(**) | |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
X.Org ANSI C Emulation: 0.4
X.Org Video Driver: 4.1
X.Org XInput driver : 2.1
X.Org Server Extension : 1.1
X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation GeForce 8600GT rev 161, Mem @ 0xa2000000/0, 0x80000000/0, 0xa0000000/0, I/O @ 0x00002000/0
(II) System resource ranges:
[0] -1 0 0xffffffff - 0xffffffff (0x1) MX[B]
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[B]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[B]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[B]
[4] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[B]
[5] -1 0 0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.0.0
Module class: X.Org Server Extension
ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.0.0
Module class: X.Org Server Extension
ABI class: X.Org Server Extension, version 1.1
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

(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
compiled for 1.5.2, module version = 2.1.0
Module class: X.Org Font Renderer
ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
compiled for 4.0.2, module version = 1.0.0
Module class: X.Org Server Extension
(II) NVIDIA GLX Module 180.22 Tue Jan 6 09:58:42 PST 2009
(II) Loading extension GLX
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.13.0
Module class: X.Org Server Extension
ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.0.0
ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"

(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
compiled for 4.0.2, module version = 1.0.0
Module class: X.Org Video Driver
(II) LoadModule: "kbd"

(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
compiled for 1.4.99.905, module version = 1.3.1
Module class: X.Org XInput Driver
ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "mouse"

(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
compiled for 1.4.99.905, module version = 1.3.0
Module class: X.Org XInput Driver
ABI class: X.Org XInput driver, version 2.1
(II) NVIDIA dlloader X Driver 180.22 Tue Jan 6 09:35:46 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.0.0
ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"

(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.0.0
ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
[0] -1 0 0xffffffff - 0xffffffff (0x1) MX[B]
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[B]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[B]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[B]
[4] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[B]
[5] -1 0 0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "1024x768_60 +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0): enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

5191 4914
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe with-gdm -- /usr/bin/X :0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7 -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log

X: warning; process set to priority -1 instead of requested priority 0

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux rob-desktop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686
Build Date: 24 October 2008 08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd)
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Fri Jan 30 13:17:02 2009
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
error setting MTRR (base = 0xa1000000, size = 0x00e00000, type = 1) Invalid argument (22)
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
5191 4914


I have no idea what's going on. In version 2.6.27-7 it works fine but in -11 it doesn't work at all. I'm on my -7 install right now, but when I go to load my -11, it's just a black screen then it says need to load in low res mode. I don't understand what's going on, I've tried everything I could think of. Been searching for a fix , can't seem to find one.

---

### Post by xx.canes.rites on 2009-04-13
I activated the "Hardware Drivers" from Ubuntu, then I deactivated them, restarted into my 2.6.27-11 it let me go into the new kernel without a driver, then I just installed the 80.44 drivers inside the 27-11 version kernel and it seems to work now.

I have no idea how to label this thread as solved, but it seems to be solved now for those that were having the type 1 module errors and the other errors I listed above.

---

### Post by glok_twen on 2009-04-27
i'm getting this same same error. occurred right after reboot when upgrading from hardy to jaunty.

can you provide any additional detail on what the commands were to accomplish the fix?

---

### Post by rhm on 2009-04-29
<Bump>

This happened right after I upgraded from Intrepid to Jaunty.

I am getting a "Failed to load Nvidia kernel modules" error on boot and I am currently running in low graphics mode. The Nvidia X Server tells me to run nvidia-xconfig, which I do to no apparent result. I am unable to restart X by means of Alt+Ctrl+Backspace and rebooting just brings me back to step one.

Here's the output of my lspci:

```
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

---

### Post by inobe on 2009-04-29
> **rhm said:**
> <Bump>

This happened right after I upgraded from Intrepid to Jaunty.

I am getting a "Failed to load Nvidia kernel modules" error on boot and I am currently running in low graphics mode. The Nvidia X Server tells me to run nvidia-xconfig, which I do to no apparent result. I am unable to restart X by means of Alt+Ctrl+Backspace and rebooting just brings me back to step one.

Here's the output of my lspci:

```
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

have a look at this [http://ubuntuforums.org/showthread.php?t=1129280](http://ubuntuforums.org/showthread.php?t=1129280)

he was up and going

edit: didn't i just help you.

---

### Post by rhm on 2009-04-29
> **inobe said:**
> have a look at this [http://ubuntuforums.org/showthread.php?t=1129280](http://ubuntuforums.org/showthread.php?t=1129280)

he was up and going

edit: didn't i just help you.

Yes, just a day or two ago. Then I upgraded to Jaunty and everything came apart and I was left in a 800 x 600 hell =P

Followed the link to the thread and it seemed oddly familiar... I was reluctant to repeat the process when the error first happened because it seemed like everything was in the same place where we put it (drivers and such) and because I thought the repo we added was Intrepid-specific. Is it Intrepid-specific?

As I stand now, there was a conflict between the 180.51 driver and the 180.44 kernel module (?). Don't remember well off the top of my head and won't be able to check it or work on it again for another 7 hours or so.

---

### Post by lessgov2007 on 2009-04-29
Other than what's in your log file, does it give you any error when trying to start X? Mine gave me an error telling me it failed to load the driver, and some other stuff, and it suggested I use -ignoreABI. I dunno if this is same for you, but you can find the [destructions here]("http://ubuntuforums.org/showthread.php?t=1142924"). It's a simple thing to do, and if it doesn't help you, you can reverse it just as easy. I dunno, seems lots of people are having NVidia trouble. I feel so lucky right now, usually it's me having issues because of my old hardware, lol. Best of luck to you...

---

### Post by inobe on 2009-04-29
> **rhm said:**
> Yes, just a day or two ago. Then I upgraded to Jaunty and everything came apart and I was left in a 800 x 600 hell =P

Followed the link to the thread and it seemed oddly familiar... I was reluctant to repeat the process when the error first happened because it seemed like everything was in the same place where we put it (drivers and such) and because I thought the repo we added was Intrepid-specific. Is it Intrepid-specific?

As I stand now, there was a conflict between the 180.51 driver and the 180.44 kernel module (?). Don't remember well off the top of my head and won't be able to check it or work on it again for another 7 hours or so.

send me a pm when your ready' point me to a thread you started here in multimedia and video.

yes you want to start a new thread to keep this one clean.

---

### Post by rhm on 2009-04-30
I started a new thread here: [http://ubuntuforums.org/showthread.php?p=7181489#post7181489]("http://ubuntuforums.org/showthread.php?p=7181489#post7181489")

---

### Post by khanw on 2010-02-06
Just as a note to anyone coming here searching for information on loading problems for the "type1" and "freetype" modules:

I got this problem reported out of the blue, without running any updates. One minute everything was working, I rebooted and X wouldn't start. The X server log file reported that it couldn't find these two modules.

It turned out that my hard disk was full... :oops: Removing some big log files solved the problem, X now starts again without any problems.

---

