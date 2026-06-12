---
title: "System freeze just before login after installing restricted nvidia drivers"
date: 2010-08-02
forum: Multimedia Software
---

### Post by BungleFeet on 2010-08-02
Hello,

I've been trawling these forums (and the rest of the net) without joy for a solution to this problem, perhaps somebody with experience of installing nvidia drivers on 64bit Lucid can come to the rescue...

I'm trying to get the 8400GS card working with the restricted nvidia drivers (for 3d support). I've tried following numerous how-tos scattered around the forum, and the furthest I've managed to get is with installing the official drivers using the installer from the nVidia website.  However, my system appears to lock up after the splash screen and just before the login screen appears, requiring a REISUB to reboot the system.

Here is what my **/var/log/Xorg.0.log** shows:

```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux ewan-desktop 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=800f1b92-7e17-4fb3-adb2-adaa092c4c19 ro quiet splash
Build Date: 16 June 2010  09:34:29AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Aug  1 00:54:21 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(**) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins,
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(WW) Disabling Keyboard0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 6.0
        X.Org XInput driver : 7.0
        X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:13:0:0) 10de:06e4:196e:05cf nVidia Corporation G98 [GeForce 8400 GS] rev 161, Mem @ 0xd1000000/16777216, 0xc0000000/268435456, 0xd2000000/33554432, I/O @ 0x0000a000/128
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Server Extension
(II) NVIDIA GLX Module  256.35  Wed Jun 16 19:10:31 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.1.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  256.35  Wed Jun 16 18:45:02 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 0d@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) Aug 01 00:54:22 NVIDIA(0): Enabling RENDER acceleration
(II) Aug 01 00:54:22 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Aug 01 00:54:22 NVIDIA(0):     enabled.

```

The NVIDIA driver appears to load, with no error messages. When I tried installing the nvidia-current drivers from the canonical repo, I would get an error message at this point in the logs. No errors this time, but same result - system appears to lock before login.

The 8400GS has both DVI and VGA outputs. My monitor is connected to the VGA output - could it be that once the driver loads it is sending the outout to DVI only? If so, how can I change this behaviour?

Are there any other logs I should be looking at? I scanned through syslog, but that too seemed to show the NVIDIA drivers had loaded okay.

Any help much appreciated.

Cheers,

Bungle

---

### Post by Lawrence Talbot on 2010-08-02
Is there an older version of this driver you can try when open Hardware Drivers.  Sometimes the newest one is not recommended.

---

### Post by BungleFeet on 2010-08-03
> **Lawrence Talbot said:**
> Is there an older version of this driver you can try when open Hardware Drivers.  Sometimes the newest one is not recommended.

Hi Lawrence, thanks for the response. There were two options in the Hardware Drivers wizard: nvidia-185 and nvidia-current.  I tried both, with no success.

Using the installer from the nVidia site seems to have gotten me the furthest so far; I can see no error messages in my Xorg logs, whereas when I tried nvidia-current and nvidia-185, I was getting an error message when Xorg tried to load the drivers.

Cheers,
Bungle

---

