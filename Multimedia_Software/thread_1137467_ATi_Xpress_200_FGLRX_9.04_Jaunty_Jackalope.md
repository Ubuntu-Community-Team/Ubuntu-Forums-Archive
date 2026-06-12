---
title: "ATi Xpress 200 FGLRX 9.04 Jaunty Jackalope"
date: 2009-04-25
forum: Multimedia Software
---

### Post by sti11_learning on 2009-04-25
I upgraded to 9.04 this morning. Prior to upgrading I was using FGLRX 8.543 for my Xpress 200. I had not realised that AMD dropped support in Febuary for that chipset and thought that there would be no problems upgrading. It was not till after upgrading that I went AMD's site ([http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)) and found that they had apparently dropped support for that chipset. (That is, if I understood it correctly)

So I was wondering if there is any way to put FGLRX version 8.543 in place of 8.600. I tried adding the intrepid repos back in then locking the version of xorg-driver-fglrx at 8.543 but that failed miserably and I had to boot to recovery mode to remove the package.

So, any ideas on how to get FGLRX working in 9.04 or am I going to have to reinstall? Thanks in advance. :)

---

### Post by sti11_learning on 2009-04-26
Bump. :)

---

### Post by sdraft on 2009-04-26
I'm waiting for a solution too...

It seems that maybe open source driver with a patch may fix our problem though.

---

### Post by Sand &amp; Mercury on 2009-04-26
Unfortunately with Jaunty it's the open source Radeon driver or bust. Using the last Catalyst before support was dropped won't work, because it doesn't work with the latest version of Xorg that Jaunty uses.

ATi hath forsaken us.

---

### Post by sti11_learning on 2009-04-27
Thanks for the answers. Well, if nothing else, I now have a good reason to upgrade my hardware.:)

SL

---

### Post by k4ever on 2009-04-27
There has got to be a better way! I'm using a laptop (Gateway 7510gx) with an ATI Mobility Radeon X600. I want to continue using Jaunty but I need the fglrx driver. The open source driver does not support the extension I need to run my favorite game (Red Alert 3) in Wine. I installed Jaunty and the open source driver keeps locking up when I try to play Nexuiz, Armagetron, Alien Arena, and Scorched3d. So gaming seems to be completely out of the question for me with Jaunty. Is there a way to make the legacy fglrx driver work with the new xorg? This is keeping me from switching completely to Jaunty and this will definitely end my run with Ubuntu until I have enough money to replace my laptop.

---

### Post by stuart.trusty on 2009-04-28
Greetings,

I can think of a couple potential directions for a solution to this problem.  

First off, I do not know what the benefit was in moving to the new xorg-server in Jaunty, except imagning some issue of it working better in the Jaunty kernel 2.6.28-11.  (Can anyone confirm why the imperative to run xorg 1:7.4~5ubuntu18 in Jaunty?)  

I am pretty sure the last version of the xorg xserver in 8.10 would run just fine in Jaunty, meaning compatibility with fglrx.  However, that would mean that the old kernel from 8.10 (2.6.27-11) would have to be used to make this work, which would break all the other kernel modules from Jaunty.  Probably not good.

I would imagine that the xserver from 8.10 could be compiled from scratch in Jaunty without incident, meaning the previous fglrx (not 9.04) would remain compatible with the xserver from 8.10 and kernel 2.6.28-11.  That is probably the solution.  

I also imagine that a commercial xserver could be dropped in place with the radeon xpress 200m acceleration in place, but that is obviously at least US$50 and a hassle.

Perhaps sometime soon, the xserver-ati driver will work for the 200m, as I do see that there is some code being inserted to fix glxgears running at 100fps or less, but even best case will be around 1000fps... when the fglrx seems to be more like 2000fps- still not a great solution.  

Would anyone like to compile the Ubuntu 8.10 xserver from scratch and make a private repo for the resulting Jaunty-compatible xorg and fglrx, or is my thinking here fundamentally flawed?

Cheers,
Stuart Trusty
Atlanta, USA

---

### Post by stuart.trusty on 2009-04-29
Regarding above... looking further:

From x.org website:
The current X.Org release is [X11R**7.4**]("http://www.x.org/wiki/Releases/7.4")**.**  The next major release will be [X11R7.5]("http://www.x.org/wiki/Releases/7.5").

From Dselect inside Jaunty, regarding xorg:
xorg         1:**7.4**~5ubun

From ATI website, on version 9.3 of the catalyst / fglrx drivers, which are stated to be the **correct version for Xpress 200m**...  ([http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English) ) ...

States:

Automated installer and Display Drivers for X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3, or **7.4**


Conclusion:  I see no reason why this should not work

---

### Post by antario91 on 2009-04-29
Anyhow... it doesn't work. Neither for me... :( I always had problems with OpenGL applications with FGLRX and thought that maybe Jaunty will help... I am pretty annoyed, that it didn't!

---

### Post by stuart.trusty on 2009-04-29
The problem is here:

xerver-xorg 2:_**1.6**_.0-0ub

It is an API/ABI change rendering previous versions (9.3 and pre) useless.

I still don't see a reason why Jaunty's xorg and friends can't simply be removed, then installed from an Ubunut 8.10 source, and then catalyst 9.3 installed from the ati installer.  It does not appear to be anything related to the kernel.

---

### Post by mihai.ile on 2009-04-29
Well I think that ATI dropped support too early and second I don't blame Ubuntu for bringing the latest and greatest but should gave an option for all those affected by ATI blacklist and provide an alternate compatible xorg for jaunty.

There is just so many people complaining everywhere....

EDIT: I think we could all gather over here to share available information/solutions/tips about the issue: [http://ubuntuforums.org/showthread.php?t=1133931](http://ubuntuforums.org/showthread.php?t=1133931)

---

### Post by lordmorgoth on 2009-04-29
I have encountered the same problem here.

VGA: Asus EAX850 with ATI Radeon X850 chipset.

I tried installing the fglrx using the repos, my system's X crashed big time. (ie had to re-install ubuntu)
Tried downloading it using Envy, X crashed again. (ie had to re-install ubuntu)
Tried to compile the driver provided from ATI (9.3) or even produce a package from the installer. not leaving room for u to speculate X CRASHED...(ie had to re-install ubuntu)

...and certanly the MESA driver is messed up. i have only 4 display resolution and none of them is compatible with the human eye :)

HELP !!!!

---

### Post by stuart.trusty on 2009-04-29
Greetings,

I don't have it working, but I got very close.  What I did was:

1.  quit X, goto shell prompt as root and remove xorg and all xserver-xorg packages, et al.
2.  put in the 8.10 Intrepid disk and ran 'apt-cdrom add' to get the correct sources.list
3.  commented out all but the CD
4.  reinstalled xorg and xserver-xorg from 8.10
5.  ran X (works fine)
6.  secured ati-driver-installer-9-3-x86.x86_64.run from ATI website and ran it
7.  _recognizes, compiles, and installs flawlessly_
8.  ran X (had wrong screen size)
9.  ran ati-config --initial (something something, as said in the final screen of the ati installer)
10.  runs great.



modules DRM and radeon install just fine:

#lsmod

radeon                357792  1 
drm                   123232  2 radeon

but, fglrx gives strange errors that look highly correctable:


root@nirvana:~# modprobe -v fglrx
WARNING: All config files need .conf: /etc/modprobe.d/nvidia-kernel-nkc, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
insmod /lib/modules/2.6.28-11-generic/updates/dkms/fglrx.ko 
FATAL: Error inserting fglrx (/lib/modules/2.6.28-11-generic/updates/dkms/fglrx.ko): Operation not permitted

kernel reports from /var/log/messages:

Apr 29 18:03:42 nirvana kernel: [341775.163933] [fglrx] Maximum main memory to use for locked dma buffers: 1619 MBytes.
Apr 29 18:03:42 nirvana kernel: [341775.164058] [fglrx]   vendor: 1002 device: 5975 count: 1
Apr 29 18:03:42 nirvana kernel: [341775.167883] [fglrx] ioport: bar 1, base 0xc000, size: 0x100
Apr 29 18:03:42 nirvana kernel: [341775.169599] [fglrx] Driver built-in PAT support is enabled successfully


BUT, here is where it falls down...

last line from dmesg...

[341775.171242] [fglrx:firegl_init_module] *ERROR* firegl_stub_register failed


I know I got close.  I am posting this right now using the Xserver from Intrepid, the ATI-configured /etc/x11/xorg.conf after it successfully compiled the Xpress 200m compatible Radeon 9.3 software against Intrepid's Xserver, and everything else is Jaunty.  

ldconfig was run.  tried a -f when modprobing fglrx.  

Someone throw us a bone here?

Thanks in advance,
Stuart

---

### Post by stuart.trusty on 2009-04-29
** Update:  it looks like fglrx for the 200m may have broken at ubuntu 8.10, not in 9.04.  i did the two upgrades in succession, and i am hard pressed to see much success with Intrepid 8.10 running fglrx for the xpress 200m.  that means that my process may have been OK below, but I need to back up to the xserver on the 8.04 cd and not 8.10.  I will report when I have this done.


Jaunty is now happy with fglrx on the xpress 200m, just one problem remains.

All you have to do to make fglrx load is :

 "rmmod drm" and "rmmod radeon"

the remaining problem is this:

$glxgears

Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  13
  Current serial number in output stream:  13


sysadmin@nirvana:~$ uname -a
Linux nirvana 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux


sysadmin@nirvana:~$ lsmod
Module                  Size  Used by
fglrx                2361128  0 

[342374.509766] [fglrx] Maximum main memory to use for locked dma buffers: 1619 MBytes.
[342374.509995] [fglrx]   vendor: 1002 device: 5975 count: 1
[342374.514917] [fglrx] ioport: bar 1, base 0xc000, size: 0x100
[342374.519804] [fglrx] Driver built-in PAT support is enabled successfully
[342374.519946] [fglrx] module loaded - fglrx 8.59.2 [Mar 13 2009] with 1 minors



/var/log/Xorg.0.log reports:
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux nirvana 2.6.28-11-generic #42-Ubuntu SMP Fri Apr
 17 01:58:03 UTC 2009 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd) 
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr 29 18:37:34 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
        Entry deleted from font path.
(==) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/
X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:u
nscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/
X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
        /usr/share/fonts/X11/misc,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/cyrillic,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7b7320
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 4.1
        X.Org XInput driver : 2.1
        X.Org Server Extension : 1.1
        X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0@1:5:0) ATI Technologies Inc RS482 [Radeon Xpress 200M] rev 0, Mem @
 0xd0000000/268435456, 0xfbff0000/65536, I/O @ 0x0000c000/256, BIOS @ 0x????????
/131072
(II) System resource ranges:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [5] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [6] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [7] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [8] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [9] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [10] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [11] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [12] -1 0       0xffffffff - 0xffffffff (0x1) MX[b]
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [14] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [15] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [16] -1 0       0xffffffff - 0xffffffff (0x1) MX[b]
        [17] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [18] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [19] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [20] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [21] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [22] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [23] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [24] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [25] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [26] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [27] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [28] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [29] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
(II) "extmod" will be loaded. This was enabled by default and also specified in 
the config file.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the
 config file.
(II) "freetype" will be loaded. This was enabled by default and also specified i
n the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the
 config file.
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 7.4.0, module version = 1.0.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 1.5.2, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 7.4.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 1.1
(==) AIGLX disabled
(WW) fglrx: Force AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.0.0
        ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "type1"

(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.1.0
        ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "fglrx"

(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
        compiled for 1.4.99.906, module version = 8.59.2
        Module class: X.Org Video Driver
(II) LoadModule: "kbd"

(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 1.4.99.905, module version = 1.3.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "mouse"

(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 1.4.99.905, module version = 1.3.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "wacom"

(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 4.3.99.902, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.1
(II) Wacom driver level: 47-0.8.1-4 $
(II) LoadModule: "synaptics"

(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 0.15.2
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.1
(II) Primary Device is: PCI 01@00:05:0
(WW) Falling back to old probe method for fglrx
(II) ATI Proprietary Linux Driver Version Identifier:8.59.2
(II) ATI Proprietary Linux Driver Release Identifier: 8.593                     
           
(II) ATI Proprietary Linux Driver Build Date: Mar 12 2009 23:40:06
(II) Loading PCS database from /etc/ati/amdpcsdb
(WW) This ATI Proprietary Linux Driver does not guarantee support of video drive
r ABI higher than 2.0
(WW) Video driver ABI version of the X server is 4.1
(II) AMD ASIC control file status: R2 S1 B330 N330 T329
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:0:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:1:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:4:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:6:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:7:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
(--) Assigning device section with no busID to primary device
(--) Chipset Supported AMD Graphics Processor (0x5975) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:0:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:1:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:4:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:6:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:7:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
(II) AMD Video driver is running on a device belonging to a group targeted for t
his release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [5] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [6] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [7] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [8] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [9] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [10] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [11] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [12] -1 0       0xffffffff - 0xffffffff (0x1) MX[b]
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [14] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [15] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [16] -1 0       0xffffffff - 0xffffffff (0x1) MX[b]
        [17] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [18] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [19] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [20] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [21] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [22] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [23] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [24] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [25] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [26] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [27] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [28] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [29] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
(II) fglrx(0): pEnt->device->identifier=0x27ec450
(II) resource ranges after probing:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [5] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [6] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [7] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [8] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [9] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [10] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [11] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [12] -1 0       0xffffffff - 0xffffffff (0x1) MX[b]
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [14] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [15] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [16] -1 0       0xffffffff - 0xffffffff (0x1) MX[b]
        [17] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [18] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [19] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [20] 0  0       0x000a0000 - 0x000affff (0x10000) MS[b]
        [21] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[b]
        [22] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[b]
        [23] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [24] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [25] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [26] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [27] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [28] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [29] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [30] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [31] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [32] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [33] 0  0       0x000003b0 - 0x000003bb (0xc) IS[b]
        [34] 0  0       0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 0.1.0
        ABI class: X.Org Video Driver, version 4.1
(II) fglrx(0): PCI bus 1 card 5 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(II) fglrx(0): 10BitPixelFormat disabled by default
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"

(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
        compiled for 1.4.99.906, module version = 8.59.2
(--) fglrx(0): Chipset: "ATI Radeon Xpress Series      " (Chipset = 0x5975)
(--) fglrx(0): (PciSubVendor = 0x10cf, PciSubDevice = 0x13b8)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfbff0000
(--) fglrx(0): I/O port at 0x0000c000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI Radeon<AE> Xpress 1150    
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: MS48
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card1
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card2
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card3
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card4
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card5
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card6
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card7
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card8
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card9
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card10
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card11
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card12
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card13
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card14
drmOpenByBusid: drmOpenMinor returns -1
(WW) fglrx(0): Failed to open DRM connection
(--) fglrx(0): Video RAM: 1052672 kByte, Type: DDR SGRAM / SDRAM
(EE) fglrx(0): [FB] Can not get FB MC address range.
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): ***Display: ConnectedDisplayTypes=0x00000002, disabled=0x00000000
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0):  Display1: No EDID information from DDC.
(EE) fglrx(0): Unknown EDID version 0
(II) fglrx(0):  Display1: Failed to get EDID information. 
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  2 power states available:
(II) fglrx(0):   1. 401/401MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 100/133MHz @ 60Hz []
(==) fglrx(0): QBS disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 14 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x800 (pitch 0)
(**) fglrx(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"x60.0   68.90  1280 1288 1336 1408  800 802 805 816 (48.9 kHz)
(**) fglrx(0): *Mode "1280x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   68.90  1280 1288 1336 1408  768 784 787 816 (48.9 kHz)
(**) fglrx(0): *Mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   68.90  1024 1160 1208 1408  768 784 787 816 (48.9 kHz)
(**) fglrx(0): *Mode "848x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"x60.0   68.90  848 1072 1120 1408  480 640 643 816 (48.9 kHz)
(**) fglrx(0): *Mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   68.90  800 1048 1096 1408  600 700 703 816 (48.9 kHz)
(**) fglrx(0): *Mode "720x576": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"x60.0   68.90  720 1008 1056 1408  576 688 691 816 (48.9 kHz)
(**) fglrx(0): *Mode "720x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   68.90  720 1008 1056 1408  480 640 643 816 (48.9 kHz)
(**) fglrx(0): *Mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   68.90  640 968 1016 1408  480 640 643 816 (48.9 kHz)
(**) fglrx(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   68.90  640 968 1016 1408  400 600 603 816 (48.9 kHz)
(**) fglrx(0):  Default mode "640x350": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"x60.0   68.90  640 968 1016 1408  350 575 578 816 (48.9 kHz)
(**) fglrx(0):  Default mode "512x384": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   68.90  512 904 952 1408  384 592 595 816 (48.9 kHz)
(**) fglrx(0):  Default mode "400x300": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   68.90  400 848 896 1408  300 700 703 816 doublescan (48.9 kHz)
(**) fglrx(0):  Default mode "320x240": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   68.90  320 808 856 1408  240 640 643 816 doublescan (48.9 kHz)
(**) fglrx(0):  Default mode "320x200": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   68.90  320 808 856 1408  200 611 614 816 doublescan (48.9 kHz)
(==) fglrx(0): DPI set to (96, 96)
(--) fglrx(0): Virtual size is 1280x800 (pitch 1280)
(**) fglrx(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"x60.0   68.90  1280 1288 1336 1408  800 802 805 816 (48.9 kHz)
(**) fglrx(0): *Mode "1280x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   68.90  1280 1288 1336 1408  768 784 787 816 (48.9 kHz)
(**) fglrx(0): *Mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   68.90  1024 1160 1208 1408  768 784 787 816 (48.9 kHz)
(**) fglrx(0): *Mode "848x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"x60.0   68.90  848 1072 1120 1408  480 640 643 816 (48.9 kHz)
(**) fglrx(0): *Mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   68.90  800 1048 1096 1408  600 700 703 816 (48.9 kHz)
(**) fglrx(0): *Mode "720x576": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"x60.0   68.90  720 1008 1056 1408  576 688 691 816 (48.9 kHz)
(**) fglrx(0): *Mode "720x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   68.90  720 1008 1056 1408  480 640 643 816 (48.9 kHz)
(**) fglrx(0): *Mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   68.90  640 968 1016 1408  480 640 643 816 (48.9 kHz)
(**) fglrx(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   68.90  640 968 1016 1408  400 600 603 816 (48.9 kHz)
(**) fglrx(0):  Default mode "640x350": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"x60.0   68.90  640 968 1016 1408  350 575 578 816 (48.9 kHz)
(**) fglrx(0):  Default mode "512x384": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   68.90  512 904 952 1408  384 592 595 816 (48.9 kHz)
(**) fglrx(0):  Default mode "400x300": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   68.90  400 848 896 1408  300 700 703 816 doublescan (48.9 kHz)
(**) fglrx(0):  Default mode "320x240": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   68.90  320 808 856 1408  240 640 643 816 doublescan (48.9 kHz)
(**) fglrx(0):  Default mode "320x200": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   68.90  320 808 856 1408  200 611 614 816 doublescan (48.9 kHz)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.2.0
        ABI class: X.Org Video Driver, version 4.1
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"

(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(II) fglrx(0): Direct rendering disabled
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [5] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [6] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [7] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [8] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [9] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [10] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [11] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [12] -1 0       0xffffffff - 0xffffffff (0x1) MX[b]
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [14] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [15] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [16] -1 0       0xffffffff - 0xffffffff (0x1) MX[b]
        [17] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [18] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [19] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [20] 0  0       0x000a0000 - 0x000affff (0x10000) MS[b](OprU)
        [21] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[b](OprU)
        [22] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[b](OprU)
        [23] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [24] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [25] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [26] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [27] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [28] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [29] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [30] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [31] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [32] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [33] 0  0       0x000003b0 - 0x000003bb (0xc) IS[b](OprU)
        [34] 0  0       0x000003c0 - 0x000003df (0x20) IS[b](OprU)
(II) fglrx(0): driver needs X.org 1.4.x.y with x.y >= 99.906
(II) fglrx(0): detected X.org 7.4.2.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0x0 FBMappedSize: 0x08000000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 7391
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        Solid Horizontal and Vertical Lines
        Setting up tile and stipple cache:
                32 128x128 slots
                32 256x256 slots
                16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) LoadModule: "amdxmm"

(II) Loading /usr/lib/xorg/modules//amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
        compiled for 1.4.99.906, module version = 1.0.0
        ABI class: X.Org Server Extension, version 1.1
(EE) fglrx(0): XMM failed to open CMMQS connection.
(II) fglrx(0): XMM failed to initialize!
(II) fglrx(0): Enable composite support successfully
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI capable
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) /dev/wacom: Tablet PC buttons on 
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) /dev/wacom: Tablet PC buttons on 
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) /dev/wacom: Tablet PC buttons on 
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) Synaptics touchpad driver version 0.15.2
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event10
(II) Synaptics Touchpad: x-axis range 0 - 1023
(II) Synaptics Touchpad: y-axis range 0 - 767
(**) Option "Device" "/dev/input/event10"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (stylus)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) evaluating device (cursor)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) evaluating device (eraser)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: TOUCHPAD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) Synaptics Touchpad: x-axis range 0 - 1023
(II) Synaptics Touchpad: y-axis range 0 - 767
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 2.0.99
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.1
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device PS/2 Mouse
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event9"
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event7"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
(II) config/hal: Adding input device Fujitsu FUJ02B1
(**) Fujitsu FUJ02B1: always reports core events
(**) Fujitsu FUJ02B1: Device: "/dev/input/event5"
(II) Fujitsu FUJ02B1: Found keys
(II) Fujitsu FUJ02B1: Configuring as keyboard
(II) XINPUT: Adding extended input device "Fujitsu FUJ02B1" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Fujitsu FUJ02B1: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Fujitsu FUJ02B1: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Fujitsu FUJ02B1: xkb_layout: "us"
(II) config/hal: Adding input device Fujitsu FUJ02E3
(**) Fujitsu FUJ02E3: always reports core events
(**) Fujitsu FUJ02E3: Device: "/dev/input/event6"
(II) Fujitsu FUJ02E3: Found keys
(II) Fujitsu FUJ02E3: Configuring as keyboard
(II) XINPUT: Adding extended input device "Fujitsu FUJ02E3" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Fujitsu FUJ02E3: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Fujitsu FUJ02E3: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Fujitsu FUJ02E3: xkb_layout: "us"
(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
(II) Synaptics touchpad driver version 0.15.2
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(**) Option "Device" "/dev/input/event10"
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(WW) AlpsPS/2 ALPS GlidePoint can't grab event device, errno=16
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(II) UnloadModule: "kbd"
(II) UnloadModule: "mouse"
(II) UnloadModule: "synaptics"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) PS/2 Mouse: Close
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(WW) AlpsPS/2 ALPS GlidePoint can't grab event device, errno=16
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(II) UnloadModule: "kbd"
(II) UnloadModule: "mouse"
(II) UnloadModule: "synaptics"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) PS/2 Mouse: Close
(II) UnloadModule: "evdev"
(II) Video Bus: Close
(II) UnloadModule: "evdev"
(II) Fujitsu FUJ02B1: Close
(II) UnloadModule: "evdev"
(II) Fujitsu FUJ02E3: Close
(II) UnloadModule: "evdev"
(II) UnloadModule: "synaptics"
(II) UnloadModule: "wacom"
(II) UnloadModule: "wacom"
(II) UnloadModule: "wacom"

---

### Post by stuart.trusty on 2009-04-30
Well, it works now, but it is rather anticlimactic...

sysadmin@nirvana:~$ lspci -v | grep Xpress
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]

sysadmin@nirvana:~$ glxgears
4440 frames in 5.0 seconds = 885.909 FPS
5560 frames in 5.0 seconds = 1111.460 FPS
5520 frames in 5.0 seconds = 1101.018 FPS

sysadmin@nirvana:~$ uname -a
Linux nirvana 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

sysadmin@nirvana:~dmesg 
<truncated>
[   23.942464] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   23.974748] [fglrx] Maximum main memory to use for locked dma buffers: 1619 MBytes.
[   23.974865] [fglrx]   vendor: 1002 device: 5975 count: 1
[   23.982830] [fglrx] ioport: bar 1, base 0xc000, size: 0x100
[   23.982862] pci 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   23.985394] [fglrx] Driver built-in PAT support is enabled successfully
[   23.985486] [fglrx] module loaded - fglrx 8.59.2 [Mar 13 2009] with 1 minors


I went and grabbed the Xorg packages from 8.04.2, then ran the ATI installer, but it was a much different game then grabbing the ones from 8.10.  The dependencies create an enormous problem, largely centric to x11-common.  It was more or less a tearing down of Jaunty to the very basics, letting dselect have its way with removing everything related to X according to the 8.04.2 sources.list, and then putting the jaunty sources.list back in and reinstalling the removed packages.  However, this solution is not even fodder for those not faint of heart, it is a kludge from the 3rd layer of hell.  I don't recommend it to anyone, and my Fujitsu A3120 laptop and its abandoned ATI driver is all of one year old.

However, it does show that the cause is not lost- this is easily fixable with some alternate dependencies or a slightly forked jaunty tree centric to the X server from 8.04.  X is essentially a standalone system and there is no reason I can see to make everything but the kitchen sink a dependency on one version of x11-common that is probably uniformly compatible with all the dependencies to begin with.  

This problem shows some of the weaknesses in the Ubuntu distribution structure, as anyone with an xpress 200m will be permanently frozen into this version of the X server (remember, the ati driver for Jaunty and the xpress 200m doesn't even work at all), but this isn't really a bad thing- the bad thing is that Ubuntu is forcing people to upgrade their X servers in the same manner that Microsoft forces users to upgrade to a new version of Windows based on hardware progress; something which should really be completely optional based on the inevitabiltiy of hardware life cycles- this is why commercial X server solutions should be drag and drop to any Linux platform- X is an independent subsystem that doesn't need to be tethered and chained to the rest of the workings.  Ubuntu needs to model a path forward that is not based on forced-upgrades that fall down at the whim of 3rd party hardware vendors- that is not the Linux way.

I will probably go back to 8.04.2 or even consider going back to Debian, since glxgears working a little faster but things like CoolIris failing silently isn't really my cup of tea.  I hope we can find a solution in the meantime, since this is proof positive that there is no reason whatsoever why Jaunty Jackalope cannot support the Xpress 200m and fglrx subsystems with a little bit of elbow grease, and I'm not even a competent package maintainer or coder.

Cheers,

Stuart Trusty, Chairman
Linux Labs International, Inc.
+1.678.362.2706

---

### Post by Wiebelhaus on 2009-04-30
what the heck , my post ended up in the wrong thread , my bad.

---

### Post by stuart.trusty on 2009-05-01
Really, probably the best solution to this problem is to go back to 8.04.2 Hardy.

Steps:  

0.  Remove the files /vmlinux and /initrd.img
1..  Download and burn the CD (Alternate Installer)
2.  Install in expert mode
3.  At partition time, make sure you DON'T ERASE DATA (if that's important), set your existing ext3 partition as ext3 and mount at "/".
4..  Install away.
5.  Make sure you install the restricted drivers for 2.6.24-23
6. Enable fglrx.

Don't forget to do step 0 or the installer CD will error out.

Cheers,
Stuart

---

### Post by damers21 on 2009-05-02
Hey stuart.trusty, your progress is quite intriguing to me!  Do you mind detailing more specifically, or even step-by-step if you have a spare moment, how I would go about installing the older version of Xorg and ATI's 9.3 drivers on my Jaunty installation?  Thank you in advance for your time and assistance!

---

### Post by stuart.trusty on 2009-05-02
Hi Damers,

I don't like the solution you are requesting and will post an alternate after I test it, but the long and short of backporting the xserver-xorg is below.  I might mention that I probably gave up to soon on the fglrx in Jaunty because I found out the only problem for running Cooliris in Firefox was that the Flash 10.x plug-in wasn't in place.  It was definitely working, just had a depencies headache I didn't want.  

1..  have ati-driver-installer-9-3-x86.x86_64.run handy that you downloaded from ATI.

2.  grab that sporty Ubuntu Hardy 8.04.2 hardy CD and burn it down!

3.  run apt-cdrom add to get the CD source info for sources.list in /etc/apt.  put the line it creates in a file called sources.cd.

4..  I'd quit out of X with /etc/init.d/gdm stop (or kdm or whatever), and get ready to get root on one of the virtual ttys.  (sudo su -)

5.  run dselect.  if you haven't haven't installed it its apt-get install dselect.

6.  deselect the xserver-xorg, xserver-xorg-core, xorg packages.  when it complains about dependencies, go ahead and allow it to remove all packages it complains about.

7.  mv your /etc/apt/sources.list to /etc/apt/sources.list.was .  mv that /etc/apt/sources.cd to /etc/apt/sources.list

8.  run apt-get update

9.  go into deselect and add the xserver-xorg, xserver-xorg-core, xorg, etc. and all the supporting files it wants.  when you are done, put the old sources.list.was back in place and keep a copy of your cd-based sources.list.  running apt-get update again probably wouldn't hurt either.

10.  its time to run that ati installer.... sh ati-driver-installer-9-3-x86.x86_64.run . 

11.  modprobe your fglrx.  if it gives an error, make sure you rmmod-ed those modules i mentioned a post or two ago.

12.  /etc/init.d/gdm restart.

13.  that's it.  you are now running fglrx in jaunty with 3d accelration using the xpress 200m, and theoretically this should not interfere with any other apps.  the problem is so many things are dependently related to x11-common between 8.04 and 8.10 that it will make you want to pull your hair out.  i do mean 8.10- backporting the 8.10 xserver to 9.04 is a piece of cake, but you lose all the 3d acccerlation even though fglrx looks like it works.

For my next trick, I am getting Hardy upgraded to current kernel 2.6.29.2 with fglrx, sound, atheros ath_9k (broke in 8.10 or 9.04 somewhere for me and couldnt resolve) and the em28xx driver (the pinnacle pro usb stick) in working order, which is getting close to the same thing, since I intend to use the jaunty repositories to install things like me-tv, mplayer, etc.   I'll report my progress.  My motivation for doing this is that em28xx has been broken all over the place and incompatible with the stock kernel in Hardy, the atheros driver broke wireless on the way to jaunty (saw networks, wouldnt connect, multiple drivers tried and compiled) and the apps in Jaunty are way more mature (unfortunately Jaunty's kernel didn't fix the em28xx problem anyway).  I would rather deal with going-forward dependencies on applications then core-level x11-common dependencies looking backward.

Cheers,
Stuart

---

### Post by stuart.trusty on 2009-05-02
I think it will be possible to get Jaunty running with fglrx using the ati xpress 200 in a little less dramatic way.  I am experimenting right now.

1..  load up hardy 8.04.2 on your system
2.  upgrade to the kernel of your choice (google: custom kernel the ubuntu way).
3.  install ati-installer to compile and install fglrx.
4.  yay, you're running hardy with fglrx 9.3 (aka 8.593) and a kernel up to 2.6.29.2.  (Note if you are using kernel 2.6.29.1 or 2.6.29.2, you will need to patch fglrx with this patch... [http://liquorix.net/patches/FGLRX-2.6.29-9.2-5.diff](http://liquorix.net/patches/FGLRX-2.6.29-9.2-5.diff)
4.  using dselect, set everything in the x11 section as an =, meaning leave unchanged.
5.  change your sources.list to hardy sources... (sed -e "s/hardy/intrepid/g" < sources.list > new.sources.list... make the new.sources.list your new sources.list file after backing up sources.list)
6.  apt-get update
7.  apt-get dist-upgrade (make sure all the xorg and x11 stuff is held back).
(Update:  * 7a.  must blacklist module evdev in /etc/modprobe.d/blacklist.  keyboard will be munged if not.  Cooliris running still, but notably slower.  All still works however)

8.  go back to step 5, changing intrepid to jaunty, go through to step 7 again and stop.

I think that should leave the kernel of your choice in play, along with the fglrx module, wrapped around the xserver from hardy, but the system is now jaunty.  Will confirm this works in update to this message.  

Cheers,
Stuart

---

### Post by hanspb on 2009-05-05
Keep in mind that this will not give you the extra speed at boot time that            comes from ext4, since 8.04 and 8.10 need to be on an ext3 file system. I look forward to see if this really works.

---

### Post by stuart.trusty on 2009-05-06
hi [hanspb]("http://ubuntuforums.org/member.php?u=21337")

i am going hand off the torch on this.  at the upgrade step from 8.10 to 9.04 one of my selections, an apparently essential one to hold back,  got inadvertently upgraded that sent my proof of concept at 9.04 into non-3d accelerated (2d was ok) because it could not figure out a DRI version according to xorg.log.  the fglrx module loads just fine in 9.04 with the 8.04 xserver under the original kernel, but it is unnecessary to go back that far, just starting with intrepid and its xorg stuff from 8.10 should be fine, that's what i need to settle on right now for more than just fglrx compatibility.

in the plain old Debian days, we dist-upgraded around xorg all the time for similar types of reasons- if it isn't broke, why fix it?  i think holding off just xorg-xserver, xorg and friends in dselect isn't enough, some of the x11-common, libgl1-mesa-dri,  libX11, and x11-stuff probably needs to be held back also for things to interroperate in 9.04, even though the kernel and fglrx and xorg are the exact same programs that were running before- the essence of the problem is solved.

I have gotten it this far, its just a couple of hours away from someone testing it against 8.10 -> 9.04 with dselect, I just can't spare this box from production any more.

Cheers,
Stuart

---

### Post by RavanH on 2009-05-15
Thank you, stuart.trusty for trying and sharing. I completely understand you cannot keep on trying and I commend you for getting this far!

After doing a clean Jaunty install myself, and failing with the FGLRX driver for my Radeon Xpress 200M card, I have decided to stick with the open source radeon driver. This ofcource means no OpenGL / direct 3D but then I get stable multiple monitor support in exchange ;)

I just hope devs will pick up on this problem because there seem to be soooo many ATI card users (lots of which have a mobo integrated Radeon Xpress 200 M in their laptop, so upgrading video card is not an option) horribly surprised to find support for their card dropped after upgrade. Some report not even being able to boot up / log in any more because of this.

After all, when I take a look at the AMD site to find what driver they recommend for my card... Guess what? I get the FGLRX driver!!

Or will there be OpenGL support on the radeon driver in the near future?

---

### Post by jecompton on 2009-05-21
I'm using ratpoison and I'm afraid that the upgrade will hose my wm.

Sarcasm aside, I boot into gnome now and then to wow non-linux people w/ compiz. That's worth something.

The idea of upgrading to 9.04 and having an unbootable machine is unappealing, though.

I completely agree RavanH, I've got a Compaq presario v5000 (amd) as my everyday work machine, and it has a Radeon Xpress 200m built in. Mine's probably just like you described. When Intrepid reaches the end, hopefully I'll have a new machine or I'll have to downgrade to LTS, switch distros, or something else drastic. I wonder if I can run ratpoison on windows.

Here's my vote saying I wish they hadn't dropped support for the card.

---

### Post by dardf on 2009-06-18
Yeah I was extremely dissapointed they dropped the card as well. It seems really unreasonable that a relatively new card with wide usage could be cut out in such a manner. 
Another thing is that I was extremely unhappy with the overall 2d/3d performance I was getting with this card using the mesa drivers with jaunty. Video playback was sluggish, and even when playing ppracer, my laptop would labor and stutter heavily. 
```
$ glxgears
979 frames in 5.0 seconds = 195.553 FPS
922 frames in 5.0 seconds = 184.016 FPS
963 frames in 5.0 seconds = 192.446 FPS
```
What I ended up doing (for the time being, until a fglrx fix is made) was to download the newest radeon-rewrite ([http://cgit.freedesktop.org/mesa/mesa/commit/?h=radeon-rewrite]("http://cgit.freedesktop.org/mesa/mesa/commit/?h=radeon-rewrite")) and apply it over the ubuntu provided libs.
```

./autogen.sh --prefix=/usr --with-dri-drivers=radeon,r200,r300
make
sudo make install
restarted
```

You can also use the --disable-gallium flag during autogen, if you don't plan on using it (the --with-dri option cuts build time significantly down)
Now glxgears performs signifcantly better (albiet, not as well as it used to under fglrx)
```
$ glxgears
5862 frames in 5.0 seconds = 1172.293 FPS
6352 frames in 5.0 seconds = 1270.400 FPS
6734 frames in 5.0 seconds = 1346.660 FPS
```

With a bit of tweaking to my xorg.conf specifically
```
Section "Module"
        Load  "dri
EndSection
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "radeon"
        Option          "DRI"                    "on"
        Option          "EnablePageFlip"         "on"
        Option          "AccelMethod"            "EXA"
        Option          "EXAOptimizeMigration"   "true"
        Option          "MigrationHeuristic"     "greedy"
        Option          "AccelDFS"               "on"
EndSection
Section "ServerFlags"
        Option          "BackingStore"  "true"
EndSection
```
I was able to gain a small (in reality negligable) fps gain:
```
$ glxgears
7362 frames in 5.0 seconds = 1472.318 FPS
7555 frames in 5.0 seconds = 1510.947 FPS
7624 frames in 5.0 seconds = 1524.665 FPS
```
However, still not as good as it was under fglrx, but it does allievate some of the problems that I (and probably others) use to have. 
Anyone else got fglrx driver running? Stuart's method is still too ambitious for me at this time right now...

---

### Post by LepeKaname on 2009-06-21
I'm also a victim of this problem. Everything was fine in Intrepid, but I wanted to use openoffice 3 and see some enhancements of XFCE. I use Jaunty in my job and I didn't have a problem (of course, I have nvidia there). So I give Jaunty a try. The rest you know.

If ATI dropped the support for so many cards, why they don't realease their drivers code? Maybe the community could continue the support... Its a same that this kind of things happen. I'm really thinking in getting a NVIDIA card for my PC just to play Tremulous... 

I tried to roll back as much as possible but I failed. I was able to use the open source "ati/radeon" driver (2D only) but I couldn't make radeonhd to make it work. Any success with radeonhd?

I will follow some of the recommendations here and see what happen. I think this forum should have some kind of hardware sub-categorization to facilitate community support.

UPDATE:
I followed "dardf" suggestion. In order to compile you need these packages:
autoconf
libdrm-dev
x11proto-dri2-dev
libxxf86vm-dev
x11proto-gl-dev
It compiled and installed successfully. 

After restart, I tried "glxgears" but this is what I got:
> Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

I tried with "load glx" in my xorg.conf but nothing... 

These are the Xorg error:

$ cat /var/log/Xorg.0.log | grep EE
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) module ABI major version (1) doesn't match the server's version (2)
(EE) Failed to load module "glx" (module requirement mismatch, 0)
(EE) module ABI major version (1) doesn't match the server's version (2)
(EE) Failed to load module "dri" (module requirement mismatch, 0)
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM

---

### Post by dardf on 2009-06-22
> **LepeKaname said:**
> 

$ cat /var/log/Xorg.0.log | grep EE
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) module ABI major version (1) doesn't match the server's version (2)
(EE) Failed to load module "glx" (module requirement mismatch, 0)
(EE) module ABI major version (1) doesn't match the server's version (2)
(EE) Failed to load module "dri" (module requirement mismatch, 0)
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM

Hmm... thats odd. 
Have you tried disabling composite extenstion in your xorg? 
```
Section "Extensions"
Option "Composite" "Disable"
EndSection
```

I vaguely remember having this same problem, but Im sure it was with my old nvidia geforce 4.
Also, did you by chance run a 
```
$sudo ldconfig
```
after you did a sudo make install?
Maybe that might clear up the issue.

---

### Post by LepeKaname on 2009-06-22
Yes, I have:

> Section "Extensions"
Option "Composite" "Disable"
EndSection

I didn't try "ldconfig". I will try it and post again.

BTW, after I run "make install", and having those errors, I wanted to uninstall that compilation so, I run checkinstall, and it notify that will overwrite files "owned" by other packages (and exit with error). Removing those packages solves the problem, but at one point I need to remove a lot of packages and I wasn't sure to continue... Did you use checkinstall? Is there any way to uninstall it (in case it does not work for me?)

---

### Post by dardf on 2009-06-23
> **LepeKaname said:**
> 
Removing those packages solves the problem, but at one point I need to remove a lot of packages and I wasn't sure to continue... Did you use checkinstall? Is there any way to uninstall it (in case it does not work for me?)

Hmmm.. I just ran a "sudo make uninstall" and everything uninstalled cleanly on my machine and reverted back to the ubuntu-provided mesa 7.4 on my machine, and I did not need to use checkinstall. 

I am guessing the necessary changes can also be reverted back by aptitude/synaptic reinstall libgl1-mesa-dev, libgl1-mesa-glx, libgl1-mesa-dri, and xserver-xorg-video-radeon. It theoretically should override any of the radeon-rewrite files that you tried to install. 

Unfortunately I at a loss as to why the install of the rewrite has been so difficult for you. Could you by chance provide me a:
glxinfo | grep OpenGL
of your system before you go ahead and uninstall?

My successful install of the re-write shows this:
```
$ glxinfo | grep OpenGL
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 (RS400 5955) 20090101 x86/MMX+/3DNow!+/SSE2 NO-TCL
OpenGL version string: 1.4 Mesa 7.6-devel
```
I have a sneaking suspicion that your OpenGL is pointing back to the old 7.4 libs and thus most likely causing your errors.

---

### Post by LepeKaname on 2009-06-24
I tried "sudo ldconfig" and restarted, but no difference.

The output of "glxinfo" is:

> name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Segmentation fault

 cat /var/log/Xorg.0.log | grep EE
> (EE) module ABI major version (1) doesn't match the server's version (2)
(EE) Failed to load module "glx" (module requirement mismatch, 0)
(EE) module ABI major version (1) doesn't match the server's version (2)
(EE) Failed to load module "dri" (module requirement mismatch, 0)
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM

uname -a

> Linux localhost 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 i686 GNU/Linux

My /etc/X11/xorg.conf: (without comments)

> Section "Monitor"
    Identifier  "Configured Monitor"
    Option      "DPMS" "true"
EndSection

Section "Screen"
    Identifier  "Default Screen"
    Monitor     "Configured Monitor"
    Device      "Configured Video Device"
    DefaultDepth     24
    SubSection "Display"
        Depth    24
        Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Module"
    Load  "i2c"
    Load  "bitmap"
    Load  "int10"
    Load  "vbe"
    Load  "extmod"
    Load  "record"
    Load  "dri"
    Load  "dbe"
    Load  "glx"
EndSection

Section "DRI"
    #Mode         0666
EndSection

Section "Extensions"
    Option      "Composite" "Disable"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
    BusID       "PCI:1:5:0"
    Option      "OpenGLOverlay"          "on"
    Option      "DRI"                    "on"
    Option      "EnablePageFlip"         "on"
    Option      "AccelMethod"            "EXA"
    Option      "EXAOptimizeMigration"   "true"
    Option      "MigrationHeuristic"     "greedy"
    Option      "AccelDFS"               "on"
    
    #Identifier  "ATI Radeon Xpress 200"
    #Driver     "ati"
    Driver      "radeon" 
EndSection

I downloaded:
[http://cgit.freedesktop.org/mesa/mesa/snapshot/mesa-radeon-rewrite.tar.gz](http://cgit.freedesktop.org/mesa/mesa/snapshot/mesa-radeon-rewrite.tar.gz)
and compiled as you (dardf) suggested: 
./autogen.sh --prefix=/usr --with-dri-drivers=radeon,r200,r300

If I try to uninstall it:
# make uninstall
> make: *** No rule to make target `uninstall'.  Stop.

I had already installed :
libgl1-mesa-glx (7.4)
libgl1-mesa-dri (7.4)
xserver-xorg-video-radeon (1:6:12.99+)

Others:
xserver-xorg-video-radeonhd (1.2.5+git2)
xserver-xorg-video-ati (1:6:12.99+)


And I removed completely the fglrx drivers before compiling.

Any idea? I know you may not have experience with this case, but what do you suggest to do next? how the "-dbg" packages may help in this?

I will remove the radeonhd and ati to see what happens:

Then, I will reinstall libgl1-mesa drivers to see if that change something.

Be back.

---

### Post by LepeKaname on 2009-06-24
> I will remove the radeonhd and ati to see what happens:
Then, I will reinstall libgl1-mesa drivers to see if that change something.

I did that and nothing changed...

Then, I found this:
[http://ubuntuforums.org/showthread.php?t=926530](http://ubuntuforums.org/showthread.php?t=926530)
I reinstalled xserver-xorg* and libg1-mesa*  packages
and fixed my problem when loading the dri and glx modules and now,
"glxinfo | grep OpenGL" display:

> OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX+/3DNow!+/SSE2 NO-TCL
OpenGL version string: 1.3 Mesa 7.4
OpenGL extensions:

$ glxgears 
> 1582 frames in 5.0 seconds = 316.330 FPS
1694 frames in 5.0 seconds = 338.755 FPS

So I feel I'm again at the starting point. I'm not sure if I already had the xorg problem even before compiling... So I will try to do everything again and I will be back here.

NOTE:

Something interesting happened. Before doing all this, I was able to enter to tremulous (3D game) but It was sooooo slow that I couldn't even play. Now, I was able to enter and I got 25 to 35 FPS which is not that bad... of course with the fglrx drivers I was getting 85 to 100 FPS. I hope I can increase it with Mesa 7.6.

---

### Post by LepeKaname on 2009-06-24
dardf Thank you!

Finally my "glxinfo | grep OpenGL" displays:

> OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 (RS400 5974) 20090101 x86/MMX+/3DNow!+/SSE2 NO-TCL
OpenGL version string: 1.4 Mesa 7.6-devel
OpenGL extensions:

And glxgears: 
> 4304 frames in 5.0 seconds = 860.616 FPS
4371 frames in 5.0 seconds = 874.158 FPS

Tremulous: 30FPS (not so much gain...but it works!)

I just executed "make install" again with the already compiled codes and restarted.

Anyway... better than nothing. Thank you!!!:D

---

### Post by dardf on 2009-06-25
Ah no need to thank me, It looks like you did all the heavy lifting and trouble shooting yourself. 
Though 30fps on Tremulous and your glxgears stats still seem kind of low (currently Im running at steady 75-80 fps in game). All I can suggest to improve performance is two things:
1. Now that you have a working glx you should enable the Composite extension in your xorg.conf.
2. If you have RAM to spare, you should enable UMA+Sideport for your xpress200m (via your BIOS) and provide additional memory for the card. 

In addition you could also experiment around with xorg.conf options to find out which setting provide you optimal results (maybe my options are causing decreased performance for your card? You never really know how ATI cards react in linux). A good place to start is to change the MigrationHeuristic from greedy to smart to see how the performance is affected. 
I find it helpful to have the
```
Section "ServerFlags"
        Option          "DontZap" "false"
EndSection

```
option set in my xorg, for it brings back the ability to quickly kill and restart X via Cntrl+Alt+Bkspce . Good luck with your config testing. And as always I am interested if you find out some xorg/compile options that provide increased performance or if you somehow managed to easily install fglrx.

---

### Post by LepeKaname on 2009-06-25
> Option          "DontZap" "false"

Thank you.. I added it.

I have 256MB video shared memory. I will check the "UMA+Sideport" option you commented. 

The most important part was to make it work... I already started to play with the settings as you said, for example, adding the "Mode 0666" (DRI) (I don't know if it was related) the glxgears increased to 890FPS aprox (which is not that much compared to 875FPS I had). 

For Tremulous, at first I tried with a 1024x768 resolution. But yesterday I tried at 800x600 and I can't said it was different than with the flgrx driver. I had around 90FPS and I asked other people and they had even bellow that in the same area as me... so I suppose that will do the trick. 

> currently Im running at steady 75-80 fps in game
What resolution are you using?

---

### Post by dardf on 2009-06-26
1024x768 windowed on high settings. 
To be fair though, those numbers came when no one was around, and no one was firing. 

Just to test the driver out, I played a LAN game on with 3 other people on Transit Station. When the shooting became chaotic, the game would drop down to 9-14 fps and my cpu's temp would ratchet up to 100C. So the re-write still does not perform as well as fglrx (naturally).

---

### Post by LepeKaname on 2009-06-27
I wish I could get that FPS rate with 1024x768... even no-one is around... The FPS also depends on where are you (and what map are you in). I tested it over the bunker in ATCS map. In which I can get around 35 FPS (1024x768 ) and around 50 FPS (800x600). If I go into the hall, I got 50 FPS (1024x768 ) and around 70 FPS (800x600). However, yesterday when I was playing online, there were moments I got 80-90 FPS (800x600) in the same map. I joined 2 servers in which the Building points are almost unlimited (so you can imagine it gets really laggy sometimes), but my FPS never got below 20 FPS even in chaotic moments (20+ players). 
As I said before, I personally don't feel almost any difference between 800x600 and 1024x768 (I have a 17" LCD monitor). So I think I'm happy with the results for now. 
So you also play tremulous? it would be nice to see you around... 
Cya!

---

### Post by zeusz4u on 2009-08-19
Hi everyone,

I'm experiencing the same problem as you on Ubuntu 9.04. I have a Dell Inspiron 1501 laptop with ATI Radeon Xpress 1150 chipset, and from ATI 9.3 on i'm unable to get fglrx working for my card (they dropped support for my card as well).

However, compiz has good 3D acceleration, and everithing works fine (suspend mode now works, films run fine even when compiz is enabled, screen doesn't flicker anymore in fullscreen applications; i experienced some issues with fglrx, mainly while compiz was active). There is only one problem: poor 3D performance in 3D applications. I tested superTux Racer, and had only 6-7 FPS, even on the lowest resolution (i think 800*600 px). In Celestia or GoogleEarth i have the same problem, i can't use neither of them. 

Is there any possibility to have fully functional MESA drivers for Xpress series in Ubuntu 9.10? I have to mention that in glxgears i get more FPS than in games, in fact muych more. I know it's not a benchmarking application but tells you something about you card and drivers.

Is there any way to increase performance of those MESA drivers for my card (DRI driver R300 series)? I found some info on forums hat some cfg-s must be modified, but i don't know what and how. Can anyone help me please??? If these problem still remains unsolved i must use windows again :(.

FGLRX won't suport those ATI cards again, so the only way to get good performance in future releases on long term is MESA. I hope they'll optimize the dri drivers for the XPress series by the time Kamic will be released. :-k

---

### Post by ssri on 2009-08-19
> **zeusz4u said:**
> Hi everyone,

I'm experiencing the same problem as you on Ubuntu 9.04. I have a Dell Inspiron 1501 laptop with ATI Radeon Xpress 1150 chipset, and from ATI 9.3 on i'm unable to get fglrx working for my card (they dropped support for my card as well).

However, compiz has good 3D acceleration, and everithing works fine (suspend mode now works, films run fine even when compiz is enabled, screen doesn't flicker anymore in fullscreen applications; i experienced some issues with fglrx, mainly while compiz was active). There is only one problem: poor 3D performance in 3D applications. I tested superTux Racer, and had only 6-7 FPS, even on the lowest resolution (i think 800*600 px). In Celestia or GoogleEarth i have the same problem, i can't use neither of them. 

Is there any possibility to have fully functional MESA drivers for Xpress series in Ubuntu 9.10? I have to mention that in glxgears i get more FPS than in games, in fact muych more. I know it's not a benchmarking application but tells you something about you card and drivers.

Is there any way to increase performance of those MESA drivers for my card (DRI driver R300 series)? I found some info on forums hat some cfg-s must be modified, but i don't know what and how. Can anyone help me please??? If these problem still remains unsolved i must use windows again :(.

FGLRX won't suport those ATI cards again, so the only way to get good performance in future releases on long term is MESA. I hope they'll optimize the dri drivers for the XPress series by the time Kamic will be released. :-k

If you really need to have 3D from fglrx, you can install it in Jaunty if you downgrade xserver ([http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)).  So far, everything has worked well for me.  Googleearth is running very smoothly/

180+ fps in Extreme Tux Racer
40-50 fps in Nexuiz 2.5

OS: Kubuntu Jaunty
My card: ATI Mobility Radeon x2300 (M64-S)

---

### Post by zeusz4u on 2009-08-19
I read that post before writing here. I just wanted to know if there is any way to make those open-source radeon drivers work well with my graphics card. Downgrading Xserver is not a long term solution, i suppose i will have to do that again anytime a new distribution release comes out. In fact, as i mentioned, in some aspects the open-source driver works better, it lets me suspend my computer, while the fglrx driver made my computer broke when tried to resume my computer, and also experienced problems when watching films. There must be some other way to "tune up" those open-source drivers. In fact my card wasn't supported 100% by ATI even before they dropped support. I didn't have the same performance that i had in windows XP, or even Vista.

Is anyone working on those open-source drivers right now?? i didn't find anything about it. I also found out that ATI had made public the source code of those "older" card drivers, so that communities and linux programmers can work on it to make it better, and to support it in new distribution releases. So how can i tune up those open source drivers if there is any way?:confused:

---

### Post by ssri on 2009-08-19
> **zeusz4u said:**
> Downgrading Xserver is not a long term solution, i suppose i will have to do that again anytime a new distribution release comes out.

Nope, due to the fact that Catalyst 9.3 only supports kernels <2.6.29.  Seeing that karmic is going to be either 2.6.30 or 2.6.31, Jaunty is the end of the line.  Some of the patches used to get this driver to work with >2.6.29 has some nasty bugs.  I'm just holding out until the opensource drivers delivers the performance I want (working TVOut for my R500).

> **zeusz4u said:**
> There must be some other way to "tune up" those open-source drivers. In fact my card wasn't supported 100% by ATI even before they dropped support. I didn't have the same performance that i had in windows XP, or even Vista.

There are alot of xorg.confs people posted in getting some better performance out of their opensource drivers.  You should search out for them.  In fact here's one: [http://ubuntuforums.org/showpost.php?p=7506319&postcount=7](http://ubuntuforums.org/showpost.php?p=7506319&postcount=7).  Also, there is no way your card is going to match XP's or Vista's performance in Linux, you just have to live with that reality.  Even the lead in-house dev (bridgman) for ATI/AMD says that they are aiming for 80% of their cards' capability.

> **zeusz4u said:**
> Is anyone working on those open-source drivers right now?? i didn't find anything about it. I also found out that ATI had made public the source code of those "older" card drivers, so that communities and linux programmers can work on it to make it better, and to support it in new distribution releases. So how can i tune up those open source drivers if there is any way?:confused:

The only source code release from AMD that I can recall is 3D code for R600/R700 cards ([http://linux.slashdot.org/article.pl?sid=08/12/30/0337204](http://linux.slashdot.org/article.pl?sid=08/12/30/0337204))--the rest has been documentation.  Also, the opensource driver released during Jaunty is utter crap.  It is better to check out the latest version in git ([http://ubuntuforums.org/showthread.php?t=1231030](http://ubuntuforums.org/showthread.php?t=1231030)) or in tormod volden's ppa ([https://launchpad.net/~tormodvolden/+archive/ppa](https://launchpad.net/~tormodvolden/+archive/ppa)).  Those are much, much better in my experience.  Many games and apps that require 3D need shader support, featured in opengl 2.0 (GLSL), to run smoothly.  Unfortunately, that feature won't be ready till next summer at the earliest, as the devs are waiting for Gallium3D to be stabilized in the mainline kernel.
   
[http://www.phoronix.com/forums/showthread.php?t=17887](http://www.phoronix.com/forums/showthread.php?t=17887)
[http://www.phoronix.com/forums/showthread.php?t=18292](http://www.phoronix.com/forums/showthread.php?t=18292)

---

### Post by zeusz4u on 2009-08-19
Well, thanks a lot, i will try to find something that makes my card work better. In fact the problem is that anyway i would try to get rid of windows i would not be able, because of many apps that are released and compiled for windows ONLY, and i'm not talking about drivers now. I had this same problem when i first "test-drived" a linux distro, Freespire at that time. It hadn't had ATI drivers, or at least i couldn't install them. For some time i was using OpenSuse, but as they released version 11 which was full of bugs, and didn't work as well as the earlier 10.3 version did. In fact Opensuse 11 made me try out ubuntu, and since then i use Ubuntu. Of course i tryed other ditros as well, but only from livecd, i didn't install them on my HDD.

And what about other distros? Are they changing/upgrading their Xservers as well, just like Ubuntu did?? I refer now to OpenSuse 11.2, in case if not i will try that again, until a performant open-source radeon driver will be released. I don't have the monay to buy me a new laptop every 2 years because of ATI. Next time i'll be more careful before jumping into relatively cheap offers.

---

### Post by zeusz4u on 2009-08-19
I checked out those posts with open-source drivers, but since they aren't tested for my card & i'm not a linux expert, i don't know wether to try them or not. Can i try them from the live cd somehow? I have an almost fully functional Intrepid now, configured as i like it, and for a non-tested conf i won't intall Jaunty again, because if they doesn't work, i'll have to install Intrepid, so it doesn't make any sense to me right now. I'll try to modify the xorg-conf of the live cd, because it already has the open-radeon drivers enabled, and then i'll only restart the X. 

In fact these kinda conf-editing-hacks are for those users who what they are doing. I repeat: I'm not a linux expert. There'll just be fine to have them already tested on a similar configuration of mines :), many people have this model (Inspiron 1501) of Dell. On the other hand, as i know the radeon x series is for desktop computers, not for laptops, and has nothing to do with my xpress card (which is a chipset for mobile devices, such as ATI Xpress 200 and 200M). 

Running the lspci command under Intrepid, with fglrx drivers gives the following:
```
ede@ede-laptop:~$ lspci | grep "ATI"
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]

```So it still uses the 200M driver?? WTF?? I think they are NOT the same. While fglrxinfo gives the following:
```
ede@ede-laptop:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series      
OpenGL version string: 2.1.8494 Release

```And glxgears has a relatively high framerate:
```
ede@ede-laptop:~$ glxgears
9003 frames in 5.0 seconds = 1800.530 FPS
8848 frames in 5.0 seconds = 1769.576 FPS
8926 frames in 5.0 seconds = 1785.085 FPS
8914 frames in 5.0 seconds = 1782.701 FPS
8835 frames in 5.0 seconds = 1766.919 FPS

```I think that is not bad: 1800 FPS!! Well, in games it hasn't got that framrate, but is acceptable (even in UrbanTerror or Nexuiz, or even FarCry which i tried last winter running in Wine). Now i will boot the live cd to show you the performance of the open source radeon driver, and i'll post those values too.

---

### Post by zeusz4u on 2009-08-19
I'm back using Jaunty live CD...

```
ubuntu@ubuntu:~$ glxinfo | grep 'rendering'
direct rendering: Yes
ubuntu@ubuntu:~$ glxinfo | grep 'OpenGL'
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX+/3DNow!+/SSE2 NO-TCL
OpenGL version string: 1.3 Mesa 7.4

```

And the magical glxgears:
```
ubuntu@ubuntu:~$ glxgears
1493 frames in 5.0 seconds = 298.432 FPS
1693 frames in 5.0 seconds = 338.474 FPS
1680 frames in 5.0 seconds = 335.875 FPS
1705 frames in 5.0 seconds = 340.897 FPS
1676 frames in 5.0 seconds = 335.119 FPS

```

So you see? the performance is about 1/5 of the fglrx driver... However, after installing Extreme tuxRacer, and disabling all the effects in the game, at a 800*600 pixels resolution i have only 11-11.3 FPS, and all the shadowed surfaces appear black, and have a few 10 pixels area flickering in the bottom right corner of the screen!! After enabling fog and shadows, at the same resolution the FPS is 8-10.

---

### Post by Yellow Pasque on 2009-08-19
Unfortunately, ATI dropped support for your card in their latest fglrx drivers, so your only option on Jaunty is the open-source drivers, and they don't have the best 3D performance.

---

### Post by zeusz4u on 2009-08-20
> **Temüjin said:**
> Unfortunately, ATI dropped support for your card in their latest fglrx drivers, so your only option on Jaunty is the open-source drivers, and they don't have the best 3D performance.

yeah, i know that... :(

Now i'm looking for some way to increase that open-source radeon performance... I followed a tutorial, and compiled the newest drivers but, nothing happened, in fact i had to modify the xorg.conf, and i  included "Load module" "radeonhd", but it said that module not found, and i ended up with no desktop again. I included some other options, but nothing happened: Options at AGPMode, tried 4 and 8 -nothing, EXA and XAA Accel MEthods, again nothing, and i tried "RenderAccel" "on", but it changed nothing. That tutorial was made on x1200 series card, i think there is the problem, because my card must be using other drivers, that's why it doesn't let me use those radeonhd drivers. I didn't find much threads on this topic :confused:, everybody's just asking questions, but no one can help us out with those open-source driver options.

---

### Post by nardis_Miles1 on 2009-10-06
I just wanted to add my thanks. I'm running a compaq presario V5000 with X200 m graphics card. Your fix gave big improvement in glxgears, and I now have direct rendering and compiz. Yes, the radeon driver eliminates the tearing that fglrx had. I don't game, so I think I'll be pretty happy.

---

### Post by nardis_Miles1 on 2009-10-06
> **dardf said:**
> Hmmm.. I just ran a "sudo make uninstall" and everything uninstalled cleanly on my machine and reverted back to the ubuntu-provided mesa 7.4 on my machine, and I did not need to use checkinstall. 

I am guessing the necessary changes can also be reverted back by aptitude/synaptic reinstall libgl1-mesa-dev, libgl1-mesa-glx, libgl1-mesa-dri, and xserver-xorg-video-radeon. It theoretically should override any of the radeon-rewrite files that you tried to install. 

Unfortunately I at a loss as to why the install of the rewrite has been so difficult for you. Could you by chance provide me a:
glxinfo | grep OpenGL
of your system before you go ahead and uninstall?

My successful install of the re-write shows this:
```
$ glxinfo | grep OpenGL
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 (RS400 5955) 20090101 x86/MMX+/3DNow!+/SSE2 NO-TCL
OpenGL version string: 1.4 Mesa 7.6-devel
```
I have a sneaking suspicion that your OpenGL is pointing back to the old 7.4 libs and thus most likely causing your errors.
Sorry to be back:

I have gotten about a 3x improvement in speed, and that is better. However, this is the response I get from glxinfo | grep OpenGL

lapdog/home/edwardsa>glxinfo | grep OpenGL
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 (RS400 5955) 20090101  NO-TCL
OpenGL version string: 1.4 Mesa 7.6-devel
OpenGL extensions:

Note that I'm missing the sse2 etc. I used Dardf's prescription exactly, and installed the required packages when autoconf croaked. Any insight would be useful.

---

### Post by Yellow Pasque on 2009-10-06
> **nardis_Miles1 said:**
> Note that I'm missing the sse2 etc.
This probably depends on whether you're using 32-bit or 64-bit, what compile flags were used, etc.

---

### Post by Maeda_Keiji on 2009-10-17
Hi there mates i've followed this [tuturial]("http://ubuntuforums.org/showthread.php?t=1287702") and i'm actually running Ubuntu 9.04 with FGLRX i do have a problem or two when i try to call the glxgears, fglrxinfo it gives me this error message:
> 
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
4209 frames in 5.0 seconds = 841.747 FPS
5085 frames in 5.0 seconds = 1016.999 FPS
5205 frames in 5.0 seconds = 1040.389 FPS
5175 frames in 5.0 seconds = 1034.929 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 58 requests (57 known processed) with 0 events remaining.

and my computer performance seems to have been reduced i don't know if it's because i'm using JFS instead of EXT3 or XFS.
uname -a
> Linux lestat-laptop 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux
My laptop it's a Compaq NX6125 with a Ati X200 chipset and graphic with 128Mb shared memory my system only has 512mb main memory is it because of this?

If someone could help i'd love it.

Thank you all,
Maeda

---

### Post by stuart.trusty on 2010-01-01
After all is said and done on the issue of getting Radeon Xpress 200m working with the correct X server (Intrepid 8.10 wrt: lost support in newest Radeon driver) in Jaunty, confirming that [http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue) is a complete solution along the lines discussed and I am using this presently with full 3d glx acceleration under Ubuntu 9.04.  

Thanks much Tyler for redacting the essential steps to get this working for everyone, which I finally had to revisit again to make some headway with e17 again.

Cheers,

[EMAIL="Stuart.Trusty@gmail.com"]Stuart.Trusty@gmail.com[/EMAIL]
Chairman, Linux Labs International
Atlanta, Georgia

---

