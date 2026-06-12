---
title: "X not working on new install of 12.04"
date: 2013-07-09
forum: Multimedia Software
---

### Post by mike-g2 on 2013-07-09
Hi,

I've got a new install of 12.04 on a server in my lab.  I can access the server remotely or through the non-X virtual terminals, but I can't get X to start properly.  It has a NVIDIA GT200 [GeForce GTX 295].  I have tried uninstalling tnd then reinstalling the nvidia drivers (NB the nvidia proprietary drivers are currently uninstalled again since I thought it would be easiest to get things working with nouveau).  I have also reinstalled both the nouveau and xserver-xorg packages.  I have tried starting X both from a normal boot, via the failsafe mode, and from a virtual terminal using 'service gdm start' but none of these work.

I have no idea what to do now. There is no /etc/X11/xorg.conf file but there is an xorg.conf.failsafe. I've attached a copy of that and the Xorg.failsafe.log and Xorg.0.log below.

Can anyone help me figure out what's going wrong here and/or how to fix it?


Thanks.

Mike


Xorg.0.log
```

[  2230.020] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[  2230.020] X Protocol Version 11, Revision 0
[  2230.020] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[  2230.020] Current Operating System: Linux turing 3.5.0-36-generic #57~precise1-Ubuntu SMP Thu Jun 20 18:21:09 UTC 2013 x86_64
[  2230.020] Kernel command line: BOOT_IMAGE=/vmlinuz-3.5.0-36-generic root=UUID=ac579f27-68b3-4710-8053-e1d60f6bfd50 ro recovery nomodeset
[  2230.020] Build Date: 11 April 2013  01:05:39PM
[  2230.020] xorg-server 2:1.11.4-0ubuntu10.13 (For technical support please see http://www.ubuntu.com/support) 
[  2230.020] Current version of pixman: 0.24.4
[  2230.020]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[  2230.020] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  2230.020] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul  9 11:49:57 2013
[  2230.020] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  2230.020] (==) No Layout section.  Using the first Screen section.
[  2230.020] (==) No screen section available. Using defaults.
[  2230.020] (**) |-->Screen "Default Screen Section" (0)
[  2230.020] (**) |   |-->Monitor "<default monitor>"
[  2230.020] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[  2230.020] (==) Automatically adding devices
[  2230.020] (==) Automatically enabling devices
[  2230.020] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  2230.020]    Entry deleted from font path.
[  2230.020] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  2230.020]    Entry deleted from font path.
[  2230.020] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  2230.020]    Entry deleted from font path.
[  2230.020] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  2230.020]    Entry deleted from font path.
[  2230.020] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  2230.020]    Entry deleted from font path.
[  2230.020] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[  2230.020]    Entry deleted from font path.
[  2230.020] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[  2230.020] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  2230.020] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[  2230.020] (II) Loader magic: 0x7fcc42b1fb00
[  2230.020] (II) Module ABI versions:
[  2230.020]    X.Org ANSI C Emulation: 0.4
[  2230.020]    X.Org Video Driver: 11.0
[  2230.020]    X.Org XInput driver : 16.0
[  2230.020]    X.Org Server Extension : 6.0
[  2230.022] (--) PCI: (0:9:0:0) 10de:05eb:3842:1295 rev 161, Mem @ 0xde000000/16777216, 0xb0000000/268435456, 0xdc000000/33554432, I/O @ 0x0000dc80/128, BIOS @ 0x????????/524288
[  2230.022] (--) PCI:*(0:10:0:0) 10de:05eb:3842:1295 rev 161, Mem @ 0xd9000000/16777216, 0xc0000000/268435456, 0xda000000/33554432, I/O @ 0x0000cc80/128, BIOS @ 0x????????/524288
[  2230.022] (II) Open ACPI successful (/var/run/acpid.socket)
[  2230.022] (II) LoadModule: "extmod"
[  2230.022] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  2230.022] (II) Module extmod: vendor="X.Org Foundation"
[  2230.022]    compiled for 1.11.3, module version = 1.0.0
[  2230.022]    Module class: X.Org Server Extension
[  2230.022]    ABI class: X.Org Server Extension, version 6.0
[  2230.022] (II) Loading extension MIT-SCREEN-SAVER
[  2230.022] (II) Loading extension XFree86-VidModeExtension
[  2230.022] (II) Loading extension XFree86-DGA
[  2230.022] (II) Loading extension DPMS
[  2230.022] (II) Loading extension XVideo
[  2230.022] (II) Loading extension XVideo-MotionCompensation
[  2230.022] (II) Loading extension X-Resource
[  2230.022] (II) LoadModule: "dbe"
[  2230.022] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  2230.022] (II) Module dbe: vendor="X.Org Foundation"
[  2230.022]    compiled for 1.11.3, module version = 1.0.0
[  2230.022]    Module class: X.Org Server Extension
[  2230.022]    ABI class: X.Org Server Extension, version 6.0
[  2230.022] (II) Loading extension DOUBLE-BUFFER
[  2230.022] (II) LoadModule: "glx"
[  2230.023] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  2230.023] (II) Module glx: vendor="X.Org Foundation"
[  2230.023]    compiled for 1.11.3, module version = 1.0.0
[  2230.023]    ABI class: X.Org Server Extension, version 6.0
[  2230.023] (==) AIGLX enabled
[  2230.023] (II) Loading extension GLX
[  2230.023] (II) LoadModule: "record"
[  2230.023] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  2230.023] (II) Module record: vendor="X.Org Foundation"
[  2230.023]    compiled for 1.11.3, module version = 1.13.0
[  2230.023]    Module class: X.Org Server Extension
[  2230.023]    ABI class: X.Org Server Extension, version 6.0
[  2230.023] (II) Loading extension RECORD
[  2230.023] (II) LoadModule: "dri"
[  2230.023] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  2230.023] (II) Module dri: vendor="X.Org Foundation"
[  2230.023]    compiled for 1.11.3, module version = 1.0.0
[  2230.023]    ABI class: X.Org Server Extension, version 6.0
[  2230.023] (II) Loading extension XFree86-DRI
[  2230.023] (II) LoadModule: "dri2"
[  2230.024] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  2230.024] (II) Module dri2: vendor="X.Org Foundation"
[  2230.024]    compiled for 1.11.3, module version = 1.2.0
[  2230.024]    ABI class: X.Org Server Extension, version 6.0
[  2230.024] (II) Loading extension DRI2
[  2230.024] (==) Matched nvidia as autoconfigured driver 0
[  2230.024] (==) Matched nouveau as autoconfigured driver 1
[  2230.024] (==) Matched nv as autoconfigured driver 2
[  2230.024] (==) Matched vesa as autoconfigured driver 3
[  2230.024] (==) Matched fbdev as autoconfigured driver 4
[  2230.024] (==) Assigned the driver to the xf86ConfigLayout
[  2230.024] (II) LoadModule: "nvidia"
[  2230.024] (WW) Warning, couldn't open module nvidia
[  2230.024] (II) UnloadModule: "nvidia"
[  2230.024] (II) Unloading nvidia
[  2230.024] (EE) Failed to load module "nvidia" (module does not exist, 0)
[  2230.024] (II) LoadModule: "nouveau"
[  2230.024] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[  2230.024] (II) Module nouveau: vendor="X.Org Foundation"
[  2230.024]    compiled for 1.11.3, module version = 0.0.16
[  2230.025]    Module class: X.Org Video Driver
[  2230.025]    ABI class: X.Org Video Driver, version 11.0
[  2230.025] (II) LoadModule: "nv"
[  2230.025] (WW) Warning, couldn't open module nv
[  2230.025] (II) UnloadModule: "nv"
[  2230.025] (II) Unloading nv
[  2230.025] (EE) Failed to load module "nv" (module does not exist, 0)
[  2230.025] (II) LoadModule: "vesa"
[  2230.025] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  2230.025] (II) Module vesa: vendor="X.Org Foundation"
[  2230.025]    compiled for 1.11.3, module version = 2.3.0
[  2230.025]    Module class: X.Org Video Driver
[  2230.025]    ABI class: X.Org Video Driver, version 11.0
[  2230.025] (II) LoadModule: "fbdev"
[  2230.025] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  2230.025] (II) Module fbdev: vendor="X.Org Foundation"
[  2230.025]    compiled for 1.11.3, module version = 0.4.2
[  2230.025]    ABI class: X.Org Video Driver, version 11.0
[  2230.025] (==) Matched nvidia as autoconfigured driver 0
[  2230.025] (==) Matched nouveau as autoconfigured driver 1
[  2230.025] (==) Matched nv as autoconfigured driver 2
[  2230.025] (==) Matched vesa as autoconfigured driver 3
[  2230.025] (==) Matched fbdev as autoconfigured driver 4
[  2230.025] (==) Assigned the driver to the xf86ConfigLayout
[  2230.025] (II) LoadModule: "nvidia"
[  2230.026] (WW) Warning, couldn't open module nvidia
[  2230.026] (II) UnloadModule: "nvidia"
[  2230.026] (II) Unloading nvidia
[  2230.026] (EE) Failed to load module "nvidia" (module does not exist, 0)
[  2230.026] (II) LoadModule: "nouveau"
[  2230.026] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[  2230.026] (II) Module nouveau: vendor="X.Org Foundation"
[  2230.026]    compiled for 1.11.3, module version = 0.0.16
[  2230.026]    Module class: X.Org Video Driver
[  2230.026]    ABI class: X.Org Video Driver, version 11.0
[  2230.026] (II) UnloadModule: "nouveau"
[  2230.026] (II) Unloading nouveau
[  2230.026] (II) Failed to load module "nouveau" (already loaded, 0)
[  2230.026] (II) LoadModule: "nv"
[  2230.026] (WW) Warning, couldn't open module nv
[  2230.026] (II) UnloadModule: "nv"
[  2230.026] (II) Unloading nv
[  2230.026] (EE) Failed to load module "nv" (module does not exist, 0)
[  2230.026] (II) LoadModule: "vesa"
[  2230.026] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  2230.026] (II) Module vesa: vendor="X.Org Foundation"
[  2230.026]    compiled for 1.11.3, module version = 2.3.0
[  2230.026]    Module class: X.Org Video Driver
[  2230.027]    ABI class: X.Org Video Driver, version 11.0
[  2230.027] (II) UnloadModule: "vesa"
[  2230.027] (II) Unloading vesa
[  2230.027] (II) Failed to load module "vesa" (already loaded, 0)
[  2230.027] (II) LoadModule: "fbdev"
[  2230.027] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  2230.027] (II) Module fbdev: vendor="X.Org Foundation"
[  2230.027]    compiled for 1.11.3, module version = 0.4.2
[  2230.027]    ABI class: X.Org Video Driver, version 11.0
[  2230.027] (II) UnloadModule: "fbdev"
[  2230.027] (II) Unloading fbdev
[  2230.027] (II) Failed to load module "fbdev" (already loaded, 0)
[  2230.027] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[  2230.027] (II) NOUVEAU driver for NVIDIA chipset families :
[  2230.027]    RIVA TNT        (NV04)
[  2230.027]    RIVA TNT2       (NV05)
[  2230.027]    GeForce 256     (NV10)
[  2230.027]    GeForce 2       (NV11, NV15)
[  2230.027]    GeForce 4MX     (NV17, NV18)
[  2230.027]    GeForce 3       (NV20)
[  2230.027]    GeForce 4Ti     (NV25, NV28)
[  2230.027]    GeForce FX      (NV3x)
[  2230.027]    GeForce 6       (NV4x)
[  2230.027]    GeForce 7       (G7x)
[  2230.027]    GeForce 8       (G8x)
[  2230.027]    GeForce GTX 200 (NVA0)
[  2230.027]    GeForce GTX 400 (NVC0)
[  2230.027] (II) VESA: driver for VESA chipsets: vesa
[  2230.027] (II) FBDEV: driver for framebuffer: fbdev
[  2230.027] (--) using VT number 7

[  2230.030] drmOpenDevice: node name is /dev/dri/card0
[  2230.036] drmOpenByBusid: Searching for BusID pci:0000:0a:00.0
[  2230.036] drmOpenDevice: node name is /dev/dri/card0
[  2230.040] drmOpenByBusid: drmOpenMinor returns -1
[  2230.040] drmOpenDevice: node name is /dev/dri/card1
[  2230.044] drmOpenByBusid: drmOpenMinor returns -1
[  2230.044] drmOpenDevice: node name is /dev/dri/card2
[  2230.048] drmOpenByBusid: drmOpenMinor returns -1
[  2230.048] drmOpenDevice: node name is /dev/dri/card3
[  2230.052] drmOpenByBusid: drmOpenMinor returns -1
[  2230.052] drmOpenDevice: node name is /dev/dri/card4
[  2230.056] drmOpenByBusid: drmOpenMinor returns -1
[  2230.056] drmOpenDevice: node name is /dev/dri/card5
[  2230.060] drmOpenByBusid: drmOpenMinor returns -1
[  2230.060] drmOpenDevice: node name is /dev/dri/card6
[  2230.064] drmOpenByBusid: drmOpenMinor returns -1
[  2230.064] drmOpenDevice: node name is /dev/dri/card7
[  2230.068] drmOpenByBusid: drmOpenMinor returns -1
[  2230.068] drmOpenDevice: node name is /dev/dri/card8
[  2230.072] drmOpenByBusid: drmOpenMinor returns -1
[  2230.072] drmOpenDevice: node name is /dev/dri/card9
[  2230.076] drmOpenByBusid: drmOpenMinor returns -1
[  2230.076] drmOpenDevice: node name is /dev/dri/card10
[  2230.080] drmOpenByBusid: drmOpenMinor returns -1
[  2230.080] drmOpenDevice: node name is /dev/dri/card11
[  2230.084] drmOpenByBusid: drmOpenMinor returns -1
[  2230.084] drmOpenDevice: node name is /dev/dri/card12
[  2230.088] drmOpenByBusid: drmOpenMinor returns -1
[  2230.088] drmOpenDevice: node name is /dev/dri/card13
[  2230.092] drmOpenByBusid: drmOpenMinor returns -1
[  2230.092] drmOpenDevice: node name is /dev/dri/card14
[  2230.096] drmOpenByBusid: drmOpenMinor returns -1
[  2230.096] drmOpenDevice: node name is /dev/dri/card15
[  2230.100] drmOpenByBusid: drmOpenMinor returns -1
[  2230.307] (EE) [drm] failed to open device
[  2230.308] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  2230.308] vesa: Ignoring device with a bound kernel driver
[  2230.308] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  2230.308] vesa: Ignoring device with a bound kernel driver
[  2230.308] (WW) Falling back to old probe method for vesa
[  2230.308] (II) Loading sub module "fbdevhw"
[  2230.308] (II) LoadModule: "fbdevhw"
[  2230.308] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  2230.308] (II) Module fbdevhw: vendor="X.Org Foundation"
[  2230.308]    compiled for 1.11.3, module version = 0.0.2
[  2230.308]    ABI class: X.Org Video Driver, version 11.0
[  2230.308] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  2230.308] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  2230.308] (EE) open /dev/fb0: No such file or directory
[  2230.308] (WW) Falling back to old probe method for fbdev
[  2230.308] (II) UnloadModule: "vesa"
[  2230.308] (II) Unloading vesa
[  2230.308] (II) UnloadModule: "vesa"
[  2230.308] (II) Unloading vesa
[  2230.308] (II) UnloadModule: "fbdev"
[  2230.308] (II) Unloading fbdev
[  2230.308] (II) UnloadModule: "fbdevhw"
[  2230.308] (II) Unloading fbdevhw
[  2230.308] (EE) Screen(s) found, but none have a usable configuration.
[  2230.308] 
Fatal server error:
[  2230.308] no screens found
[  2230.308] 
Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
[  2230.308] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  2230.308] 
[  2230.310]  ddxSigGiveUp: Closing log
[  2230.310] Server terminated with error (1). Closing log file.


```

Xorg.failsafe.log
```

[   804.893] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[   804.894] X Protocol Version 11, Revision 0
[   804.894] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[   804.894] Current Operating System: Linux turing 3.5.0-36-generic #57~precise1-Ubuntu SMP Thu Jun 20 18:21:09 UTC 2013 x86_64
[   804.894] Kernel command line: BOOT_IMAGE=/vmlinuz-3.5.0-36-generic root=UUID=ac579f27-68b3-4710-8053-e1d60f6bfd50 ro recovery nomodeset
[   804.894] Build Date: 11 April 2013  01:05:39PM
[   804.895] xorg-server 2:1.11.4-0ubuntu10.13 (For technical support please see http://www.ubuntu.com/support) 
[   804.895] Current version of pixman: 0.24.4
[   804.895]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[   804.895] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   804.896] (++) Log file: "/var/log/Xorg.failsafe.log", Time: Tue Jul  9 12:07:22 2013
[   804.926] (++) Using config file: "/etc/X11/xorg.conf.failsafe"
[   804.926] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   804.935] (==) No Layout section.  Using the first Screen section.
[   804.935] (**) |-->Screen "Default Screen" (0)
[   804.935] (**) |   |-->Monitor "Configured Monitor"
[   804.944] (**) |   |-->Device "Configured Video Device"
[   804.944] (==) Automatically adding devices
[   804.944] (==) Automatically enabling devices
[   804.971] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   804.971]    Entry deleted from font path.
[   804.971] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   804.971]    Entry deleted from font path.
[   804.971] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   804.971]    Entry deleted from font path.
[   804.972] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   804.972]    Entry deleted from font path.
[   804.972] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   804.972]    Entry deleted from font path.
[   804.972] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   804.972]    Entry deleted from font path.
[   804.972] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[   804.972] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   804.972] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[   804.972] (II) Loader magic: 0x7fa88eb81b00
[   804.972] (II) Module ABI versions:
[   804.972]    X.Org ANSI C Emulation: 0.4
[   804.972]    X.Org Video Driver: 11.0
[   804.972]    X.Org XInput driver : 16.0
[   804.972]    X.Org Server Extension : 6.0
[   804.973] (--) PCI: (0:9:0:0) 10de:05eb:3842:1295 rev 161, Mem @ 0xde000000/16777216, 0xb0000000/268435456, 0xdc000000/33554432, I/O @ 0x0000dc80/128, BIOS @ 0x????????/524288
[   804.973] (--) PCI:*(0:10:0:0) 10de:05eb:3842:1295 rev 161, Mem @ 0xd9000000/16777216, 0xc0000000/268435456, 0xda000000/33554432, I/O @ 0x0000cc80/128, BIOS @ 0x????????/524288
[   804.973] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[   804.973] (II) LoadModule: "extmod"
[   805.011] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   805.021] (II) Module extmod: vendor="X.Org Foundation"
[   805.021]    compiled for 1.11.3, module version = 1.0.0
[   805.021]    Module class: X.Org Server Extension
[   805.021]    ABI class: X.Org Server Extension, version 6.0
[   805.021] (II) Loading extension MIT-SCREEN-SAVER
[   805.021] (II) Loading extension XFree86-VidModeExtension
[   805.021] (II) Loading extension XFree86-DGA
[   805.021] (II) Loading extension DPMS
[   805.021] (II) Loading extension XVideo
[   805.021] (II) Loading extension XVideo-MotionCompensation
[   805.021] (II) Loading extension X-Resource
[   805.021] (II) LoadModule: "dbe"
[   805.021] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   805.033] (II) Module dbe: vendor="X.Org Foundation"
[   805.033]    compiled for 1.11.3, module version = 1.0.0
[   805.033]    Module class: X.Org Server Extension
[   805.033]    ABI class: X.Org Server Extension, version 6.0
[   805.033] (II) Loading extension DOUBLE-BUFFER
[   805.033] (II) LoadModule: "glx"
[   805.033] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   805.049] (II) Module glx: vendor="X.Org Foundation"
[   805.049]    compiled for 1.11.3, module version = 1.0.0
[   805.049]    ABI class: X.Org Server Extension, version 6.0
[   805.049] (==) AIGLX enabled
[   805.050] (II) Loading extension GLX
[   805.050] (II) LoadModule: "record"
[   805.050] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   805.050] (II) Module record: vendor="X.Org Foundation"
[   805.050]    compiled for 1.11.3, module version = 1.13.0
[   805.050]    Module class: X.Org Server Extension
[   805.050]    ABI class: X.Org Server Extension, version 6.0
[   805.050] (II) Loading extension RECORD
[   805.050] (II) LoadModule: "dri"
[   805.050] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   805.072] (II) Module dri: vendor="X.Org Foundation"
[   805.072]    compiled for 1.11.3, module version = 1.0.0
[   805.072]    ABI class: X.Org Server Extension, version 6.0
[   805.072] (II) Loading extension XFree86-DRI
[   805.072] (II) LoadModule: "dri2"
[   805.072] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   805.081] (II) Module dri2: vendor="X.Org Foundation"
[   805.081]    compiled for 1.11.3, module version = 1.2.0
[   805.081]    ABI class: X.Org Server Extension, version 6.0
[   805.081] (II) Loading extension DRI2
[   805.081] (II) LoadModule: "vesa"
[   805.081] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   805.085] (II) Module vesa: vendor="X.Org Foundation"
[   805.085]    compiled for 1.11.3, module version = 2.3.0
[   805.085]    Module class: X.Org Video Driver
[   805.085]    ABI class: X.Org Video Driver, version 11.0
[   805.086] (II) VESA: driver for VESA chipsets: vesa
[   805.086] (--) using VT number 2

[   805.089] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   805.089] vesa: Ignoring device with a bound kernel driver
[   805.089] (WW) Falling back to old probe method for vesa
[   805.089] (II) UnloadModule: "vesa"
[   805.089] (II) Unloading vesa
[   805.089] (EE) Screen(s) found, but none have a usable configuration.
[   805.089] 
Fatal server error:
[   805.089] no screens found
[   805.089] 
Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
[   805.089] Please also check the log file at "/var/log/Xorg.failsafe.log" for additional information.
[   805.089] 
[   805.091]  ddxSigGiveUp: Closing log
[   805.092] Server terminated with error (1). Closing log file.

```

xorg.config.failsafe
```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

---

### Post by tgalati4 on 2013-07-09
If this is a new install of 12.04, then boot into the rescue console and do the following:

```
apt-get update
apt-get upgrade
```

Perform any upgrades needed  or post any errors.  Then try rebooting into your desktop environment.  Somehow the nouveau (open source nvidia module) never got reinstalled correctly.  You can try reinstalling them, but make sure you have other updates installed first.

```
apt-get install xserver-xorg-video-nouveau
```

tgalati4@Mint14-Extensa ~ $ apt-cache search xorg nv
libxmu-dev - X11 miscellaneous utility library (development headers)
libxmu6 - X11 miscellaneous utility library
libxmu6-dbg - X11 miscellaneous utility library (debug package)
libxmuu-dev - X11 miscellaneous micro-utility library (development headers)
libxmuu1 - X11 miscellaneous micro-utility library
libxmuu1-dbg - X11 miscellaneous micro-utility library (debug package)
libxorg-gtest-dev - X.Org dummy testing environment for Google Test - headers
libxorg-gtest-doc - X.org dummy testing environment for Google Test - documentation
libxp6-dbg - X Printing Extension (Xprint) client library (unstripped)
libxrender1-dbg - X Rendering Extension client library (unstripped)
**xserver-xorg-video-nouveau** - X.Org X server -- Nouveau display driver
xserver-xorg-video-nouveau-dbg - X.Org X server -- Nouveau display driver (debug symbols)
nvidia-173 - NVIDIA binary Xorg driver, kernel module and VDPAU library
nvidia-173-dev - NVIDIA binary Xorg driver development files
nvidia-173-updates - NVIDIA binary Xorg driver, kernel module and VDPAU library
nvidia-173-updates-dev - NVIDIA binary Xorg driver development files
nvidia-current - NVIDIA binary Xorg driver, kernel module and VDPAU library
nvidia-current-dev - NVIDIA binary Xorg driver development files
nvidia-current-updates - NVIDIA binary Xorg driver, kernel module and VDPAU library
nvidia-current-updates-dev - NVIDIA binary Xorg driver development files
nvidia-experimental-304 - Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library
nvidia-experimental-304-dev - NVIDIA binary Xorg driver development files
sysinfo - display computer and system information
nvidia-experimental-310 - Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library
nvidia-experimental-310-dev - NVIDIA binary Xorg driver development files

---

### Post by mike-g2 on 2013-07-09
Already did that.  But thanks for the suggestion.

---

### Post by mike-g2 on 2013-07-09
Things have progressed, but I'm still not there yet
I reinstalled nouveau
[INDENT]apt-get --reinstall install xserver-xorg-video-nouveau [/INDENT]
and then ran 
[INDENT] sudo update-initramfs -u[/INDENT]
 since the kernel was still trying to install the nvidia module.  This fixed that

I rebooted the machine and I now get a X window that says 
>  The system is running in low-graphics mode.  Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself.
Pressing return triggers the "OK" button and then I get a screen that says
> 
What would you like to do
[LIST]
[*]Run in low-grpahics mode for just one session
[*]REconfigure graphics
[*]Troubleshoot the error
[*]Exit to console login
[*]
[/LIST]


Unfortunately, the screen is frozen at this point and the only keyboard commands that work are the Ctl-Alt-F[1-8] key combinations.  Interestingly the X window is on T-8 not VT-7 as I am used to.

Anyone?

---

### Post by tgalati4 on 2013-07-09
Try using a standard 4:3 monitor with a standard resolution (say 1600x1200).  If you are using a widescreen (16:9) monitor, then you would probably need to put a custom modeline in your xorg.conf.

Put in the native resolution for your display:

tgalati4@Mint14-Extensa ~ $ gtf 1920 1280 60

  # 1920x1280 @ 60.00 Hz (GTF) hsync: 79.50 kHz; pclk: 207.34 MHz
  Modeline "1920x1280_60.00"  207.34  1920 2056 2264 2608  1280 1281 1284 1325  -HSync +Vsync

---

