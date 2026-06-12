---
title: "pooched by nvidia (and myself)"
date: 2013-09-05
forum: Multimedia Software
---

### Post by milesnorth on 2013-09-05
Installed Kubuntu 12.04 64-bit with the 3rd party software option selected several weeks ago to rebuild my HTPC.  

Updated packages, installed MYTHTV, and then made the fatal mistake.  Read somewhere that steam needed nvidia 310 drivers so I went to the  "additional drivers" in the system menu to change the installed "nvidia 304" driver to "nvidia 310".  Things updated and  I rebooted.   Now I end up at the cli login prompt.  Logged on, mounted the partitions and tried several commands like:

sudo apt-get purge nvidia-current  [or experimental-304, or experimental-310]
sudo apt-get install nvidia-current  [or experimental-304, or experimental-310] 
and so forth ...

So after running all 3 variations of these two commands I still end up at the cli login.  Now I don't know what I've got messed up, so I took a few weeks off to get some patience back.

Any debugging or other advice would be greatly appreciated,

---

### Post by Bucky Ball on 2013-09-05
*Thread moved to **Multimedia & Video**.*

When in the CLI have you tried issuing:
```

startx

```
or 
```

start lightdm
```

(I think that last one is the correct one for Unity if that's applicable.)

If you can get to the grub menu list after boot (where your list of kernels is) select the kernel you normally boot and hit 'e'. Find the kernel line that ends in 'splash', 'quiet' or a combination of the two. Add 'nomodset' after a space to the end of that line (no apostrophes). 

Follow instructions at bottom of screen to continue with normal boot. Any luck? Get to a desktop?

---

### Post by dannyboy79 on 2013-09-05
when you login via the command line, can you view your Xorg.0.log file, what's the error in there

---

### Post by milesnorth on 2013-09-06
Took a look at Xorg.0.log and tried startx.

Xorg.0.log Follows:
```
[    65.562] 
X.Org X Server 1.11.3
Release Date: 2011-12-16

[    65.562] X Protocol Version 11, Revision 0

[    65.562] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu

[    65.562] Current Operating System: Linux microlinux 3.2.0-51-generic #77-Ubuntu SMP Wed Jul 24 20:18:19 UTC 2013 x86_64

[    65.562] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-51-generic root=UUID=ce15c3e7-3d72-41f7-8ea2-1be8878eb58c ro quiet splash

[    65.563] Build Date: 11 April 2013  01:05:39PM
[    65.563] xorg-server 2:1.11.4-0ubuntu10.13 (For technical support please see http://www.ubuntu.com/support) 

[    65.563] Current version of pixman: 0.24.4
[    65.563]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.

[    65.563] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

[    65.563] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep  5 19:20:14 2013

[    65.563] (==) Using config file: "/etc/X11/xorg.conf"

[    65.563] (==) Using system config directory "/usr/share/X11/xorg.conf.d"

[    65.563] (==) No Layout section.  Using the first Screen section.

[    65.563] (==) No screen section available. Using defaults.

[    65.563] (**) |-->Screen "Default Screen Section" (0)

[    65.563] (**) |   |-->Monitor "<default monitor>"

[    65.563] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.

[    65.563] (**) |   |-->Device "Default Device"

[    65.563] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.

[    65.563] (==) Automatically adding devices

[    65.563] (==) Automatically enabling devices

[    65.563] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.

[    65.563]     Entry deleted from font path.
[    65.563] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.

[    65.563]     Entry deleted from font path.

[    65.563] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.

[    65.563]     Entry deleted from font path.

[    65.563] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.

[    65.563]     Entry deleted from font path.

[    65.563] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.

[    65.563]     Entry deleted from font path.

[    65.563] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.

[    65.563]     Entry deleted from font path.

[    65.563] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins

[    65.563] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"

[    65.563] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.

[    65.563] (II) Loader magic: 0x7fddd32e3b00

[    65.563] (II) Module ABIversions:

[    65.563]     X.Org ANSI C Emulation: 0.4

[    65.563]     X.Org Video Driver: 11.0

[    65.563]     X.Org XInput driver : 16.0

[    65.563]     X.Org Server Extension : 6.0

[    65.564] (--) PCI:*(0:1:0:0) 10de:05e2:3842:1264 rev 161, Mem @ 0xf6000000/16777216, 0xd0000000/268435456, 0xf4000000/33554432, I/O @ 0x0000bc00/128, BIOS @ 0x????????/524288

[    65.564] (II) Open ACPI successful (/var/run/acpid.socket)
[    65.564] (II) LoadModule: "extmod"

[    65.565] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so

[    65.565] (II) Module extmod: vendor="X.Org Foundation"

[    65.565]     compiled for 1.11.3, module version = 1.0.0

[    65.565]     Module class: X.Org Server Extension

[    65.565]     ABI class: X.Org Server Extension, version 6.0

[    65.565] (II) Loading extension MIT-SCREEN-SAVER

[    65.565] (II) Loading extension XFree86-VidModeExtension

[    65.565] (II) Loading extension XFree86-DGA

[    65.565] (II) Loading extension DPMS

[    65.565] (II) Loading extension XVideo

[    65.565] (II) Loading extension XVideo-MotionCompensation

[    65.565] (II) Loading extension X-Resource

[    65.565] (II) LoadModule: "dbe"

[    65.565] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so

[    65.565] (II) Module dbe: vendor="X.Org Foundation"

[    65.565]     compiled for 1.11.3, module version = 1.0.0

[    65.565]     Module class: X.Org Server Extension

[    65.565]     ABI class: X.Org Server Extension, version 6.0

[    65.565] (II) Loading extension DOUBLE-BUFFER

[    65.565] (II) LoadModule: "glx"

[    65.565] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so

[    65.579] (II) Module glx: vendor="NVIDIA Corporation"

[    65.579]     compiled for 4.0.2, module version = 1.0.0

[    65.579]     Module class: X.Org Server Extension

[    65.579] (II) NVIDIA GLX Module  310.14  Tue Oct  9 12:14:30 PDT 2012

[    65.579] (II) Loading extension GLX

[    65.579] (II) LoadModule: "record"

[    65.580] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so

[    65.580] (II) Module record: vendor="X.Org Foundation"

[    65.580]     compiled for 1.11.3, module version = 1.13.0

[    65.580]     Module class: X.Org Server Extension

[    65.580]     ABI class: X.Org Server Extension, version 6.0

[    65.580] (II) Loading extension RECORD

[    65.580] (II) LoadModule: "dri"

[    65.580] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so

[    65.580] (II) Module dri: vendor="X.Org Foundation"

[    65.580]     compiled for 1.11.3, module version = 1.0.0

[    65.580]     ABI class: X.Org Server Extension, version 6.0

[    65.580] (II) Loading extension XFree86-DRI

[    65.580] (II) LoadModule: "dri2"

[    65.581] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so

[    65.581] (II) Module dri2: vendor="X.Org Foundation"

[    65.581]     compiled for 1.11.3, module version = 1.2.0

[    65.581]     ABI class: X.Org Server Extension, version 6.0

[    65.581] (II) Loading extension DRI2

[    65.581] (==) Matched nvidia as autoconfigured driver 0

[    65.581] (==) Matched nouveau as autoconfigured driver 1

[    65.581] (==) Matched nv as autoconfigured driver 2

[    65.581] (==) Matched vesa as autoconfigured driver 3

[    65.581] (==) Matched fbdev as autoconfigured driver 4

[    65.581] (==) Assigned the driver to the xf86ConfigLayout

[    65.581] (II) LoadModule: "nvidia"

[    65.581] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so

[    65.581] (II) Module nvidia: vendor="NVIDIA Corporation"

[    65.581]     compiled for 4.0.2, module version = 1.0.0

[    65.581]     Module class: X.Org Video Driver

[    65.581] (II) LoadModule: "nouveau"

[    65.582] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so

[    65.582] (II) Module nouveau: vendor="X.Org Foundation"

[    65.582]     compiled for 1.11.3, module version = 0.0.16

[    65.582]     Module class: X.Org Video Driver

[    65.582]     ABI class: X.Org Video Driver, version 11.0

[    65.582] (II) LoadModule: "nv"

[    65.582] (WW) Warning, couldn't open module nv

[    65.582] (II) UnloadModule: "nv"

[    65.582] (II) Unloading nv

[    65.582] (EE) Failed to load module "nv" (module does not exist, 0)

[    65.582] (II) LoadModule: "vesa"

[    65.582] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so

[    65.582] (II) Module vesa: vendor="X.Org Foundation"

[    65.582]     compiled for 1.11.3, module version = 2.3.0

[    65.582]     Module class: X.Org Video Driver

[    65.582]     ABI class: X.Org Video Driver, version 11.0

[    65.582] (II) LoadModule: "fbdev"

[    65.583] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so

[    65.583] (II) Module fbdev: vendor="X.Org Foundation"

[    65.583]     compiled for 1.11.3, module version = 0.4.2

[    65.583]     ABI class: X.Org Video Driver, version 11.0

[    65.583] (==) Matched nvidia as autoconfigured driver 0

[    65.583] (==) Matched nouveau as autoconfigured driver 1

[    65.583] (==) Matched nv as autoconfigured driver 2

[    65.583] (==) Matched vesa as autoconfigured driver 3

[    65.583] (==) Matched fbdev as autoconfigured driver 4

[    65.583] (==) Assigned the driver to the xf86ConfigLayout

[    65.583] (II) LoadModule: "nvidia"

[    65.583] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so

[    65.583] (II) Module nvidia: vendor="NVIDIA Corporation"

[    65.583]     compiled for 4.0.2, module version = 1.0.0

[    65.583]     Module class: X.Org Video Driver

[    65.583] (II) UnloadModule: "nvidia"

[    65.583] (II) Unloading nvidia

[    65.583] (II) Failed to load module "nvidia" (already loaded, 32733)

[    65.583] (II) LoadModule: "nouveau"

[    65.583] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so

[    65.583] (II) Module nouveau: vendor="X.Org Foundation"

[    65.583]     compiled for 1.11.3, module version = 0.0.16

[    65.583]     Module class: X.Org Video Driver

[    65.583]     ABI class: X.Org Video Driver, version 11.0

[    65.583] (II) UnloadModule: "nouveau"

[    65.583] (II) Unloading nouveau

[    65.583] (II) Failed to load module "nouveau" (already loaded, 32733)

[    65.583] (II) LoadModule: "nv"

[    65.583] (WW) Warning, couldn't open module nv

[    65.584] (II) UnloadModule: "nv"

[    65.584] (II) Unloading nv

[    65.584] (EE) Failed to load module "nv" (module does not exist, 0)

[    65.584] (II) LoadModule: "vesa"

[    65.584] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so

[    65.584] (II) Module vesa: vendor="X.Org Foundation"

[    65.584]     compiled for 1.11.3, module version = 2.3.0

[    65.584]     Module class: X.Org Video Driver

[    65.584]     ABI class: X.Org Video Driver, version 11.0

[    65.584] (II) UnloadModule: "vesa"

[    65.584] (II) Unloading vesa

[    65.584] (II) Failed to load module "vesa" (already loaded, 0)

[    65.584] (II) LoadModule: "fbdev"

[    65.584] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so

[    65.584] (II) Module fbdev: vendor="X.Org Foundation"

[    65.584]     compiled for 1.11.3, module version = 0.4.2

[    65.584]     ABI class: X.Org Video Driver, version 11.0

[    65.584] (II) UnloadModule: "fbdev"

[    65.584] (II) Unloading fbdev

[    65.584] (II) Failed to load module "fbdev" (already loaded, 0)

[    65.584] (II) NVIDIA dlloader X Driver  310.14  Tue Oct  9 11:54:19 PDT 2012

[    65.584] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs

[    65.584] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100

[    65.584] (II) NOUVEAU driver for NVIDIA chipset families :

[    65.584]     RIVA TNT        (NV04)

[    65.584]     RIVA TNT2       (NV05)

[    65.584]     GeForce 256     (NV10)

[    65.584]     GeForce 2       (NV11, NV15)

[    65.584]     GeForce 4MX     (NV17, NV18)

[    65.584]     GeForce 3       (NV20)

[    65.584]     GeForce 4Ti     (NV25, NV28)

[    65.584]     GeForce FX      (NV3x)

[    65.584]     GeForce 6       (NV4x)

[    65.584]     GeForce 7       (G7x)

[    65.584]     GeForce 8       (G8x)

[    65.584]     GeForce GTX 200 (NVA0)

[    65.584]     GeForce GTX 400 (NVC0)

[    65.584] (II) VESA: driver for VESA chipsets: vesa

[    65.584] (II) FBDEV: driver for framebuffer: fbdev

[    65.584] (++) using VT number 7


[    65.587] (II) Loading sub module "wfb"

[    65.587] (II) LoadModule: "wfb"

[    65.587] (II) Loading /usr/lib/xorg/modules/libwfb.so

[    65.587] (II) Module wfb: vendor="X.Org Foundation"

[    65.587]     compiled for 1.11.3, module version = 1.0.0

[    65.587]     ABI class: X.Org ANSI C Emulation, version 0.4

[    65.587] (II) Loading sub module "ramdac"

[    65.587] (II) LoadModule: "ramdac"

[    65.587] (II) Module "ramdac" already built-in

[    65.587] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so

[    65.587] (II) Loading /usr/lib/xorg/modules/libwfb.so

[    65.587] (WW) Falling back to old probe method for vesa

[    65.587] (WW) Falling back to old probe method for fbdev

[    65.587] (II) Loading sub module "fbdevhw"

[    65.587] (II) LoadModule: "fbdevhw"

[    65.587] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so

[    65.588] (II) Module fbdevhw: vendor="X.Org Foundation"

[    65.588]     compiled for 1.11.3, module version = 0.0.2

[    65.588]     ABI class: X.Org Video Driver, version 11.0

[    65.588] (EE) open /dev/fb0: No such file or directory

[    65.588] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32

[    65.588] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32

[    65.588] (==) NVIDIA(0): RGB weight 888

[    65.588] (==) NVIDIA(0): Default visual is TrueColor

[    65.588] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)

[    65.588] (**) NVIDIA(0): Option "NoLogo" "True"

[    65.588] (**) NVIDIA(0): Enabling 2D acceleration

[    65.588] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the

[    65.588] (EE) NVIDIA(0):     system's kernel log for additional error messages and

[    65.588] (EE) NVIDIA(0):     consult the NVIDIA README for details.

[    65.588] (EE) NVIDIA(0):  *** Aborting ***

[    65.588] (EE) NVIDIA(0): Failing initialization of X screen 0

[    65.588] (II) UnloadModule: "nvidia"

[    65.588] (II) Unloading nvidia

[    65.588] (II) UnloadModule: "wfb"

[    65.588] (II) Unloading wfb

[    65.588] (EE) Screen(s) found, but none have a usable configuration.

[    65.588] 
Fatal server error:

[    65.588] no screens found

[    65.588] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 

[    65.588] Please also check the log file at "/var/log/Xorg.0.log" for additional information.

[    65.588] 

[    65.590]  ddxSigGiveUp: Closing log

[    65.590] Server terminated with error (1). Closing log file.


```

Startx gave bunch of line reports, the gist of which was:
Nvidia: API mismatch
Kernal component is 304.48
Nvidia component is 310.14

How does one get the Nvidia components to match?
Does steam really need nvidia-experimental-310 to work?

Thanks for the feedback

---

### Post by Bucky Ball on 2013-09-06
> Does steam really need nvidia-experimental-310 to work?

No doubt you can find that out from here, but from a quick sniff, no. Says works in 12.04 and 12.10 (and Kubuntu) and mentions nothing of additional software. (One page I've looked at has it working with OpenGL, no proprietary drivers, without issue.)

[https://support.steampowered.com/kb_article.php?ref=1313-QIPD-5381](https://support.steampowered.com/kb_article.php?ref=1313-QIPD-5381)

There are also links to Steam/Linux blogs and forums at that link which you will/might find helpful. Easiest way to find out if proprietary drivers (and the 3.10 specifically) are required is to get rid of the 3.10 Nvidia driver, get back to a working system, as it was, and try it.

---

### Post by oldfred on 2013-09-06
What nVidia chip/card do you have?
sudo lshw -c display


Also with some versions of Ubuntu you needed headers first. I did not need them with 12.04 but did with 12.10. Not sure then if the newer 12.04 versions may need them or not.  (They should be installed if needed anyway).

---

### Post by milesnorth on 2013-09-06
> **Bucky Ball said:**
> Easiest way to find out if proprietary drivers (and the 3.10 specifically) are required is to get rid of the 3.10 Nvidia driver, get back to a working system, as it was, and try it.

Good point, it's all moot until the system works again.  Any ideas how to get the system lined up again with the Nvidia API mismatch between the kernel with 304.48 drivers and the Nvidia component using ver. 310.14.  How does one purge Nvidia and/or rebuild it again?

P.S. a 260 GTX card

---

### Post by oldfred on 2013-09-06
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:

 sudo apt-get purge nvidia-common
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

Also see 2a in this post

 Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

---

### Post by milesnorth on 2013-09-08
> **oldfred said:**
> # Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:

 sudo apt-get purge nvidia-common
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

Also see 2a in this post

 Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

Got x started with the help of info above from oldfred.

```
dpkg --get-selections | grep nvidia
sudo apt-get purge nvidia-common
sudo apt-get purge nvidia*
dpkg --get-selections | grep nvidia
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo apt-get update
sudo apt-get install linux-source
sudo apt-get install linux-headers-generic
sudo apt-get install nvidia-current-updates

then shutdown
```

I don't know if I can call this solved though.  The projector screen doesn't open applications (except Mythtv), the font is too small to read, but the keyboard works.  The monitor screen opens all other windows which are then  automatically pinned to the upper left corner of the display with the top window bar missing and the keyboard doesn't work.  I think I'm going to reinstall and work out all display management problems from scratch.

Thanks everyone for your help.

---

