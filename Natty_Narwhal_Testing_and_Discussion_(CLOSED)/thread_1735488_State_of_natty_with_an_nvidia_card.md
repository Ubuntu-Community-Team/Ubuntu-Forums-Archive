---
title: "State of natty with an nvidia card?"
date: 2011-04-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ELD on 2011-04-21
Okay so i ordered an nvidia gtx560ti (yeahhh!), it is supposed to be being delivered today although i will no doubt miss it...anyway.
 
What is the state of it's support in natty? Do the latest nvidia drivers support the new xorg?

---

### Post by ratcheer on 2011-04-21
I am using a GT430 card in a fully updated Natty with the latest nVidia current driver for Natty. All is well.

Tim

---

### Post by screaminj3sus on 2011-04-21
afiak they support it. There was a memory leak issue but I think the latest nvidia drivers solved that.

---

### Post by VeeDubb on 2011-04-21
I'm running Natty 64bit, fully updated as of last night (haven't checked this morning)

According to nvidia-settings I'm running 270.41.03  and according to glxgears my GeForce 9800GT is getting over 10,100 FPS, which is pretty good for a 9800.  I suspect Natty will play nice with your new card.

---

### Post by Harry33 on 2011-04-21
> **VeeDubb said:**
> I'm running Natty 64bit, fully updated as of last night (haven't checked this morning)

According to nvidia-settings I'm running 270.41.03  and according to glxgears my GeForce 9800GT is getting over 10,100 FPS, which is pretty good for a 9800.  I suspect Natty will play nice with your new card.

The latest nvidia-current in Natty repos is version 270.41.06.

Here:
[https://launchpad.net/ubuntu/natty/+source/nvidia-graphics-drivers/270.41.06-0ubuntu1](https://launchpad.net/ubuntu/natty/+source/nvidia-graphics-drivers/270.41.06-0ubuntu1)

---

### Post by Harry33 on 2011-04-21
> **ELD said:**
> Okay so i ordered an nvidia gtx560ti (yeahhh!), it is supposed to be being delivered today although i will no doubt miss it...anyway.
 
What is the state of it's support in natty? Do the latest nvidia drivers support the new xorg?

The latest nvidia-current (nvidia proprietary drivers) 270.41.06 in Natty repos supports these newest models:

```

Added support for the following GPUs:
GeForce GT 520
GeForce GT 525M
GeForce GT 520M
GeForce GT 445M
GeForce GT 530
GeForce 405
GeForce GTX 590
GeForce GTX 550 Ti
GeForce GTX 560 Ti
GeForce GT 420
GeForce GT 440
GeForce GTX 470M
GeForce GTX 485M
GeForce GT 550M
GeForce GT 555M
NVS 4200M
Quadro 1000M
Quadro 2000M
Quadro 2000 D
Quadro 400

```

So your GTX560Ti is also supported.

---

### Post by WorLord on 2011-04-21
GTX560Ti user here.  

Natty works _very well_ with this card.  No crashes or freezes or overheating that I can see.  Smooth as butter.

---

### Post by ELD on 2011-04-22
Ideal cheers guys :D

---

### Post by nIRV on 2011-04-22
Everything looks fine over here with my GeForce GT 330M.

Be warned, backlight's brightness control doesn't work, leaving you with a little more than an hour of battery time with a very bright screen. (see [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/764195](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/764195))

---

### Post by rusty725 on 2011-04-22
perhaps it's a bit offtopic but when my powermizer set to adaptive switching between windows lags sometimes when set to prefer maximum perfomance all is fine.
Anyone else has this problem ?

---

### Post by Bobhuber on 2011-04-22
> **ELD said:**
> Okay so i ordered an nvidia gtx560ti (yeahhh!), it is supposed to be being delivered today although i will no doubt miss it...anyway.
 
What is the state of it's support in natty? Do the latest nvidia drivers support the new xorg?

GT220 only boots about half of the time without problems. No way I'm updating or using Natty for everyday usage  in it's present state and I've been testing it since Beta1

---

### Post by cariboo on 2011-04-23
> **Bobhuber said:**
> GT220 only boots about half of the time without problems. No way I'm updating or using Natty for everyday usage  in it's present state and I've been testing it since Beta1

I'm using a GT210 on this system, and haven't had any problems booting to a desktop. Have you checked /var/log/Xorg.0.log, to see what is happening?

---

### Post by 23dornot23d on 2011-04-23
I have a couple of Nvidia cards and both were working properly ......

Yesterday I updated my desktop machine ...... nothing of a problem graphics were working fine ,,,,

Today I boot up and it tells me my graphics card is not set up properly .......

[IMG]http://img861.imageshack.us/img861/9951/lowgraphicsmodes.jpg[/IMG]

because I know it is OK I just restart the xserver ..... and guess what ,,,,,,,

[IMG]http://img215.imageshack.us/img215/7427/restartxs.jpg[/IMG]

All is fine ........


But I check the logs to see what is happening .......

here is the one that comes up when I look for the one that failed ....... xorg.0.log.old

```

[    21.987] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    22.004] X Protocol Version 11, Revision 0
[    22.004] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    22.004] Current Operating System: Linux keith-MS-7181 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[    22.004] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=7aa2ad6d-45fa-46b2-a4aa-41246a6152ab ro quiet splash vt.handoff=7
[    22.004] Build Date: 19 April 2011  03:40:45PM
[    22.004] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    22.004] Current version of pixman: 0.20.2
[    22.004]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    22.004] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.004] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 23 13:17:17 2011
[    22.005] (==) Using config file: "/etc/X11/xorg.conf"
[    22.005] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.005] (==) ServerLayout "Layout0"
[    22.005] (**) |-->Screen "Screen0" (0)
[    22.005] (**) |   |-->Monitor "Monitor0"
[    22.005] (**) |   |-->Device "Device0"
[    22.005] (**) |-->Input Device "Keyboard0"
[    22.005] (**) |-->Input Device "Mouse0"
[    22.005] (==) Automatically adding devices
[    22.005] (==) Automatically enabling devices
[    22.006] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.006]     Entry deleted from font path.
[    22.006] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    22.006]     Entry deleted from font path.
[    22.006] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    22.006]     Entry deleted from font path.
[    22.006] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    22.006]     Entry deleted from font path.
[    22.006] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    22.006]     Entry deleted from font path.
[    22.006] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    22.006] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.006] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    22.006] (WW) Disabling Keyboard0
[    22.006] (WW) Disabling Mouse0
[    22.006] (II) Loader magic: 0x7e0280
[    22.006] (II) Module ABI versions:
[    22.006]     X.Org ANSI C Emulation: 0.4
[    22.006]     X.Org Video Driver: 10.0
[    22.006]     X.Org XInput driver : 12.3
[    22.006]     X.Org Server Extension : 5.0
[    22.007] (--) PCI:*(0:1:0:0) 10de:0221:0000:0000 rev 161, Mem @ 0xf0000000/16777216, 0xe0000000/268435456, 0xf1000000/16777216, BIOS @ 0x????????/131072
[    22.007] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    22.007] (II) LoadModule: "extmod"
[    22.012] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    22.012] (II) Module extmod: vendor="X.Org Foundation"
[    22.012]     compiled for 1.10.1, module version = 1.0.0
[    22.012]     Module class: X.Org Server Extension
[    22.012]     ABI class: X.Org Server Extension, version 5.0
[    22.012] (II) Loading extension MIT-SCREEN-SAVER
[    22.012] (II) Loading extension XFree86-VidModeExtension
[    22.012] (II) Loading extension XFree86-DGA
[    22.012] (II) Loading extension DPMS
[    22.012] (II) Loading extension XVideo
[    22.012] (II) Loading extension XVideo-MotionCompensation
[    22.012] (II) Loading extension X-Resource
[    22.012] (II) LoadModule: "dbe"
[    22.013] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    22.013] (II) Module dbe: vendor="X.Org Foundation"
[    22.013]     compiled for 1.10.1, module version = 1.0.0
[    22.013]     Module class: X.Org Server Extension
[    22.013]     ABI class: X.Org Server Extension, version 5.0
[    22.013] (II) Loading extension DOUBLE-BUFFER
[    22.013] (II) LoadModule: "glx"
[    22.013] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    22.108] (II) Module glx: vendor="NVIDIA Corporation"
[    22.108]     compiled for 4.0.2, module version = 1.0.0
[    22.108]     Module class: X.Org Server Extension
[    22.108] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:10:15 PDT 2011
[    22.108] (II) Loading extension GLX
[    22.108] (II) LoadModule: "record"
[    22.109] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    22.109] (II) Module record: vendor="X.Org Foundation"
[    22.109]     compiled for 1.10.1, module version = 1.13.0
[    22.109]     Module class: X.Org Server Extension
[    22.109]     ABI class: X.Org Server Extension, version 5.0
[    22.109] (II) Loading extension RECORD
[    22.109] (II) LoadModule: "dri"
[    22.118] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    22.119] (II) Module dri: vendor="X.Org Foundation"
[    22.119]     compiled for 1.10.1, module version = 1.0.0
[    22.119]     ABI class: X.Org Server Extension, version 5.0
[    22.119] (II) Loading extension XFree86-DRI
[    22.119] (II) LoadModule: "dri2"
[    22.120] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.120] (II) Module dri2: vendor="X.Org Foundation"
[    22.120]     compiled for 1.10.1, module version = 1.2.0
[    22.120]     ABI class: X.Org Server Extension, version 5.0
[    22.120] (II) Loading extension DRI2
[    22.120] (II) LoadModule: "nvidia"
[    22.120] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    22.121] (II) Module nvidia: vendor="NVIDIA Corporation"
[    22.121]     compiled for 4.0.2, module version = 1.0.0
[    22.121]     Module class: X.Org Video Driver
[    22.148] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    22.148] (EE) NVIDIA:     system's kernel log for additional error messages.
[    22.148] (II) UnloadModule: "nvidia"
[    22.148] (II) Unloading nvidia
[    22.148] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    22.148] (EE) No drivers available.
[    22.148] 
Fatal server error:
[    22.148] no screens found
[    22.148] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    22.148] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    22.148] 

```Here is the log after restarting the xserver with no changes made .....

```

[   268.443] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[   268.443] X Protocol Version 11, Revision 0
[   268.443] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[   268.443] Current Operating System: Linux keith-MS-7181 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[   268.443] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=7aa2ad6d-45fa-46b2-a4aa-41246a6152ab ro quiet splash vt.handoff=7
[   268.443] Build Date: 19 April 2011  03:40:45PM
[   268.443] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[   268.443] Current version of pixman: 0.20.2
[   268.443]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   268.443] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   268.443] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 23 13:21:24 2011
[   268.444] (==) Using config file: "/etc/X11/xorg.conf"
[   268.444] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   268.444] (==) ServerLayout "Layout0"
[   268.444] (**) |-->Screen "Screen0" (0)
[   268.444] (**) |   |-->Monitor "Monitor0"
[   268.444] (**) |   |-->Device "Device0"
[   268.444] (**) |-->Input Device "Keyboard0"
[   268.444] (**) |-->Input Device "Mouse0"
[   268.444] (==) Automatically adding devices
[   268.444] (==) Automatically enabling devices
[   268.445] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   268.445]     Entry deleted from font path.
[   268.445] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   268.445]     Entry deleted from font path.
[   268.445] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   268.445]     Entry deleted from font path.
[   268.445] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   268.445]     Entry deleted from font path.
[   268.445] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   268.445]     Entry deleted from font path.
[   268.445] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   268.445] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   268.445] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   268.445] (WW) Disabling Keyboard0
[   268.445] (WW) Disabling Mouse0
[   268.445] (II) Loader magic: 0x7e0280
[   268.445] (II) Module ABI versions:
[   268.445]     X.Org ANSI C Emulation: 0.4
[   268.445]     X.Org Video Driver: 10.0
[   268.445]     X.Org XInput driver : 12.3
[   268.445]     X.Org Server Extension : 5.0
[   268.446] (--) PCI:*(0:1:0:0) 10de:0221:0000:0000 rev 161, Mem @ 0xf0000000/16777216, 0xe0000000/268435456, 0xf1000000/16777216, BIOS @ 0x????????/131072
[   268.446] (II) Open ACPI successful (/var/run/acpid.socket)
[   268.446] (II) LoadModule: "extmod"
[   268.447] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   268.447] (II) Module extmod: vendor="X.Org Foundation"
[   268.447]     compiled for 1.10.1, module version = 1.0.0
[   268.447]     Module class: X.Org Server Extension
[   268.447]     ABI class: X.Org Server Extension, version 5.0
[   268.447] (II) Loading extension MIT-SCREEN-SAVER
[   268.447] (II) Loading extension XFree86-VidModeExtension
[   268.447] (II) Loading extension XFree86-DGA
[   268.447] (II) Loading extension DPMS
[   268.447] (II) Loading extension XVideo
[   268.447] (II) Loading extension XVideo-MotionCompensation
[   268.447] (II) Loading extension X-Resource
[   268.447] (II) LoadModule: "dbe"
[   268.448] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   268.448] (II) Module dbe: vendor="X.Org Foundation"
[   268.448]     compiled for 1.10.1, module version = 1.0.0
[   268.448]     Module class: X.Org Server Extension
[   268.448]     ABI class: X.Org Server Extension, version 5.0
[   268.448] (II) Loading extension DOUBLE-BUFFER
[   268.448] (II) LoadModule: "glx"
[   268.448] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[   268.469] (II) Module glx: vendor="NVIDIA Corporation"
[   268.469]     compiled for 4.0.2, module version = 1.0.0
[   268.469]     Module class: X.Org Server Extension
[   268.469] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:10:15 PDT 2011
[   268.469] (II) Loading extension GLX
[   268.469] (II) LoadModule: "record"
[   268.470] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   268.470] (II) Module record: vendor="X.Org Foundation"
[   268.470]     compiled for 1.10.1, module version = 1.13.0
[   268.470]     Module class: X.Org Server Extension
[   268.470]     ABI class: X.Org Server Extension, version 5.0
[   268.470] (II) Loading extension RECORD
[   268.470] (II) LoadModule: "dri"
[   268.471] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   268.471] (II) Module dri: vendor="X.Org Foundation"
[   268.471]     compiled for 1.10.1, module version = 1.0.0
[   268.471]     ABI class: X.Org Server Extension, version 5.0
[   268.471] (II) Loading extension XFree86-DRI
[   268.471] (II) LoadModule: "dri2"
[   268.472] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   268.472] (II) Module dri2: vendor="X.Org Foundation"
[   268.472]     compiled for 1.10.1, module version = 1.2.0
[   268.472]     ABI class: X.Org Server Extension, version 5.0
[   268.472] (II) Loading extension DRI2
[   268.472] (II) LoadModule: "nvidia"
[   268.472] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[   268.473] (II) Module nvidia: vendor="NVIDIA Corporation"
[   268.473]     compiled for 4.0.2, module version = 1.0.0
[   268.473]     Module class: X.Org Video Driver
[   268.473] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:25 PDT 2011
[   268.473] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   268.473] (++) using VT number 7

[   268.473] (II) Loading sub module "fb"
[   268.474] (II) LoadModule: "fb"
[   268.474] (II) Loading /usr/lib/xorg/modules/libfb.so
[   268.474] (II) Module fb: vendor="X.Org Foundation"
[   268.474]     compiled for 1.10.1, module version = 1.0.0
[   268.474]     ABI class: X.Org ANSI C Emulation, version 0.4
[   268.474] (II) Loading sub module "wfb"
[   268.474] (II) LoadModule: "wfb"
[   268.474] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   268.475] (II) Module wfb: vendor="X.Org Foundation"
[   268.475]     compiled for 1.10.1, module version = 1.0.0
[   268.475]     ABI class: X.Org ANSI C Emulation, version 0.4
[   268.475] (II) Loading sub module "ramdac"
[   268.475] (II) LoadModule: "ramdac"
[   268.475] (II) Module "ramdac" already built-in
[   268.475] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[   268.475] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   268.475] (II) Loading /usr/lib/xorg/modules/libfb.so
[   268.475] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[   268.475] (==) NVIDIA(0): RGB weight 888
[   268.475] (==) NVIDIA(0): Default visual is TrueColor
[   268.475] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   268.576] (II) NVIDIA(GPU-0): Display (PHILIPS 107E (CRT-1)) does not support NVIDIA 3D
[   268.576] (II) NVIDIA(GPU-0):     Vision stereo.
[   268.577] (II) NVIDIA(0): NVIDIA GPU GeForce 6200 (NV44) at PCI:1:0:0 (GPU-0)
[   268.577] (--) NVIDIA(0): Memory: 262144 kBytes
[   268.577] (--) NVIDIA(0): VideoBIOS: 05.44.a2.10.52
[   268.577] (II) NVIDIA(0): Detected AGP rate: 8X
[   268.577] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[   268.577] (--) NVIDIA(0): Connected display device(s) on GeForce 6200 at PCI:1:0:0
[   268.577] (--) NVIDIA(0):     PHILIPS 107E (CRT-1)
[   268.577] (--) NVIDIA(0): PHILIPS 107E (CRT-1): 400.0 MHz maximum pixel clock
[   268.577] (II) NVIDIA(0): Assigned Display Device: CRT-1
[   268.577] (==) NVIDIA(0): 
[   268.577] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[   268.577] (==) NVIDIA(0):     will be used as the requested mode.
[   268.577] (==) NVIDIA(0): 
[   268.578] (II) NVIDIA(0): Validated modes:
[   268.578] (II) NVIDIA(0):     "nvidia-auto-select"
[   268.578] (II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
[   268.580] (--) NVIDIA(0): DPI set to (104, 113); computed from "UseEdidDpi" X config
[   268.580] (--) NVIDIA(0):     option
[   268.580] (--) Depth 24 pixmap format is 32 bpp
[   268.586] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[   268.613] (II) Loading extension NV-GLX
[   268.649] (==) NVIDIA(0): Disabling shared memory pixmaps
[   268.649] (==) NVIDIA(0): Backing store disabled
[   268.649] (==) NVIDIA(0): Silken mouse enabled
[   268.649] (**) NVIDIA(0): DPMS enabled
[   268.649] (II) Loading extension NV-CONTROL
[   268.650] (II) Loading extension XINERAMA
[   268.650] (II) Loading sub module "dri2"
[   268.650] (II) LoadModule: "dri2"
[   268.650] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   268.650] (II) Module dri2: vendor="X.Org Foundation"
[   268.651]     compiled for 1.10.1, module version = 1.2.0
[   268.651]     ABI class: X.Org Server Extension, version 5.0
[   268.651] (II) NVIDIA(0): [DRI2] Setup complete
[   268.651] (==) RandR enabled
[   268.651] (II) Initializing built-in extension Generic Event Extension
[   268.651] (II) Initializing built-in extension SHAPE
[   268.651] (II) Initializing built-in extension MIT-SHM
[   268.651] (II) Initializing built-in extension XInputExtension
[   268.651] (II) Initializing built-in extension XTEST
[   268.651] (II) Initializing built-in extension BIG-REQUESTS
[   268.651] (II) Initializing built-in extension SYNC
[   268.651] (II) Initializing built-in extension XKEYBOARD
[   268.651] (II) Initializing built-in extension XC-MISC
[   268.651] (II) Initializing built-in extension SECURITY
[   268.651] (II) Initializing built-in extension XINERAMA
[   268.651] (II) Initializing built-in extension XFIXES
[   268.651] (II) Initializing built-in extension RENDER
[   268.651] (II) Initializing built-in extension RANDR
[   268.651] (II) Initializing built-in extension COMPOSITE
[   268.651] (II) Initializing built-in extension DAMAGE
[   268.651] (II) Initializing built-in extension GESTURE
[   268.654] (II) Initializing extension GLX
[   268.682] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   268.693] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   268.693] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   268.693] (II) LoadModule: "evdev"
[   268.693] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   268.694] (II) Module evdev: vendor="X.Org Foundation"
[   268.694]     compiled for 1.10.0.902, module version = 2.6.0
[   268.694]     Module class: X.Org XInput Driver
[   268.694]     ABI class: X.Org XInput driver, version 12.3
[   268.694] (II) Using input driver 'evdev' for 'Power Button'
[   268.694] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   268.694] (**) Power Button: always reports core events
[   268.694] (**) Power Button: Device: "/dev/input/event1"
[   268.694] (--) Power Button: Found keys
[   268.694] (II) Power Button: Configuring as keyboard
[   268.694] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   268.694] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   268.694] (**) Option "xkb_rules" "evdev"
[   268.694] (**) Option "xkb_model" "pc105"
[   268.694] (**) Option "xkb_layout" "gb"
[   268.697] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[   268.701] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   268.701] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   268.701] (II) Using input driver 'evdev' for 'Power Button'
[   268.701] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   268.701] (**) Power Button: always reports core events
[   268.701] (**) Power Button: Device: "/dev/input/event0"
[   268.701] (--) Power Button: Found keys
[   268.701] (II) Power Button: Configuring as keyboard
[   268.701] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   268.701] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   268.701] (**) Option "xkb_rules" "evdev"
[   268.701] (**) Option "xkb_model" "pc105"
[   268.701] (**) Option "xkb_layout" "gb"
[   268.707] (II) config/udev: Adding input device HID 04d9:048e (/dev/input/event3)
[   268.707] (**) HID 04d9:048e: Applying InputClass "evdev pointer catchall"
[   268.707] (II) Using input driver 'evdev' for 'HID 04d9:048e'
[   268.707] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   268.708] (**) HID 04d9:048e: always reports core events
[   268.708] (**) HID 04d9:048e: Device: "/dev/input/event3"
[   268.708] (--) HID 04d9:048e: Found 9 mouse buttons
[   268.708] (--) HID 04d9:048e: Found scroll wheel(s)
[   268.708] (--) HID 04d9:048e: Found relative axes
[   268.708] (--) HID 04d9:048e: Found x and y relative axes
[   268.708] (II) HID 04d9:048e: Configuring as mouse
[   268.708] (II) HID 04d9:048e: Adding scrollwheel support
[   268.708] (**) HID 04d9:048e: YAxisMapping: buttons 4 and 5
[   268.708] (**) HID 04d9:048e: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   268.708] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.3/usb5/5-1/5-1:1.0/input/input3/event3"
[   268.708] (II) XINPUT: Adding extended input device "HID 04d9:048e" (type: MOUSE)
[   268.708] (II) HID 04d9:048e: initialized for relative axes.
[   268.708] (**) HID 04d9:048e: (accel) keeping acceleration scheme 1
[   268.708] (**) HID 04d9:048e: (accel) acceleration profile 0
[   268.708] (**) HID 04d9:048e: (accel) acceleration factor: 2.000
[   268.708] (**) HID 04d9:048e: (accel) acceleration threshold: 4
[   268.709] (II) config/udev: Adding input device HID 04d9:048e (/dev/input/mouse0)
[   268.709] (II) No input driver/identifier specified (ignoring)
[   268.715] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[   268.716] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   268.716] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   268.716] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   268.716] (**) AT Translated Set 2 keyboard: always reports core events
[   268.716] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[   268.716] (--) AT Translated Set 2 keyboard: Found keys
[   268.716] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[   268.716] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[   268.716] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[   268.716] (**) Option "xkb_rules" "evdev"
[   268.716] (**) Option "xkb_model" "pc105"
[   268.716] (**) Option "xkb_layout" "gb"
[   352.349] (II) XKB: reuse xkmfile /var/lib/xkb/server-58118CAC4FF2A02B3A940F3A7A58FD5C451401BC.xkm
[   356.681] (II) XKB: reuse xkmfile /var/lib/xkb/server-58118CAC4FF2A02B3A940F3A7A58FD5C451401BC.xkm

```All is well .......... but why it has just started to happen I do not know ...... but its as annoying as hell
even removed the nvidia drivers and re-installed them ...... this will work ...... for the next warm reboot.

Reboot again or cold reboot ....... and it tells me I have no available useable graphics ...... 

Restart the xserver as it at this point drops me into safe mode ....... and it will boot up and I have my
graphics ....... 

but the xorg.0.log ...... is not showing the problem - its only recording it in the previous one

xorg.0.log.old


This may be a similar problem for you too ...... my laptop which I have not upgraded for about a week now is working fine ....... and it will stay that way ...... ( until the new release is launched and that then may go into a separate partition as a clean install - to see how good it is )

What is more annoying than anything is that the computer is now over riding any decisions I have made to set it it up properly.

( are the developers playing it safe here and putting as many people as they can into safe graphics mode due to all the compiz problems - of which I have none as I run Gnome-shell ).

More to the point what needs changing to stop this happening ........ my computer wants safe-mode only .

1. I re-installed the graphic card drivers ...... ( this works only for the initial session after re-boot - re-boot one more time and it changes back to safe-mode - very bizarre )
2. I tried it with a new xorg.conf to try to take control and I also tried it without one ..... neither option changes anything.

---

