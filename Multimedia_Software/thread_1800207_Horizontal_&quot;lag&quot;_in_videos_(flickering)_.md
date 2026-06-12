---
title: "Horizontal &quot;lag&quot; in videos (flickering?) probably compiz related"
date: 2011-07-08
forum: Multimedia Software
---

### Post by dragao-azul on 2011-07-08
Hey,

The best explanation I can get to my problem is in the title, I get some horizontal strips that I notice specially in videos (I use XBMC, full screen).

I had this problem before in 10.4 and I was able to solve it simply by choosing no effects on the old menu for the appearance.

Unfortunately I followed the mote that states "If it works fine in needs more features" and I installed 11.4, now I can't seem to solve this problem... In the loggin screen I have the default option has Ubuntu classic (no effects) and I installed compiz settings and disabled everything there, but I still have the problem.

I tried mint debian and I didn't have this problem there with everything off on the settings.

How can I get the same effect as that "old" 10.4 menu to disable compiz?

Any other suggestions?

Thanks.

---
My system:
Ubuntu 11.04
Acer revo R3610 (atom + ion)
4gb ram
(And I have the nvidia drivers installed)

---

### Post by dragao-azul on 2011-07-09
Small update: I tried installing the drivers directly from the nvidia site instead of letting ubuntu install them (version 275 vs 270) but now every time I restart the computer I have to reinstall the drivers or else gnome won't start.

Any idea why?
(I run nvidia-xconfig after installing the drivers)

The other problem persists.

Thanks

---

### Post by lidex on 2011-07-09
What is this output:
```
cat /var/log/Xorg.0.log | grep -C1 -E 'EE|WW'
```

Did you ever try 
```
metacity --replace
```
to kill compiz?

---

### Post by dragao-azul on 2011-07-10
> **lidex said:**
> What is this output:
```
cat /var/log/Xorg.0.log | grep -C1 -E 'EE|WW'
```

	```
(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   366.792] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul  9 16:34:41 2011
--
[   366.794] (==) Automatically enabling devices
[   366.795] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   366.795] 	Entry deleted from font path.
[   366.795] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   366.795] 	Entry deleted from font path.
[   366.795] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   366.795] 	Entry deleted from font path.
[   366.795] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   366.795] 	Entry deleted from font path.
[   366.795] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   366.795] 	Entry deleted from font path.
--
[   366.796] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   366.796] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   366.796] (WW) Disabling Keyboard0
[   366.796] (WW) Disabling Mouse0
[   366.796] (II) Loader magic: 0x81ffde0
--
[   366.802] 	ABI class: X.Org Server Extension, version 5.0
[   366.802] (II) Loading extension MIT-SCREEN-SAVER
[   366.802] (II) Loading extension XFree86-VidModeExtension

```
I don't know if by reinstalling the drivers the log was cleared or not.

> **lidex said:**
> Did you ever try 
```
metacity --replace
```
to kill compiz?
Right now I only have ssh access, I can only try it later, but I did install fusion-icon and enabled metacity and I had the same problems with XBMC, I can try it again though because I reinstalled ubuntu 2 days ago.

Thanks

---

### Post by dragao-azul on 2011-07-11
Here's that log after a new reboot and missing gnome again:

```

[   206.425] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   206.425] (WW) Disabling Keyboard0
[   206.425] (WW) Disabling Mouse0
[   206.425] (II) Loader magic: 0x81ffde0
--
[   206.432] 	ABI class: X.Org Server Extension, version 5.0
[   206.432] (II) Loading extension MIT-SCREEN-SAVER
[   206.432] (II) Loading extension XFree86-VidModeExtension
--
[   206.564] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   206.566] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
[   206.566] (EE) NVIDIA(0):     system's kernel log for additional error messages and
[   206.566] (EE) NVIDIA(0):     consult the NVIDIA README for details.
[   206.566] (EE) NVIDIA(0):  *** Aborting ***
[   206.566] (II) UnloadModule: "nvidia"
--
[   206.566] (II) Unloading fb
[   206.566] (EE) Screen(s) found, but none have a usable configuration.
[   206.566] 

```

Look's like it's more helpful this time.

---

### Post by Longshankss on 2011-08-23
I had the same problem,ith my fresh install of natty. lag and flicker..... HOWEVER, if you turn OFF sync to vblank inside xbmc, and leave them turned ON in the nvidea settings, the lag and flicker is gone and playback is smooooooth....!!!

Hope this will work for you :)

---

### Post by dragao-azul on 2011-09-02
I left the pc untouched on the holidays and I was just going to try and figure this out again, I'm glad to see I got a reply!

Thanks I'll check it! I'm having a bit of trouble with the nvidia drivers though, They don't start when I power up the pc, I have to reinstall them each time or I won't have a gui to work with.

Thanks ;)

---

### Post by lidex on 2011-09-02
> **dragao-azul said:**
> I left the pc untouched on the holidays and I was just going to try and figure this out again, I'm glad to see I got a reply!

Thanks I'll check it! I'm having a bit of trouble with the nvidia drivers though, They don't start when I power up the pc, I have to reinstall them each time or I won't have a gui to work with.

Thanks ;)

Try running this command to configure xorg.conf to load correct driver:
```
sudo nvidia-xconfig
```

---

### Post by dragao-azul on 2011-09-03
Don't you mean n**v**idia-xconfig?
If so I already run that command a few times, no success.

I tried removing the nvidia drivers and reinstall them but I think I broke something, unless I change to console (alt+ctrl+f4 for example) fast during boot the pc crashes with some wired lines on the screen. (and before gnome starts)

Anyway I tried re-installing the drivers again and I managed to go to into gnome as usual, I tried disabling vsync on xbmc and leave it on in the drivers but no luck. Leaving it on or off in both places also doesn't work.

And again, on reboot gnome doesn't start.

I think I'll make a clean install of ubuntu, how do you guys install the nvidia drivers without problems? Simply stop gnome and run the install script, which I did the first time, or is there any other "trick"?

I'll still have the xbmc problem, so I'm still searching for a solution on that one.

Thanks
;)

---

### Post by lidex on 2011-09-03
Yes, that's what I meant. Fixed.
How about this output:
```
cat /var/log/Xorg.0.log
```

---

### Post by dragao-azul on 2011-09-03
Here it is:

```
[    16.364] X.Org X Server 1.10.1
Release Date: 2011-04-15
[    16.365] X Protocol Version 11, Revision 0
[    16.365] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    16.365] Current Operating System: Linux acer 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686
[    16.365] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=9ff85e4e-d6f7-4b58-ac07-f8ddcfe0ac12 ro quiet splash vt.handoff=7
[    16.365] Build Date: 21 May 2011  11:38:35AM
[    16.365] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    16.365] Current version of pixman: 0.20.2
[    16.365]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    16.366] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.366] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Sep  3 01:06:39 2011
[    16.367] (==) Using config file: "/etc/X11/xorg.conf"
[    16.367] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    16.369] (==) ServerLayout "Layout0"
[    16.369] (**) |-->Screen "Screen0" (0)
[    16.369] (**) |   |-->Monitor "Monitor0"
[    16.370] (**) |   |-->Device "Device0"
[    16.370] (**) |-->Input Device "Keyboard0"
[    16.370] (**) |-->Input Device "Mouse0"
[    16.370] (==) Automatically adding devices
[    16.370] (==) Automatically enabling devices
[    16.392] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.392]     Entry deleted from font path.
[    16.392] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    16.392]     Entry deleted from font path.
[    16.392] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    16.392]     Entry deleted from font path.
[    16.402] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    16.402]     Entry deleted from font path.
[    16.402] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    16.402]     Entry deleted from font path.
[    16.416] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    16.416] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    16.416] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    16.416] (WW) Disabling Keyboard0
[    16.416] (WW) Disabling Mouse0
[    16.416] (II) Loader magic: 0x81ffde0
[    16.416] (II) Module ABI versions:
[    16.416]     X.Org ANSI C Emulation: 0.4
[    16.417]     X.Org Video Driver: 10.0
[    16.417]     X.Org XInput driver : 12.3
[    16.417]     X.Org Server Extension : 5.0
[    16.420] (--) PCI:*(0:3:0:0) 10de:087d:1025:0222 rev 177, Mem @ 0xfb000000/16777216, 0xe0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/131072
[    16.421] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    16.421] (II) LoadModule: "extmod"
[    16.505] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    16.506] (II) Module extmod: vendor="X.Org Foundation"
[    16.506]     compiled for 1.10.1, module version = 1.0.0
[    16.506]     Module class: X.Org Server Extension
[    16.506]     ABI class: X.Org Server Extension, version 5.0
[    16.506] (II) Loading extension MIT-SCREEN-SAVER
[    16.506] (II) Loading extension XFree86-VidModeExtension
[    16.506] (II) Loading extension XFree86-DGA
[    16.506] (II) Loading extension DPMS
[    16.506] (II) Loading extension XVideo
[    16.506] (II) Loading extension XVideo-MotionCompensation
[    16.506] (II) Loading extension X-Resource
[    16.507] (II) LoadModule: "dbe"
[    16.508] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    16.509] (II) Module dbe: vendor="X.Org Foundation"
[    16.509]     compiled for 1.10.1, module version = 1.0.0
[    16.509]     Module class: X.Org Server Extension
[    16.509]     ABI class: X.Org Server Extension, version 5.0
[    16.509] (II) Loading extension DOUBLE-BUFFER
[    16.509] (II) LoadModule: "glx"
[    16.511] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    16.568] (II) Module glx: vendor="NVIDIA Corporation"
[    16.568]     compiled for 4.0.2, module version = 1.0.0
[    16.568]     Module class: X.Org Server Extension
[    16.568] (II) NVIDIA GLX Module  275.09.07  Wed Jun  8 16:01:21 PDT 2011
[    16.569] (II) Loading extension GLX
[    16.569] (II) LoadModule: "record"
[    16.570] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    16.570] (II) Module record: vendor="X.Org Foundation"
[    16.570]     compiled for 1.10.1, module version = 1.13.0
[    16.570]     Module class: X.Org Server Extension
[    16.570]     ABI class: X.Org Server Extension, version 5.0
[    16.570] (II) Loading extension RECORD
[    16.570] (II) LoadModule: "dri"
[    16.571] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    16.572] (II) Module dri: vendor="X.Org Foundation"
[    16.572]     compiled for 1.10.1, module version = 1.0.0
[    16.572]     ABI class: X.Org Server Extension, version 5.0
[    16.572] (II) Loading extension XFree86-DRI
[    16.572] (II) LoadModule: "dri2"
[    16.573] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    16.574] (II) Module dri2: vendor="X.Org Foundation"
[    16.574]     compiled for 1.10.1, module version = 1.2.0
[    16.574]     ABI class: X.Org Server Extension, version 5.0
[    16.574] (II) Loading extension DRI2
[    16.574] (II) LoadModule: "nvidia"
[    16.574] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    16.575] (II) Module nvidia: vendor="NVIDIA Corporation"
[    16.575]     compiled for 4.0.2, module version = 1.0.0
[    16.576]     Module class: X.Org Video Driver
[    16.576] (II) NVIDIA dlloader X Driver  275.09.07  Wed Jun  8 15:43:48 PDT 2011
[    16.576] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    16.576] (++) using VT number 7


[    16.577] (II) Loading sub module "fb"
[    16.577] (II) LoadModule: "fb"
[    16.578] (II) Loading /usr/lib/xorg/modules/libfb.so
[    16.578] (II) Module fb: vendor="X.Org Foundation"
[    16.578]     compiled for 1.10.1, module version = 1.0.0
[    16.578]     ABI class: X.Org ANSI C Emulation, version 0.4
[    16.578] (II) Loading sub module "wfb"
[    16.579] (II) LoadModule: "wfb"
[    16.580] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    16.580] (II) Module wfb: vendor="X.Org Foundation"
[    16.580]     compiled for 1.10.1, module version = 1.0.0
[    16.580]     ABI class: X.Org ANSI C Emulation, version 0.4
[    16.580] (II) Loading sub module "ramdac"
[    16.580] (II) LoadModule: "ramdac"
[    16.581] (II) Module "ramdac" already built-in
[    16.581] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    16.581] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    16.581] (II) Loading /usr/lib/xorg/modules/libfb.so
[    16.581] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    16.581] (==) NVIDIA(0): RGB weight 888
[    16.581] (==) NVIDIA(0): Default visual is TrueColor
[    16.581] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    16.583] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
[    16.583] (EE) NVIDIA(0):     system's kernel log for additional error messages and
[    16.583] (EE) NVIDIA(0):     consult the NVIDIA README for details.
[    16.583] (EE) NVIDIA(0):  *** Aborting ***
[    16.583] (II) UnloadModule: "nvidia"
[    16.583] (II) Unloading nvidia
[    16.583] (II) UnloadModule: "wfb"
[    16.583] (II) Unloading wfb
[    16.583] (II) UnloadModule: "fb"
[    16.583] (II) Unloading fb
[    16.583] (EE) Screen(s) found, but none have a usable configuration.
[    16.583] 
Fatal server error:
[    16.583] no screens found
[    16.584] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    16.584] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    16.584] 
[    16.636]  ddxSigGiveUp: Closing log
```

Here are the commands I run before the situation got worst:
- Apt-get remove nvidia-*
- dpkg-reconfigure xserver-xorg

---

### Post by lidex on 2011-09-04
Now this output please:
```
sudo lshw -C display

```

---

### Post by dragao-azul on 2011-09-04
I managed to get the network up and renning in the recovery mode and I'm trying to reinstall the drivers from the repositories.

Here is that output (handcopied):
description: VGA compatible conroller
product: ion vga
cendor: nvidia
physical id: 0
bus info:  pci@000:03:00.0
version: b1
width: 64bits
clock: 33mhz
capabilities pm msi vga_controller bus:master cap_list rom
configuration: driver=nouveau latency=0      (I see the wrong driver here)
resources: (ask if needed xD)

;)

PS - If the problem gets fixed with this new driver installation I'll let you know.

---

### Post by dragao-azul on 2011-09-04
Solved! Well it installed the 270 drivers instead of the 280, but it's working!

I also solved the video problem adding
```
Section "Extensions"
  Option "Composite" "Disable"
EndSection
```
to Xorg.conf

Thanks for the help.

;)

---

### Post by lidex on 2011-09-18
> **dragao-azul said:**
> Solved! Well it installed the 270 drivers instead of the 280, but it's working!

I also solved the video problem adding
```
Section "Extensions"
  Option "Composite" "Disable"
EndSection
```
to Xorg.conf

Thanks for the help.

;)
Thanks for posting your fix ;)

---

