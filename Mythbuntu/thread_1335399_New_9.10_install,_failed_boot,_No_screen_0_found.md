---
title: "New 9.10 install, failed boot, No screen 0 found"
date: 2009-11-23
forum: Mythbuntu
---

### Post by jjuzwik on 2009-11-23
Longtime MythTV User...

I installed 9.10 on my ~2004 HP n376n Media Center PC.  NVidia 6200 AGP.  Install worked fine.  When i rebooted, all i see is a flickering shell login prompt.  GDM fails to start.  Typing on the keyboard is choppy and nearly useless.  Logging in via ssh gets me in ok...

During the install i chose NVidia as the video driver, and auto-login.

**from xorg.0.log:**

[SIZE="1"]tail -500 /var/log/Xorg.0.log

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux mythtv-10 2.6.31-15-generic-pae #50-Ubuntu SMP Tue Nov 10 16:12:10 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-15-generic-pae root=UUID=b33e6b02-afd7-4c19-948c-c064f8f66a9c ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 23 13:09:19 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
        Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
        Using a default monitor configuration.
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

(--) PCI:*(0:1:0:0) 10de:0221:1682:2152 nVidia Corporation NV44A [GeForce 6200] rev 161, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf5000000/16777216, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 1.0.0
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
        compiled for 1.6.4, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 17:50:12 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 1.1.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Video Driver
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(II) UnloadModule: "nvidia"
(II) Unloading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
         at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.[/SIZE]

**From daemon.log:**

[SIZE="1"]Nov 23 13:17:58 mythtv-10 init: gdm main process (24992) terminated with status 1
Nov 23 13:17:58 mythtv-10 init: gdm main process ended, respawning
Nov 23 13:17:58 mythtv-10 gdm-binary[25026]: WARNING: Unable to find users: no seat-id found
Nov 23 13:17:59 mythtv-10 acpid: client 25022[0:0] has disconnected
Nov 23 13:17:59 mythtv-10 acpid: client connected from 25031[0:0]
Nov 23 13:17:59 mythtv-10 gdm-binary[25026]: WARNING: GdmDisplay: display lasted 0.171413 seconds
Nov 23 13:17:59 mythtv-10 acpid: client 25031[0:0] has disconnected
Nov 23 13:17:59 mythtv-10 acpid: client connected from 25036[0:0]
Nov 23 13:17:59 mythtv-10 gdm-binary[25026]: WARNING: GdmDisplay: display lasted 0.167129 seconds
Nov 23 13:17:59 mythtv-10 acpid: client 25036[0:0] has disconnected
Nov 23 13:17:59 mythtv-10 acpid: client connected from 25041[0:0]
Nov 23 13:17:59 mythtv-10 gdm-binary[25026]: WARNING: GdmDisplay: display lasted 0.165177 seconds
Nov 23 13:17:59 mythtv-10 acpid: client 25041[0:0] has disconnected
Nov 23 13:17:59 mythtv-10 acpid: client connected from 25046[0:0]
Nov 23 13:17:59 mythtv-10 gdm-binary[25026]: WARNING: GdmDisplay: display lasted 0.165867 seconds
Nov 23 13:17:59 mythtv-10 acpid: client 25046[0:0] has disconnected
Nov 23 13:17:59 mythtv-10 acpid: client connected from 25051[0:0]
Nov 23 13:17:59 mythtv-10 gdm-binary[25026]: WARNING: GdmDisplay: display lasted 0.165997 seconds
Nov 23 13:17:59 mythtv-10 acpid: client 25051[0:0] has disconnected
Nov 23 13:17:59 mythtv-10 acpid: client connected from 25056[0:0]
Nov 23 13:17:59 mythtv-10 gdm-binary[25026]: WARNING: GdmDisplay: display lasted 0.165873 seconds
Nov 23 13:17:59 mythtv-10 gdm-binary[25026]: WARNING: GdmLocalDisplayFactory: maximum number of X display failures reached: check X server log for errors
Nov 23 13:17:59 mythtv-10 init: gdm main process (25026) terminated with status 1
Nov 23 13:17:59 mythtv-10 init: gdm main process ended, respawning
Nov 23 13:18:00 mythtv-10 gdm-binary[25060]: WARNING: Unable to find users: no seat-id found
Nov 23 13:18:00 mythtv-10 acpid: client 25056[0:0] has disconnected
Nov 23 13:18:00 mythtv-10 acpid: client connected from 25065[0:0]
Nov 23 13:18:00 mythtv-10 gdm-binary[25060]: WARNING: GdmDisplay: display lasted 0.169198 seconds
Nov 23 13:18:00 mythtv-10 acpid: client 25065[0:0] has disconnected
Nov 23 13:18:00 mythtv-10 acpid: client connected from 25070[0:0]
Nov 23 13:18:00 mythtv-10 gdm-binary[25060]: WARNING: GdmDisplay: display lasted 0.164934 seconds
Nov 23 13:18:00 mythtv-10 acpid: client 25070[0:0] has disconnected
Nov 23 13:18:00 mythtv-10 acpid: client connected from 25075[0:0]
Nov 23 13:18:00 mythtv-10 gdm-binary[25060]: WARNING: GdmDisplay: display lasted 0.164053 seconds
Nov 23 13:18:00 mythtv-10 acpid: client 25075[0:0] has disconnected
Nov 23 13:18:00 mythtv-10 acpid: client connected from 25080[0:0]
Nov 23 13:18:00 mythtv-10 gdm-binary[25060]: WARNING: GdmDisplay: display lasted 0.164822 seconds
Nov 23 13:18:00 mythtv-10 acpid: client 25080[0:0] has disconnected
Nov 23 13:18:00 mythtv-10 acpid: client connected from 25085[0:0]
Nov 23 13:18:00 mythtv-10 gdm-binary[25060]: WARNING: GdmDisplay: display lasted 0.166411 seconds
Nov 23 13:18:00 mythtv-10 acpid: client 25085[0:0] has disconnected
Nov 23 13:18:00 mythtv-10 acpid: client connected from 25090[0:0]
Nov 23 13:18:01 mythtv-10 gdm-binary[25060]: WARNING: GdmDisplay: display lasted 0.165022 seconds
Nov 23 13:18:01 mythtv-10 gdm-binary[25060]: WARNING: GdmLocalDisplayFactory: maximum number of X display failures reached: check X server log for errors
Nov 23 13:18:01 mythtv-10 init: gdm main process (25060) terminated with status 1
Nov 23 13:18:01 mythtv-10 init: gdm main process ended, respawning
Nov 23 13:18:01 mythtv-10 gdm-binary[25094]: WARNING: Unable to find users: no seat-id found
Nov 23 13:18:01 mythtv-10 acpid: client 25090[0:0] has disconnected
Nov 23 13:18:01 mythtv-10 acpid: client connected from 25099[0:0]
Nov 23 13:18:01 mythtv-10 gdm-binary[25094]: WARNING: GdmDisplay: display lasted 0.169033 seconds
Nov 23 13:18:01 mythtv-10 acpid: client 25099[0:0] has disconnected
Nov 23 13:18:01 mythtv-10 acpid: client connected from 25104[0:0]
Nov 23 13:18:01 mythtv-10 gdm-binary[25094]: WARNING: GdmDisplay: display lasted 0.166620 seconds
Nov 23 13:18:01 mythtv-10 acpid: client 25104[0:0] has disconnected
Nov 23 13:18:01 mythtv-10 acpid: client connected from 25109[0:0]
Nov 23 13:18:01 mythtv-10 gdm-binary[25094]: WARNING: GdmDisplay: display lasted 0.176433 seconds
Nov 23 13:18:01 mythtv-10 acpid: client 25109[0:0] has disconnected
Nov 23 13:18:01 mythtv-10 acpid: client connected from 25123[0:0]
Nov 23 13:18:01 mythtv-10 gdm-binary[25094]: WARNING: GdmDisplay: display lasted 0.166146 seconds
Nov 23 13:18:01 mythtv-10 acpid: client 25123[0:0] has disconnected
Nov 23 13:18:01 mythtv-10 acpid: client connected from 25128[0:0]
Nov 23 13:18:01 mythtv-10 gdm-binary[25094]: WARNING: GdmDisplay: display lasted 0.164898 seconds
Nov 23 13:18:02 mythtv-10 acpid: client 25128[0:0] has disconnected
Nov 23 13:18:02 mythtv-10 acpid: client connected from 25133[0:0]
Nov 23 13:18:02 mythtv-10 gdm-binary[25094]: WARNING: GdmDisplay: display lasted 0.166221 seconds
Nov 23 13:18:02 mythtv-10 gdm-binary[25094]: WARNING: GdmLocalDisplayFactory: maximum number of X display failures reached: check X server log for errors
Nov 23 13:18:02 mythtv-10 init: gdm main process (25094) terminated with status 1
Nov 23 13:18:02 mythtv-10 init: gdm main process ended, respawning
Nov 23 13:18:02 mythtv-10 gdm-binary[25137]: WARNING: Unable to find users: no seat-id found
Nov 23 13:18:02 mythtv-10 acpid: client 25133[0:0] has disconnected
Nov 23 13:18:02 mythtv-10 acpid: client connected from 25142[0:0]
Nov 23 13:18:02 mythtv-10 gdm-binary[25137]: WARNING: GdmDisplay: display lasted 0.169704 seconds
Nov 23 13:18:02 mythtv-10 acpid: client 25142[0:0] has disconnected
Nov 23 13:18:02 mythtv-10 acpid: client connected from 25147[0:0]
Nov 23 13:18:02 mythtv-10 gdm-binary[25137]: WARNING: GdmDisplay: display lasted 0.165893 seconds
Nov 23 13:18:02 mythtv-10 acpid: client 25147[0:0] has disconnected
Nov 23 13:18:02 mythtv-10 acpid: client connected from 25152[0:0]
Nov 23 13:18:02 mythtv-10 gdm-binary[25137]: WARNING: GdmDisplay: display lasted 0.165596 seconds
Nov 23 13:18:02 mythtv-10 acpid: client 25152[0:0] has disconnected
Nov 23 13:18:02 mythtv-10 acpid: client connected from 25157[0:0]
Nov 23 13:18:02 mythtv-10 gdm-binary[25137]: WARNING: GdmDisplay: display lasted 0.164816 seconds
Nov 23 13:18:02 mythtv-10 acpid: client 25157[0:0] has disconnected
Nov 23 13:18:02 mythtv-10 acpid: client connected from 25162[0:0]
Nov 23 13:18:03 mythtv-10 gdm-binary[25137]: WARNING: GdmDisplay: display lasted 0.167695 seconds
Nov 23 13:18:03 mythtv-10 acpid: client 25162[0:0] has disconnected
Nov 23 13:18:03 mythtv-10 acpid: client connected from 25167[0:0]
Nov 23 13:18:03 mythtv-10 gdm-binary[25137]: WARNING: GdmDisplay: display lasted 0.166944 seconds
Nov 23 13:18:03 mythtv-10 gdm-binary[25137]: WARNING: GdmLocalDisplayFactory: maximum number of X display failures reached: check X server log for errors
Nov 23 13:18:03 mythtv-10 init: gdm main process (25137) terminated with status 1
Nov 23 13:18:03 mythtv-10 init: gdm main process ended, respawning
Nov 23 13:18:03 mythtv-10 gdm-binary[25171]: WARNING: Unable to find users: no seat-id found
Nov 23 13:18:03 mythtv-10 acpid: client 25167[0:0] has disconnected
Nov 23 13:18:03 mythtv-10 acpid: client connected from 25176[0:0]
Nov 23 13:18:03 mythtv-10 gdm-binary[25171]: WARNING: GdmDisplay: display lasted 0.169875 seconds
Nov 23 13:18:03 mythtv-10 acpid: client 25176[0:0] has disconnected
Nov 23 13:18:03 mythtv-10 acpid: client connected from 25181[0:0]
Nov 23 13:18:03 mythtv-10 gdm-binary[25171]: WARNING: GdmDisplay: display lasted 0.177110 seconds
Nov 23 13:18:03 mythtv-10 acpid: client 25181[0:0] has disconnected
Nov 23 13:18:03 mythtv-10 acpid: client connected from 25195[0:0]
Nov 23 13:18:03 mythtv-10 gdm-binary[25171]: WARNING: GdmDisplay: display lasted 0.165267 seconds
Nov 23 13:18:03 mythtv-10 acpid: client 25195[0:0] has disconnected
Nov 23 13:18:03 mythtv-10 acpid: client connected from 25200[0:0]
Nov 23 13:18:03 mythtv-10 gdm-binary[25171]: WARNING: GdmDisplay: display lasted 0.166720 seconds
Nov 23 13:18:04 mythtv-10 acpid: client 25200[0:0] has disconnected
Nov 23 13:18:04 mythtv-10 acpid: client connected from 25205[0:0]
Nov 23 13:18:04 mythtv-10 gdm-binary[25171]: WARNING: GdmDisplay: display lasted 0.167246 seconds
Nov 23 13:18:04 mythtv-10 acpid: client 25205[0:0] has disconnected
Nov 23 13:18:04 mythtv-10 acpid: client connected from 25210[0:0]
Nov 23 13:18:04 mythtv-10 gdm-binary[25171]: WARNING: GdmDisplay: display lasted 0.167057 seconds
Nov 23 13:18:04 mythtv-10 gdm-binary[25171]: WARNING: GdmLocalDisplayFactory: maximum number of X display failures reached: check X server log for errors
Nov 23 13:18:04 mythtv-10 init: gdm main process (25171) terminated with status 1
Nov 23 13:18:04 mythtv-10 init: gdm main process ended, respawning
Nov 23 13:18:04 mythtv-10 gdm-binary[25214]: WARNING: Unable to find users: no seat-id found
Nov 23 13:18:04 mythtv-10 acpid: client 25210[0:0] has disconnected
Nov 23 13:18:04 mythtv-10 acpid: client connected from 25219[0:0]
Nov 23 13:18:04 mythtv-10 gdm-binary[25214]: WARNING: GdmDisplay: display lasted 0.168326 seconds
Nov 23 13:18:04 mythtv-10 acpid: client 25219[0:0] has disconnected
Nov 23 13:18:04 mythtv-10 acpid: client connected from 25224[0:0][/SIZE]




I'm still investigating.  Any tips would be much appreciated.  Thanks!!!!

---

### Post by jjuzwik on 2009-11-23
**FIXED**

How to fix?  Read on...

1.  ssh to your box from another computer (while screen is showing the flickering login)

2.  from ssh session, kill GDM by running:  *sudo /etc/init.d/gdm stop*  (the screen should stop flickering now)

3.  from ssh session, download latest nvidia [drivers]("http://us.download.nvidia.com/XFree86/Linux-x86/190.42/NVIDIA-Linux-x86-190.42-pkg1.run"):  *wget [http://us.download.nvidia.com/XFree86/Linux-x86/190.42/NVIDIA-Linux-x86-190.42-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/190.42/NVIDIA-Linux-x86-190.42-pkg1.run)*

4.  Goto your keyboard and monitor, login into the console (not ssh!)

5.  From the console, run:  *sudo sh NVIDIA-Linux-x86-190.42-pkg1.run*

6.  Go through the driver install wizard, let it overwrite your existing X configuration when it asks.

7.  When it is finished, reboot your box:  *sudo reboot*

8.  It should reboot and boot into XFCE as expected.


I suspect this is a bug in the mythbuntu installation, where the nvidia driver isnt setup properly.  Either way, its an easy fix!

---

### Post by Shockburner on 2009-11-24
I am having the same problem I am running 64 bit ubuntu so the nvidia driver posted here doesn't work for me I tried a 64 bit one and it didn't work but I'll try a few more later. 

When I use the [SIZE=1]2.6.31-14-generic kernel instead of the [/SIZE][SIZE=1]2.6.31-15-generic[/SIZE][SIZE=1] kernel everything works fine. Additionally, I don't have mythtv on my computer however I do have an nvida graphics card.

This problem developed today after I perform an update (I think there were some kernel updates) and i was prompted to reboot. Once I rebooted I had the exact same problem.[/SIZE] > When i rebooted, all i see is a flickering shell login prompt. GDM fails to start. Typing on the keyboard is choppy and nearly useless. Logging in via ssh gets me in ok...I have an nvidia GeForce 9500 GT. 

I also my not get around to trying to fix my problem until after thanksgiving since everything runs fine in [SIZE=1]2.6.31-14-generic.[/SIZE]

---

