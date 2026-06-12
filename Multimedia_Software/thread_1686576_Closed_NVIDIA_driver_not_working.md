---
title: "Closed NVIDIA driver not working"
date: 2011-02-12
forum: Multimedia Software
---

### Post by nbjensen on 2011-02-12
Hi, I'm trying to get a fresh install of Ubuntu 10.10 working with the closed Nvidia driver, as I would like to get the HDMI output working. 

I have a Sony Vaio VPCCW18FX, with a Nvidia GT 230M graphics card. The open source nouveau driver works fine, but does not run smoothly. The only problem here is that it's needed to run with "nomodeset".

If i just activate the Proprietary Nvidia driver and reboot, it will hang after writing "Checking battery State [ok]". I have tried to add EDID from Windows partition, and here it hangs at a blank black/grey screen. I have tried hooking up an external display, no output on it either.

Can you help me? :)

Thank you very much!

---

### Post by BicyclerBoy on 2011-02-12
The nomodeset option is to stop any kernel video driver modules from changing the video modes for splash & console framebuffer.
Nvidia binary driver does not load before the Xorg starts.
Nouveau has a kernel module that does load unless "nomodeset". AFAIK this is part of the problem.

For some people/hardware the nomodeset is required to be able to use nvidia drivers.
Normally the nouveau driver must be blacklisted.

Are you sure the nomodeset is permanently set ?
Check/reapply at GRUB boot screen.
Have you blacklisted the nouveau driver ? 

Remove your EDID hacks..
reboot
Post your /var/log/Xorg.0.log..

---

### Post by nbjensen on 2011-02-12
I am reapplying nomodeset verytime in GRUB.

I have removed the nouveau driver, and have now blacklisted it by adding blacklist nouveau in /etc/modprobe.d/blacklist.conf. Is this the correct method?

As the system gets stock during bootup: I booted it up normally. Rebooted when it got stuck and entered failsafex recovery mode, where the log file was extracted. Hope this is a correct method.

The content of my /var/log/Xorg.0.log
```

[    15.486] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    15.487] X Protocol Version 11, Revision 0
[    15.487] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    15.487] Current Operating System: Linux nicklas-VPCCW18FX 2.6.35-25-generic-pae #44-Ubuntu SMP Fri Jan 21 19:01:46 UTC 2011 i686
[    15.487] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=23a28cf3-b996-4952-84f6-3ae101f09a4f ro vga=792 nomodeset
[    15.487] Build Date: 16 September 2010  05:39:22PM
[    15.487] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    15.487] Current version of pixman: 0.18.4
[    15.487] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    15.487] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.487] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Feb 12 23:26:21 2011
[    15.487] (==) Using config file: "/etc/X11/xorg.conf"
[    15.487] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.499] (==) ServerLayout "Layout0"
[    15.499] (**) |-->Screen "Screen0" (0)
[    15.499] (**) |   |-->Monitor "Monitor0"
[    15.500] (**) |   |-->Device "Device0"
[    15.500] (**) |-->Input Device "Keyboard0"
[    15.500] (**) |-->Input Device "Mouse0"
[    15.500] (==) Automatically adding devices
[    15.500] (==) Automatically enabling devices
[    15.500] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.500] 	Entry deleted from font path.
[    15.500] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    15.500] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.500] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    15.500] (WW) Disabling Keyboard0
[    15.500] (WW) Disabling Mouse0
[    15.500] (II) Loader magic: 0x81f8e00
[    15.500] (II) Module ABI versions:
[    15.500] 	X.Org ANSI C Emulation: 0.4
[    15.500] 	X.Org Video Driver: 8.0
[    15.500] 	X.Org XInput driver : 11.0
[    15.500] 	X.Org Server Extension : 4.0
[    15.501] (--) PCI:*(0:1:0:0) 10de:0a2a:104d:905e rev 162, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000d000/128, BIOS @ 0x????????/524288
[    15.502] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    15.502] (II) LoadModule: "extmod"
[    15.510] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    15.510] (II) Module extmod: vendor="X.Org Foundation"
[    15.510] 	compiled for 1.9.0, module version = 1.0.0
[    15.510] 	Module class: X.Org Server Extension
[    15.510] 	ABI class: X.Org Server Extension, version 4.0
[    15.510] (II) Loading extension MIT-SCREEN-SAVER
[    15.510] (II) Loading extension XFree86-VidModeExtension
[    15.510] (II) Loading extension XFree86-DGA
[    15.510] (II) Loading extension DPMS
[    15.510] (II) Loading extension XVideo
[    15.510] (II) Loading extension XVideo-MotionCompensation
[    15.510] (II) Loading extension X-Resource
[    15.510] (II) LoadModule: "dbe"
[    15.511] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    15.511] (II) Module dbe: vendor="X.Org Foundation"
[    15.511] 	compiled for 1.9.0, module version = 1.0.0
[    15.511] 	Module class: X.Org Server Extension
[    15.511] 	ABI class: X.Org Server Extension, version 4.0
[    15.511] (II) Loading extension DOUBLE-BUFFER
[    15.511] (II) LoadModule: "glx"
[    15.511] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    17.105] (II) Module glx: vendor="NVIDIA Corporation"
[    17.105] 	compiled for 4.0.2, module version = 1.0.0
[    17.105] 	Module class: X.Org Server Extensi

```

Thank you very much.

---

### Post by BicyclerBoy on 2011-02-13
The original nouveau blacklisting involved blacklisted 3 or 4 devices in 2 files...but that was 18 months ago..

The Xorg.0.log seems okay (blacklisting)  as far as can be seen..
Can you attach the whole file ?
Search the file for lines containing nouveau: cat /var/log/Xorg.0.log | grep nouveau

---

### Post by nbjensen on 2011-02-14
The command returns nothing.

I have attached the whole file. 

Should note that i have done as recommended by [BinaryDriverHowto]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") and run the command:

sudo apt-get --purge remove xserver-xorg-video-nouveau

Thank you very much for your help.

---

### Post by BicyclerBoy on 2011-02-14
Looks like X server crashes after loading the glx module..

Why do you use this ..  vga=792 ?
Just to get the right console video mode ?
Maybe this loads a framebuffer driver that interferes with X server..
This method (vga=792) is out-dated with Grub2.
GRUB2 method is editing /etc/default/grub as the following sample:  GRUB_GFXMODE=1024x768x32
I would try removing vga=792 & commenting out/deleting any modules section in the /etc/X11/xorg.conf file..

---

### Post by nbjensen on 2011-02-15
Hmm, ok. The vga=792 is not something i have added. It was there from the beginning i guess.

I have tried removing it, and now it is not hanging on Checking battery state [ok], but get past this and hangs at a black/gray screen.

I'm not sure about /etc/X11/xorg.conf. I have attached the file, how would you change it?

Thank you very much.

---

### Post by BicyclerBoy on 2011-02-15
logs show still Xserver crashing/stopping when glx module is loaded..

When your computer stops at grey screen  (X server stops) can you flick to a console login screen ? <ctrl><alt><F2>.

Can only suggest try a more recent nvidia driver, 260.19.29 is reported to be better than the version you are using.

You can find a 3rd party ppa pre-compiled nvidia driver if you search hard enough..

You are using a 32 bit pae kernel version ? is that a normal install ?
If you are felling very adventurous you could try the latest nvidia driver installer from nvidia..note you need compiling tools & kernel headers packages.

---

### Post by BicyclerBoy on 2011-02-16
This laptop is not another optimus thing is it ?

Are there BIOS options for integrated GPU only & discrete GPU only ??

Just found that this is a core2duo CPU so definitely not optimus...

---

### Post by nbjensen on 2011-02-17
Cannot flick to a console login screen ? <ctrl><alt><F2>. Nothing happens.

Do you know a nice tutorial or guide for installing latest nvidia drivers? Or another Linux distro where the drivers probably work? Like Debian?

Thank you very much for all your help :)

---

### Post by realzippy on 2011-02-17
Have a look [here]("http://ubuntuforums.org/showthread.php?t=1369420"),maybe it is this vaio-edid issue.
Your xorg.conf looks fine.

**EDIT**:
Sorry,overread that you already tried to feed an "edid" file.
Have you done this correctly?Rename file to ".bin" and edit xorg.conf?

---

### Post by nbjensen on 2011-02-17
Yes, have followed the guide closely on the edid-issue.

Also they get output on VGA, I do not get any output..

Thank you very much.

---

### Post by nbjensen on 2011-02-17
Installed newest driver from nvidia.com, everything went well, and now it WORKS :D

Thank you very much for your help!

---

### Post by realzippy on 2011-02-18
Fine;please set thread as solved (ThreadTools)..

Only new driver (which?) or 
feeded EDID file + new driver?

---

### Post by nbjensen on 2011-02-18
Installed 260.19.36.

Edid not needed.

Thank you :)

---

