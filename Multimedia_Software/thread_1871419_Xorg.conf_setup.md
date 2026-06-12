---
title: "Xorg.conf setup"
date: 2011-10-28
forum: Multimedia Software
---

### Post by 01001101 on 2011-10-28
Hey, I'm trying to set up my graphics card to work with my computer. Right now it recognizes my board graphics only, and I want to use the card. I installed Nvidia's software drivers, but it still uses the board graphics because I don't have a xorg.conf file. So, I wanted to create one for my computer, and I didn't quite know how to do that. After looking around for a bit I found that the Nvidia drivers came with an application that configures your xorg.conf file for you under administration -> Nvidia Xserver settings.

When I start that application, it comes up with a window that says, "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." I'm assuming that if I want the application I need to do this.

So, I open up terminal and run nvidia-xconfig. One time I restarted X server and the other time I restarted my computer. Both times it brought me to a non-gui screen that looks as if it is Ubuntu console edition. The difference is I can't do anything in it. When I type a command nothing happens. I've had to reinstall my OS twice because of this, and I still can't get the proper graphics settings to work. Can you help?

---

### Post by BicyclerBoy on 2011-10-29
Optimus graphics ?

You don't give many clues..

---

### Post by 01001101 on 2011-10-30
The graphics card is an Nvidia Quadro FX580 workstation card from PNY, if that helps.

---

### Post by BicyclerBoy on 2011-10-30
Have you set the BIOS to boot the PEG graphics first (before PCI) ?

You run X server configuration tool:
sudo nvidia-xconfig

You then logout/login or reboot...

If you end up with no X server or console then you can login with username & password..

The plymouth/login/greeter GUI does not use the nVidia driver but a universal framebuffer driver.

The file :
/var/log/Xorg.0.log
will contain the clues to why it failed for that session...

The xorg.conf file is located in 
/etc/X11/xorg.conf
Just delete/rename if it all goes bad..you do not have to re-install.

Normally you get warnings about low res & safe mode..

---

### Post by 01001101 on 2011-10-31
So, I redid nvidia-xconfig and the same thing happened. When I typed the command into the console I noticed that I got this error:

```
VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
Device section "Default Device" must have a Driver line.
```

Anyway, I booted my computer under safe mode and recovered Xorg.0.log. This is what's on it:


```
[    22.153] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    22.153] X Protocol Version 11, Revision 0
[    22.153] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    22.153] Current Operating System: Linux ubuntu-m 2.6.38-12-generic-pae #51-Ubuntu SMP Wed Sep 28 16:11:32 UTC 2011 i686
[    22.153] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-12-generic-pae root=UUID=91faa052-0458-49d9-85b6-05de462685c3 ro quiet splash vt.handoff=7
[    22.153] Build Date: 13 October 2011  05:38:22PM
[    22.153] xorg-server 2:1.10.1-1ubuntu1.3 (For technical support please see http://www.ubuntu.com/support) 
[    22.153] Current version of pixman: 0.20.2
[    22.153] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    22.153] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.153] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 31 20:22:06 2011
[    22.154] (==) Using config file: "/etc/X11/xorg.conf"
[    22.154] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.154] (==) ServerLayout "Layout0"
[    22.154] (**) |-->Screen "Screen0" (0)
[    22.154] (**) |   |-->Monitor "Monitor0"
[    22.154] (**) |   |-->Device "Device0"
[    22.154] (**) |-->Input Device "Keyboard0"
[    22.154] (**) |-->Input Device "Mouse0"
[    22.154] (==) Automatically adding devices
[    22.154] (==) Automatically enabling devices
[    22.154] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.154] 	Entry deleted from font path.
[    22.154] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    22.154] 	Entry deleted from font path.
[    22.154] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    22.154] 	Entry deleted from font path.
[    22.154] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    22.154] 	Entry deleted from font path.
[    22.154] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    22.154] 	Entry deleted from font path.
[    22.154] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    22.154] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.154] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    22.154] (WW) Disabling Keyboard0
[    22.154] (WW) Disabling Mouse0
[    22.154] (II) Loader magic: 0x8200ac0
[    22.154] (II) Module ABI versions:
[    22.154] 	X.Org ANSI C Emulation: 0.4
[    22.154] 	X.Org Video Driver: 10.0
[    22.154] 	X.Org XInput driver : 12.3
[    22.154] 	X.Org Server Extension : 5.0
[    22.155] (--) PCI:*(0:1:5:0) 1002:9616:1462:7501 rev 0, Mem @ 0xb0000000/268435456, 0xf9ff0000/65536, 0xf9e00000/1048576, I/O @ 0x0000c000/256
[    22.155] (--) PCI: (0:2:0:0) 10de:0659:10de:063a rev 161, Mem @ 0xfd000000/16777216, 0xc0000000/536870912, 0xfa000000/33554432, I/O @ 0x0000d800/128, BIOS @ 0x????????/524288
[    22.155] (II) Open ACPI successful (/var/run/acpid.socket)
[    22.155] (II) LoadModule: "extmod"
[    22.169] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    22.169] (II) Module extmod: vendor="X.Org Foundation"
[    22.169] 	compiled for 1.10.1, module version = 1.0.0
[    22.169] 	Module class: X.Org Server Extension
[    22.169] 	ABI class: X.Org Server Extension, version 5.0
[    22.169] (II) Loading extension MIT-SCREEN-SAVER
[    22.169] (II) Loading extension XFree86-VidModeExtension
[    22.169] (II) Loading extension XFree86-DGA
[    22.169] (II) Loading extension DPMS
[    22.169] (II) Loading extension XVideo
[    22.169] (II) Loading extension XVideo-MotionCompensation
[    22.169] (II) Loading extension X-Resource
[    22.169] (II) LoadModule: "dbe"
[    22.169] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    22.169] (II) Module dbe: vendor="X.Org Foundation"
[    22.169] 	compiled for 1.10.1, module version = 1.0.0
[    22.169] 	Module class: X.Org Server Extension
[    22.169] 	ABI class: X.Org Server Extension, version 5.0
[    22.169] (II) Loading extension DOUBLE-BUFFER
[    22.169] (II) LoadModule: "glx"
[    22.169] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    23.597] (II) Module glx: vendor="NVIDIA Corporation"
[    23.598] 	compiled for 4.0.2, module version = 1.0.0
[    23.598] 	Module class: X.Org Server Extension
[    23.598] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[    23.598] (II) Loading extension GLX
[    23.598] (II) LoadModule: "record"
[    23.598] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    23.598] (II) Module record: vendor="X.Org Foundation"
[    23.598] 	compiled for 1.10.1, module version = 1.13.0
[    23.598] 	Module class: X.Org Server Extension
[    23.598] 	ABI class: X.Org Server Extension, version 5.0
[    23.598] (II) Loading extension RECORD
[    23.598] (II) LoadModule: "dri"
[    23.598] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    23.598] (II) Module dri: vendor="X.Org Foundation"
[    23.598] 	compiled for 1.10.1, module version = 1.0.0
[    23.598] 	ABI class: X.Org Server Extension, version 5.0
[    23.598] (II) Loading extension XFree86-DRI
[    23.598] (II) LoadModule: "dri2"
[    23.598] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    23.598] (II) Module dri2: vendor="X.Org Foundation"
[    23.598] 	compiled for 1.10.1, module version = 1.2.0
[    23.598] 	ABI class: X.Org Server Extension, version 5.0
[    23.598] (II) Loading extension DRI2
[    23.598] (II) LoadModule: "nvidia"
[    23.598] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    23.636] (II) Module nvidia: vendor="NVIDIA Corporation"
[    23.636] 	compiled for 4.0.2, module version = 1.0.0
[    23.636] 	Module class: X.Org Video Driver
[    23.673] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:51 PDT 2011
[    23.677] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    23.678] (++) using VT number 7

[    23.678] (EE) No devices detected.
[    23.678] 
Fatal server error:
[    23.678] no screens found
[    23.678] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    23.678] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    23.678] 
```

Thanks for your help with this.

---

### Post by BicyclerBoy on 2011-11-01
Looks to me that you have the display plugged into the mobo jacks & not the video card..
Seems you have no display detected (by nVidia driver).

Once only you have to use:
sudo nvidia-xconfig

From terminal or menus:
nvidia-settings  (no sudo)


Is this h/w a laptop with iCPU (i3,i5, i7) or AMD APU fusion ?

---

### Post by 01001101 on 2011-11-01
Ok, I'll try that. I'm using an AMD Phenom II and its not a laptop. I do have the monitor plugged into the board using a VGA cable so that I can view the BIOS menu, but I also have a DVI cable hooked into my graphics card. What I want is for xorg to use the graphics card and the DVI output rather than the VGA output.

---

### Post by 01001101 on 2011-11-01
I tried nvidia-xconfig again but it just did the same thing with the console that can't accept input. What am I supposed to do in the nvidia xserver settings window? It still has the message that says, "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

---

### Post by BicyclerBoy on 2011-11-01
The BIOS should POST on the graphics card..
The video card firmware must provide a text mode & basic VGA compatible video mode support for POST.

The kernel uses a framebuffer driver until the X server starts..

I assume you are multiplexing the 2 cables using the cable switch in the monitor.
Your monitor must not be providing any load on the cable (or EDID) when it is switched to the other cable... that's a bit odd.

---

### Post by 01001101 on 2011-11-02
Yes, that's correct. I'm sorry, but I'm not very good when it comes to graphics information. I fixed this problem before by downloading the nvidia drivers then using its xserver utility to tell xorg.conf that it needs to use my graphics card, not the VGA cable from the board. It worked under ubuntu 10.04, but under ubuntu 11.10 I get the error message "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." when I open the utility.

---

### Post by BicyclerBoy on 2011-11-02
Unplug the VGA cable..
You can force the DVI output on (nVidia card) but you just need it to be detected..remove the VGA from the monitor..

You must run nvidia-xconfig as root (needs root priviledges to write xorg.conf)

Another alternative is to delete /etc/X11/xorg.conf file.

---

