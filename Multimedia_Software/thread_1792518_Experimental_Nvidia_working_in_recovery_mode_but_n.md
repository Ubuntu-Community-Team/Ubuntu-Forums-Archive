---
title: "Experimental Nvidia working in recovery mode but not after normal boot"
date: 2011-06-28
forum: Multimedia Software
---

### Post by Sander1979 on 2011-06-28
Hi there,

I have a very strange problem. I tried to make Compiz work using the experimental 3D support of the free Nvidia driver, because I am suffering from a bug in the proprietary driver ([click here for launchpad entry]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/753144")). The free driver I mean is the one that shows up as "Experimental 3D support for NVIDIA cards" in the "Additional Drivers" manager (note: for some reason, this option will only present itself when no proprietary driver is currently active).

Now the strange thing is: the driver does not provide 3d support, and behaves generally awful (lots of glitches and so on) when I boot my system normally. But when instead I boot from the grub menu into recovery mode, then select "failsafe graphics", and then select "restart X", the whole thing works perfectly! So now I am running the experimental 3d driver, I have compositing working, 3d animations on docky. Somehow, the failsafe boot sequence does something right that my normal boot sequence does not. When I reboot in normal mode, everything is screwed up again.

I have no idea what statistics about my system I should include here, because I really have no idea what could possibly be wrong. I am running 32bits Natty in Classic mode, on an Ahtlon Dual Core 4850e machine, with a GeForce 6150 LE graphics card.

These are the normal and recovery entries in my grub.cfg:

```

menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 74a69553-666f-4ca6-afbb-27d59b4793ac
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=74a69553-666f-4ca6-afbb-27d59b4793ac ro   quiet splash nomodeset vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 74a69553-666f-4ca6-afbb-27d59b4793ac
    echo    'Loading Linux 2.6.38-8-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=74a69553-666f-4ca6-afbb-27d59b4793ac ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}

```Any suggestions are welcome!

---

### Post by coffeecat on 2011-06-28
The experimental support is the package libgl1-mesa-dri-experimental which complements the open-source nouveau driver, as you say. You can, in fact, install it with the proprietary nvidia driver enabled using Synaptic or apt-get. I don't know why it doesn't present itself in Jockey (Additional Drivers) when the nvidia driver is enabled. It might be a bug.  

Whatever - I wonder if the nvidia driver has not been completely purged from your system, and somehow the sequence you've found via the recovery mode gets around this. Three things to check:

1 - have a look in /etc/modprobe.d/nvidia-graphics-drivers.conf. Make sure the nouveau driver is not blacklisted. In my system with the current nvidia driver enabled, that file is simply a symlink to /etc/alternatives/nvidia_modconf, so if it's not there in your system, don't worry about it.

2 - check to see if you have a /etc/X11/xorg.conf file. You need one for the nvidia driver, but not for the nouveau. Having said that, the xorg.conf in my system is so terse, I doubt it would interfere with the nouveau driver.

3 - Open Synaptic and search for packages beginning with nvidia. The package nvidia-common is OK to have, but the presence of any others may interfere with the nouveau driver.

---

### Post by Sander1979 on 2011-06-29
Thanks for the suggestions. There is no /etc/modprobe.d/nvidia-graphics-drivers.conf and also no /etc/alternatives/nvidia_modconf on my system, and the only installed package with "nvidia" in it is nvidia-common. It seems that all proprietary nvidia stuff is purged.

Furthermore, I had no xorg.conf file on my system anymore, as I had renamed it myself after uninstalling my proprietary nvidia drivers. However, I found that the failsafe sequence is using an xorg.conf.failsafe file, so I took a look at it, and it reads as follows:

```

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "fbdev"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```So the failsafe sequence loads the fbdev graphics driver. Is this driver supposed to work in conjunction with the nouveau driver, or is it yet another alternative for it? Anyway, here's a section from my Xorg.failsafe.log where it loads the fbdev:

```

[    22.550] (II) LoadModule: "fbdev"
[    22.550] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.556] (II) Module fbdev: vendor="X.Org Foundation"
[    22.556]     compiled for 1.10.0, module version = 0.4.2
[    22.556]     ABI class: X.Org Video Driver, version 10.0
[    22.556] (II) FBDEV: driver for framebuffer: fbdev
[    22.556] (--) using VT number 2

[    22.558] (II) Loading sub module "fbdevhw"
[    22.558] (II) LoadModule: "fbdevhw"
[    22.559] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.563] (II) Module fbdevhw: vendor="X.Org Foundation"
[    22.563]     compiled for 1.10.1, module version = 0.0.2
[    22.563]     ABI class: X.Org Video Driver, version 10.0
[    22.563] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.563] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.563] (**) FBDEV(0): claimed PCI slot 0@0:5:0
[    22.563] (II) FBDEV(0): using default device
[    22.563] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    22.563] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    22.563] (==) FBDEV(0): RGB weight 888
[    22.563] (==) FBDEV(0): Default visual is TrueColor
[    22.563] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    22.563] (II) FBDEV(0): hardware: nouveaufb (video memory: 5120kB)
[    22.563] (II) FBDEV(0): checking modes against framebuffer device...
[    22.563] (II) FBDEV(0): checking modes against monitor...
[    22.563] (--) FBDEV(0): Virtual size is 1280x1024 (pitch 1280)
[    22.563] (**) FBDEV(0):  Built-in mode "current"
[    22.563] (==) FBDEV(0): DPI set to (96, 96)

```There is no logging of a nouveau or nv driver being loaded, but notice that the logs about fbdev do mention "hardware: nouveaufb". I have no idea what it means.

Now I have just tried the following: I copied the xorg.conf.failsafe to xorg.conf and rebooted into normal mode. The system failed to boot succesfully. Here's the section from Xorg.0.log where it loads fbdev and fails to initialize my display:

```

[    13.492] (II) LoadModule: "fbdev"
[    13.492] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    13.498] (II) Module fbdev: vendor="X.Org Foundation"
[    13.498]     compiled for 1.10.0, module version = 0.4.2
[    13.498]     ABI class: X.Org Video Driver, version 10.0
[    13.498] (II) FBDEV: driver for framebuffer: fbdev
[    13.498] (++) using VT number 7

[    13.501] (II) Loading sub module "fbdevhw"
[    13.501] (II) LoadModule: "fbdevhw"
[    13.501] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    13.505] (II) Module fbdevhw: vendor="X.Org Foundation"
[    13.505]     compiled for 1.10.1, module version = 0.0.2
[    13.505]     ABI class: X.Org Video Driver, version 10.0
[    13.505] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    13.505] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    13.505] (EE) open /dev/fb0: No such file or directory
[    13.505] (WW) Falling back to old probe method for fbdev
[    13.505] (II) UnloadModule: "fbdev"
[    13.505] (II) Unloading fbdev
[    13.505] (II) UnloadModule: "fbdevhw"
[    13.505] (II) Unloading fbdevhw
[    13.505] (EE) Screen(s) found, but none have a usable configuration.
[    13.505] 
Fatal server error:
[    13.505] no screens found

```For reference, here are the complete logfiles:

Xorg.0.log:
```

[    13.462] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    13.462] X Protocol Version 11, Revision 0
[    13.462] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    13.462] Current Operating System: Linux voerman 2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686
[    13.462] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=74a69553-666f-4ca6-afbb-27d59b4793ac ro quiet splash nomodeset vt.handoff=7
[    13.462] Build Date: 21 May 2011  11:38:35AM
[    13.462] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    13.462] Current version of pixman: 0.20.2
[    13.462]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    13.462] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    13.462] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun 29 12:38:51 2011
[    13.462] (==) Using config file: "/etc/X11/xorg.conf"
[    13.462] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    13.463] (==) No Layout section.  Using the first Screen section.
[    13.463] (**) |-->Screen "Default Screen" (0)
[    13.463] (**) |   |-->Monitor "Configured Monitor"
[    13.463] (**) |   |-->Device "Configured Video Device"
[    13.463] (==) Automatically adding devices
[    13.463] (==) Automatically enabling devices
[    13.463] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    13.463]     Entry deleted from font path.
[    13.463] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    13.463] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    13.463] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    13.463] (II) Loader magic: 0x81ffde0
[    13.463] (II) Module ABI versions:
[    13.463]     X.Org ANSI C Emulation: 0.4
[    13.463]     X.Org Video Driver: 10.0
[    13.463]     X.Org XInput driver : 12.3
[    13.463]     X.Org Server Extension : 5.0
[    13.464] (--) PCI:*(0:0:5:0) 10de:0241:1028:01ec rev 162, Mem @ 0xfc000000/16777216, 0xe0000000/268435456, 0xfb000000/16777216, BIOS @ 0x????????/131072
[    13.464] (II) Open ACPI successful (/var/run/acpid.socket)
[    13.464] (II) LoadModule: "extmod"
[    13.480] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    13.480] (II) Module extmod: vendor="X.Org Foundation"
[    13.480]     compiled for 1.10.1, module version = 1.0.0
[    13.480]     Module class: X.Org Server Extension
[    13.480]     ABI class: X.Org Server Extension, version 5.0
[    13.480] (II) Loading extension MIT-SCREEN-SAVER
[    13.480] (II) Loading extension XFree86-VidModeExtension
[    13.480] (II) Loading extension XFree86-DGA
[    13.480] (II) Loading extension DPMS
[    13.480] (II) Loading extension XVideo
[    13.480] (II) Loading extension XVideo-MotionCompensation
[    13.480] (II) Loading extension X-Resource
[    13.480] (II) LoadModule: "dbe"
[    13.481] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    13.481] (II) Module dbe: vendor="X.Org Foundation"
[    13.481]     compiled for 1.10.1, module version = 1.0.0
[    13.481]     Module class: X.Org Server Extension
[    13.481]     ABI class: X.Org Server Extension, version 5.0
[    13.481] (II) Loading extension DOUBLE-BUFFER
[    13.481] (II) LoadModule: "glx"
[    13.481] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    13.489] (II) Module glx: vendor="X.Org Foundation"
[    13.489]     compiled for 1.10.1, module version = 1.0.0
[    13.489]     ABI class: X.Org Server Extension, version 5.0
[    13.490] (==) AIGLX enabled
[    13.490] (II) Loading extension GLX
[    13.490] (II) LoadModule: "record"
[    13.491] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    13.491] (II) Module record: vendor="X.Org Foundation"
[    13.491]     compiled for 1.10.1, module version = 1.13.0
[    13.491]     Module class: X.Org Server Extension
[    13.491]     ABI class: X.Org Server Extension, version 5.0
[    13.491] (II) Loading extension RECORD
[    13.491] (II) LoadModule: "dri"
[    13.491] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    13.491] (II) Module dri: vendor="X.Org Foundation"
[    13.491]     compiled for 1.10.1, module version = 1.0.0
[    13.491]     ABI class: X.Org Server Extension, version 5.0
[    13.491] (II) Loading extension XFree86-DRI
[    13.491] (II) LoadModule: "dri2"
[    13.491] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    13.491] (II) Module dri2: vendor="X.Org Foundation"
[    13.492]     compiled for 1.10.1, module version = 1.2.0
[    13.492]     ABI class: X.Org Server Extension, version 5.0
[    13.492] (II) Loading extension DRI2
[    13.492] (II) LoadModule: "fbdev"
[    13.492] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    13.498] (II) Module fbdev: vendor="X.Org Foundation"
[    13.498]     compiled for 1.10.0, module version = 0.4.2
[    13.498]     ABI class: X.Org Video Driver, version 10.0
[    13.498] (II) FBDEV: driver for framebuffer: fbdev
[    13.498] (++) using VT number 7

[    13.501] (II) Loading sub module "fbdevhw"
[    13.501] (II) LoadModule: "fbdevhw"
[    13.501] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    13.505] (II) Module fbdevhw: vendor="X.Org Foundation"
[    13.505]     compiled for 1.10.1, module version = 0.0.2
[    13.505]     ABI class: X.Org Video Driver, version 10.0
[    13.505] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    13.505] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    13.505] (EE) open /dev/fb0: No such file or directory
[    13.505] (WW) Falling back to old probe method for fbdev
[    13.505] (II) UnloadModule: "fbdev"
[    13.505] (II) Unloading fbdev
[    13.505] (II) UnloadModule: "fbdevhw"
[    13.505] (II) Unloading fbdevhw
[    13.505] (EE) Screen(s) found, but none have a usable configuration.
[    13.505] 
Fatal server error:
[    13.505] no screens found
[    13.505] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    13.505] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    13.505] 
[    13.505]  ddxSigGiveUp: Closing log

```Xorg.failsafe.log:
```

[    22.513] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    22.514] X Protocol Version 11, Revision 0
[    22.514] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    22.514] Current Operating System: Linux voerman 2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686
[    22.515] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=74a69553-666f-4ca6-afbb-27d59b4793ac ro single
[    22.515] Build Date: 21 May 2011  11:38:35AM
[    22.515] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    22.515] Current version of pixman: 0.20.2
[    22.516]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    22.516] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.518] (++) Log file: "/var/log/Xorg.failsafe.log", Time: Wed Jun 29 12:05:31 2011
[    22.518] (++) Using config file: "/etc/X11/xorg.conf.failsafe"
[    22.519] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.519] (==) No Layout section.  Using the first Screen section.
[    22.519] (**) |-->Screen "Default Screen" (0)
[    22.519] (**) |   |-->Monitor "Configured Monitor"
[    22.520] (**) |   |-->Device "Configured Video Device"
[    22.520] (==) Automatically adding devices
[    22.520] (==) Automatically enabling devices
[    22.520] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.520]     Entry deleted from font path.
[    22.520] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    22.520] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.520] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    22.520] (II) Loader magic: 0x81ffde0
[    22.520] (II) Module ABI versions:
[    22.520]     X.Org ANSI C Emulation: 0.4
[    22.520]     X.Org Video Driver: 10.0
[    22.520]     X.Org XInput driver : 12.3
[    22.520]     X.Org Server Extension : 5.0
[    22.521] (--) PCI:*(0:0:5:0) 10de:0241:1028:01ec rev 162, Mem @ 0xfc000000/16777216, 0xe0000000/268435456, 0xfb000000/16777216, BIOS @ 0x????????/131072
[    22.521] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    22.521] (II) LoadModule: "extmod"
[    22.531] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    22.531] (II) Module extmod: vendor="X.Org Foundation"
[    22.531]     compiled for 1.10.1, module version = 1.0.0
[    22.531]     Module class: X.Org Server Extension
[    22.531]     ABI class: X.Org Server Extension, version 5.0
[    22.531] (II) Loading extension MIT-SCREEN-SAVER
[    22.531] (II) Loading extension XFree86-VidModeExtension
[    22.531] (II) Loading extension XFree86-DGA
[    22.531] (II) Loading extension DPMS
[    22.531] (II) Loading extension XVideo
[    22.531] (II) Loading extension XVideo-MotionCompensation
[    22.531] (II) Loading extension X-Resource
[    22.531] (II) LoadModule: "dbe"
[    22.531] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    22.532] (II) Module dbe: vendor="X.Org Foundation"
[    22.532]     compiled for 1.10.1, module version = 1.0.0
[    22.532]     Module class: X.Org Server Extension
[    22.532]     ABI class: X.Org Server Extension, version 5.0
[    22.532] (II) Loading extension DOUBLE-BUFFER
[    22.532] (II) LoadModule: "glx"
[    22.532] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    22.547] (II) Module glx: vendor="X.Org Foundation"
[    22.547]     compiled for 1.10.1, module version = 1.0.0
[    22.548]     ABI class: X.Org Server Extension, version 5.0
[    22.548] (==) AIGLX enabled
[    22.548] (II) Loading extension GLX
[    22.548] (II) LoadModule: "record"
[    22.549] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    22.549] (II) Module record: vendor="X.Org Foundation"
[    22.549]     compiled for 1.10.1, module version = 1.13.0
[    22.549]     Module class: X.Org Server Extension
[    22.549]     ABI class: X.Org Server Extension, version 5.0
[    22.549] (II) Loading extension RECORD
[    22.549] (II) LoadModule: "dri"
[    22.549] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    22.549] (II) Module dri: vendor="X.Org Foundation"
[    22.549]     compiled for 1.10.1, module version = 1.0.0
[    22.549]     ABI class: X.Org Server Extension, version 5.0
[    22.549] (II) Loading extension XFree86-DRI
[    22.549] (II) LoadModule: "dri2"
[    22.550] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.550] (II) Module dri2: vendor="X.Org Foundation"
[    22.550]     compiled for 1.10.1, module version = 1.2.0
[    22.550]     ABI class: X.Org Server Extension, version 5.0
[    22.550] (II) Loading extension DRI2
[    22.550] (II) LoadModule: "fbdev"
[    22.550] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.556] (II) Module fbdev: vendor="X.Org Foundation"
[    22.556]     compiled for 1.10.0, module version = 0.4.2
[    22.556]     ABI class: X.Org Video Driver, version 10.0
[    22.556] (II) FBDEV: driver for framebuffer: fbdev
[    22.556] (--) using VT number 2

[    22.558] (II) Loading sub module "fbdevhw"
[    22.558] (II) LoadModule: "fbdevhw"
[    22.559] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.563] (II) Module fbdevhw: vendor="X.Org Foundation"
[    22.563]     compiled for 1.10.1, module version = 0.0.2
[    22.563]     ABI class: X.Org Video Driver, version 10.0
[    22.563] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.563] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.563] (**) FBDEV(0): claimed PCI slot 0@0:5:0
[    22.563] (II) FBDEV(0): using default device
[    22.563] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    22.563] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    22.563] (==) FBDEV(0): RGB weight 888
[    22.563] (==) FBDEV(0): Default visual is TrueColor
[    22.563] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    22.563] (II) FBDEV(0): hardware: nouveaufb (video memory: 5120kB)
[    22.563] (II) FBDEV(0): checking modes against framebuffer device...
[    22.563] (II) FBDEV(0): checking modes against monitor...
[    22.563] (--) FBDEV(0): Virtual size is 1280x1024 (pitch 1280)
[    22.563] (**) FBDEV(0):  Built-in mode "current"
[    22.563] (==) FBDEV(0): DPI set to (96, 96)
[    22.563] (II) Loading sub module "fb"
[    22.563] (II) LoadModule: "fb"
[    22.563] (II) Loading /usr/lib/xorg/modules/libfb.so
[    22.563] (II) Module fb: vendor="X.Org Foundation"
[    22.563]     compiled for 1.10.1, module version = 1.0.0
[    22.563]     ABI class: X.Org ANSI C Emulation, version 0.4
[    22.563] (**) FBDEV(0): using shadow framebuffer
[    22.563] (II) Loading sub module "shadow"
[    22.563] (II) LoadModule: "shadow"
[    22.563] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    22.573] (II) Module shadow: vendor="X.Org Foundation"
[    22.573]     compiled for 1.10.1, module version = 1.1.0
[    22.573]     ABI class: X.Org ANSI C Emulation, version 0.4
[    22.573] (==) Depth 24 pixmap format is 32 bpp
[    22.584] (==) FBDEV(0): Backing store disabled
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.589] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.590] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.591] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.592] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.593] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.594] (==) FBDEV(0): DPMS enabled
[    22.594] (==) RandR enabled
[    22.594] (II) Initializing built-in extension Generic Event Extension
[    22.594] (II) Initializing built-in extension SHAPE
[    22.594] (II) Initializing built-in extension MIT-SHM
[    22.594] (II) Initializing built-in extension XInputExtension
[    22.594] (II) Initializing built-in extension XTEST
[    22.594] (II) Initializing built-in extension BIG-REQUESTS
[    22.594] (II) Initializing built-in extension SYNC
[    22.594] (II) Initializing built-in extension XKEYBOARD
[    22.594] (II) Initializing built-in extension XC-MISC
[    22.594] (II) Initializing built-in extension SECURITY
[    22.594] (II) Initializing built-in extension XINERAMA
[    22.594] (II) Initializing built-in extension XFIXES
[    22.594] (II) Initializing built-in extension RENDER
[    22.594] (II) Initializing built-in extension RANDR
[    22.594] (II) Initializing built-in extension COMPOSITE
[    22.594] (II) Initializing built-in extension DAMAGE
[    22.594] (II) Initializing built-in extension GESTURE
[    22.604] (II) AIGLX: Screen 0 is not DRI2 capable
[    22.604] (II) AIGLX: Screen 0 is not DRI capable
[    22.604] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[    22.680] (II) AIGLX: Loaded and initialized swrast
[    22.680] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    22.711] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    22.721] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    22.721] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.722] (II) LoadModule: "evdev"
[    22.731] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.731] (II) Module evdev: vendor="X.Org Foundation"
[    22.731]     compiled for 1.10.0.902, module version = 2.6.0
[    22.731]     Module class: X.Org XInput Driver
[    22.731]     ABI class: X.Org XInput driver, version 12.3
[    22.731] (II) Using input driver 'evdev' for 'Power Button'
[    22.731] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.731] (**) Power Button: always reports core events
[    22.731] (**) Power Button: Device: "/dev/input/event1"
[    22.731] (--) Power Button: Found keys
[    22.731] (II) Power Button: Configuring as keyboard
[    22.731] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    22.732] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    22.732] (**) Option "xkb_rules" "evdev"
[    22.732] (**) Option "xkb_model" "pc105"
[    22.732] (**) Option "xkb_layout" "us"
[    22.732] (**) Option "xkb_variant" "intl"
[    22.732] (**) Option "xkb_options" "lv3:ralt_switch"
[    22.734] (II) XKB: reuse xkmfile /var/lib/xkb/server-A56E63F16102D5B0903F3FDBDC0FB5D20109AAF6.xkm
[    22.739] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    22.739] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.739] (II) Using input driver 'evdev' for 'Power Button'
[    22.739] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.739] (**) Power Button: always reports core events
[    22.739] (**) Power Button: Device: "/dev/input/event0"
[    22.740] (--) Power Button: Found keys
[    22.740] (II) Power Button: Configuring as keyboard
[    22.740] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    22.740] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    22.740] (**) Option "xkb_rules" "evdev"
[    22.740] (**) Option "xkb_model" "pc105"
[    22.740] (**) Option "xkb_layout" "us"
[    22.740] (**) Option "xkb_variant" "intl"
[    22.740] (**) Option "xkb_options" "lv3:ralt_switch"
[    22.743] (II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event2)
[    22.743] (**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    22.743] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard'
[    22.743] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.743] (**) Dell Dell USB Keyboard: always reports core events
[    22.743] (**) Dell Dell USB Keyboard: Device: "/dev/input/event2"
[    22.743] (--) Dell Dell USB Keyboard: Found keys
[    22.743] (II) Dell Dell USB Keyboard: Configuring as keyboard
[    22.743] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-5/2-5:1.0/input/input2/event2"
[    22.743] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
[    22.743] (**) Option "xkb_rules" "evdev"
[    22.743] (**) Option "xkb_model" "pc105"
[    22.743] (**) Option "xkb_layout" "us"
[    22.743] (**) Option "xkb_variant" "intl"
[    22.743] (**) Option "xkb_options" "lv3:ralt_switch"
[    22.744] (II) config/udev: Adding input device HID 413c:3010 (/dev/input/event3)
[    22.744] (**) HID 413c:3010: Applying InputClass "evdev pointer catchall"
[    22.744] (II) Using input driver 'evdev' for 'HID 413c:3010'
[    22.744] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.744] (**) HID 413c:3010: always reports core events
[    22.744] (**) HID 413c:3010: Device: "/dev/input/event3"
[    22.744] (--) HID 413c:3010: Found 3 mouse buttons
[    22.744] (--) HID 413c:3010: Found scroll wheel(s)
[    22.744] (--) HID 413c:3010: Found relative axes
[    22.744] (--) HID 413c:3010: Found x and y relative axes
[    22.744] (II) HID 413c:3010: Configuring as mouse
[    22.744] (II) HID 413c:3010: Adding scrollwheel support
[    22.744] (**) HID 413c:3010: YAxisMapping: buttons 4 and 5
[    22.744] (**) HID 413c:3010: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.745] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-6/2-6:1.0/input/input3/event3"
[    22.745] (II) XINPUT: Adding extended input device "HID 413c:3010" (type: MOUSE)
[    22.745] (II) HID 413c:3010: initialized for relative axes.
[    22.745] (**) HID 413c:3010: (accel) keeping acceleration scheme 1
[    22.745] (**) HID 413c:3010: (accel) acceleration profile 0
[    22.745] (**) HID 413c:3010: (accel) acceleration factor: 2.000
[    22.745] (**) HID 413c:3010: (accel) acceleration threshold: 4
[    22.745] (II) config/udev: Adding input device HID 413c:3010 (/dev/input/mouse0)
[    22.745] (II) No input driver/identifier specified (ignoring)
[    22.749] (II) config/udev: Adding input device HDA NVidia Line In at Ext Rear Jack (/dev/input/event4)
[    22.749] (II) No input driver/identifier specified (ignoring)
[    22.749] (II) config/udev: Adding input device HDA NVidia Mic at Ext Front Jack (/dev/input/event5)
[    22.749] (II) No input driver/identifier specified (ignoring)
[    22.749] (II) config/udev: Adding input device HDA NVidia Line Out at Ext Rear Jack (/dev/input/event6)
[    22.749] (II) No input driver/identifier specified (ignoring)
[    22.750] (II) config/udev: Adding input device HDA NVidia HP Out at Ext Front Jack (/dev/input/event7)
[    22.750] (II) No input driver/identifier specified (ignoring)

```Note that the failsafe log is reporting several errors as well, but despite that, my system seems to work fine in failsafe mode (though I haven't tested the front audo jacks, but that is not a priority right now).

Afterthought: I am wondering whether the failsafe log is really the log of my 3d-enabled session, or whether it is merely a log of what happened up till the point where I select the "restart X" option during the recovery mode boot sequence.

---

### Post by afrodeity on 2012-05-13
I have similar issue with a manual installed nvidia driver, works fine in recovery mode, but not booting in normal mode. It is the pae kernel.

---

