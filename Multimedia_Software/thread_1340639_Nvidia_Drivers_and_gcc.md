---
title: "Nvidia Drivers and gcc"
date: 2009-11-28
forum: Multimedia Software
---

### Post by root45 on 2009-11-28
Okay,

I'm trying to install [these]("http://www.nvidia.com/object/linux_display_amd64_173.14.22.html") Nvidia drivers for my graphics card. This is something I do on a regular basis since they need to be updated everytime the kernel changes. This time, however, I get the error

"The CC version check failed:

The compiler used to compile the kernel (gcc 4.3) does not exactly match the current compiler (gcc 4.4). The Linux 2.6 kernel module loader rejects kernel modules built with a version of gcc that does not exactly match that of the compiler used to built the running kernel.

If you know what you are doing and want to ignore the gcc version check, select "No" to continue installation. Otherwise, select "Yes" to abort installation, set the CC environment veriable to the name of the compiler used to compile your kernel, and restart installation. Abort now?"

I've searched around for the solution to this, and as best I can tell, what I should be doing is entering the following:

export CC=/usr/bin/gcc-4.3

Unfortunately, I did that and it still doesn't work. Also, choosing "No" causes the installer to fail as well.

This is all happening because I'm not booting from the newest installed kernel. Unfortunately, right now there's no immediate way around that. If anyone wants to help me fix that problem, I have another thread over here:

[http://ubuntuforums.org/showthread.php?t=1339833](http://ubuntuforums.org/showthread.php?t=1339833)

Because of the problems from that thread, I can't actually start gdm at all, so I'm stuck in a shell for now. Any help would be appreciated greatly.

-Kris

---

### Post by dozch on 2009-11-28
Is there a specific reason why you can't use the (newer) nVidia driver that Ubuntu provides?

See: [http://ubuntuguide.org/wiki/Ubuntu:Karmic#Install_Latest_Nvidia.2FATI_drivers]("http://ubuntuguide.org/wiki/Ubuntu:Karmic#Install_Latest_Nvidia.2FATI_drivers")

---

### Post by dozch on 2009-11-28
Apologies, I just read your other thread and see that have other issues as well.

I recently had that flashing screen after booting the default kernel and it was because I did not have the nVidia-185 drivers installed. I would try to fix that first. So boot the 2.6.31-16-generic (recovery mode) kernel which drops you in the command line. Then install the nVidia driver:

```
sudo apt-get install nvidia-glx-185 nvidia-185-modaliases nvidia-185-libvdpau
```

That should get the normal 2.6.31-16 going. From here you might be able to fix up the other kernel (-302-ec2). 

Hope this helps

---

### Post by root45 on 2009-11-28
Okay, this seems like a reasonable idea, unfortunately I can't access the internet from the command line right now. I only have wireless access and after a few hours of trying to get it working, I believe my drivers aren't supported (although I'm skeptical of this because the wireless worked with 9.04 in the GUI).

Anyway, is there a way I can download those packages to install them without the internet? I have access to another computer and the ability to transfer the files over, I just don't know where to download the packages or how to install them after they're transferred.

Thanks for your help.

---

### Post by root45 on 2009-11-29
Okay, well I installed all those packages (the ones recommended) and I still get the flashing screen problem when I boot into the non-recovery-mode 2.6.31-16. Any other ideas?

---

### Post by dozch on 2009-11-29
You may have to reconfigure the xorg.conf. Boot the recovery mode again and type:

```
sudo nvidia-xconfig
```

---

### Post by root45 on 2009-11-29
No go. Still flashing after a reboot. I should mention that I originally tried to install Nvidia's drivers instead of the repository ones because of this thread:

[http://ubuntuforums.org/showthread.php?t=1335399](http://ubuntuforums.org/showthread.php?t=1335399)

He seems to have had the same problem and was able to solve it by using the drivers from Nvidia's website. I just can't install the drivers because of the problem I mentioned earlier.

---

### Post by dozch on 2009-11-29
How far did you get with installing these drivers from the nVidia website? Even if it installed only partially, I wonder if uninstalling them first would help:

```
sudo sh <nVidia package>.run --uninstall
```

where <nVidia package>.run is the package you got from nvidia...

---

### Post by root45 on 2009-11-29
No luck. I uninstalled it, also uninstalled the old driver and then reinstalled all the repository packages. I still get the flashing screen.

---

### Post by dozch on 2009-11-29
Are there any errors in the /var/log/Xorg.0.log and /var/log/kern.log?

(I presume it is a bit hard to post them?)

---

### Post by root45 on 2009-11-29
I booted up from the LiveCD and these are the outputs from the logs:

Xorg.0.log

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux Kris 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:32 UTC 2009 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.28-16-generic root=UUID=155d64e8-60bd-446a-b2ae-5e2dae382f16 ro quiet splash
Build Date: 26 October 2009  05:19:56PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@)
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 29 07:55:10 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
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
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0xb40
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0:0:13:0) 10de:03d1:1019:2602 nVidia Corporation C61 [GeForce 6100 nForce 405] rev 162, Mem @ 0xfb000000/16777216, 0xe0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072
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
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
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
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(WW) Warning, couldn't open module freetype
(II) UnloadModule: "freetype"
(EE) Failed to load module "freetype" (module does not exist, 0)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 18:27:24 PDT 2009
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
     at http://wiki.x.org
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```

I've posted the kern.log file here:

[http://dl.dropbox.com/u/2214330/kern.txt](http://dl.dropbox.com/u/2214330/kern.txt)

I'm not entirely sure how to look for errors in that. I just copied everything dated since I upgraded.

---

### Post by dozch on 2009-11-30
If these are the outputs from when you boot the LiveCD they won't tell you much (btw does the LiveCD boot up correctly?). You need to find the errors in the logs after a boot of your 2.6.31-16-generic kernel.

Can't you connect this PC to the net with an ethernet cable, so you can do an update (as in: boot in recovery mode and do 'sudo apt-get update' and then another 'sudo nvidia-xconfig')? 

Your PC seems to be in a bit of a messy state, it is hard to isolate your problem from a distance. An update would hopefully get it to a more stable state.

---

### Post by root45 on 2009-11-30
Well, I booted from the Live CD and then took the logs from the harddrive. I didn't think the live CD would write to those logs when booting. That drive wasn't even mounted until I mounted it after it finished booting. But if it'll make a difference I'll just boot into recovery mode and then copy the logs over to a USB drive then post them.

The LiveCD boots fine for the most part. I have a small display resolution issue, but I think that can be fixed later.

There really isn't a way for me to connect to the internet with an ethernet cable. It's a shared internet connection. Is there a way to run sudo apt-get update and nvidia-xconfig from the LiveCD but have those commands act on the harddrive? I can connect to the internet from the LiveCD.

---

### Post by root45 on 2009-11-30
Okay. These are the outputs of Xorg.0.log and kern.log when I only boot the 2.6.31-16 kernel into recovery mode:

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux Kris 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:32 UTC 2009 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.28-16-generic root=UUID=155d64e8-60bd-446a-b2ae-5e2dae382f16 ro quiet splash
Build Date: 26 October 2009  05:19:56PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 29 07:55:10 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
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
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0:0:13:0) 10de:03d1:1019:2602 nVidia Corporation C61 [GeForce 6100 nForce 405] rev 162, Mem @ 0xfb000000/16777216, 0xe0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
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
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(WW) Warning, couldn't open module freetype
(II) UnloadModule: "freetype"
(EE) Failed to load module "freetype" (module does not exist, 0)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 18:27:24 PDT 2009
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
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

```

The kern.log is here:

[http://dl.dropbox.com/u/2214330/kern.txt](http://dl.dropbox.com/u/2214330/kern.txt)

---

### Post by dozch on 2009-12-01
The kern.log states that it is loading kernel version 2.6.28-16-generic  (gcc version 4.3.3), not 2.6.31-16?? But I can't see any other errors.. Have a look in the 'dmesg' log file.

I know this is a cop-out, but it is perhaps quicker to do a clean install.

---

### Post by dozch on 2009-12-01
I am such a goose... 

There is no 2.6.31-16 kernel, the latest one is 2.6.31-15. The 2.6.28-16 kernel is the kernel from Ubuntu 9.04.

Can you try the same as above, starting from #6, but now with 2.6.31-15?

---

### Post by root45 on 2009-12-01
Okay I booted into 2.6.31-15 (recovery mode) and ran nvidia-xconfig, but the screen still flashes when I try to boot into the regular 2.6.31-15 kernel.

I've copied the kern.log, Xorg.0.log and dmesg over.

dmesg:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-15-generic (buildd@yellow) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 (Ubuntu 2.6.31-15.50-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-15-generic root=UUID=155d64e8-60bd-446a-b2ae-5e2dae382f16 ro single
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007bee0000 (usable)
[    0.000000]  BIOS-e820: 000000007bee0000 - 000000007bee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007bee3000 - 000000007bef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007bef0000 - 000000007bf00000 (reserved)
[    0.000000]  BIOS-e820: 000000007c000000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.2 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x7bee0 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFC0000000 write-back
[    0.000000]   1 base 0040000000 mask FFE0000000 write-back
[    0.000000]   2 base 0060000000 mask FFF0000000 write-back
[    0.000000]   3 base 0070000000 mask FFF8000000 write-back
[    0.000000]   4 base 0078000000 mask FFFC000000 write-back
[    0.000000]   5 base 007BF00000 mask FFFFF00000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f400 (usable)
[    0.000000]  modified: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007bee0000 (usable)
[    0.000000]  modified: 000000007bee0000 - 000000007bee3000 (ACPI NVS)
[    0.000000]  modified: 000000007bee3000 - 000000007bef0000 (ACPI data)
[    0.000000]  modified: 000000007bef0000 - 000000007bf00000 (reserved)
[    0.000000]  modified: 000000007c000000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-000000007bee0000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 007be00000 page 2M
[    0.000000]  007be00000 - 007bee0000 page 4k
[    0.000000] kernel direct mapping tables up to 7bee0000 @ 10000-14000
[    0.000000] RAMDISK: 37958000 - 37fef935
[    0.000000] ACPI: RSDP 00000000000f7a10 00014 (v00 Nvidia)
[    0.000000] ACPI: RSDT 000000007bee3040 00038 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: FACP 000000007bee30c0 00074 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0000000000000000/1 20090521 tbfadt-558
[    0.000000] ACPI: DSDT 000000007bee3180 06395 (v01 NVIDIA NVDAACPI 00001000 MSFT 0100000E)
[    0.000000] ACPI: FACS 000000007bee0000 00040
[    0.000000] ACPI: SSDT 000000007bee9640 001C4 (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
[    0.000000] ACPI: _HPT 000000007bee9880 00038 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000098)
[    0.000000] ACPI: MCFG 000000007bee9900 0003C (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: APIC 000000007bee9580 0007C (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007bee0000
[    0.000000] Bootmem setup node 0 0000000000000000-000000007bee0000
[    0.000000]   NODE_DATA [0000000000012000 - 0000000000016fff]
[    0.000000]   bootmap [0000000000017000 -  00000000000267df] pages 10
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 007bee0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e4ccc]    TEXT DATA BSS ==> [0001000000 - 00019e4ccc]
[    0.000000]   #3 [0037958000 - 0037fef935]          RAMDISK ==> [0037958000 - 0037fef935]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [00019e5000 - 00019e5096]              BRK ==> [00019e5000 - 00019e5096]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000] found SMP MP-table at [ffff8800000f3a00] f3a00
[    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff880001e00000-ffff8800039fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007bee0
[    0.000000] On node 0 totalpages: 507503
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 102 pages reserved
[    0.000000]   DMA zone: 3825 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6885 pages used for memmap
[    0.000000]   DMA32 zone: 496635 pages, LIFO batch:31
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 0 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:70000000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff8800019f6000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 500460
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-15-generic root=UUID=155d64e8-60bd-446a-b2ae-5e2dae382f16 ro single
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 630000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Memory: 1984056k/2030464k available (5315k kernel code, 452k absent, 45956k reserved, 3018k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1908.938 MHz processor.
[    0.000012] spurious 8259A interrupt: IRQ7.
[    0.003251] Console: colour VGA+ 80x25
[    0.003254] console [tty0] enabled
[    0.010000] allocated 20971520 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3817.87 BogoMIPS (lpj=19089380)
[    0.010156] Security Framework initialized
[    0.010236] AppArmor: AppArmor initialized
[    0.010488] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.011746] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.012392] Mount-cache hash table entries: 256
[    0.012602] Initializing cgroup subsys ns
[    0.012664] Initializing cgroup subsys cpuacct
[    0.012725] Initializing cgroup subsys memory
[    0.012790] Initializing cgroup subsys freezer
[    0.012850] Initializing cgroup subsys net_cls
[    0.012921] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.012984] CPU: L2 Cache: 512K (64 bytes/line)
[    0.013045] CPU 0/0x0 -> Node 0
[    0.013103] tseg: 007bf00000
[    0.013105] CPU: Physical Processor ID: 0
[    0.013163] CPU: Processor Core ID: 0
[    0.013223] mce: CPU supports 5 MCE banks
[    0.013290] using C1E aware idle routine
[    0.013349] Performance Counters: AMD PMU driver.
[    0.013455] ... version:                 0
[    0.013514] ... bit width:               48
[    0.013572] ... generic counters:        4
[    0.013631] ... value mask:              0000ffffffffffff
[    0.013692] ... max period:              00007fffffffffff
[    0.013752] ... fixed-purpose counters:  0
[    0.013810] ... counter mask:            000000000000000f
[    0.015524] ACPI: Core revision 20090521
[    0.025320] Setting APIC routing to flat
[    0.025837] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.125936] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 3600+ stepping 01
[    0.130000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 3817.71 BogoMIPS (lpj=19088564)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 5 MCE banks
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.280501] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 3600+ stepping 01
[    0.281192] Brought up 2 CPUs
[    0.281250] Total of 2 processors activated (7635.58 BogoMIPS).
[    0.281401] CPU0 attaching sched-domain:
[    0.281405]  domain 0: span 0-1 level MC
[    0.281408]   groups: 0 1
[    0.281413] CPU1 attaching sched-domain:
[    0.281415]  domain 0: span 0-1 level MC
[    0.281418]   groups: 1 0
[    0.281490] Booting paravirtualized kernel on bare hardware
[    0.281490] regulator: core version 0.5
[    0.281490] Time: 15:13:34  Date: 12/01/09
[    0.281490] NET: Registered protocol family 16
[    0.281490] node 0 link 0: io port [9000, ffff]
[    0.281490] TOM: 0000000080000000 aka 2048M
[    0.281490] node 0 link 0: mmio [a0000, bffff]
[    0.281490] node 0 link 0: mmio [80000000, efffffff]
[    0.281490] node 0 link 0: mmio [f4000000, fe02ffff]
[    0.281490] node 0 link 0: mmio [f0000000, f04fffff]
[    0.281490] bus: [00,04] on node 0 link 0
[    0.281490] bus: 00 index 0 io port: [0, ffff]
[    0.281490] bus: 00 index 1 mmio: [a0000, bffff]
[    0.281490] bus: 00 index 2 mmio: [80000000, f3ffffff]
[    0.281490] bus: 00 index 3 mmio: [f4000000, fcffffffff]
[    0.281490] ACPI: bus type pci registered
[    0.281490] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.281490] PCI: MCFG area at f0000000 reserved in E820
[    0.282311] PCI: Using MMCONFIG at f0000000 - f3ffffff
[    0.282373] PCI: Using configuration type 1 for base access
[    0.283256] bio: create slab <bio-0> at 0
[    0.283256] ACPI: EC: Look up EC in DSDT
[    0.294305] ACPI: Interpreter enabled
[    0.294368] ACPI: (supports S0 S1 S3 S4 S5)
[    0.294669] ACPI: Using IOAPIC for interrupt routing
[    0.304060] ACPI: No dock devices found.
[    0.305167] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.305449] pci 0000:00:01.1: reg 10 io port: [0xfc00-0xfc3f]
[    0.305460] pci 0000:00:01.1: reg 20 io port: [0x1c00-0x1c3f]
[    0.305465] pci 0000:00:01.1: reg 24 io port: [0xf400-0xf43f]
[    0.305484] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.305549] pci 0000:00:01.1: PME# disabled
[    0.305656] pci 0000:00:02.0: reg 10 32bit mmio: [0xfe02f000-0xfe02ffff]
[    0.305678] pci 0000:00:02.0: supports D1 D2
[    0.305680] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.308196] pci 0000:00:02.0: PME# disabled
[    0.308277] pci 0000:00:02.1: reg 10 32bit mmio: [0xfe02e000-0xfe02e0ff]
[    0.308303] pci 0000:00:02.1: supports D1 D2
[    0.308306] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.308369] pci 0000:00:02.1: PME# disabled
[    0.308489] pci 0000:00:05.0: reg 10 32bit mmio: [0xfe028000-0xfe02bfff]
[    0.308515] pci 0000:00:05.0: PME# supported from D3hot D3cold
[    0.308577] pci 0000:00:05.0: PME# disabled
[    0.308670] pci 0000:00:06.0: reg 20 io port: [0xf000-0xf00f]
[    0.308706] pci 0000:00:07.0: reg 10 32bit mmio: [0xfe02d000-0xfe02dfff]
[    0.308711] pci 0000:00:07.0: reg 14 io port: [0xec00-0xec07]
[    0.308733] pci 0000:00:07.0: supports D1 D2
[    0.308736] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.308800] pci 0000:00:07.0: PME# disabled
[    0.308882] pci 0000:00:08.0: reg 10 io port: [0x9f0-0x9f7]
[    0.308886] pci 0000:00:08.0: reg 14 io port: [0xbf0-0xbf3]
[    0.308890] pci 0000:00:08.0: reg 18 io port: [0x970-0x977]
[    0.308894] pci 0000:00:08.0: reg 1c io port: [0xb70-0xb73]
[    0.308898] pci 0000:00:08.0: reg 20 io port: [0xd800-0xd80f]
[    0.308903] pci 0000:00:08.0: reg 24 32bit mmio: [0xfe02c000-0xfe02cfff]
[    0.308952] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.309015] pci 0000:00:09.0: PME# disabled
[    0.309105] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.309168] pci 0000:00:0b.0: PME# disabled
[    0.309256] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.309320] pci 0000:00:0c.0: PME# disabled
[    0.309395] pci 0000:00:0d.0: reg 10 32bit mmio: [0xfb000000-0xfbffffff]
[    0.309401] pci 0000:00:0d.0: reg 14 64bit mmio: [0xe0000000-0xefffffff]
[    0.309407] pci 0000:00:0d.0: reg 1c 64bit mmio: [0xfc000000-0xfcffffff]
[    0.309412] pci 0000:00:0d.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.309532] pci 0000:01:06.0: reg 10 32bit mmio: [0xfdff8000-0xfdffffff]
[    0.309594] pci 0000:00:04.0: transparent bridge
[    0.309655] pci 0000:00:04.0: bridge io port: [0xc000-0xcfff]
[    0.309659] pci 0000:00:04.0: bridge 32bit mmio: [0xfdf00000-0xfdffffff]
[    0.309663] pci 0000:00:04.0: bridge 32bit mmio pref: [0xfd800000-0xfd8fffff]
[    0.309702] pci 0000:00:09.0: bridge io port: [0xb000-0xbfff]
[    0.309706] pci 0000:00:09.0: bridge 32bit mmio: [0xfde00000-0xfdefffff]
[    0.309710] pci 0000:00:09.0: bridge 64bit mmio pref: [0xfdd00000-0xfddfffff]
[    0.309749] pci 0000:00:0b.0: bridge io port: [0xa000-0xafff]
[    0.309752] pci 0000:00:0b.0: bridge 32bit mmio: [0xfdc00000-0xfdcfffff]
[    0.309756] pci 0000:00:0b.0: bridge 64bit mmio pref: [0xfdb00000-0xfdbfffff]
[    0.309795] pci 0000:00:0c.0: bridge io port: [0x9000-0x9fff]
[    0.309799] pci 0000:00:0c.0: bridge 32bit mmio: [0xfda00000-0xfdafffff]
[    0.309803] pci 0000:00:0c.0: bridge 64bit mmio pref: [0xfd900000-0xfd9fffff]
[    0.309816] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.310042] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.355347] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.356055] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 *10 11 14 15)
[    0.356661] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.357367] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.358069] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.358770] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.359472] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.360155] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.360859] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
[    0.361464] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.362166] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[    0.362772] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[    0.363381] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[    0.363985] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.364688] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[    0.365295] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
[    0.365900] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.366602] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.367205] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.367954] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.368434] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[    0.368868] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.369352] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.369831] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.370344] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.370825] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.371303] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.371782] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
[    0.372348] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.372914] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.373479] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.374090] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.374655] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.375232] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.375799] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.376411] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.377023] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.377589] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[    0.378195] SCSI subsystem initialized
[    0.378303] libata version 3.00 loaded.
[    0.378303] usbcore: registered new interface driver usbfs
[    0.378303] usbcore: registered new interface driver hub
[    0.378303] usbcore: registered new device driver usb
[    0.378303] ACPI: WMI: Mapper loaded
[    0.378303] PCI: Using ACPI for IRQ routing
[    0.400007] Bluetooth: Core ver 2.15
[    0.400082] NET: Registered protocol family 31
[    0.400082] Bluetooth: HCI device and connection manager initialized
[    0.400135] Bluetooth: HCI socket layer initialized
[    0.400195] NetLabel: Initializing
[    0.400253] NetLabel:  domain hash size = 128
[    0.400312] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.400388] NetLabel:  unlabeled traffic allowed by default
[    0.430014] pnp: PnP ACPI init
[    0.430096] ACPI: bus type pnp registered
[    0.436423] pnp: PnP ACPI: found 12 devices
[    0.436484] ACPI: ACPI bus type pnp unregistered
[    0.436552] system 00:01: ioport range 0x1000-0x107f has been reserved
[    0.436616] system 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.436679] system 00:01: ioport range 0x1400-0x147f has been reserved
[    0.436742] system 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.436805] system 00:01: ioport range 0x1800-0x187f has been reserved
[    0.436868] system 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.436931] system 00:01: ioport range 0x2000-0x207f has been reserved
[    0.436994] system 00:01: ioport range 0x2080-0x20ff has been reserved
[    0.437058] system 00:01: iomem range 0xfec80000-0xfecbffff has been reserved
[    0.437121] system 00:01: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    0.437185] system 00:01: iomem range 0xfefe1000-0xfefe10ff has been reserved
[    0.437249] system 00:01: iomem range 0x7c000000-0x7fffffff has been reserved
[    0.437316] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.437379] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.437441] system 00:02: ioport range 0x290-0x297 has been reserved
[    0.437508] system 00:0a: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.437575] system 00:0b: iomem range 0xf0000-0xfffff could not be reserved
[    0.437638] system 00:0b: iomem range 0xfeff0000-0xfeff00ff has been reserved
[    0.437702] system 00:0b: iomem range 0x7bee0000-0x7befffff could not be reserved
[    0.437776] system 00:0b: iomem range 0xffff0000-0xffffffff has been reserved
[    0.437839] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.437902] system 00:0b: iomem range 0x100000-0x7bedffff could not be reserved
[    0.437975] system 00:0b: iomem range 0x7bf00000-0x7fefffff could not be reserved
[    0.438049] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.438122] system 00:0b: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.438186] system 00:0b: iomem range 0xfefff000-0xfeffffff has been reserved
[    0.438251] system 00:0b: iomem range 0xfff80000-0xfff80fff has been reserved
[    0.438315] system 00:0b: iomem range 0xfff90000-0xfffbffff has been reserved
[    0.438379] system 00:0b: iomem range 0xfffed000-0xfffeffff has been reserved
[    0.443139] AppArmor: AppArmor Filesystem Enabled
[    0.443231] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
[    0.443294] pci 0000:00:04.0:   IO window: 0xc000-0xcfff
[    0.443357] pci 0000:00:04.0:   MEM window: 0xfdf00000-0xfdffffff
[    0.443420] pci 0000:00:04.0:   PREFETCH window: 0xfd800000-0xfd8fffff
[    0.443484] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
[    0.443546] pci 0000:00:09.0:   IO window: 0xb000-0xbfff
[    0.443608] pci 0000:00:09.0:   MEM window: 0xfde00000-0xfdefffff
[    0.443671] pci 0000:00:09.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
[    0.443745] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03
[    0.443807] pci 0000:00:0b.0:   IO window: 0xa000-0xafff
[    0.443868] pci 0000:00:0b.0:   MEM window: 0xfdc00000-0xfdcfffff
[    0.443931] pci 0000:00:0b.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
[    0.444005] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[    0.444067] pci 0000:00:0c.0:   IO window: 0x9000-0x9fff
[    0.444128] pci 0000:00:0c.0:   MEM window: 0xfda00000-0xfdafffff
[    0.444191] pci 0000:00:0c.0:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
[    0.444270] pci 0000:00:04.0: setting latency timer to 64
[    0.444276] pci 0000:00:09.0: setting latency timer to 64
[    0.444280] pci 0000:00:0b.0: setting latency timer to 64
[    0.444285] pci 0000:00:0c.0: setting latency timer to 64
[    0.444289] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.444292] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.444295] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.444298] pci_bus 0000:01: resource 1 mem: [0xfdf00000-0xfdffffff]
[    0.444301] pci_bus 0000:01: resource 2 pref mem [0xfd800000-0xfd8fffff]
[    0.444304] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.444307] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.444310] pci_bus 0000:02: resource 0 io:  [0xb000-0xbfff]
[    0.444313] pci_bus 0000:02: resource 1 mem: [0xfde00000-0xfdefffff]
[    0.444316] pci_bus 0000:02: resource 2 pref mem [0xfdd00000-0xfddfffff]
[    0.444319] pci_bus 0000:03: resource 0 io:  [0xa000-0xafff]
[    0.444322] pci_bus 0000:03: resource 1 mem: [0xfdc00000-0xfdcfffff]
[    0.444325] pci_bus 0000:03: resource 2 pref mem [0xfdb00000-0xfdbfffff]
[    0.444328] pci_bus 0000:04: resource 0 io:  [0x9000-0x9fff]
[    0.444331] pci_bus 0000:04: resource 1 mem: [0xfda00000-0xfdafffff]
[    0.444333] pci_bus 0000:04: resource 2 pref mem [0xfd900000-0xfd9fffff]
[    0.444373] NET: Registered protocol family 2
[    0.444580] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.445620] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.447717] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.448306] TCP: Hash tables configured (established 262144 bind 65536)
[    0.448370] TCP reno registered
[    0.448531] NET: Registered protocol family 1
[    0.448653] Trying to unpack rootfs image as initramfs...
[    0.450026] Switched to high resolution mode on CPU 0
[    0.450433] Switched to high resolution mode on CPU 1
[    0.627368] Freeing initrd memory: 6750k freed
[    0.631273] Scanning for low memory corruption every 60 seconds
[    0.631479] audit: initializing netlink socket (disabled)
[    0.631552] type=2000 audit(1259680414.630:1): initialized
[    0.641545] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.643185] VFS: Disk quotas dquot_6.5.2
[    0.643306] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.644063] fuse init (API version 7.12)
[    0.644208] msgmni has been set to 3888
[    0.644550] alg: No test for stdrng (krng)
[    0.644634] io scheduler noop registered
[    0.644693] io scheduler anticipatory registered
[    0.644752] io scheduler deadline registered
[    0.644860] io scheduler cfq registered (default)
[    0.660075] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.660185] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.660304] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.660423] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.660546] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.660673] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.660805] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.660871] pci 0000:00:0d.0: Boot video device
[    0.661021]   alloc irq_desc for 24 on node 0
[    0.661024]   alloc kstat_irqs on node 0
[    0.661032] pcieport-driver 0000:00:09.0: irq 24 for MSI/MSI-X
[    0.661038] pcieport-driver 0000:00:09.0: setting latency timer to 64
[    0.661148]   alloc irq_desc for 25 on node 0
[    0.661150]   alloc kstat_irqs on node 0
[    0.661156] pcieport-driver 0000:00:0b.0: irq 25 for MSI/MSI-X
[    0.661160] pcieport-driver 0000:00:0b.0: setting latency timer to 64
[    0.661266]   alloc irq_desc for 26 on node 0
[    0.661269]   alloc kstat_irqs on node 0
[    0.661274] pcieport-driver 0000:00:0c.0: irq 26 for MSI/MSI-X
[    0.661278] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    0.661350] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.661436] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.661639] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.661713] ACPI: Power Button [PWRF]
[    0.661821] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.661895] ACPI: Power Button [PWRB]
[    0.662020] fan PNP0C0B:00: registered as cooling_device0
[    0.662090] ACPI: Fan [FAN] (on)
[    0.662605] processor LNXCPU:00: registered as cooling_device1
[    0.662701] processor LNXCPU:01: registered as cooling_device2
[    0.668193] thermal LNXTHERM:01: registered as thermal_zone0
[    0.668261] ACPI: Thermal Zone [THRM] (21 C)
[    0.669507] Linux agpgart interface v0.103
[    0.669576] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.672215] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.672556] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.673618] brd: module loaded
[    0.674144] loop: module loaded
[    0.674282] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.674636] sata_nv 0000:00:08.0: version 3.5
[    0.675023] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    0.675088]   alloc irq_desc for 23 on node 0
[    0.675091]   alloc kstat_irqs on node 0
[    0.675102] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    0.675221] sata_nv 0000:00:08.0: setting latency timer to 64
[    0.675296] scsi0 : sata_nv
[    0.675468] scsi1 : sata_nv
[    0.675690] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 23
[    0.675754] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 23
[    0.675945] pata_amd 0000:00:06.0: version 0.4.1
[    0.675978] pata_amd 0000:00:06.0: setting latency timer to 64
[    0.676053] scsi2 : pata_amd
[    0.676162] scsi3 : pata_amd
[    0.676874] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.676938] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.677651] Fixed MDIO Bus: probed
[    0.677744] PPP generic driver version 2.4.2
[    0.677907] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.678335] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    0.678400]   alloc irq_desc for 22 on node 0
[    0.678402]   alloc kstat_irqs on node 0
[    0.678412] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
[    0.678500] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.678504] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.678615] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.678717] ehci_hcd 0000:00:02.1: debug port 1
[    0.678780] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.678801] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000
[    0.686228] ata1: SATA link down (SStatus 0 SControl 300)
[    0.690022] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.690167] usb usb1: configuration #1 chosen from 1 choice
[    0.690259] hub 1-0:1.0: USB hub found
[    0.690323] hub 1-0:1.0: 8 ports detected
[    0.690467] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.690946] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[    0.691010]   alloc irq_desc for 21 on node 0
[    0.691012]   alloc kstat_irqs on node 0
[    0.691022] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, low) -> IRQ 21
[    0.691110] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.691113] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.691219] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.691318] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfe02f000
[    0.752078] usb usb2: configuration #1 chosen from 1 choice
[    0.752168] hub 2-0:1.0: USB hub found
[    0.752235] hub 2-0:1.0: 8 ports detected
[    0.752356] uhci_hcd: USB Universal Host Controller Interface driver
[    0.752549] PNP: No PS/2 controller found. Probing ports directly.
[    0.752979] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.753045] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.753186] mice: PS/2 mouse device common for all mice
[    0.753346] rtc_cmos 00:04: RTC can wake from S4
[    0.753438] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.753532] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.753714] device-mapper: uevent: version 1.0.3
[    0.753874] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.754049] device-mapper: multipath: version 1.1.0 loaded
[    0.754111] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.754393] cpuidle: using governor ladder
[    0.754452] cpuidle: using governor menu
[    0.754962] TCP cubic registered
[    0.755156] NET: Registered protocol family 10
[    0.755675] lo: Disabled Privacy Extensions
[    0.756033] NET: Registered protocol family 17
[    0.756112] Bluetooth: L2CAP ver 2.13
[    0.756170] Bluetooth: L2CAP socket layer initialized
[    0.756232] Bluetooth: SCO (Voice Link) ver 0.6
[    0.756291] Bluetooth: SCO socket layer initialized
[    0.756388] Bluetooth: RFCOMM TTY layer initialized
[    0.756449] Bluetooth: RFCOMM socket layer initialized
[    0.756509] Bluetooth: RFCOMM ver 1.11
[    0.756592] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 3600+ processors (2 cpu cores) (version 2.20.00)
[    0.756722] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0xa
[    0.756783] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xb
[    0.756844] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[    0.757046] PM: Resume from disk failed.
[    0.757059] registered taskstats version 1
[    0.757244]   Magic number: 5:868:233
[    0.757403] rtc_cmos 00:04: setting system clock to 2009-12-01 15:13:35 UTC (1259680415)
[    0.757478] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.757539] EDD information not available.
[    0.842540] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.860329] ata3.00: ATAPI: _NEC DVD_RW ND-3550A, 1.05, max UDMA/33
[    0.860416] ata3: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:600:0x13)
[    0.897707] ata2.00: ATA-7: MAXTOR STM3320620AS, 3.AAE, max UDMA/133
[    0.897771] ata2.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.900287] ata3.00: configured for UDMA/33
[    0.981037] ata2.00: configured for UDMA/133
[    0.981201] scsi 1:0:0:0: Direct-Access     ATA      MAXTOR STM332062 3.AA PQ: 0 ANSI: 5
[    0.981404] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    0.981505] sd 1:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    0.981629] sd 1:0:0:0: [sda] Write Protect is off
[    0.981690] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.981714] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.981920]  sda:
[    0.982887] scsi 2:0:0:0: CD-ROM            _NEC     DVD_RW ND-3550A  1.05 PQ: 0 ANSI: 5
[    0.984445] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    0.984509] Uniform CD-ROM driver Revision: 3.20
[    0.984647] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    0.984691] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    0.984788] ata4: port disabled. ignoring.
[    1.020693]  sda1 sda3 < sda5 sda6 sda7 >
[    1.057883] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.057979] Freeing unused kernel memory: 660k freed
[    1.058369] Write protecting the kernel read-only data: 7584k
[    1.082549] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    1.295042] usb 1-6: configuration #1 chosen from 1 choice
[    1.312272] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.312769] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
[    1.312835]   alloc irq_desc for 20 on node 0
[    1.312837]   alloc kstat_irqs on node 0
[    1.312849] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 20 (level, low) -> IRQ 20
[    1.312925] forcedeth 0000:00:07.0: setting latency timer to 64
[    1.366841] FDC 0 is a post-1991 82077
[    1.371292] Initializing USB Mass Storage driver...
[    1.375191] scsi4 : SCSI emulation for USB Mass Storage devices
[    1.375589] usbcore: registered new interface driver usb-storage
[    1.375654] USB Mass Storage support registered.
[    1.376744] usb-storage: device found at 3
[    1.376748] usb-storage: waiting for device to settle before scanning
[    1.642527] usb 2-3: new low speed USB device using ohci_hcd and address 2
[    1.840835] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x50ef @ 1, addr 00:19:21:07:3a:7e
[    1.840914] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
[    1.871235] usb 2-3: configuration #1 chosen from 1 choice
[    1.880259] usbcore: registered new interface driver hiddev
[    1.886416] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input3
[    1.886563] generic-usb 0003:046D:C505.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:02.0-3/input0
[    1.897721] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.1/input/input4
[    1.897869] generic-usb 0003:046D:C505.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-3/input1
[    1.897963] usbcore: registered new interface driver usbhid
[    1.898028] usbhid: v2.6:USB HID core driver
[    2.045086] PM: Starting manual resume from disk
[    2.045151] PM: Resume from partition 8:7
[    2.045153] PM: Checking hibernation image.
[    2.045340] PM: Resume from disk failed.
[    2.053179] kjournald starting.  Commit interval 5 seconds
[    2.053252] EXT3-fs: mounted filesystem with writeback data mode.
[    2.975775] type=1505 audit(1259680417.712:2): operation="profile_load" pid=400 name=/usr/share/gdm/guest-session/Xsession
[    2.985910] type=1505 audit(1259680417.725:3): operation="profile_load" pid=401 name=/sbin/dhclient3
[    2.986298] type=1505 audit(1259680417.725:4): operation="profile_load" pid=401 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    2.986550] type=1505 audit(1259680417.725:5): operation="profile_load" pid=401 name=/usr/lib/connman/scripts/dhclient-script
[    3.019619] type=1505 audit(1259680417.755:6): operation="profile_load" pid=402 name=/usr/bin/evince
[    3.024880] type=1505 audit(1259680417.765:7): operation="profile_load" pid=402 name=/usr/bin/evince-previewer
[    3.028051] type=1505 audit(1259680417.765:8): operation="profile_load" pid=402 name=/usr/bin/evince-thumbnailer
[    3.060306] type=1505 audit(1259680417.795:9): operation="profile_load" pid=404 name=/usr/lib/cups/backend/cups-pdf
[    3.060772] type=1505 audit(1259680417.795:10): operation="profile_load" pid=404 name=/usr/sbin/cupsd
[    3.953401] Adding 1542204k swap on /dev/sda7.  Priority:-1 extents:1 across:1542204k 
[    5.989183] udev: starting version 147
[    6.372822] usb-storage: device scan complete
[    6.373906] scsi 4:0:0:0: Direct-Access     OCZ      DIESEL           PMAP PQ: 0 ANSI: 0 CCS
[    6.374313] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    6.376157] sd 4:0:0:0: [sdb] 15663104 512-byte logical blocks: (8.01 GB/7.46 GiB)
[    6.376650] sd 4:0:0:0: [sdb] Write Protect is off
[    6.376654] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    6.376656] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    6.378774] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    6.378841]  sdb: sdb1 sdb2
[    6.672301] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    6.672368] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    7.801486] EDAC MC: Ver: 2.1.0 Nov 10 2009
[    8.177574] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[    8.178573] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[    8.178597] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf400
[    8.218881] parport_pc 00:09: reported by Plug and Play ACPI
[    8.218943] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[    8.228478] EDAC amd64_edac:  Ver: 3.2.0 Nov 10 2009
[    8.229036] EDAC amd64: This node reports that Memory ECC is currently disabled.
[    8.229043] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[    8.229047] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[    8.229049]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[    8.229050]     Might be a BIOS bug, if BIOS says ECC is enabled
[    8.229051]     Use of the override can cause unknown side effects.
[    8.229079] amd64_edac: probe of 0000:00:18.2 failed with error -22
[    8.409141] ip_tables: (C) 2000-2006 Netfilter Core Team
[    8.511851] ppdev: user-space parallel port driver
[    8.587839] lp0: using parport0 (interrupt-driven).
[    8.702595] cfg80211: Calling CRDA to update world regulatory domain
[    9.525714] cfg80211: World regulatory domain updated:
[    9.525718] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.525722] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.525725] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.525728] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.525730] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.525733] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.896399] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[    9.896406]   alloc irq_desc for 17 on node 0
[    9.896408]   alloc kstat_irqs on node 0
[    9.896420] rt61pci 0000:01:06.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[    9.896426] rt61pci 0000:01:06.0: setting latency timer to 64
[   10.366338] phy0: Selected rate control algorithm 'minstrel'
[   10.367169] Registered led device: rt61pci-phy0::radio
[   10.367189] Registered led device: rt61pci-phy0::assoc
[   10.834326] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   10.834333] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 23 (level, low) -> IRQ 23
[   10.834363] HDA Intel 0000:00:05.0: setting latency timer to 64
[   12.151991] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:05.0/input/input5
[  118.376357] EXT3 FS on sda6, internal journal
[  118.453346] kjournald starting.  Commit interval 5 seconds
[  118.453543] EXT3 FS on sda5, internal journal
[  118.453548] EXT3-fs: mounted filesystem with writeback data mode.
[  119.909490] __ratelimit: 3 callbacks suppressed
[  119.909494] type=1505 audit(1259702134.645:12): operation="profile_replace" pid=919 name=/usr/share/gdm/guest-session/Xsession
[  119.911492] type=1505 audit(1259702134.645:13): operation="profile_replace" pid=920 name=/sbin/dhclient3
[  119.911807] type=1505 audit(1259702134.645:14): operation="profile_replace" pid=920 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[  119.911985] type=1505 audit(1259702134.645:15): operation="profile_replace" pid=920 name=/usr/lib/connman/scripts/dhclient-script
[  119.916909] type=1505 audit(1259702134.655:16): operation="profile_replace" pid=921 name=/usr/bin/evince
[  119.922025] type=1505 audit(1259702134.655:17): operation="profile_replace" pid=921 name=/usr/bin/evince-previewer
[  119.926351] type=1505 audit(1259702134.665:18): operation="profile_replace" pid=921 name=/usr/bin/evince-thumbnailer
[  119.932803] type=1505 audit(1259702134.675:19): operation="profile_replace" pid=925 name=/usr/lib/cups/backend/cups-pdf
[  119.933195] type=1505 audit(1259702134.675:20): operation="profile_replace" pid=925 name=/usr/sbin/cupsd
[  119.935453] type=1505 audit(1259702134.675:21): operation="profile_replace" pid=926 name=/usr/sbin/tcpdump
[  120.462708] rt61pci 0000:01:06.0: firmware: requesting rt2561s.bin
[  120.662951] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  120.665081]   alloc irq_desc for 27 on node 0
[  120.665085]   alloc kstat_irqs on node 0
[  120.665095] forcedeth 0000:00:07.0: irq 27 for MSI/MSI-X
[  120.665282] eth0: no link during initialization.
[  120.665918] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

Xorg.0.log:

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux Kris 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-15-generic root=UUID=155d64e8-60bd-446a-b2ae-5e2dae382f16 ro quiet splash
Build Date: 26 October 2009  05:19:56PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec  1 15:13:00 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
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
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0:0:13:0) 10de:03d1:1019:2602 nVidia Corporation C61 [GeForce 6100 nForce 405] rev 162, Mem @ 0xfb000000/16777216, 0xe0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
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
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(WW) Warning, couldn't open module freetype
(II) UnloadModule: "freetype"
(EE) Failed to load module "freetype" (module does not exist, 0)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 18:27:24 PDT 2009
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
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

```

kern.log is here:

[http://dl.dropbox.com/u/2214330/kern.txt](http://dl.dropbox.com/u/2214330/kern.txt)

I only copied the entries after I started using 2.6.31-15. I think the entires in the previous log of the 2.6.28-16 you saw before were from before I upgraded to 9.10.

If you see any obvious errors in these that I can fix, let me know, but otherwise I think I'm just going to do a reinstall. I was hoping to learn a few things by trying to fix this, but I don't really have this much time to spend on it. Even if I get this working, I still need to figure out why the latest kernel won't boot, and I was hoping to have everything finished before my school goes on break in a couple weeks.

Let me know if these logs have anything of interest, and if not, thanks for your help.

---

### Post by dozch on 2009-12-03
Hi,

Sorry, I can't see anything wrong except for the nvidia driver not loading...

---

