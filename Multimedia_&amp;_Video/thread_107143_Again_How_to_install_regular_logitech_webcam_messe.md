---
title: "Again: How to install regular logitech webcam messenger ?"
date: 2005-12-22
forum: Multimedia &amp; Video
---

### Post by patrick295767 on 2005-12-22
Again: How to install regular logitech webcam messenger ?
  
Thank you !

(I couldnt find the how-to)

---

### Post by WhizCas on 2005-12-23
I got the same question, cant use same the webcam, when i plug it in linux freezes and i need to reboot

---

### Post by LoclynGrey on 2005-12-23
I've got the same problem, except that it's the last thing to do on my list of "switchover" (say to speak)
I'll post what I find. (once i find it lol)

---

### Post by patrick295767 on 2005-12-30
Thank you of ur support !! 

I think I'll have fun to make it installed this webcam !! :-(

---

### Post by patrick295767 on 2005-12-30
A wonderful How to :
[http://doc.ubuntu-fr.org/materiel/webcam_logitech_msn](http://doc.ubuntu-fr.org/materiel/webcam_logitech_msn)
 
Let's try ...

---

### Post by patrick295767 on 2005-12-30
I got this error message : 
what should I do now ?
  
> 

-=- Logitech QuickCam USB camera driver installer -=-
Hello! I am the (hopefully) easy-to-use, fully automated
qc-usb driver installation script.
At the moment, this is experimental, and if it doesn't work,
don't hesitate to quit this with Ctrl+C and install the
driver manually.

The driver is provided in source code form, so it has to be
compiled. This should happen automatically, but it does mean
that there are some steps required before installation.

You also need to know "root" user password to test and
install the driver.

Basically you need only to keep hitting Enter whenever you
see this prompt: --->. Sometimes you're asked root password.
Pay special attention to lines beginning with [!].
It means that some trouble has been detected.

To most important location is the path to your kernel source
or headers. This can be guessed, but you can specify it by
giving it as an argument to this script like this:
        ./quickcam.sh LINUX_DIR=/usr/src/linux

If you haven't done it yet, now it would be a good moment to
take a look at file README.

Next I'm going to check if you have some important programs installed
and if they and the kernel are of suitable version.
Press Ctrl+C to quit, Enter to continue --->

./quickcam.sh
/usr/bin/whoami
/bin/su
/bin/ls
/bin/cat
/usr/bin/gcc
/usr/bin/gcc
/usr/bin/make
/bin/grep
/bin/egrep
/usr/bin/awk
/bin/sed
/usr/bin/tail
/usr/bin/head
/usr/bin/install
/usr/bin/ld
/bin/uname
/usr/bin/tr
/usr/bin/xawtv
/usr/bin/X11/xdpyinfo
/bin/dmesg
/usr/bin/wc
/bin/readlink
gcc version: gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)
gcc version: gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)
Make version: GNU Make 3.80
Linker version: GNU ld version 2.15
Kernel compiler: gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)
Looking for more necessary programs...
Found program /sbin/depmod
Found program /sbin/insmod
Found program /sbin/rmmod
Found program /sbin/modprobe
Found program /bin/mount
Found program /usr/sbin/lsusb
depmod version: module-init-tools 3.1
insmod version: module-init-tools version 3.1
rmmod version: module-init-tools version 3.1
modprobe version: module-init-tools version 3.1
Checking whether we're root... root
[!] Running script as root.
You shouldn't run this script as root. It should work,
but is unsafe. Please run this as an ordinary user.
When root access is really needed, you will be prompted
for the root password.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->

Checking for driver source code...
Checking for write permission...

Previous round done. Now checking if you have kernel source installed.
Press Ctrl+C to quit, Enter to continue --->

Kernel source directory: /lib/modules/2.6.10-5-386/build
Detected kernel version is 2.6.x.
Kernel version name: 2.6.10-5-386
Kernel source version code: 132618
Driver file name: quickcam.ko
Module install directory: /lib/modules/2.6.10-5-386
Driver source directory (PWD):         /root/qc-usb-messenger-0.9
Kernel source directory (LINUX_DIR):   /lib/modules/2.6.10-5-386/build
Module install directory (MODULE_DIR): /lib/modules/2.6.10-5-386
Utility install directory (PREFIX):    /usr/local
User options (USER_OPT):
Driver file name (use with insmod):    quickcam.ko
Kernel version code:                   132618

The QuickCam driver requires other drivers from kernel.
I'll now check if those seem to be loaded.
Press Ctrl+C to quit, Enter to continue --->

Modules loaded into the kernel:
quickcam videodev isofs udf nls_iso8859_1 nls_cp437 vfat fat nfs nfsd exportfs lockd sunrpc r128 drm autofs4 ipv6 sd_mod tsdev usbhid snd_usb_audio snd_usb_lib usb_storage scsi_mod i2c_viapro i2c_core via_ircc irda crc_ccitt ehci_hcd uhci_hcd af_packet usbcore emu10k1_gp snd_emu10k1 snd_rawmidi snd_seq_device snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd_page_alloc snd_util_mem snd_hwdep snd soundcore ne2k_pci 8390 shpchp pci_hotplug via_agp agpgart pcspkr rtc analog gameport floppy evdev md dm_mod capability commoncap psmouse mousedev parport_pc lp parport ide_cd cdrom ext3 jbd ide_generic via82cxxx ide_disk ide_core unix thermal processor fan fbcon font bitblit vesafb cfbcopyarea cfbimgblt cfbfillrect
[!] The QuickCam driver is already loaded!
You should first remove the (old?) module by issuing
        rmmod mod_quickcam || rmmod quickcam
as root, otherwise I will fail to install the new module.
I will now try to unload it for you automatically,
if you just give me the root password (Ctrl+D to cancel):
=== Entering root mode ===
Trying to unload QuickCam driver...
=== Leaving root mode ===

Next round: let's see if you have a supported QuickCam.
Please plug in your USB camera before continuing.
Press Ctrl+C to quit, Enter to continue --->

I can find the following probably compatible devices:
[!] Didn't find compatible cameras.
If you got message: "Permission denied", it means that
you simply have too old lsusb, and you can ignore this problem.
In this case you have to be root to use lsusb, but I won't do that.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->


Another round done. Let's now compile the driver, it takes a while.
This step will also clear old unnecessary files from the directory.
Press Ctrl+C to quit, Enter to continue --->

rm -f *.o qcset input_read show *~ .\#* .*.cmd *.mod.c *.ko
rm -rf .tmp_versions
cd testquickcam ; make clean
make[1]: Entering directory `/root/qc-usb-messenger-0.9/testquickcam'
rm -f testquickcam *~ pic.ppm pic.gif
make[1]: Leaving directory `/root/qc-usb-messenger-0.9/testquickcam'
make -C "/lib/modules/2.6.10-5-386/build" SUBDIRS="/root/qc-usb-messenger-0.9" modules V=1 USER_OPT=""
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
mkdir -p /root/qc-usb-messenger-0.9/.tmp_versions
make -f scripts/Makefile.build obj=/root/qc-usb-messenger-0.9
  gcc -Wp,-MD,/root/qc-usb-messenger-0.9/.qc-driver.o.d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Os     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i386 -Iinclude/asm-i386/mach-default  -DNOKERNEL   -DMODULE -DKBUILD_BASENAME=qc_driver -DKBUILD_MODNAME=quickcam -c -o /root/qc-usb-messenger-0.9/.tmp_qc-driver.o /root/qc-usb-messenger-0.9/qc-driver.c

  gcc -Wp,-MD,/root/qc-usb-messenger-0.9/.qc-vv6450.o.d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Os     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i386 -Iinclude/asm-i386/mach-default  -DNOKERNEL   -DMODULE -DKBUILD_BASENAME=qc_vv6450 -DKBUILD_MODNAME=quickcam -c -o /root/qc-usb-messenger-0.9/.tmp_qc-vv6450.o /root/qc-usb-messenger-0.9/qc-vv6450.c
  gcc -Wp,-MD,/root/qc-usb-messenger-0.9/.qc-formats.o.d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Os     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i386 -Iinclude/asm-i386/mach-default  -DNOKERNEL   -DMODULE -DKBUILD_BASENAME=qc_formats -DKBUILD_MODNAME=quickcam -c -o /root/qc-usb-messenger-0.9/.tmp_qc-formats.o /root/qc-usb-messenger-0.9/qc-formats.c
  gcc -Wp,-MD,/root/qc-usb-messenger-0.9/.qc-memory.o.d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Os     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i386 -Iinclude/asm-i386/mach-default  -DNOKERNEL   -DMODULE -DKBUILD_BASENAME=qc_memory -DKBUILD_MODNAME=quickcam -c -o /root/qc-usb-messenger-0.9/.tmp_qc-memory.o /root/qc-usb-messenger-0.9/qc-memory.c
  ld -m elf_i386  -r -o /root/qc-usb-messenger-0.9/quickcam.o /root/qc-usb-messenger-0.9/qc-driver.o /root/qc-usb-messenger-0.9/qc-vv6450.o /root/qc-usb-messenger-0.9/qc-formats.o /root/qc-usb-messenger-0.9/qc-memory.o
  Building modules, stage 2.
make -rR -f /usr/src/linux-headers-2.6.10-5-386/scripts/Makefile.modpost
  scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.10-5-386/Module.symvers /root/qc-usb-messenger-0.9/quickcam.o
  gcc -Wp,-MD,/root/qc-usb-messenger-0.9/.quickcam.mod.o.d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Os     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i386 -Iinclude/asm-i386/mach-default     -DKBUILD_BASENAME=quickcam -DKBUILD_MODNAME=quickcam -DMODULE -c -o /root/qc-usb-messenger-0.9/quickcam.mod.o /root/qc-usb-messenger-0.9/quickcam.mod.c
  ld -m elf_i386 -r -o /root/qc-usb-messenger-0.9/quickcam.ko /root/qc-usb-messenger-0.9/quickcam.o /root/qc-usb-messenger-0.9/quickcam.mod.o
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
gcc -Wall -O2 -s qcset.c -o qcset -lm
gcc -Wall -O2 -s input_read.c -o input_read
-rw-r--r--  1 root root 126661 2005-12-31 00:33 quickcam.ko

Now everything should be well and the driver compiled.
Let's then try actually loading the fresh driver and testing
if it works.
Press Ctrl+C to quit, Enter to continue --->
To load the driver, I need to know the root password.
=== Entering root mode ===

I will now try to enable the SysRq key.
If your computer crashes, you can try pressing:
        Alt + SysRq + S: Emergency Sync (write everything on hard disk)
        Alt + SysRq + U: Unmount all harddisks
        Alt + SysRq + B: Reboot system immediately
Press Ctrl+C to quit, Enter to continue --->

Now I finally will try to load the module.
If you're unlucky, your computer might crash right now!!!!
Consider long if you really want to continue.
Press Ctrl+C to quit, Enter to continue --->

You decided to do it, here we go...
=== Leaving root mode ===
The driver detected the following supported cameras:
quickcam [25.876039]: ----------LOADING QUICKCAM MODULE------------
quickcam [25.876429]: struct quickcam size: 3900
I will be using , if there are more cameras I'll not test them.
Press Ctrl+C to quit, Enter to continue --->

Testing if  is correct.
ls: : No such file or directory
./quickcam.sh: line 699: [: too many arguments
ls: : No such file or directory
ls: : No such file or directory
[!]  major number is .
Usually it should be 81, so there are problems ahead.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->


Right now driver is loaded and should be ready to run.
Let's test if user applications can see it, starting with qcset.
Press Ctrl+C to quit, Enter to continue --->

./qcset: can not open /dev/video0 (No such device)
[!] qcset did not found the QuickCam camera
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->

If you like, you can quit now and start using the camera -
you have good chances that it works, if no problems were detected.
If you have X Window System running and xawtv installed,
I can now run it automatically for you.
You will then also have opportunity to install the driver permanently.
Press Ctrl+C to quit, Enter to continue --->

Launching xawtv (press q on xawtv window to quit it)...
If the image is not sharp, try focusing it by turning the
wheel around the camera lens.
        xawtv -noscale -noxv -c ""
This is xawtv-3.94, running on Linux/i686 (2.6.10-5-386)
v4l-conf: option requires an argument -- c
usage: v4l-conf  [ options ]

options:
    -q        quiet
    -d <dpy>  X11 Display     [:0.0]
    -c <dev>  video device    [/dev/video0]
    -b <n>    displays color depth is <n> bpp
    -s <n>    shift display by <n> bytes
    -f        query frame buffer device for info
    -a <addr> set framebuffer address to <addr>
              (in hex, root only, successful autodetect
               will overwrite this address)
    -1        force v4l API
    -2        force v4l2 API
v4l-conf had some trouble, trying to continue anyway
v4l2: open : No such file or directory
v4l2: open : No such file or directory
v4l: open : No such file or directory
no video grabber device available

Well, did it work, did you get a picture?
If you did, you might now want to install the driver
permanently. Just proceed to do that...
Press Ctrl+C to quit, Enter to continue --->

Just an extra warning: the driver (quickcam.ko) and
the utility (qcset) will be now copied into system
directories. If you have already other versions,
they will be overwritten. Verify by giving root password.
=== Entering root mode ===
/usr/bin/install -c -D -m 644 quickcam.ko        /lib/modules/2.6.10-5-386/misc/quickcam.ko
/usr/bin/install -c -D -m 755 qcset /usr/local/bin/qcset
/sbin/depmod -a
=== Leaving root mode ===
Hopefully the driver is now installed and can be loaded
with command
        modprobe quickcam
as root. You can put this command into some startup
script to do it always automatically at boot.
The exact location depends on distribution, and this
script is yet too dumb to do this automatically.
Press Ctrl+C to quit, Enter to continue --->

Goodbye...



---

### Post by DaMaster_Architect on 2006-01-04
That's not an error! It means the script succeeded! :)
I got the same output, and it works like a charm here.

---

### Post by Dannyblueyes on 2008-03-29
I tried putting the first line of code into the terminal

[i]./quickcam.sh
/usr/bin/dan
/bin/su
/bin/ls
/bin/cat
/usr/bin/gcc
/usr/bin/gcc
/usr/bin/make
/bin/grep
/bin/egrep
/usr/bin/awk
/bin/sed
/usr/bin/tail
/usr/bin/head
/usr/bin/install
/usr/bin/ld
/bin/uname
/usr/bin/tr
/usr/bin/xawtv
/usr/bin/X11/xdpyinfo
/bin/dmesg
/usr/bin/wc
/bin/readlink
gcc version: gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)
gcc version: gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)
Make version: GNU Make 3.80
Linker version: GNU ld version 2.15
Kernel compiler: gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)
Looking for more necessary programs...
Found program /sbin/depmod
Found program /sbin/insmod
Found program /sbin/rmmod
Found program /sbin/modprobe
Found program /bin/mount
Found program /usr/sbin/lsusb
depmod version: module-init-tools 3.1
insmod version: module-init-tools version 3.1
rmmod version: module-init-tools version 3.1
modprobe version: module-init-tools version 3.1[/i]

The computer prompted me for a password. I entered my system password, the same one that works for everything else, and it said authentication failed. 

So what's the real way to install a driver for this webcam then?

---

