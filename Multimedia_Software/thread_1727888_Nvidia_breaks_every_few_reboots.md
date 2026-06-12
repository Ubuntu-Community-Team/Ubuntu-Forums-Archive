---
title: "Nvidia breaks every few reboots"
date: 2011-04-13
forum: Multimedia Software
---

### Post by sharq1 on 2011-04-13
My nvidia drivers breaks every 2-3 reboots - instead of Nvidia logo and log-in window i can only login to console. Starting gdm manually doesn't help. startx gives output "no screens found". I found, that below helps:
```
sudo apt-get --purge remove nvidia-*
sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
sudo reboot
```
but that takes too much time. Does anyone have any idea how can i fix this permamently?

Current configuration:
[LIST]
[*]card: Nvidia 8600M GT
[*]system: Ubuntu 10.10 x64
[*]kernel: 2.6.35-23.41
[*]driver: nvidia 270.29
[*]xorg update to 1.9.0
[*]xorg.conf:
[/LIST]
```
...
Section "ServerFlags"
    Option "ignoreABI" "True"
EndSection
```

---

### Post by sharq1 on 2011-04-18
bump

---

### Post by matt_symes on 2011-04-18
Hi

Is there any change to your xorg.conf before and after X crashes ?

Post the output of ```
cat /var/log/Xorg.0.log
``` after the server crashes.

I would try to compare and contrast that log file before and after the crash to identify what has changed.

Kind regards

---

### Post by sharq1 on 2011-04-24
Thanks for reply **matt_symes**.
Here's what's in xorg.0.log after crash (also included as attachment):
```
[    17.135] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    17.135] X Protocol Version 11, Revision 0
[    17.135] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    17.135] Current Operating System: Linux sharq 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 x86_64
[    17.135] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=c0327f27-fd01-4bf3-ab93-48f9bbe0c598 ro quiet splash
[    17.135] Build Date: 09 January 2011  12:14:27PM
[    17.135] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    17.135] Current version of pixman: 0.18.4
[    17.135] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    17.135] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.136] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 24 09:35:02 2011
[    17.137] (==) Using config file: "/etc/X11/xorg.conf"
[    17.137] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    17.137] (==) ServerLayout "Layout0"
[    17.137] (**) |-->Screen "Screen0" (0)
[    17.137] (**) |   |-->Monitor "Monitor0"
[    17.138] (**) |   |-->Device "Device0"
[    17.138] (**) |-->Input Device "Keyboard0"
[    17.138] (**) |-->Input Device "Mouse0"
[    17.138] (**) Option "IgnoreABI" "True"
[    17.138] (**) Ignoring ABI Version
[    17.138] (==) Automatically adding devices
[    17.138] (==) Automatically enabling devices
[    17.138] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    17.138] 	Entry deleted from font path.
[    17.138] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    17.138] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    17.138] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    17.138] (WW) Disabling Keyboard0
[    17.138] (WW) Disabling Mouse0
[    17.138] (II) Loader magic: 0x7d17a0
[    17.138] (II) Module ABI versions:
[    17.138] 	X.Org ANSI C Emulation: 0.4
[    17.138] 	X.Org Video Driver: 8.0
[    17.138] 	X.Org XInput driver : 11.0
[    17.138] 	X.Org Server Extension : 4.0
[    17.140] (--) PCI:*(0:1:0:0) 10de:0407:0000:0000 rev 161, Mem @ 0xc6000000/16777216, 0xd0000000/268435456, 0xc4000000/33554432, I/O @ 0x00002000/128
[    17.140] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    17.140] (II) LoadModule: "extmod"
[    17.155] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    17.155] (II) Module extmod: vendor="X.Org Foundation"
[    17.155] 	compiled for 1.9.0, module version = 1.0.0
[    17.155] 	Module class: X.Org Server Extension
[    17.155] 	ABI class: X.Org Server Extension, version 4.0
[    17.155] (II) Loading extension MIT-SCREEN-SAVER
[    17.155] (II) Loading extension XFree86-VidModeExtension
[    17.155] (II) Loading extension XFree86-DGA
[    17.155] (II) Loading extension DPMS
[    17.155] (II) Loading extension XVideo
[    17.155] (II) Loading extension XVideo-MotionCompensation
[    17.155] (II) Loading extension X-Resource
[    17.155] (II) LoadModule: "dbe"
[    17.156] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    17.156] (II) Module dbe: vendor="X.Org Foundation"
[    17.156] 	compiled for 1.9.0, module version = 1.0.0
[    17.156] 	Module class: X.Org Server Extension
[    17.156] 	ABI class: X.Org Server Extension, version 4.0
[    17.156] (II) Loading extension DOUBLE-BUFFER
[    17.156] (II) LoadModule: "glx"
[    17.156] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    17.168] (II) Module glx: vendor="NVIDIA Corporation"
[    17.168] 	compiled for 4.0.2, module version = 1.0.0
[    17.168] 	Module class: X.Org Server Extension
[    17.168] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 04:54:41 PDT 2010
[    17.169] (II) Loading extension GLX
[    17.169] (II) LoadModule: "record"
[    17.169] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    17.169] (II) Module record: vendor="X.Org Foundation"
[    17.169] 	compiled for 1.9.0, module version = 1.13.0
[    17.169] 	Module class: X.Org Server Extension
[    17.169] 	ABI class: X.Org Server Extension, version 4.0
[    17.169] (II) Loading extension RECORD
[    17.169] (II) LoadModule: "dri"
[    17.169] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    17.170] (II) Module dri: vendor="X.Org Foundation"
[    17.170] 	compiled for 1.9.0, module version = 1.0.0
[    17.170] 	ABI class: X.Org Server Extension, version 4.0
[    17.170] (II) Loading extension XFree86-DRI
[    17.170] (II) LoadModule: "dri2"
[    17.170] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    17.170] (II) Module dri2: vendor="X.Org Foundation"
[    17.170] 	compiled for 1.9.0, module version = 1.2.0
[    17.170] 	ABI class: X.Org Server Extension, version 4.0
[    17.170] (II) Loading extension DRI2
[    17.170] (II) LoadModule: "nvidia"
[    17.170] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    17.171] (II) Module nvidia: vendor="NVIDIA Corporation"
[    17.171] 	compiled for 4.0.2, module version = 1.0.0
[    17.171] 	Module class: X.Org Video Driver
[    17.173] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    17.173] (EE) NVIDIA:     system's kernel log for additional error messages.
[    17.173] (II) UnloadModule: "nvidia"
[    17.173] (II) Unloading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    17.173] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    17.173] (EE) No drivers available.
[    17.173] 
Fatal server error:
[    17.173] no screens found
[    17.173] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    17.173] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    17.173] 
```

---

