---
title: "New beta NVidia driver 270.18 - support for xserver 1.10"
date: 2011-01-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-01-22
Well Nvidia has released a new beta driver (version 270.18 ).
That one has of course bug fixes, but also it has a preliminary supprot for xserver 1.10.
You can download it from Ubuntu-X PPA here:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+packages](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+packages)

Thank You Robert Hooker for this. :D

  * New upstream beta release. Changes:
    - Updated the NVIDIA kernel module to ensure that all system memory
      allocated by it for use with GPUs or within user-space components of
      the NVIDIA driver stack is initialized to zero. A new NVIDIA kernel
      module option, InitializeSystemMemoryAllocations, allows
      administrators to revert to the previous behavior.
    - Added preliminary support for xserver 1.10.
    - Reorganized the NVIDIA driver's /proc file system layout to better
    - reflect current needs: /proc/driver/nvidia/cards/0..N has been
      moved to /proc/driver/nvidia/gpus/0..N/information
    - Added new shared library: libnvidia-ml.so.
      NVML provides programmatic access to static information and
      monitoring data for NVIDIA GPUs, as well as limited managment
      capabilities. It is intended for use with Tesla compute products.
    - Added a new X configuration option "3DVisionDisplayType" to specify
      the display type when NVIDIA 3D Vision is enabled with a non 3D
      Vision ready display.
    - Fixed several bugs relating to hardware-accelerated gradients, which
      were causing visual corruption in some of the default Ubuntu GNOME
      themes.
    - Modified colormap updates to no longer be synchronized to vblank. This
      allows applications to send XStoreColor and XStoreColors requests faster
      than the screen's refresh rate.
  * Install libnvidia-ml.so links.
  * Drop X ABI provides because it works with multiple video ABI's.
 -- Robert Hooker <email address hidden>   Fri, 21 Jan 2011 23:54:17 -0500

---

### Post by Harry33 on 2011-01-22
Well ATM the build failed on both 32- and 64-bit architectures.
We will wait then.

---

### Post by plun on 2011-01-22
Yup... the build broke so I manually installed this driver and it works ;)

[[IMG]http://i.imgur.com/cikugs.jpg[/IMG]](http://imgur.com/cikug)

But there is a problem with Compiz which probably must be rebuilt

```
Xlib:  extension "GLX" missing on display ":0.0".
```

I am compiling Compiz from GIT for the moment with Soreus script and see how it works.

---

### Post by Intrepid Ibex on 2011-01-22
For some reason this driver doesn't work here with Xorg Server 1.10 RC1 in Arch Linux 64-bit (1.9.3 RC4 works fine).

This is the full Xorg.0.log I got when loading the driver:
```
[    16.737]
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.
[    16.737]
X.Org X Server 1.9.99.901 (1.10.0 RC 1)
Release Date: 2010-12-06
[    16.738] X Protocol Version 11, Revision 0
[    16.738] Build Operating System: Linux 2.6.37-ck x86_64
[    16.738] Current Operating System: Linux Archlinux 2.6.37-ck #1 SMP PREEMPT Thu Jan 13 14:53:37 EET 2011 x86_64
[    16.738] Kernel command line: BOOT_IMAGE=/boot/vmlinuz26-ck root=/dev/sda1 ro quiet rootfstype=ext4 fastboot resume=swap:/dev/sda1:0x1350000
[    16.738] Build Date: 09 January 2011  03:06:47PM
[    16.738]
[    16.738] Current version of pixman: 0.20.2
[    16.738] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    16.739] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.739] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan 22 11:35:15 2011
[    16.837] (==) Using config directory: "/etc/X11/xorg.conf.d"
[    16.891] (==) No Layout section.  Using the first Screen section.
[    16.892] (==) No screen section available. Using defaults.
[    16.892] (**) |-->Screen "Default Screen Section" (0)
[    16.892] (**) |   |-->Monitor "<default monitor>"
[    16.892] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[    16.892] (**) |   |-->Device "Default nvidia Device"
[    16.892] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    16.892] (**) Option "IgnoreABI" "1"
[    16.892] (**) Ignoring ABI Version
[    16.892] (==) Automatically adding devices
[    16.892] (==) Automatically enabling devices
[    16.932] (WW) The directory "/usr/share/fonts/OTF/" does not exist.
[    16.932] 	Entry deleted from font path.
[    16.976] (==) FontPath set to:
	/usr/share/fonts/misc/,
	/usr/share/fonts/TTF/,
	/usr/share/fonts/Type1/,
	/usr/share/fonts/100dpi/,
	/usr/share/fonts/75dpi/
[    16.976] (==) ModulePath set to "/usr/lib/xorg/modules"
[    16.976] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    16.976] (II) Loader magic: 0x7d91c0
[    16.976] (II) Module ABI versions:
[    16.976] 	X.Org ANSI C Emulation: 0.4
[    16.976] 	X.Org Video Driver: 9.0
[    16.976] 	X.Org XInput driver : 12.0
[    16.976] 	X.Org Server Extension : 5.0
[    16.977] (--) PCI:*(0:2:0:0) 10de:0614:1458:34ae rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/131072
[    16.977] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    16.977] (II) LoadModule: "extmod"
[    17.028] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    17.041] (II) Module extmod: vendor="X.Org Foundation"
[    17.041] 	compiled for 1.9.99.901, module version = 1.0.0
[    17.041] 	Module class: X.Org Server Extension
[    17.041] 	ABI class: X.Org Server Extension, version 5.0
[    17.041] (II) Loading extension MIT-SCREEN-SAVER
[    17.041] (II) Loading extension XFree86-VidModeExtension
[    17.041] (II) Loading extension XFree86-DGA
[    17.041] (II) Loading extension DPMS
[    17.041] (II) Loading extension XVideo
[    17.041] (II) Loading extension XVideo-MotionCompensation
[    17.041] (II) Loading extension X-Resource
[    17.041] (II) LoadModule: "dbe"
[    17.041] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    17.052] (II) Module dbe: vendor="X.Org Foundation"
[    17.052] 	compiled for 1.9.99.901, module version = 1.0.0
[    17.052] 	Module class: X.Org Server Extension
[    17.052] 	ABI class: X.Org Server Extension, version 5.0
[    17.052] (II) Loading extension DOUBLE-BUFFER
[    17.052] (II) LoadModule: "glx"
[    17.059] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    17.765] (II) Module glx: vendor="NVIDIA Corporation"
[    17.774] 	compiled for 4.0.2, module version = 1.0.0
[    17.774] 	Module class: X.Org Server Extension
[    17.774] (II) NVIDIA GLX Module  270.18  Tue Jan 18 22:03:05 PST 2011
[    17.774] (EE) NVIDIA GLX: No supported server extension ABI found.
[    17.774] (II) UnloadModule: "glx"
[    17.774] (II) Unloading glx
[    17.774] (EE) Failed to load module "glx" (module requirement mismatch, 5)
[    17.774] (II) LoadModule: "record"
[    17.775] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    17.782] (II) Module record: vendor="X.Org Foundation"
[    17.783] 	compiled for 1.9.99.901, module version = 1.13.0
[    17.783] 	Module class: X.Org Server Extension
[    17.783] 	ABI class: X.Org Server Extension, version 5.0
[    17.783] (II) Loading extension RECORD
[    17.783] (II) LoadModule: "dri"
[    17.783] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    17.808] (II) Module dri: vendor="X.Org Foundation"
[    17.808] 	compiled for 1.9.99.901, module version = 1.0.0
[    17.808] 	ABI class: X.Org Server Extension, version 5.0
[    17.808] (II) Loading extension XFree86-DRI
[    17.808] (II) LoadModule: "dri2"
[    17.808] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    17.808] (II) Module dri2: vendor="X.Org Foundation"
[    17.808] 	compiled for 1.9.99.901, module version = 1.2.0
[    17.808] 	ABI class: X.Org Server Extension, version 5.0
[    17.808] (II) Loading extension DRI2
[    17.808] (II) LoadModule: "nvidia"
[    17.808] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    17.863] (II) Module nvidia: vendor="NVIDIA Corporation"
[    17.865] 	compiled for 4.0.2, module version = 1.0.0
[    17.865] 	Module class: X.Org Video Driver
[    17.865] ================ WARNING WARNING WARNING WARNING ================
[    17.865] This server has a video driver ABI version of 9.0 that this
driver does not officially support.  Please check
http://www.nvidia.com/ for driver updates or downgrade to an X
server with a supported driver ABI.
[    17.865] =================================================================
[    17.865] (WW) NVIDIA: The driver will continue to load, but may behave strangely.
[    17.865] (WW) NVIDIA: This driver was compiled against the X.Org server SDK from git commit 780754050bc9cb1489f92a2a890ab5665e3e6358 and may not be compatible with the final version of this SDK.
[    17.866] (WW) NVIDIA: This server has an unsupported input driver ABI version (have 12.0, need < 12.0).  The driver will continue to load, but may behave strangely.
[    17.893] (II) NVIDIA dlloader X Driver  270.18  Tue Jan 18 21:47:56 PST 2011
[    17.893] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    17.894] (--) using VT number 4

[    17.919] (II) Loading sub module "fb"
[    17.919] (II) LoadModule: "fb"
[    17.919] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.935] (II) Module fb: vendor="X.Org Foundation"
[    17.935] 	compiled for 1.9.99.901, module version = 1.0.0
[    17.935] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    17.935] (II) Loading sub module "wfb"
[    17.935] (II) LoadModule: "wfb"
[    17.935] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    17.950] (II) Module wfb: vendor="X.Org Foundation"
[    17.950] 	compiled for 1.9.99.901, module version = 1.0.0
[    17.950] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    17.950] (II) Loading sub module "ramdac"
[    17.950] (II) LoadModule: "ramdac"
[    17.950] (II) Module "ramdac" already built-in
[    17.960] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    17.960] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    17.960] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.969] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    17.969] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    17.969] (==) NVIDIA(0): RGB weight 888
[    17.969] (==) NVIDIA(0): Default visual is TrueColor
[    17.969] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    17.969] (**) NVIDIA(0): Enabling RENDER acceleration
[    17.969] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    17.969] (II) NVIDIA(0):     enabled.

```

There's (of course) a lot of information there but these few lines are especially interesting:
```
[    17.052] (II) LoadModule: "glx"
[    17.059] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    17.765] (II) Module glx: vendor="NVIDIA Corporation"
[    17.774] 	compiled for 4.0.2, module version = 1.0.0
[    17.774] 	Module class: X.Org Server Extension
[    17.774] (II) NVIDIA GLX Module  270.18  Tue Jan 18 22:03:05 PST 2011
[    17.774] (EE) NVIDIA GLX: No supported server extension ABI found.
[    17.774] (II) UnloadModule: "glx"
[    17.774] (II) Unloading glx
[    17.774] (EE) Failed to load module "glx" (module requirement mismatch, 5)
...
[    17.969] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    17.969] (II) NVIDIA(0):     enabled.
```

So it _seems_ that the Nvidia glx library (libglx.so) just doesn't support the new Xorg Server ABI. But I don't understand as to why then does the GLX support still get enabled in the end (despite the module not loading up).

Using Xorg Server 1.10 RC1 and Nvidia drivers 270.18.

---

### Post by plun on 2011-01-22
> **Intrepid Ibex said:**
> 

So it _seems_ that the Nvidia glx library (libglx.so) just doesn't support the new Xorg Server ABI. But I don't understand as to why then does the GLX support still get enabled in the end (despite the module not loading up).

Using Xorg Server 1.10 RC1 and Nvidia drivers 270.18.

Yep.. confirmed with the same log file output.

Digging for a solution....;)

---

### Post by Harry33 on 2011-01-22
So now nvidia-current_270.18 is available from Ubuntu-X PPA and Xorg-Edgers PPA.
The problem of build failure was only a missing libxv1.

---

### Post by plun on 2011-01-22
> **Harry33 said:**
> So now nvidia-current_270.18 is available from Ubuntu-X PPA and Xorg-Edgers PPA.
The problem of build failure was only a missing libxv1.

I still got no glx-extension.....

Removed the manually installed driver with the --uninstall option and then installed nvidia-current and dkms.

ABI errror when glx starts.....:^o  (as earlier posted log file shows)

But... maybe I messed up things again ? :D

---

### Post by Harry33 on 2011-01-22
> **plun said:**
> I still got no glx-extension.....

Removed the manually installed driver with the --uninstall option and then installed nvidia-current and dkms.

ABI errror when glx starts.....:^o  (as earlier posted log file shows)

But... maybe I messed up things again ? :D

Plun,
do you use this?

Section "ServerFlags"
Option "IgnoreABI" "True"
EndSection

So the X starts but compiz does not work?

---

### Post by plun on 2011-01-22
> **Harry33 said:**
> Plun,
do you use this?

Section "ServerFlags"
Option "IgnoreABI" "True"
EndSection

So the X starts but compiz does not work?

Yep... but I don't think ignoreABI is needed now. I have it in my xorg.conf nevertheless

Please check glxinfo

```
glxinfo
```

What does it say for you ?

---

### Post by Harry33 on 2011-01-22
> **plun said:**
> Yep... but I don't think ignoreABI is needed now. I have it in my xorg.conf nevertheless
Please check glxinfo
```
glxinfo
```
What does it say for you ?

Right now (with nvidia-current 270.18 and xserver 1.9.2):

    glxinfo:
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
...

---

### Post by plun on 2011-01-22
> **Harry33 said:**
> Right now (with nvidia-current 270.18 and xserver 1.9.2):

    glxinfo:
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
...

Well, then you haven't upgraded to Xserver 1.10

```
plun@plun-laptop:~$ X -version

X.Org X Server 1.9.99.901 (1.10.0 RC 1)
Release Date: 2010-12-06
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-xen x86_64 Ubuntu
Current Operating System: Linux plun-laptop 2.6.38-020638rc2-generic #201101220905 SMP Sat Jan 22 09:09:13 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-020638rc2-generic root=UUID=cce29c05-0460-47f8-a591-171a60947546 ro quiet nosplash
Build Date: 12 January 2011  03:14:12PM
xorg-server 2:1.9.99.901+git20110111.6358a600-0ubuntu0chris5 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.21.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.

```

---

### Post by Harry33 on 2011-01-22
Oh, and BTW, the following lines ought to be in the xorg.conf:
```

    Section "ServerFlags"
    Option "IgnoreABI" "True"
    EndSection

```

If not, the loading of X stops.
Look at the "Xorg.0.log" from the post of Intrepid Ibex.
Loading X (without those lines) would stop at here:

    [17.865] This server has a video driver ABI version of 9.0 that this
    driver does not officially support.  Please check
    [http://www.nvidia.com/](http://www.nvidia.com/) for driver updates or downgrade to an X
    server with a supported driver ABI.

---

### Post by Harry33 on 2011-01-22
> **plun said:**
> Well, then you haven't upgraded to Xserver 1.10
...


I tested once, but was not very happy about it.
The glx issue must be solved first, before I try again.

---

### Post by plun on 2011-01-22
> **Harry33 said:**
> I tested once, but was not very happy about it.
The glx issue must be solved first, before I try again.

Ok... then we have a case with a confirmed bug !

---

### Post by plun on 2011-01-22
Added more info about this bug.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/703688](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/703688)

---

### Post by Harry33 on 2011-01-22
> **plun said:**
> Added more info about this bug.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/703688](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/703688)

Thanks, plun.

---

### Post by plun on 2011-01-22
> **Harry33 said:**
> Thanks, plun.

Well... and started a thread in nVidias forum.....

I don't believe that a open source developer can do something to this.

The glx extension must probably be fixed with a new beta driver from nVidia.

But you never knows if a Gentoo hacker maybe sees this and want something to work....:D

---

### Post by Intrepid Ibex on 2011-01-23
> **plun said:**
> But you never knows if a Gentoo hacker maybe sees this and want something to work....:D
Would require quite some [_[COLOR="DarkSlateGray"]disassembling[/COLOR]_]("http://en.wikipedia.org/wiki/Disassembler"), which in turn is [[COLOR="DarkSlateGray"]_illegal_[/COLOR]]("http://nouveau.freedesktop.org/wiki/FAQ#Whydon.2BIBk-tyoujustdisassembletheproprietarydriver.3F") in a lot of countries :).

<sidenote>Harry33, it'd make your xorg.conf options & log posts easier to read, if you used [[COLOR="DarkSlateGray"]_[code]_[/COLOR]]("http://ubuntuforums.org/misc.php?do=bbcode#code") tags with 'em. It's not like [[COLOR="DarkSlateGray"]_a matter of life and death_[/COLOR]]("http://en.wikipedia.org/wiki/A_Matter_of_Life_and_Death_(album)") but it'd just be nice.</sidenote>

---

### Post by Harry33 on 2011-01-23
Intrepid,
consider it done. :D

---

### Post by Harry33 on 2011-01-23
OK, then.
Now I have xserver 1.10 (1.9.99.901) and nvidia-current 270.18 installed.
I have the following lines in xorg.conf:
```

Section "ServerFlags"
    Option    "IgnoreABI" "True"
EndSection

```

Note, I have packages x11-common, xorg and xserver-xorg from Natty installed (the latest version 7.5+6ubuntu8 ). That is because I do not like dependency hell.

My setup boots fine and fast with full nice Plymouth.

Yes, yes - GLX is not supported. I gave up Compiz. I am using Gnome-Classic now.
Desktop really works well.

---

### Post by plun on 2011-01-23
> **Harry33 said:**
> 

Yes, yes - GLX is not supported. I gave up Compiz. I am using Gnome-Classic now.
Desktop really works well.

Give up Compiz.....#-o:grin:

No way....  nvidia fixes this within a day or two...O:)

---

### Post by Quadunit404 on 2011-01-23
This driver just showed up in my Update Manager (I added the X Swat PPA because some GLX apps caused my X Server to crash due to a bug in the NVIDIA driver Ubuntu gives you which got annoying quickly.) I do not test development releases of OSes on actual hardware (just in a VM) so I am still on Maverick. I am aware that Maverick uses X.Org 1.9. I have some questions about this driver:

- Will GLX work on X.Org 1.9?
- Will GNOME Shell work right?
- Will it punch me, cause my toaster to burst into flames or suck my printer's ink dry?

I'll stick with my current driver (269.19.29) until these questions are answered.

---

### Post by Harry33 on 2011-01-24
> **Quadunit404 said:**
> This driver just showed up in my Update Manager (I added the X Swat PPA because some GLX apps caused my X Server to crash due to a bug in the NVIDIA driver Ubuntu gives you which got annoying quickly.) I do not test development releases of OSes on actual hardware (just in a VM) so I am still on Maverick. I am aware that Maverick uses X.Org 1.9. I have some questions about this driver:

- Will GLX work on X.Org 1.9?
- Will GNOME Shell work right?
- Will it punch me, cause my toaster to burst into flames or suck my printer's ink dry?

I'll stick with my current driver (269.19.29) until these questions are answered.

NVidia drivers work perfectly with xserver 1.9 series. You can use the stable version 269.19.29 or beta 270.18.
It is only that people here have issues (GLX) with xserver 1.10.

---

### Post by Harry33 on 2011-01-24
Plun,
have you tested the latest xserver 1.10 update from xorg-edgers?
This one: xorg-server (2:1.9.99.901+git20110124.be3be758-0ubuntu0chris)

I did, and now X wont start anymore because of a segfault.
I get this backtrace:

```

Backtrace:
[    16.314] 0: /usr/bin/X (xorg_backtrace+0x26) [0x4689f6]
[    16.314] 1: /usr/bin/X (0x400000+0x6a53a) [0x46a53a]
[    16.314] 2: /lib/libpthread.so.0 (0x7ff90f07c000+0xfd70) [0x7ff90f08bd70]
[    16.314] 3: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7ff9098da000+0x41cf60) [0x7ff909cf6f60]
[    16.314] 4: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7ff9098da000+0x42769a) [0x7ff909d0169a]
[    16.314] 5: /usr/bin/X (AddScreen+0x1a8) [0x428508]
[    16.315] 6: /usr/bin/X (InitOutput+0x294) [0x46fae4]
[    16.315] 7: /usr/bin/X (0x400000+0x217c3) [0x4217c3]
[    16.315] 8: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7ff90dfd1d1e]
[    16.315] 9: /usr/bin/X (0x400000+0x21529) [0x421529]
[    16.315] Segmentation fault at address 0x18
[    16.315] 
Caught signal 11 (Segmentation fault). Server aborting
[    16.315] 

```

---

### Post by Harry33 on 2011-01-24
Here is more info on this issue.
Aaron Plattner has written the following about broken glx extension:
[http://www.nvnews.net/vbulletin/showthread.php?t=158983](http://www.nvnews.net/vbulletin/showthread.php?t=158983)
> Sorry, a bug in the build scripts prevented support from getting compiled into this release. I've fixed the build so the next release should work.

Also, as a heads-up, I should mention that another ABI break went into the X server source tree, so xserver 1.10 RC 2 will not be compatible with the limited support in 270.18.

So this means Nvidia's beta driver 270.18 does not support xserver 1.10 rc2.
I think that version might already be in xorg-edgers PPA.
That would explain the segfault.

---

### Post by Quadunit404 on 2011-01-24
> **Harry33 said:**
> NVidia drivers work perfectly with xserver 1.9 series. You can use the stable version 269.19.29 or beta 270.18.
It is only that people here have issues (GLX) with xserver 1.10.

Thank you! Just gotta wait for fgdata to finish cloning from Git and I'll update my driver! :D

But... you didn't answer question #3... :( :lol:

---

### Post by plun on 2011-01-24
> **Harry33 said:**
> 
So this means Nvidia's beta driver 270.18 does not support xserver 1.0 rc2.
I think that version might already be in xorg-edgers PPA.
That would explain the segfault.

Well... nVidia is working on it.... AaronP answered and that the signal that this will be resolved but maybe with a little jumpy road...;)

---

### Post by Sealbhach on 2011-01-24
So for the moment we can install the 270 Nvidia driver but stay with xorg 1.9 to avound any loss of functionality?

.

---

### Post by Quadunit404 on 2011-01-24
Yes! I installed driver 270.18 on my machine and even though Compiz animations are *slightly* laggy, my X server still works perfectly and OpenGL works just fine tooo.

And fortunately it didn't punch me, fry my toaster OR suck my printer ink dry :lol: :wink:

---

### Post by AaronP_ on 2011-01-26
> **Harry33 said:**
> Here is more info on this issue.
Aaron Plattner has written the following about broken glx extension:
[http://www.nvnews.net/vbulletin/showthread.php?t=158983](http://www.nvnews.net/vbulletin/showthread.php?t=158983)


So this means Nvidia's beta driver 270.18 does not support xserver 1.10 rc2.
I think that version might already be in xorg-edgers PPA.
That would explain the segfault.

xserver 1.10 RC2 (a.k.a. 1.9.99.902) hasn't been released yet, so if you're using something that claims to be RC2, it's from some random git version.  The ABI will be frozen once RC2 is released, so I'll mark the ABI as officially supported in the driver at that point.

As for the "Support for GLX with the Damage and Composite X extensions is enabled" message, all that really means is that AllowGLXWithComposite is enabled and the X server is new enough to actually support it, which has been the default for ages.  I filed a bug to get that message removed (or at least downgraded so that it only shows up with -logverbose 5) to reduce confusion.

---

### Post by Harry33 on 2011-01-26
> **AaronP_ said:**
> xserver 1.10 RC2 (a.k.a. 1.9.99.902) hasn't been released yet, so if you're using something that claims to be RC2, it's from some random git version.  The ABI will be frozen once RC2 is released, so I'll mark the ABI as officially supported in the driver at that point.
...


Aaron, thanks for the answer and the explanation.
What I meant was this.
I have tested xserver 1.9.99.901 series from xorg-edgers PPA in Launchpad.
The nvidia-current_270.18 works (without the glx server extension) with the xserver git version (2:1.9.99.901+git20110111),
but not with the current git version (2:1.9.99.901+git20110124) from that PPA.

With the latter one I get this segfault:

```

Backtrace:
[    16.314] 0: /usr/bin/X (xorg_backtrace+0x26) [0x4689f6]
[    16.314] 1: /usr/bin/X (0x400000+0x6a53a) [0x46a53a]
[    16.314] 2: /lib/libpthread.so.0 (0x7ff90f07c000+0xfd70) [0x7ff90f08bd70]
[    16.314] 3: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7ff9098da000+0x41cf60) [0x7ff909cf6f60]
[    16.314] 4: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7ff9098da000+0x42769a) [0x7ff909d0169a]
[    16.314] 5: /usr/bin/X (AddScreen+0x1a8) [0x428508]
[    16.315] 6: /usr/bin/X (InitOutput+0x294) [0x46fae4]
[    16.315] 7: /usr/bin/X (0x400000+0x217c3) [0x4217c3]
[    16.315] 8: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7ff90dfd1d1e]
[    16.315] 9: /usr/bin/X (0x400000+0x21529) [0x421529]
[    16.315] Segmentation fault at address 0x18
[    16.315] 
Caught signal 11 (Segmentation fault). Server aborting
[    16.315]

```

---

### Post by AaronP_ on 2011-01-26
> **Harry33 said:**
> 
The nvidia-current_270.18 works (without the glx server extension) with the xserver git version (2:1.9.99.901+git20110111),
but not with the current git version (2:1.9.99.901+git20110124) from that PPA.

The ABI changed again between RC1 and current git master, so that doesn't surprise me.  This is why the driver prints the git commit it was compiled against to the log file.  If you're running git snapshot X servers, you'll need to be able to evaluate for yourself whether the ABI changed between the commit the driver was compiled against and the one you're running.

Your safest bet, obviously, is to wait for the ABI to be declared frozen and then use a driver that has the IgnoreABI check disabled.  Your next safest bet (though it's not officially supported) is to use the same snapshot of the server that the driver was compiled against (1.9.99.901 in this case).  If you use something else, all bets are off and if it breaks you get to keep all the pieces.  ;)

---

### Post by Harry33 on 2011-01-26
Thanks Aaron!

For the time being I'll stick to xserver 1.9 series and the latest binary driver (270.18 beta)
and I will wait for the new one.
Really, open source nouveau is not an option for me.

---

### Post by Sealbhach on 2011-01-27
Thanks for the info Aaaron, your work is much appreciated, at least by me! :P

.

---

