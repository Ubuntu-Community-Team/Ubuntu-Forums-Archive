---
title: "Getting nvidia drivers to work"
date: 2010-06-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Jordanwb on 2010-06-07
So early in the game I didn't expect a whole lot to break, but I was wrong yet again. Nouveau works to an extent but I can't use my two monitors side by side (as opposed to mirror) so I installed the nvidia drivers. I elevated to root and deleted /etc/X11/xorg.confg and ran nvidia-xconfig and rebooted. For some reason xorg cannot startup.

Here is /var/log/Xorg.0.log:

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux JORDAN-CD3CDA3B 2.6.34-5-generic #14-Ubuntu SMP Fri Jun 4 15:47:01 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.34-5-generic root=UUID=3884eb4e-f773-4180-8f73-e4578eb2b389 ro quiet splash
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.18.2
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jun  7 15:13:24 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0a20:3842:1226 nVidia Corporation GT216 [GeForce GT 220] rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
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
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 19:18:54 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
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
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) Jun 07 15:13:24 NVIDIA(0): Enabling RENDER acceleration
(II) Jun 07 15:13:24 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Jun 07 15:13:24 NVIDIA(0):     enabled.
(EE) Jun 07 15:13:24 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Jun 07 15:13:24 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Jun 07 15:13:24 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```

I'm going to try rebuilding the nvidia module.

*Edit*

Nope that didn't fix it.

I checked dmesg and the only thing involving nvidia is the following:

```
[    8.725696] nvidia: module license 'NVIDIA' taints kernel.
[    8.725701] Disabling lock debugging due to kernel taint
***snip***
[   10.990732] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.990742] nvidia 0000:01:00.0: setting latency timer to 64
```

Beware of the taint.

---

### Post by jfernyhough on 2010-06-07
First, remove xorg.conf completely, don't run nvidia-xconfig (it makes a messy config file). Reboot and you should be using the plain old nv driver (or vesa, or whatever).

Now go into Hardware Devices and active the nvidia driver.

Reboot.

That should get it.

---

### Post by Jordanwb on 2010-06-07
Okay I deleted /etc/X11/xorg.conf, rebooted and reinstalled the nvidia drivers which I am now using. However my monitor is set to 1280x1024 instead of 1440x900 and I can only use one of my two monitors.

For giggles I ran nvidia-xconfig and hit Alt+PrntScrn+K and it seems to be working.

---

### Post by jfernyhough on 2010-06-07
Do the Nvidia settings (System, Administration) work?

--edit
Good! Though I've no idea what you mean by ALT-PRNSCRN-K. I take it that's specific to your laptop model?

---

### Post by Jordanwb on 2010-06-07
> **jfernyhough said:**
> Do the Nvidia settings (System, Administration) work?

Yes if I run nvidia-xconfig

> **jfernyhough said:**
> --edit
Good! Though I've no idea what you mean by ALT-PRNSCRN-K. I take it that's specific to your laptop model?

No it works on my laptop, my desktop and my parent's machine. It forces Xorg to restart. I rebooted my computer and xorg is complaining again.

*Sigh*

---

### Post by an0dos on 2010-06-07
You should use "nvidia-settings" to set up twinview and select the proper resolution.

---

### Post by Jordanwb on 2010-06-07
> **an0dos said:**
> You should use "nvidia-settings" to set up twinview and select the proper resolution.

I did but then xorg won't startup because of the error listed in /var/log/Xorg.0.log which I posted in my opening post.

---

### Post by jfernyhough on 2010-06-07
So go back to the beginning and this time don't use nvidia-xconfig. It's designed for older versions of X. I never needed it for my dual screen setup, I just used nvidia-settings (as an0dos says), changed the TwinView settings, applied, and bingo - dual screen.

(I've just realised that Alt-PrntSrn is also Alt-SysRq which is a magic syskey combination. You shouldn't use those unless you have a real issue as they talk direct to the kernel and can seriously screw up your system. Just try an Alt-PrintScrn-B to force an immediate reboot)

---

### Post by Jordanwb on 2010-06-07
I deleted /etc/X11/xorg.conf, rebooted and ran nvidia-settings.  Nvidia-setting complaining that I'm not using the nvidia driver even though I am ("lspci -v" confirms this). What now?

---

### Post by jfernyhough on 2010-06-07
Check the nvidia drivers are activated in Hardware Drivers. If they are, deactivate them, reboot, and try to activate the,. Otherwise, activate them, then reboot.

It's a bit of a faff, yes, but for whatever reason there seem to be a number of things that have to be enabled (it was the same when I upgraded to my ATi laptop, took a few deactivation+activation before it finally kicked in and I got the drivers working correctly).

---

### Post by Jordanwb on 2010-06-07
I deactivated the drivers, deleted /etc/X11/xorg.conf, rebooted, activated the drivers, rebooted. The monitor is set to 1280x1024 with the right screen shut off.

I think I'll report this bug.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/590980](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/590980)

---

### Post by jfernyhough on 2010-06-07
Crikey, you're impatient.

Did you try nvidia-settings? (Under System, Administration)

---

### Post by Jordanwb on 2010-06-07
Yes and it says I'm not using the nvidia drivers despite already activating the drivers.

---

### Post by jfernyhough on 2010-06-07
Does Compiz work?

---

### Post by Jordanwb on 2010-06-07
> **jfernyhough said:**
> Does Compiz work?

It does not.

---

### Post by Mblackwell on 2010-06-07
Blacklist nouveau.

---

### Post by an0dos on 2010-06-07
What nvidia card do you have in your computer and what driver do you have enabled?

---

### Post by lukem on 2010-06-07
Thank you all.  I was having a problem with this new emachine with nvidia.  Brand new install and it worked well.  then I saw an icon at the top that said I was not using the nvidia drivers and did I want to.  So I followed through the screens and it went to low graphics mode.  I did it again through the preferences menu and it cleared up.  Tonight for no apparent reason it came up in low graphics mode again???  

I don't know enough to edit the config file, but I was able to delete it and reboot.  It came up low graphics again so I went to hardware drivers and removed ( that's what its called ) the nvidia driver that was being used.  Then rebooted and I'm back in 1440 mode again ( just one monitor here).  I shut down and restarted 3 more times and each time it is 1440.  I even ran some apps that I was using just before the problem started (gthumb).  
Thanks for being there
Luke

---

### Post by Jordanwb on 2010-06-07
> **Mblackwell said:**
> Blacklist nouveau.

I'll give it a try

> **an0dos said:**
> What nvidia card do you have in your computer and what driver do you have enabled?

GeForce GT220

*Edit*

Okay I blacklisted nouveau (why do I have a hard time spelling that?), and put "nvidia" in /etc/modules When Ubuntu boots the screen resolution is still 1280x1024. Running nvidia-setting complains I'm not using the NVidia drivers even though I am.

---

### Post by Jordanwb on 2010-06-09
I'll live with nouveau until the xorg package issue is fixed:

```
root@JORDAN-CD3CDA3B:/home/jordanwb# apt-get -s dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  xserver-xorg-input-all xserver-xorg-input-mouse xserver-xorg-input-vmmouse xserver-xorg-video-all xserver-xorg-video-ati
The following NEW packages will be installed:
  libx11-xcb1 libxcb-dri2-0
The following packages have been kept back:
  libglib2.0-data xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-synaptics xserver-xorg-video-cirrus xserver-xorg-video-mga xserver-xorg-video-nouveau
  xserver-xorg-video-nv xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-vesa
The following packages will be upgraded:
  xserver-xorg-video-intel
1 upgraded, 2 newly installed, 5 to remove and 11 not upgraded.
Remv xserver-xorg-input-all [1:7.5+5ubuntu1]
Remv xserver-xorg-input-vmmouse [1:12.6.5-4ubuntu2]
Remv xserver-xorg-input-mouse [1:1.5.0-1]
Remv xserver-xorg-video-all [1:7.5+5ubuntu1]
Remv xserver-xorg-video-ati [1:6.13.0-1ubuntu5]
Inst libx11-xcb1 (2:1.3.3-3ubuntu1 Ubuntu:10.10/maverick)
Inst libxcb-dri2-0 (1.6-1 Ubuntu:10.10/maverick)
Inst xserver-xorg-video-intel [2:2.9.1-3ubuntu5] (2:2.11.0-1ubuntu1 Ubuntu:10.10/maverick)
Conf libx11-xcb1 (2:1.3.3-3ubuntu1 Ubuntu:10.10/maverick)
Conf libxcb-dri2-0 (1.6-1 Ubuntu:10.10/maverick)
Conf xserver-xorg-video-intel (2:2.11.0-1ubuntu1 Ubuntu:10.10/maverick)
root@JORDAN-CD3CDA3B:/home/jordanwb#
```

---

### Post by clivejo on 2010-06-09
I think your problem is that the nouveau driver is getting to your graphics card first.

Hold down shift and enter the GRUB menu.  
Append 'nomodeset' as a kernel option.

eg. linux   /boot/vmlinuz-2.6.32-18-generic  root=UUID=fcf85719-2242-4b65-a162-a41060902f45 ro   quiet splash  nomodeset 

This should stop the nouveau driver loading and allow the nvidia driver to work.  

I personally use the lastest NVIDIA driver from their website, seems to work best.  However, I had to append nomodeset to allow it to work and have to re-install after any kernel changes.  But its all good having Compiz and 3D!

---

### Post by Jordanwb on 2010-06-09
> **clivejo said:**
> Hold down shift and enter the GRUB menu.  
Append 'nomodeset' as a kernel option.

YAY! It works!

---

### Post by ranch hand on 2010-06-09
You can add that to your /etc/default/grub file and have it there all the time.  I would also recommend, while you are there to comment out the "GRUB_HIDDEN_TIMEOUT=0" line on these "testing OS' so that the menu shows up all the time.

You may well need to boot to an earlier kernel or to recovery mode and this will save you the bother of the shift key.

---

### Post by ronacc on 2010-06-09
I always set my GRUB_HIDDEN_TIMEOUT=  to 10 to give me a chance to select a different boot option   if I need to enven on my "stable" sys , an extra 10 sec boot time is no great hardship .

---

### Post by Jordanwb on 2010-06-09
> **ranch hand said:**
> You can add that to your /etc/default/grub file and have it there all the time.  I would also recommend, while you are there to comment out the "GRUB_HIDDEN_TIMEOUT=0" line on these "testing OS' so that the menu shows up all the time.

You may well need to boot to an earlier kernel or to recovery mode and this will save you the bother of the shift key.

Already done.

> **ronacc said:**
> I always set my GRUB_HIDDEN_TIMEOUT=  to 10 to give me a chance to select a different boot option   if I need to enven on my "stable" sys , an extra 10 sec boot time is no great hardship .

Ubuntu does when when there are other OSes installed.

---

