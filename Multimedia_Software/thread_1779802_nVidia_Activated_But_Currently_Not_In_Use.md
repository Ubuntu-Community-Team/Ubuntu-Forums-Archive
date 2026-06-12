---
title: "nVidia Activated But Currently Not In Use"
date: 2011-06-11
forum: Multimedia Software
---

### Post by Khakilang on 2011-06-11
I have install Ubuntu 11.04 with Gnome classic. I have downloaded and install my nVidia driver it say activated but it was not currently in use. What's that mean? Is there other driver being use? My graphic card is nVidia 9300GE. Here is the screen shot. Thanks in advance!

[ATTACH]194795[/ATTACH]

---

### Post by BicyclerBoy on 2011-06-11
The method you have used to download the nvidia driver is called "jockey".
This method seems to be failing for a lot of people. I guess the install scripts are wrong/broken/incomplete.

A solution suggested for others with the same problem, is to install/reinstall the driver from synaptic package manager.
Search for package nvidia-current & mark for install or re-install.
This method allows you more control over versions & sources.

Ubuntu provides very good help on using synaptic package manager.

---

### Post by Chriske on 2011-06-11
This problem just started for me yesterday.

I installed 11.04 when it was released and never had the issue before.

I tried installing from Synaptic, which cures the issue for one time, but the problem recurs next time I boot.

I see a possible solution has been posted [http://ubuntuforums.org/showpost.php?p=10742896&postcount=4](http://ubuntuforums.org/showpost.php?p=10742896&postcount=4).

I'm going to try that.

So, I can confirm that it seems to have worked for me. Here's what to try:


[LIST]
[*] go into Synaptic Package Manager
[*] mark both your linux header and linux image for reinstallation
[*]mark nvidia-common and nvidia-current for reinstallation
[*] apply the changes
[*] reboot
[/LIST]
 
It seems to have cured the problem (at least after two reboots it's still OK).

---

### Post by BicyclerBoy on 2011-06-11
Non-expert wild speculation:
These problems must be caused by the nvidia driver package install scripts.
The install script has to build the kernel module against the current kernel version.
The driver package (.deb) should have the dependencies sorted. The fault could be that it does not get the correct kernel headers package.

It would be interesting to see the install script terminal output/log.

Every kernel update will trigger a nvidia driver kernel module re-build.
This is why the package management system is preferred.

If your driver install failed to survive a reboot cycle but did work the first time...this suggests that the kernel boot image was not updated.
Exactly what update broke your system in the first place kernel or nv driver ?

The re-installing of the linux kernel headers may fix the dependency.
The re-installing the kernel image will refresh the kernel boot image (update-initramfs).

At least there is an easy solution.

---

### Post by goras on 2011-06-11
I have the same problem. But the solution didn't work. Here is the output of Synaptic:

Any ideas on how to fix it?

> 
Preconfiguring packages ...
(Reading database ... 137364 files and directories currently installed.)
Preparing to replace linux-image-2.6.38-8-generic 2.6.38-8.42 (using .../linux-image-2.6.38-8-generic_2.6.38-8.42_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.38-8-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
Preparing to replace linux-headers-2.6.38-8 2.6.38-8.42 (using .../linux-headers-2.6.38-8_2.6.38-8.42_all.deb) ...
Unpacking replacement linux-headers-2.6.38-8 ...
Preparing to replace linux-headers-2.6.38-8-generic 2.6.38-8.42 (using .../linux-headers-2.6.38-8-generic_2.6.38-8.42_amd64.deb) ...
Unpacking replacement linux-headers-2.6.38-8-generic ...
Preparing to replace nvidia-common 0.2.30 (using .../nvidia-common_0.2.30_amd64.deb) ...
Unpacking replacement nvidia-common ...
Preparing to replace nvidia-current 270.41.06-0ubuntu1 (using .../nvidia-current_270.41.06-0ubuntu1_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement nvidia-current ...
Processing triggers for man-db ...
Setting up linux-image-2.6.38-8-generic (2.6.38-8.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.38-8.42 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.38-8.42 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
 * dkms: running auto installation service for kernel 2.6.38-8-generic          
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
Setting up linux-headers-2.6.38-8 (2.6.38-8.42) ...
Setting up linux-headers-2.6.38-8-generic (2.6.38-8.42) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
 * dkms: running auto installation service for kernel 2.6.38-8-generic          
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
Setting up nvidia-common (0.2.30) ...
Setting up nvidia-current (270.41.06-0ubuntu1) ...
update-initramfs: deferring update (trigger activated)
Loading new nvidia-current-270.41.06 DKMS files...
Building only for 2.6.38-8-generic
Building for architecture x86_64
Building initial module for 2.6.38-8-generic
Done.

nvidia-current.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.38-8-generic/updates/dkms/

depmod....

DKMS: install Completed.
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
Processing triggers for python-support ...


---

### Post by BicyclerBoy on 2011-06-11
Can you try from terminal

modprobe -l | grep nvidia

if there is nothing (no text returned)
Try
modprobe nvidia 
dmesg 
Anything in the output (at the end) with clues ?

Try run
[sudo] update-initramfs

Reboot & see if it works...

Failing that try to ..
   reboot & select previous kernel at Grub menu..

Maybe you have to install by the nvidia method from console logon..
This needs kernel headers, build-essentials & other compiler/linker stuff.

---

### Post by Khakilang on 2011-06-12
I have try re installing what has been mention but it still doesn't work. Will try again. Out of curiosity since the nVidia driver is not in use what driver is in use? Anyway thanks for all the help.

---

### Post by BicyclerBoy on 2011-06-12
That is a very good question.

The way to find out is to look into the output from
dmesg

or 
cat /var/log/Xorg.0.log

& spool thru' til you try something illuminating..

---

### Post by Khakilang on 2011-06-13
This is what I got. Look like nVidia is the driver to me. Anything else I should look out for?

```
koh@koh-MS-7255:~$ cat /var/log/Xorg.0.log
[    18.353] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    18.353] X Protocol Version 11, Revision 0
[    18.353] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    18.353] Current Operating System: Linux koh-MS-7255 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[    18.353] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=837ebbe8-307a-4568-ae4f-98f300dd77f9 ro quiet splash vt.handoff=7
[    18.353] Build Date: 21 May 2011  11:48:41AM
[    18.353] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    18.353] Current version of pixman: 0.20.2
[    18.353]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    18.353] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.353] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jun 13 15:53:29 2011
[    18.354] (==) Using config file: "/etc/X11/xorg.conf"
[    18.354] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.354] (==) No Layout section.  Using the first Screen section.
[    18.354] (==) No screen section available. Using defaults.
[    18.354] (**) |-->Screen "Default Screen Section" (0)
[    18.354] (**) |   |-->Monitor "<default monitor>"
[    18.354] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[    18.354] (**) |   |-->Device "Default Device"
[    18.354] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    18.354] (==) Automatically adding devices
[    18.355] (==) Automatically enabling devices
[    18.355] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.355]     Entry deleted from font path.
[    18.355] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    18.355]     Entry deleted from font path.
[    18.355] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    18.355]     Entry deleted from font path.
[    18.355] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    18.355]     Entry deleted from font path.
[    18.355] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    18.355]     Entry deleted from font path.
[    18.355] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    18.355] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.355] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.355] (II) Loader magic: 0x7e0280
[    18.355] (II) Module ABI versions:
[    18.355]     X.Org ANSI C Emulation: 0.4
[    18.355]     X.Org Video Driver: 10.0
[    18.355]     X.Org XInput driver : 12.3
[    18.355]     X.Org Server Extension : 5.0
[    18.356] (--) PCI:*(0:2:0:0) 10de:06e0:1b0a:9004 rev 161, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/131072
[    18.357] (II) Open ACPI successful (/var/run/acpid.socket)
[    18.357] (II) LoadModule: "extmod"
[    18.372] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    18.372] (II) Module extmod: vendor="X.Org Foundation"
[    18.372]     compiled for 1.10.1, module version = 1.0.0
[    18.372]     Module class: X.Org Server Extension
[    18.372]     ABI class: X.Org Server Extension, version 5.0
[    18.372] (II) Loading extension MIT-SCREEN-SAVER
[    18.372] (II) Loading extension XFree86-VidModeExtension
[    18.372] (II) Loading extension XFree86-DGA
[    18.372] (II) Loading extension DPMS
[    18.372] (II) Loading extension XVideo
[    18.372] (II) Loading extension XVideo-MotionCompensation
[    18.372] (II) Loading extension X-Resource
[    18.372] (II) LoadModule: "dbe"
[    18.373] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    18.373] (II) Module dbe: vendor="X.Org Foundation"
[    18.373]     compiled for 1.10.1, module version = 1.0.0
[    18.373]     Module class: X.Org Server Extension
[    18.373]     ABI class: X.Org Server Extension, version 5.0
[    18.373] (II) Loading extension DOUBLE-BUFFER
[    18.373] (II) LoadModule: "glx"
[    18.373] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    18.391] (II) Module glx: vendor="NVIDIA Corporation"
[    18.391]     compiled for 4.0.2, module version = 1.0.0
[    18.391]     Module class: X.Org Server Extension
[    18.391] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:10:15 PDT 2011
[    18.391] (II) Loading extension GLX
[    18.391] (II) LoadModule: "record"
[    18.391] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    18.392] (II) Module record: vendor="X.Org Foundation"
[    18.392]     compiled for 1.10.1, module version = 1.13.0
[    18.392]     Module class: X.Org Server Extension
[    18.392]     ABI class: X.Org Server Extension, version 5.0
[    18.392] (II) Loading extension RECORD
[    18.392] (II) LoadModule: "dri"
[    18.392] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    18.392] (II) Module dri: vendor="X.Org Foundation"
[    18.392]     compiled for 1.10.1, module version = 1.0.0
[    18.392]     ABI class: X.Org Server Extension, version 5.0
[    18.392] (II) Loading extension XFree86-DRI
[    18.392] (II) LoadModule: "dri2"
[    18.392] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.393] (II) Module dri2: vendor="X.Org Foundation"
[    18.393]     compiled for 1.10.1, module version = 1.2.0
[    18.393]     ABI class: X.Org Server Extension, version 5.0
[    18.393] (II) Loading extension DRI2
[    18.393] (==) Matched nvidia as autoconfigured driver 0
[    18.393] (==) Matched nouveau as autoconfigured driver 1
[    18.393] (==) Matched nv as autoconfigured driver 2
[    18.393] (==) Matched vesa as autoconfigured driver 3
[    18.393] (==) Matched fbdev as autoconfigured driver 4
[    18.393] (==) Assigned the driver to the xf86ConfigLayout
[    18.393] (II) LoadModule: "nvidia"
[    18.393] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    18.394] (II) Module nvidia: vendor="NVIDIA Corporation"
[    18.394]     compiled for 4.0.2, module version = 1.0.0
[    18.394]     Module class: X.Org Video Driver
[    18.394] (II) LoadModule: "nouveau"
[    18.394] (WW) Warning, couldn't open module nouveau
[    18.394] (II) UnloadModule: "nouveau"
[    18.394] (II) Unloading nouveau
[    18.394] (EE) Failed to load module "nouveau" (module does not exist, 0)
[    18.394] (II) LoadModule: "nv"
[    18.395] (WW) Warning, couldn't open module nv
[    18.395] (II) UnloadModule: "nv"
[    18.395] (II) Unloading nv
[    18.395] (EE) Failed to load module "nv" (module does not exist, 0)
[    18.395] (II) LoadModule: "vesa"
[    18.395] (WW) Warning, couldn't open module vesa
[    18.395] (II) UnloadModule: "vesa"
[    18.395] (II) Unloading vesa
[    18.395] (EE) Failed to load module "vesa" (module does not exist, 0)
[    18.395] (II) LoadModule: "fbdev"
[    18.396] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    18.396] (II) Module fbdev: vendor="X.Org Foundation"
[    18.396]     compiled for 1.10.0, module version = 0.4.2
[    18.396]     ABI class: X.Org Video Driver, version 10.0
[    18.396] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:25 PDT 2011
[    18.396] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    18.396] (II) FBDEV: driver for framebuffer: fbdev
[    18.396] (++) using VT number 7

[    18.396] (II) Loading sub module "fb"
[    18.396] (II) LoadModule: "fb"
[    18.396] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.397] (II) Module fb: vendor="X.Org Foundation"
[    18.397]     compiled for 1.10.1, module version = 1.0.0
[    18.397]     ABI class: X.Org ANSI C Emulation, version 0.4
[    18.397] (II) Loading sub module "wfb"
[    18.397] (II) LoadModule: "wfb"
[    18.397] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    18.397] (II) Module wfb: vendor="X.Org Foundation"
[    18.397]     compiled for 1.10.1, module version = 1.0.0
[    18.397]     ABI class: X.Org ANSI C Emulation, version 0.4
[    18.397] (II) Loading sub module "ramdac"
[    18.397] (II) LoadModule: "ramdac"
[    18.397] (II) Module "ramdac" already built-in
[    18.397] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    18.397] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    18.397] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.397] (WW) Falling back to old probe method for fbdev
[    18.397] (II) Loading sub module "fbdevhw"
[    18.397] (II) LoadModule: "fbdevhw"
[    18.398] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    18.398] (II) Module fbdevhw: vendor="X.Org Foundation"
[    18.398]     compiled for 1.10.1, module version = 0.0.2
[    18.398]     ABI class: X.Org Video Driver, version 10.0
[    18.398] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    18.398] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    18.398] (==) NVIDIA(0): RGB weight 888
[    18.398] (==) NVIDIA(0): Default visual is TrueColor
[    18.398] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    18.398] (**) NVIDIA(0): Option "NoLogo" "True"
[    19.090] (II) NVIDIA(GPU-0): Display (HP w1907 (DFP-0)) does not support NVIDIA 3D Vision
[    19.090] (II) NVIDIA(GPU-0):     stereo.
[    19.091] (II) NVIDIA(0): NVIDIA GPU GeForce 9300 GE (G98) at PCI:2:0:0 (GPU-0)
[    19.091] (--) NVIDIA(0): Memory: 524288 kBytes
[    19.091] (--) NVIDIA(0): VideoBIOS: 62.98.22.00.41
[    19.091] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    19.091] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    19.091] (--) NVIDIA(0): Connected display device(s) on GeForce 9300 GE at PCI:2:0:0
[    19.091] (--) NVIDIA(0):     HP w1907 (DFP-0)
[    19.091] (--) NVIDIA(0): HP w1907 (DFP-0): 330.0 MHz maximum pixel clock
[    19.091] (--) NVIDIA(0): HP w1907 (DFP-0): Internal Dual Link TMDS
[    19.176] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    19.176] (==) NVIDIA(0): 
[    19.176] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    19.176] (==) NVIDIA(0):     will be used as the requested mode.
[    19.176] (==) NVIDIA(0): 
[    19.176] (II) NVIDIA(0): Validated modes:
[    19.176] (II) NVIDIA(0):     "nvidia-auto-select"
[    19.176] (II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
[    19.214] (--) NVIDIA(0): DPI set to (89, 87); computed from "UseEdidDpi" X config
[    19.214] (--) NVIDIA(0):     option
[    19.214] (II) UnloadModule: "fbdev"
[    19.214] (II) Unloading fbdev
[    19.214] (II) UnloadModule: "fbdevhw"
[    19.214] (II) Unloading fbdevhw
[    19.214] (--) Depth 24 pixmap format is 32 bpp
[    19.214] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    19.220] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    19.244] (II) Loading extension NV-GLX
[    19.287] (==) NVIDIA(0): Disabling shared memory pixmaps
[    19.287] (==) NVIDIA(0): Backing store disabled
[    19.287] (==) NVIDIA(0): Silken mouse enabled
[    19.287] (==) NVIDIA(0): DPMS enabled
[    19.288] (II) Loading extension NV-CONTROL
[    19.288] (II) Loading extension XINERAMA
[    19.288] (II) Loading sub module "dri2"
[    19.288] (II) LoadModule: "dri2"
[    19.288] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.289] (II) Module dri2: vendor="X.Org Foundation"
[    19.289]     compiled for 1.10.1, module version = 1.2.0
[    19.289]     ABI class: X.Org Server Extension, version 5.0
[    19.289] (II) NVIDIA(0): [DRI2] Setup complete
[    19.289] (==) RandR enabled
[    19.289] (II) Initializing built-in extension Generic Event Extension
[    19.289] (II) Initializing built-in extension SHAPE
[    19.289] (II) Initializing built-in extension MIT-SHM
[    19.289] (II) Initializing built-in extension XInputExtension
[    19.289] (II) Initializing built-in extension XTEST
[    19.289] (II) Initializing built-in extension BIG-REQUESTS
[    19.289] (II) Initializing built-in extension SYNC
[    19.289] (II) Initializing built-in extension XKEYBOARD
[    19.289] (II) Initializing built-in extension XC-MISC
[    19.289] (II) Initializing built-in extension SECURITY
[    19.289] (II) Initializing built-in extension XINERAMA
[    19.289] (II) Initializing built-in extension XFIXES
[    19.289] (II) Initializing built-in extension RENDER
[    19.289] (II) Initializing built-in extension RANDR
[    19.289] (II) Initializing built-in extension COMPOSITE
[    19.289] (II) Initializing built-in extension DAMAGE
[    19.289] (II) Initializing built-in extension GESTURE
[    19.291] (II) Initializing extension GLX
[    19.314] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.326] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    19.326] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.326] (II) LoadModule: "evdev"
[    19.326] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.327] (II) Module evdev: vendor="X.Org Foundation"
[    19.327]     compiled for 1.10.0.902, module version = 2.6.0
[    19.327]     Module class: X.Org XInput Driver
[    19.327]     ABI class: X.Org XInput driver, version 12.3
[    19.327] (II) Using input driver 'evdev' for 'Power Button'
[    19.327] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.327] (**) Power Button: always reports core events
[    19.327] (**) Power Button: Device: "/dev/input/event2"
[    19.360] (--) Power Button: Found keys
[    19.360] (II) Power Button: Configuring as keyboard
[    19.360] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    19.360] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    19.360] (**) Option "xkb_rules" "evdev"
[    19.360] (**) Option "xkb_model" "pc105"
[    19.360] (**) Option "xkb_layout" "us"
[    19.364] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    19.364] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.364] (II) Using input driver 'evdev' for 'Power Button'
[    19.364] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.364] (**) Power Button: always reports core events
[    19.364] (**) Power Button: Device: "/dev/input/event1"
[    19.364] (--) Power Button: Found keys
[    19.364] (II) Power Button: Configuring as keyboard
[    19.364] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    19.364] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    19.364] (**) Option "xkb_rules" "evdev"
[    19.364] (**) Option "xkb_model" "pc105"
[    19.364] (**) Option "xkb_layout" "us"
[    19.365] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    19.365] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    19.365] (II) Using input driver 'evdev' for 'Sleep Button'
[    19.365] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.365] (**) Sleep Button: always reports core events
[    19.365] (**) Sleep Button: Device: "/dev/input/event0"
[    19.365] (--) Sleep Button: Found keys
[    19.365] (II) Sleep Button: Configuring as keyboard
[    19.365] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[    19.365] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    19.365] (**) Option "xkb_rules" "evdev"
[    19.365] (**) Option "xkb_model" "pc105"
[    19.365] (**) Option "xkb_layout" "us"
[    19.374] (II) config/udev: Adding input device HDA VIA VT82xx Headphone (/dev/input/event4)
[    19.374] (II) No input driver/identifier specified (ignoring)
[    19.375] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    19.375] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    19.375] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    19.375] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.375] (**) AT Translated Set 2 keyboard: always reports core events
[    19.375] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    19.375] (--) AT Translated Set 2 keyboard: Found keys
[    19.375] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    19.375] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    19.375] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    19.375] (**) Option "xkb_rules" "evdev"
[    19.375] (**) Option "xkb_model" "pc105"
[    19.375] (**) Option "xkb_layout" "us"
[    19.376] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event5)
[    19.376] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    19.376] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[    19.376] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.376] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    19.376] (**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event5"
[    19.376] (--) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    19.376] (--) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[    19.376] (--) ImPS/2 Generic Wheel Mouse: Found relative axes
[    19.376] (--) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    19.376] (II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    19.376] (II) ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[    19.377] (**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    19.377] (**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.377] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    19.377] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[    19.377] (II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[    19.377] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[    19.377] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[    19.377] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[    19.377] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[    19.377] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[    19.377] (II) No input driver/identifier specified (ignoring)
koh@koh-MS-7255:~$ 

```

---

### Post by Chriske on 2011-06-13
Hello,

I regret to say my previous posted solution did not work after a day, or so. It seemed to be OK for a while, but the problem came back.

The only way I have found to cure the problem and seems to be sticking is to completely reinstall Ubuntu from the LiveCD. :(

I tried doing the install where you keep your documents and settings, but the problem persisted. Fortunately I have a second HDD where I could store a backup of all my data.

Sorry about that.

---

### Post by BicyclerBoy on 2011-06-13
@Khakilang
There are some odd errors in your Xorg.0.log about trying to load nouveau,nv  & vesa drivers...

I don't know why is it trying to do that & I'm not sure it is the real problem.
Have you got an old /etc/X11/xorg.conf file on your system from an earlier install ?

Try  to create this file (it should already exist )
/etc/modprobe.d/disable-nouveau.conf

put this into it...
```

blacklist nouveau
options nouveau modeset=0

```

Then run 
[sudo] update-initramfs -u

reboot & see if all is well..
glxinfo
glxgears
vdpauinfo

You could try running from terminal
sudo nvidia-xconfig

Other alternatives could be:
add another ppa for nvidia driver from x-swat team
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
Maybe their install scripts are not broken..

Or get real desperate & install the nvidia driver from nvidia website & console login..

---

### Post by Khakilang on 2011-08-05
I think I let it rest for now and see whether 11.10 had the same problem when it is release. Thank for all your help.

---

### Post by beew on 2011-08-05
I think this is a known bug. The driver is actually in use even though Jockey says it is not. 

I have installed my Nvidia driver with jockey and updated several times with the xorg-edgers ppa (now using 280.13) It has been working very well  since the very beginning even though jockey still says that  driver is activated but not in use (e.g. I watch 1080p videos with ~ 8% cpu with mplayer so vdpau is definitely working, nouveau simply can't manage that) 

So as long as you know it is actually working I wouldn't worry about what Jockey says, I think it is just a bug in reporting the status of the driver, not that there is a problem with the actual installation.

Edited:

To check if the Nvidia driver is properly installed , run the command 
```
cat /var/log/Xorg.0.log | grep nvidia
```Here are my outputs
> [    75.741] (II) LoadModule: "nvidia"
[    75.741] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    75.944] (II) Module nvidia: vendor="NVIDIA Corporation"
[    76.208] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    79.777] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    79.777] (II) NVIDIA(0):     "nvidia-auto-select"
[    80.852] (II) NVIDIA(0): Setting mode "nvidia-auto-select"






---

### Post by Khakilang on 2011-08-06
This exactly what I am thinking about. As long as I can do all the graphic thing and watch hi res movie. I just leave it as it is. That is why I mark it as solve.

---

### Post by dm215 on 2011-08-08
Don't know if it's the same issue, but I (and I guess a bunch of other folks) who are using the nvidia driver from the ubuntu repos can't even launch X.  The driver is installed, but not in use, and I don't know how to change that -- I'm not sure anybody does at the moment.  I may be trying out nouveau, or maybe doing a manual install . . . .

---

