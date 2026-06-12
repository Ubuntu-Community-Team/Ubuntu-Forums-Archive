---
title: "NVidia support for xserver 1.10 rc2 is here!"
date: 2011-02-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-02-25
You can now fully upgrade your Natty xserver 1.10 series to the latest rc2 version (1.9.99.902-2ubuntu1).
And here is the NVidia proprietary drivers that supports xserver 1.10.
Believe me, it works.

Here (X updates):
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

You better add the "X Updates" PPA into your sources.list, because this new nvidia-current depends on the virtual package xserver-video-abi-9.
This means it depends on xserver 1.10 series (must be installed at the same time), and cannot be installed at all with the old xserver 1.9 series.

You can also download the packages nvidia-current and nvidia-settings from X Updates PPA.
Then first upgrade the your xserver to 1.10 series.
Then in terminal install nvidia packages with sudo dpkg -i package1 package2.

The version of the new NVidia driver is 270.29.

---

### Post by Yofel on 2011-02-25
For those that are interested, the link to the release announcement:

[http://www.nvnews.net/vbulletin/showthread.php?t=159990](http://www.nvnews.net/vbulletin/showthread.php?t=159990)

---

### Post by rburkartjo on 2011-02-25
tks for the heads up

---

### Post by cucisan on 2011-02-25
yihaa finally.. thx for mentioning it!

---

### Post by ronacc on 2011-02-25
do I also need to add xorg-edgers ppa to get the 1.10 rc2 xserver ?

---

### Post by sgage on 2011-02-25
> **ronacc said:**
> do I also need to add xorg-edgers ppa to get the 1.10 rc2 xserver ?

I am now using the nvidia drivers from the x-swat ppa with the xserver from stock natty repos, and all seems right with the world. I will enjoy it until the ABI changes again :-)

---

### Post by Harry33 on 2011-02-25
> **ronacc said:**
> do I also need to add xorg-edgers ppa to get the 1.10 rc2 xserver ?

No you should not use xorg-edgers any more.
The xserver 1.10 rc2 can only be found in Natty official repos:
xserver-xorg-core_1.9.99.902-2ubuntu1

Use that, and get the nvidia-current and nvidia-settings (270.29) from X Updates PPA.

---

### Post by ronacc on 2011-02-25
thanks I already had that one , but with Ubuntu's wierd numbering system I wasn't sure it was the right one .

---

### Post by Quackers on 2011-02-25
Thanks for the heads up Harry33.
However, I just tried this and all was going smooth until nvidia-settings tried to install and I got this
```
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from nvidia-settings_270.29-0ubuntu1~xup_amd64.deb) ...
Setting up nvidia-current (270.29-0ubuntu1~xup) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new nvidia-current-270.29 DKMS files...
Building only for 2.6.38-5-generic
Building for architecture x86_64
Building initial module for 2.6.38-5-generic
Done.

nvidia-current.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.38-5-generic/updates/dkms/

depmod....

DKMS: install Completed.
dpkg: dependency problems prevent configuration of nvidia-settings:
 nvidia-settings depends on screen-resolution-extra (>= 0.12); however:
  Package screen-resolution-extra is not installed.
dpkg: error processing nvidia-settings (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-5-generic
Processing triggers for python-support ...
Errors were encountered while processing:
 nvidia-settings
nattyalpha@nattyalpha-VGN-AR51SU:~/Desktop$ 

```

So I ran synaptic and it said I had a broken package and when I went to fix it, it said there was a dependency problem and it installed screen-resolution-extra without me asking. 
Does that mean nvidia-settings is now installed as well or shall I run dpkg again?
I ask because I would expect to see the start button turn red, asking for a restart, but it hasn't.
Thanks

---

### Post by Quackers on 2011-02-25
Synaptic said nvidia-settings were installed so I restarted. All is well :-)
Thanks for the heads up :-)

---

### Post by t1497f35 on 2011-02-25
[The post from nvidia]("http://www.nvnews.net/vbulletin/showthread.php?t=159990") at was updated with
> 
Sorry everyone, there was a last-minute ABI change in xserver 1.10 RC 3  despite the ABI number supposedly being frozen, which means that this  driver will actually only work with xserver 1.10 RC 2.  I'll get updates  wending their way through the pipeline ASAP.
More about why RC3 changed the ABI unexpectedly so late in the release cycle:
[http://www.phoronix.com/scan.php?page=news_item&px=OTEzMA](http://www.phoronix.com/scan.php?page=news_item&px=OTEzMA)

---

### Post by webme on 2011-02-25
NVIDIA 270.29 official  is out (No  X-SWATT-PPA required), install it via update-manager.
The devs are fast!!!

---

### Post by plun on 2011-02-25
Great news....:popcorn:

Up and running...

---

### Post by Quackers on 2011-02-25
> **t1497f35 said:**
> [The post from nvidia]("http://www.nvnews.net/vbulletin/showthread.php?t=159990") at was updated with
More about why RC3 changed the ABI unexpectedly so late in the release cycle:
[http://www.phoronix.com/scan.php?page=news_item&px=OTEzMA](http://www.phoronix.com/scan.php?page=news_item&px=OTEzMA)

Fantastic! I bet nvidia are happy about that.

---

### Post by cariboo on 2011-02-25
Who cares about Nvidia :), I'm happy :)

---

### Post by sgage on 2011-02-25
> **Quackers said:**
> Fantastic! I bet nvidia are happy about that.

That was my thought exactly. I hope they don't get tired of getting jerked around...

---

### Post by Quackers on 2011-02-25
> **cariboo907 said:**
> Who cares about Nvidia :), I'm happy :)

I do! Nvidia waited a month for RC2 to appear so they could write a driver to compile against it. Now that driver's arrived somebody moves the goal posts! I'm sure they're ecstatic about that.
I suspect you'll care about nvidia too if they stop spending money creating Linux drivers.

---

### Post by cariboo on 2011-02-25
Jeez, can't you guys take a joke? I've been using nvidia with linux since 2001 and am a staunch nvidia supporter. I'm glad the Xorg devs got the bugs worked out and nvidia released a working driver.

---

### Post by VMC on 2011-02-25
> **Quackers said:**
> I do! Nvidia waited a month for RC2 to appear so they could write a driver to compile against it. Now that driver's arrived somebody moves the goal posts! I'm sure they're ecstatic about that.
I suspect you'll care about nvidia too if they stop spending money creating Linux drivers.

Wait until NVIDIA see's [Wayland]("http://en.wikipedia.org/wiki/Wayland_(display_server_protocol)"). Rumor is they may not even support it.

---

### Post by Quackers on 2011-02-25
That's the point isn't it? The new driver won't be working when RC3 comes out. So it would appear to have been a wasted effort in writing the new driver. If nvidia get sick of it we could be left with nothing at some time in the future.

---

### Post by Harry33 on 2011-02-25
> **Quackers said:**
> That's the point isn't it? The new driver won't be working when RC3 comes out. So it would appear to have been a wasted effort in writing the new driver. If nvidia get sick of it we could be left with nothing at some time in the future.

But at least we now have xserver1.10rc2 installed and it's fully working with nvidia proprietary drivers.
So it is not so bad, if we need to wait for the new drivers when xserver1.10rc3 gets pulled in.

---

### Post by Quackers on 2011-02-25
Absolutely :-)
My concern is with nvidia's state of mind, having waited for the "final" RC2 to write a compatible driver, they now find a RC3 is going to appear, necessitating further expense on their part to write a new driver. It does seem that they've been misled.
It would annoy me if I were Mr.Nvidia, spending money for nothing.

---

### Post by cariboo on 2011-02-25
Nvidia contributes to the Xorg project, so they are well aware of what is coming, they usually have the drivers ready before the latest version is released.

---

### Post by Harry33 on 2011-02-25
And this is still a growing market area for NVidia:
to be able to sell more high end graphics cards for linux users.

---

### Post by dext on 2011-02-25
**RC3 already out**

[http://lists.freedesktop.org/archives/xorg-announce/2011-February/001611.html](http://lists.freedesktop.org/archives/xorg-announce/2011-February/001611.html)

---

### Post by Yofel on 2011-02-25
As for the RC3 ABI break, some IRC quotes from today:

From #nvidia:
<aaronp> Yeah, I didn't expect Keith to do that so that was a  total surprise this morning.  I'll get that updated today and a new  build going through the release pipeline ASAP.

and #ubuntu-x:
<tseliot> tjaalton: did they break the ABI again??? [http://www.phoronix.com/scan.php?page=news_item&px=OTEzMA](http://www.phoronix.com/scan.php?page=news_item&px=OTEzMA)
<tjaalton> yes
<tjaalton> randr-1.4 was removed
<tseliot> this is not good for fglrx and nvidia
<tjaalton> it's trivial for them to fix
<tjaalton> and aaronp was aware of that
<tseliot> I'll talk them, just in case
<tjaalton> we don't have to pull rc3 until they've released newer versions for it
<tseliot> new versions as in new open drivers?
<tseliot> or new X?
<tjaalton> new blobs
<tseliot> ok, this is good to know
<tseliot> as I'm about to upload nvidia

so that shouldn't affect natty at least.

---

### Post by Harry33 on 2011-02-25
> **Yofel said:**
> As for the RC3 ABI break, some IRC quotes from today:

From #nvidia:
<aaronp> Yeah, I didn't expect Keith to do that so that was a  total surprise this morning.  I'll get that updated today and a new  build going through the release pipeline ASAP.

and #ubuntu-x:
<tseliot> tjaalton: did they break the ABI again??? [http://www.phoronix.com/scan.php?page=news_item&px=OTEzMA](http://www.phoronix.com/scan.php?page=news_item&px=OTEzMA)
<tjaalton> yes
<tjaalton> randr-1.4 was removed
<tseliot> this is not good for fglrx and nvidia
<tjaalton> it's trivial for them to fix
<tjaalton> and aaronp was aware of that
<tseliot> I'll talk them, just in case
<tjaalton> we don't have to pull rc3 until they've released newer versions for it
<tseliot> new versions as in new open drivers?
<tseliot> or new X?
<tjaalton> new blobs
<tseliot> ok, this is good to know
<tseliot> as I'm about to upload nvidia

so that shouldn't affect natty at least.

That is good to know.
However, new ABI will break all the open source drivers too:
- xserver-xorg-input-*
- xserver-xorg-video*
A lot of building work ahead.

---

### Post by rbrick49 on 2011-02-25
what about ati cards Harry I want to upgrade maverick to natty but i am not game as I have my ati 6950 card working on maverick
regards Ron

---

### Post by dext on 2011-02-25
what Opensource ATI driver version does Ubuntu currently have?

---

### Post by Harry33 on 2011-02-26
> **rbrick49 said:**
> what about ati cards Harry I want to upgrade maverick to natty but i am not game as I have my ati 6950 card working on maverick
regards Ron

AMD/ATI proprietary drivers do not work with the latest xserver 1.10.
If you use those (fglrx) in your Maverick, please do not upgrade to Natty-alfa2.

---

### Post by Harry33 on 2011-02-26
> **dext said:**
> what Opensource ATI driver version does Ubuntu currently have?

Natty has this one:
6.14.0-0ubuntu2

Here:
[https://launchpad.net/ubuntu/natty/+source/xserver-xorg-video-ati/1:6.14.0-0ubuntu2](https://launchpad.net/ubuntu/natty/+source/xserver-xorg-video-ati/1:6.14.0-0ubuntu2)

---

### Post by xeizo on 2011-02-26
I guess I got stuck at the new ABI, aptitude removed Xorg automatically when I wasn't paying attention and now refuses to install Xorg again whatsoever even using -f. Aptitude complains about wrong abi(12.1), and 12.1 doesn't exist. To me, it seems impossible to fix at the moment, any advice to get Xorg back?  edit. I had a copy of edgers in etc/apt/sources.list.d/, not in sources.list itself, but removing it solved the issue. I now have Xorg with nvidia-current  :)

---

### Post by clivejo on 2011-02-26
I am most impressed with this driver, thanks Nvidia.  All my crashes have now stopped and finally got Unity to work, not very impressed with it, but that's another story.

---

### Post by ktp on 2011-02-26
I was able to install the 279.20 drivers, on persistent usb using the 2/26 daily live cd iso.  But the display seems to be frozen/locked for any thing with 3d effects, i.e. classic desktop or unity desktop sessions.  I can move the mouse but that's about it...nothing on the screen refreshes/redraws.  

Logging into classic desktop with no effects works.  I do have older GeForce 7300 card...but I had never had any issue before.  I guess more debugging to do on my side, but wondering if anyone else seeing something like this.

---

### Post by rang501 on 2011-03-01
> **ktp said:**
> I was able to install the 279.20 drivers, on persistent usb using the 2/26 daily live cd iso.  But the display seems to be frozen/locked for any thing with 3d effects, i.e. classic desktop or unity desktop sessions.  I can move the mouse but that's about it...nothing on the screen refreshes/redraws.  

Logging into classic desktop with no effects works.  I do have older GeForce 7300 card...but I had never had any issue before.  I guess more debugging to do on my side, but wondering if anyone else seeing something like this.

I have this problem with GF Go 7300.

---

### Post by PapaNoa on 2011-03-10
I can't confirm the issue is resolved for me. My system still freezes hard when trying to start X using the proprietary nvidia drivers (and also the nouveau driver for that matter). I just did another upgrade to no avail.

Package versions:
nvidia-current 270.29-0ubuntu3
xserver-xorg-core 2:1.9.99.902-2ubuntu2

xorg.conf (the bare minimum):
```

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

```Xorg.0.log (not very helpful)
```

[    32.641]
X.Org X Server 1.9.99.902 (1.10.0 RC 2)
Release Date: 2011-2-18
[    32.641] X Protocol Version 11, Revision 0
[    32.641] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    32.641] Current Operating System: Linux fr710-laptop 2.6.38-6-generic #34-Ubuntu SMP Tue Mar 8 14:15:57 UTC 2011 x86_64
[    32.641] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-6-generic root=UUID=087ea822-8842-4ccc-9faf-99b2d34982b3 ro quiet splash vt.handoff=7
[    32.641] Build Date: 08 March 2011  09:48:33PM
[    32.641] xorg-server 2:1.9.99.902-2ubuntu2 (For technical support please see http://www.ubuntu.com/support)
[    32.641] Current version of pixman: 0.20.2
[    32.641]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    32.641] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    32.641] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar 10 14:55:32 2011
[    32.680] (==) Using config file: "/etc/X11/xorg.conf"
[    32.680] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    32.820] (==) No Layout section.  Using the first Screen section.
[    32.820] (**) |-->Screen "Default Screen" (0)
[    32.820] (**) |   |-->Monitor "<default monitor>"
[    32.821] (==) No device specified for screen "Default Screen".
        Using the first device section listed.
[    32.821] (**) |   |-->Device "Default Device"
[    32.821] (==) No monitor specified for screen "Default Screen".
        Using a default monitor configuration.
[    32.822] (==) Automatically adding devices
[    32.822] (==) Automatically enabling devices
[    32.886] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    32.886]    Entry deleted from font path.
[    32.920] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
[    32.920] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    32.920] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    32.920] (II) Loader magic: 0x7e3280
[    32.921] (II) Module ABI versions:
[    32.921]    X.Org ANSI C Emulation: 0.4
[    32.921]    X.Org Video Driver: 9.0
[    32.921]    X.Org XInput driver : 12.3
[    32.921]    X.Org Server Extension : 5.0
[    32.921] (--) PCI:*(0:1:0:0) 10de:0a6c:1028:040b rev 162, Mem @ 0xe2000000/16777216, 0xd0000000/268435456, 0xe0000000/33554432, I/O @ 0x00007000/128, BIOS @
 0x????????/524288
[    32.922] (II) Open ACPI successful (/var/run/acpid.socket)
[    32.922] (II) "extmod" will be loaded by default.
[    32.922] (II) "dbe" will be loaded by default.
[    32.922] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    32.922] (II) "record" will be loaded by default.
[    32.922] (II) "dri" will be loaded by default.
[    32.922] (II) "dri2" will be loaded by default.
[    32.922] (II) LoadModule: "glx"
[    32.947] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    33.466] (II) Module glx: vendor="NVIDIA Corporation"
[    33.473]    compiled for 4.0.2, module version = 1.0.0
[    33.473]    Module class: X.Org Server Extension
[    33.473] (II) NVIDIA GLX Module  270.29  Wed Feb 23 16:35:41 PST 2011
[    33.473] (II) Loading extension GLX
[    33.473] (II) LoadModule: "extmod"
[    33.553] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    33.568] (II) Module extmod: vendor="X.Org Foundation"
[    33.568]    compiled for 1.9.99.902, module version = 1.0.0
[    33.568]    Module class: X.Org Server Extension
[    33.568]    ABI class: X.Org Server Extension, version 5.0
[    33.569] (II) Loading extension MIT-SCREEN-SAVER
[    33.569] (II) Loading extension XFree86-VidModeExtension
[    33.569] (II) Loading extension XFree86-DGA
[    33.569] (II) Loading extension DPMS
[    33.569] (II) Loading extension XVideo
[    33.569] (II) Loading extension XVideo-MotionCompensation
[    33.569] (II) Loading extension X-Resource
[    33.569] (II) LoadModule: "dbe"
[    33.579] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    33.586] (II) Module dbe: vendor="X.Org Foundation"
[    33.586]    compiled for 1.9.99.902, module version = 1.0.0
[    33.586]    Module class: X.Org Server Extension
[    33.586]    ABI class: X.Org Server Extension, version 5.0
[    33.586] (II) Loading extension DOUBLE-BUFFER
[    33.586] (II) LoadModule: "record"
[    33.586] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    33.594] (II) Module record: vendor="X.Org Foundation"
[    33.594]    compiled for 1.9.99.902, module version = 1.13.0
[    33.594]    Module class: X.Org Server Extension
[    33.594]    ABI class: X.Org Server Extension, version 5.0
[    33.594] (II) Loading extension RECORD
[    33.594] (II) LoadModule: "dri"
[    33.594] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    33.608] (II) Module dri: vendor="X.Org Foundation"
[    33.608]    compiled for 1.9.99.902, module version = 1.0.0
[    33.608]    ABI class: X.Org Server Extension, version 5.0
[    33.608] (II) Loading extension XFree86-DRI
[    33.608] (II) LoadModule: "dri2"
[    33.608] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    33.610] (II) Module dri2: vendor="X.Org Foundation"
[    33.610]    compiled for 1.9.99.902, module version = 1.2.0
[    33.610]    ABI class: X.Org Server Extension, version 5.0
[    33.610] (II) Loading extension DRI2
[    33.610] (II) LoadModule: "nvidia"
[    33.610] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    33.686] (II) Module nvidia: vendor="NVIDIA Corporation"
[    33.714]    compiled for 4.0.2, module version = 1.0.0
[    33.714]    Module class: X.Org Video Driver
[    33.740] (II) NVIDIA dlloader X Driver  270.29  Wed Feb 23 16:20:07 PST 2011
[    33.740] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    33.750] (++) using VT number 7

[    33.758] (II) Loading sub module "fb"
[    33.758] (II) LoadModule: "fb"
[    33.758] (II) Loading /usr/lib/xorg/modules/libfb.so
[    33.774] (II) Module fb: vendor="X.Org Foundation"
[    33.774]    compiled for 1.9.99.902, module version = 1.0.0
[    33.774]    ABI class: X.Org ANSI C Emulation, version 0.4
[    33.774] (II) LLoading sub module "wfb"
[    33.774] (II) LoadModule: "wfb"
[    33.774] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    33.786] (II) Module wfb: vendor="X.Org Foundation"
[    33.786]    compiled for 1.9.99.902, module version = 1.0.0
[    33.786]    ABI class: X.Org ANSI C Emulation, version 0.4
[    33.786] (II) Loading sub module "ramdac"
[    33.786] (II) LoadModule: "ramdac"
[    33.786] (II) Module "ramdac" already built-in
[    33.805] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    33.805] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    33.805] (II) Loading /usr/lib/xorg/modules/libfb.so
[    33.812] (II) NVIDIA(0): Creating default Display subsection in Screen section
        "Default Screen" for depth/fbbpp 24/32
[    33.812] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    33.812] (==) NVIDIA(0): RGB weight 888
[    33.812] (==) NVIDIA(0): Default visual is TrueColor
[    33.812] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    33.812] (**) NVIDIA(0): Option "NoLogo" "True"

```

Apparently it crashes just after that, I'm not dropped back to the shell and I can only reboot using the magic Alt+SysRq REISUB.

What could go wrong? Any hints highly appreciated.

---

### Post by ronacc on 2011-03-10
try this , at boot selest recovery mode and at the choice box to select waht to do select safe graphics mode and then run this time only and the when safe graphics mode comes up just reboot and the nvidia driver should start on the reboot , this works on my sys but a start from cold goes to a black locked screen with a thin purple bar at the top and nothing works except alt>sysreq>b but a reboot from safe graphics goes to desktop with your Nvidia driver running .If this works for you it is plymouth causing the problem , adjust your grub.cfg accordingly .

---

### Post by PapaNoa on 2011-03-10
I'll give that a try, thanks. Could you elaborate what the plymouth problem is and how to solve it / point me to a solution? Are you referring to [https://bugs.launchpad.net/ubuntu/natty/+source/plymouth/+bug/684083](https://bugs.launchpad.net/ubuntu/natty/+source/plymouth/+bug/684083)?

---

### Post by dino99 on 2011-03-10
your xorg.log is ok, about plymouth: remove "splash" on the boot line (/etc/default/grub to make the change permanent). If you dont see the grub menu (normal on single Os), hold "shift" key down at end of bios process to see it.

---

### Post by PapaNoa on 2011-03-10
I removed "splash" and "quiet" from the grub command line and added the option "GRUB_GFXPAYLOAD_LINUX=keep" as advised in the plymouth bug report ([https://bugs.launchpad.net/ubuntu/natty/+source/plymouth/+bug/684083](https://bugs.launchpad.net/ubuntu/natty/+source/plymouth/+bug/684083)), to no avail.

Also booting into failsafe X and rebooting from there didn't help.

---

### Post by ronacc on 2011-03-10
for some reason this time around you also need to remove vthandoff=7 and change the line that says ```
set gfxpayload=$linux_gfx_mode
``` to ```
set gfxpayload=text
``` , I also remove quiet and change all other references to gfx mode to =text but that may not be necessary .

---

### Post by PapaNoa on 2011-03-10
Where would I need to change that? In my natty boot entry in /etc/grub.d?

That's quite a hack, isn't it? Since these files get overwritten when you re-run update-grub...

---

### Post by ronacc on 2011-03-10
in your grub.cfg and yes it will get over written . but you can always re write it and you haven't made any permenant changes if it don't work for you , and future updates MAY ( but I dont have much hope) make it uneset unnecessary .

---

### Post by PapaNoa on 2011-03-10
I edited the entry on the grub command line and changed gfxpayload to text. There wasn't any option vthandoff=7. Unfortunately that didn't help either.

When it hangs the kernel seems still to be responsive so far as to I can press the power button to power down. Fn key, NumLock etc. don't work anymore.

---

### Post by ronacc on 2011-03-10
same here , only alt>sysreq>b works not even alt>sysreq>k (kill xserver)  but that fix works for me , oh well it was worth a try .

---

### Post by Harry33 on 2011-03-10
The replies from #36 on are not anymore nvidia-current nor xserver issues.
These concern the grub2 configuration and its compatibility with certain older graphics cards.
I suggest this thread could be divided into two or completely new thread could be started on this grub2 issue.

---

### Post by ronacc on 2011-03-10
my graphics card is NOT a legacy one it is a 7600gs and I am using the current xserver and 270.29 driver .

---

### Post by ktp on 2011-03-12
> **rang501 said:**
> I have this problem with GF Go 7300.

I am currently using the open source 3d drivers and it is working nicely for the first time for me on the latest builds.  I have not installed proprietary drivers but that's next thing.

---

### Post by mc4man on 2011-03-16
The nvidia-current drivers (whether what's currently in natty or the 1.10 X and 2.30 in xorgers) work quite well.

If however you have a lower mem machine -  1GB or less  you may wish to keep an eye on mem in use and if going into swap.

The nvidia drivers and libcairo2 cause a significant increase in mem used at login compared to previous libcairo2 and what's seen w/ nouveau

---

### Post by dino99 on 2011-03-16
how much is that "significant increase" on your side ?

---

### Post by mc4man on 2011-03-16
> **dino99 said:**
> how much is that "significant increase" on your side ?

Well the difference here on several various nvidia machines is around 400MB between nouveau and nvidia in a unity login. (170 -180 to 550 -570  

The difference between nvidia with the previous libcairo2 and current libcairo2 is around 330 or so (200 - 230 w/ old libcairo2

Makes no difference w/ 2GB or more, can become an issue w/ 1GB or less

---

### Post by cariboo on 2011-03-16
I tried the nVidia closed source drivers on a system with only 512Mb ram, the system was unusable, it was always using at least 500Mb of swap. Removing nvidia-current, and replacing it with the nouveau driver plus libgl1-mesa-dri-experimental, brought the system back to being very usable.

---

### Post by mc4man on 2011-03-16
> **cariboo907 said:**
> I tried the nVidia closed source drivers on a system with only 512Mb ram, the system was unusable, it was always using at least 500Mb of swap. Removing nvidia-current, and replacing it with the nouveau driver plus libgl1-mesa-dri-experimental, brought the system back to being very usable.
With any of the available nvidia adapters here (7000 and 8000 series, AGP and PCI-E), the min now at login is 500 MB, usually more with the nvidia drivers.

The increase is seen spread across most of the processes, not one or 2, or so. It's somewhat manageable with 1GB, but have decided here on a P4, 1GB to go w/ the mesa 3d drivers which are ok. (though have suffered some minor setbacks the last several weeks.

Have an open bug on this, whether there will be a resolution anytime soon or ever not sure.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/725434](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/725434)

---

