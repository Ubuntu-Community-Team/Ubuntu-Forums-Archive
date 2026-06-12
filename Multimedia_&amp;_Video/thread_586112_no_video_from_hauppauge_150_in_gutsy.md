---
title: "no video from hauppauge 150 in gutsy"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by keithacole on 2007-10-22
my hauppauge 150 was working fine win feisty, now i upgrade to gutsy, actually a clean install to gutsy, and now the card doesnt give me video.

it actually did work when i first got to xubuntu, but i couldnt change the channels, so i 

sudo apt-get install ivtools-*  
thinking thats what i needed, but it wasnt, so then i went back and

sudo apt-get install ivtv*
after that i was able to change channels(i use vlc as a viewer)

then i rebooted, and now i get no video from /dev/video1 or /dev/video0

when i got my webcam feisty moved the capture card from /dev/video0 to /dev/video1

so i went back and removed ivtv* and ivtools* reboote and still no video

any ideas?

---

### Post by keithacole on 2007-10-24
keith@keith-desktop:~$ lsmod | grep ivtv
ivtv                  134928  0 
i2c_algo_bit            7428  1 ivtv
cx2341x                13316  1 ivtv
tveeprom               16784  1 ivtv
i2c_core               26112  6 wm8775,cx25840,tuner,ivtv,i2c_algo_bit,tveeprom
videodev               29312  3 zc0301,ivtv,gspca
v4l2_common            18432  7 wm8775,cx25840,tuner,zc0301,ivtv,cx2341x,videodev
v4l1_compat            15364  2 ivtv,videodev

---

### Post by keithacole on 2007-10-24
```
keith@keith-desktop:~$ locate ivtv
/var/lib/dpkg/info/ivtv-utils.md5sums
/var/lib/dpkg/info/ivtv-source.list
/var/lib/dpkg/info/libvideo-ivtv-perl.list
/var/lib/dpkg/info/libvideo-ivtv-perl.md5sums
/var/lib/dpkg/info/ivtv-utils.list
/var/lib/dpkg/info/ivtv-source.md5sums
/var/cache/apt/archives/ivtv-utils_1.0.2-2_i386.deb
/var/cache/apt/archives/ivtv-source_1.0.2-2_all.deb
/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/ivtv
/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/ivtv/ivtv.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv
/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv/driver
/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv/driver/ivtv-fb.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv/i2c-drivers
/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv/i2c-drivers/saa717x.ko
/lib/modules/2.6.23.1/kernel/drivers/media/video/ivtv
/lib/modules/2.6.23.1/kernel/drivers/media/video/ivtv/ivtv.ko
/lib/modules/2.6.22-14-rt/kernel/drivers/media/video/ivtv
/lib/modules/2.6.22-14-rt/kernel/drivers/media/video/ivtv/ivtv.ko
/lib/modules/2.6.22-14-rt/ubuntu/media/ivtv
/lib/modules/2.6.22-14-rt/ubuntu/media/ivtv/driver
/lib/modules/2.6.22-14-rt/ubuntu/media/ivtv/driver/ivtv-fb.ko
/lib/modules/2.6.22-14-rt/ubuntu/media/ivtv/i2c-drivers
/lib/modules/2.6.22-14-rt/ubuntu/media/ivtv/i2c-drivers/saa717x.ko
/home/keith/.ivtv-tune
/home/keith_/.ivtv-tune
/usr/bin/ivtvfwextract
/usr/bin/ivtv-mpegindex
/usr/bin/ivtvplay
/usr/bin/ivtv-tune
/usr/bin/ivtvctl
/usr/bin/ivtv-radio
/usr/lib/perl5/auto/Video/ivtv
/usr/lib/perl5/auto/Video/ivtv/ivtv.so
/usr/lib/perl5/auto/Video/ivtv/ivtv.bs
/usr/lib/perl5/Video/ivtv.pm
/usr/share/doc/libvideo-ivtv-perl
/usr/share/doc/libvideo-ivtv-perl/copyright
/usr/share/doc/libvideo-ivtv-perl/README
/usr/share/doc/libvideo-ivtv-perl/changelog.gz
/usr/share/doc/libvideo-ivtv-perl/changelog.Debian.gz
/usr/share/doc/ivtv-utils
/usr/share/doc/ivtv-utils/copyright
/usr/share/doc/ivtv-utils/README.Debian
/usr/share/doc/ivtv-utils/README.vbi.gz
/usr/share/doc/ivtv-utils/modules.txt
/usr/share/doc/ivtv-utils/README.ivtvfb.gz
/usr/share/doc/ivtv-utils/README.devices.gz
/usr/share/doc/ivtv-utils/README.radio
/usr/share/doc/ivtv-utils/README.utils
/usr/share/doc/ivtv-utils/README.install
/usr/share/doc/ivtv-utils/video-quality.txt
/usr/share/doc/ivtv-utils/README.lirc.gz
/usr/share/doc/ivtv-utils/changelog.gz
/usr/share/doc/ivtv-utils/changelog.Debian.gz
/usr/share/doc/ivtv-source
/usr/share/doc/ivtv-source/copyright
/usr/share/doc/ivtv-source/changelog.gz
/usr/share/doc/ivtv-source/changelog.Debian.gz
/usr/share/man/man3/Video::ivtv.3pm.gz
/usr/share/modass/packages/ivtv-source
/usr/src/linux-2.6.23/.tmp_versions/ivtv.mod
/usr/src/linux-2.6.23/drivers/media/video/ivtv
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv.ko
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-ioctl.o
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-video.o
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-udma.h
/usr/src/linux-2.6.23/drivers/media/video/ivtv/.ivtv-audio.o.cmd
/usr/src/linux-2.6.23/drivers/media/video/ivtv/.ivtv-vbi.o.cmd
/usr/src/linux-2.6.23/drivers/media/video/ivtv/.ivtv-yuv.o.cmd
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-version.h
/usr/src/linux-2.6.23/drivers/media/video/ivtv/.ivtv-mailbox.o.cmd
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-controls.c
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-irq.o
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv.o
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-streams.h
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-firmware.c
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-ioctl.h
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-controls.o
/usr/src/linux-2.6.23/drivers/media/video/ivtv/.ivtv-queue.o.cmd
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-streams.o
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-vbi.o
/usr/src/linux-2.6.23/drivers/media/video/ivtv/.ivtv-ioctl.o.cmd
/usr/src/linux-2.6.23/drivers/media/video/ivtv/.ivtv.o.cmd
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-firmware.o
/usr/src/linux-2.6.23/drivers/media/video/ivtv/built-in.o
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-i2c.c
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-cards.c
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-gpio.c
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-audio.o
/usr/src/linux-2.6.23/drivers/media/video/ivtv/.ivtv.ko.cmd
/usr/src/linux-2.6.23/drivers/media/video/ivtv/.ivtv-video.o.cmd
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-driver.c
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-yuv.o
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-yuv.c
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-i2c.o
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-vbi.c
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-vbi.h
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-queue.o
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-queue.h
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-streams.c
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-firmware.h
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-driver.o
/usr/src/linux-2.6.23/drivers/media/video/ivtv/.ivtv-driver.o.cmd
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-cards.o
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-udma.o
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-mailbox.o
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-irq.h
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-udma.c
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-yuv.h
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-fileops.h
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-gpio.o
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-ioctl.c
/usr/src/linux-2.6.23/drivers/media/video/ivtv/.ivtv-controls.o.cmd
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-driver.h
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-audio.c
/usr/src/linux-2.6.23/drivers/media/video/ivtv/.ivtv-irq.o.cmd
/usr/src/linux-2.6.23/drivers/media/video/ivtv/.ivtv-gpio.o.cmd
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-video.c
/usr/src/linux-2.6.23/drivers/media/video/ivtv/Makefile
/usr/src/linux-2.6.23/drivers/media/video/ivtv/.ivtv.mod.o.cmd
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-controls.h
/usr/src/linux-2.6.23/drivers/media/video/ivtv/.built-in.o.cmd
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-queue.c
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-cards.h
/usr/src/linux-2.6.23/drivers/media/video/ivtv/.ivtv-i2c.o.cmd
/usr/src/linux-2.6.23/drivers/media/video/ivtv/.ivtv-fileops.o.cmd
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-mailbox.c
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-i2c.h
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-fileops.c
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv.mod.c
/usr/src/linux-2.6.23/drivers/media/video/ivtv/Kconfig
/usr/src/linux-2.6.23/drivers/media/video/ivtv/.ivtv-streams.o.cmd
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-irq.c
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv.mod.o
/usr/src/linux-2.6.23/drivers/media/video/ivtv/.ivtv-cards.o.cmd
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-gpio.h
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-video.h
/usr/src/linux-2.6.23/drivers/media/video/ivtv/.ivtv-udma.o.cmd
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-audio.h
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-mailbox.h
/usr/src/linux-2.6.23/drivers/media/video/ivtv/ivtv-fileops.o
/usr/src/linux-2.6.23/drivers/media/video/ivtv/.ivtv-firmware.o.cmd
/usr/src/linux-2.6.23/debian/linux-headers-2.6.23.1/usr/src/linux-headers-2.6.23.1/drivers/media/video/ivtv
/usr/src/linux-2.6.23/debian/linux-headers-2.6.23.1/usr/src/linux-headers-2.6.23.1/drivers/media/video/ivtv/Makefile
/usr/src/linux-2.6.23/debian/linux-headers-2.6.23.1/usr/src/linux-headers-2.6.23.1/drivers/media/video/ivtv/Kconfig
/usr/src/linux-2.6.23/debian/linux-headers-2.6.23.1/usr/src/linux-headers-2.6.23.1/include/media/ivtv.h
/usr/src/linux-2.6.23/debian/linux-headers-2.6.23.1/usr/src/linux-headers-2.6.23.1/include/config/video/ivtv.h
/usr/src/linux-2.6.23/debian/linux-image-2.6.23.1/lib/modules/2.6.23.1/kernel/drivers/media/video/ivtv
/usr/src/linux-2.6.23/debian/linux-image-2.6.23.1/lib/modules/2.6.23.1/kernel/drivers/media/video/ivtv/ivtv.ko
/usr/src/linux-2.6.23/Documentation/video4linux/README.ivtv
/usr/src/linux-2.6.23/Documentation/video4linux/CARDLIST.ivtv
/usr/src/linux-2.6.23/include/media/ivtv.h
/usr/src/linux-2.6.23/include/config/video/ivtv.h
/usr/src/ivtv.tar.bz2
/usr/src/linux-headers-2.6.22-14-generic/include/config/video/ivtv.h
/usr/src/linux-headers-2.6.23.1/drivers/media/video/ivtv
/usr/src/linux-headers-2.6.23.1/drivers/media/video/ivtv/Makefile
/usr/src/linux-headers-2.6.23.1/drivers/media/video/ivtv/Kconfig
/usr/src/linux-headers-2.6.23.1/include/media/ivtv.h
/usr/src/linux-headers-2.6.23.1/include/config/video/ivtv.h
/usr/src/linux-headers-2.6.22-14/drivers/media/video/ivtv
/usr/src/linux-headers-2.6.22-14/drivers/media/video/ivtv/Makefile
/usr/src/linux-headers-2.6.22-14/drivers/media/video/ivtv/Kconfig
/usr/src/linux-headers-2.6.22-14/include/media/ivtv.h
/usr/include/linux/ivtv.h

```

---

### Post by rsambuca on 2007-10-24
Post your dmesg

---

### Post by old_salt on 2007-10-24
Mythtv install for Gutsy is not right. Do the install according to the guide and you end up with the xfce desktop. Is there an issue with the installation or instructions on the Mythtv guide part of the Ubuntu docs?

I would also like to see this desktop flavor neutral please. I H A T E Gnome and XFCE and use KDE. I can't understand why I'm forced to install both desktops, libraries and dependencies alongside my KDE desktop. 

In any case, is there anyone out there that could explain how to restore my KDE desktop please?

Thanks

UPDATED EDIT
Not sure why and silly on me but I got the desktop back. Not sure WHY an install script would change your default desktop choice but like I stated earlier, why must one always end up installing most of GNO-ME for half the stuff you install?

---

### Post by rsambuca on 2007-10-24
> **old_salt said:**
> Mythtv install for Gutsy is not right. Do the install according to the guide and you end up with the xfce desktop. Is there an issue with the installation or instructions on the Mythtv guide part of the Ubuntu docs?

I would also like to see this desktop flavor neutral please. I H A T E Gnome and XFCE and use KDE. I can't understand why I'm forced to install both desktops, libraries and dependencies alongside my KDE desktop. 

In any case, is there anyone out there that could explain how to restore my KDE desktop please?

Thanks

This is totally unrelated to the OP's problem.  Rather than hijacking this thread, perhaps you can conduct a search, and if you can't find an answer, start a new thread.

---

### Post by keithacole on 2007-10-24
I GOT IT!!

i unplugged my webcam and rebooted

then when i 

vlc /dev/video0 

it works,

so i plugged my webcam back in, checked kopete, and the webcam works also. 

so now im thinking, whats going on during boot


cant post the whole dmesg.. but here is what i got


as of now with it working

```
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2853.129 MHz processor.
[   77.034049] Console: colour VGA+ 80x25
[   77.034945] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   77.035826] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   77.065821] Memory: 1027756k/1048512k available (2015k kernel code, 20016k reserved, 916k data, 364k init, 131008k highmem)
[   77.065833] virtual kernel memory layout:
[   77.065834]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   77.065835]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   77.065836]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   77.065838]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   77.065839]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   77.065841]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   77.065842]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   77.065845] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   77.065905] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   77.145736] Calibrating delay using timer specific routine.. 5710.62 BogoMIPS (lpj=11421251)
[   77.145778] Security Framework v1.0.0 initialized
[   77.145793] SELinux:  Disabled at boot.
[   77.145808] Mount-cache hash table entries: 512
[   77.146018] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00000400 00000000 00000000
[   77.146032] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   77.146035] CPU: L2 cache: 512K
[   77.146038] CPU: Hyper-Threading is disabled
[   77.146041] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00000400 00000000 00000000
[   77.146057] Compat vDSO mapped to ffffe000.
[   77.146075] Checking 'hlt' instruction... OK.
[   77.161878] SMP alternatives: switching to UP code
[   77.162239] Freeing SMP alternatives: 11k freed
[   77.162550] Early unpacking initramfs... done
[   77.445201] ACPI: Core revision 20070126
[   77.445263] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   77.449449] CPU0: Intel(R) Pentium(R) 4 CPU 2.66GHz stepping 07
[   77.449488] Total of 1 processors activated (5710.62 BogoMIPS).
[   77.449616] ENABLING IO-APIC IRQs
[   77.449797] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   77.596667] Brought up 1 CPUs
[   77.596796] Booting paravirtualized kernel on bare hardware
[   77.596866] Time:  1:06:27  Date: 09/25/107
[   77.596894] NET: Registered protocol family 16
[   77.597002] EISA bus registered
[   77.597017] ACPI: bus type pci registered
[   77.620032] PCI: PCI BIOS revision 2.10 entry at 0xfb0e0, last bus=2
[   77.620034] PCI: Using configuration type 1
[   77.620036] Setting up standard PCI resources
[   77.636381] ACPI: EC: Look up EC in DSDT
[   77.640016] ACPI: Interpreter enabled
[   77.640020] ACPI: (supports S0 S1 S4 S5)
[   77.640040] ACPI: Using IOAPIC for interrupt routing
[   77.644881] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   77.644889] PCI: Probing PCI hardware (bus 00)
[   77.645238] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   77.645239] * this clock source is slow. If you are sure your timer does not have
[   77.645240] * this bug, please use "acpi_pm_good" to disable the workaround
[   77.645283] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   77.645286] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   77.645834] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[   77.645955] PCI: Transparent bridge - 0000:00:1e.0
[   77.645982] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   77.646108] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   77.650972] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   77.651072] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[   77.651169] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   77.651265] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   77.651369] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 *12 14 15)
[   77.651466] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   77.651563] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   77.651661] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   77.651760] Linux Plug and Play Support v0.97 (c) Adam Belay
[   77.651777] pnp: PnP ACPI init
[   77.651791] ACPI: bus type pnp registered
[   77.654926] pnp: PnP ACPI: found 15 devices
[   77.654929] ACPI: ACPI bus type pnp unregistered
[   77.654934] PnPBIOS: Disabled by ACPI PNP
[   77.654996] PCI: Using ACPI for IRQ routing
[   77.654999] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   77.673361] NET: Registered protocol family 8
[   77.673363] NET: Registered protocol family 20
[   77.673460] pnp: 00:0c: ioport range 0x400-0x4bf could not be reserved
[   77.676427] Time: tsc clocksource has been installed.
[   77.703731] PCI: Bridge: 0000:00:01.0
[   77.703733]   IO window: c000-cfff
[   77.703737]   MEM window: db000000-dcffffff
[   77.703741]   PREFETCH window: c0000000-cfffffff
[   77.703747] PCI: Bridge: 0000:00:1e.0
[   77.703750]   IO window: 9000-bfff
[   77.703755]   MEM window: d8000000-daffffff
[   77.703759]   PREFETCH window: d4000000-d7ffffff
[   77.703776] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   77.703791] NET: Registered protocol family 2
[   77.740323] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   77.740539] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   77.742801] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   77.743385] TCP: Hash tables configured (established 131072 bind 65536)
[   77.743392] TCP reno registered
[   77.752439] checking if image is initramfs... it is
[   78.203118] Switched to high resolution mode on CPU 0
[   78.313834] Freeing initrd memory: 7150k freed
[   78.314291] audit: initializing netlink socket (disabled)
[   78.314311] audit(1193274388.008:1): initialized
[   78.314410] highmem bounce pool size: 64 pages
[   78.316473] VFS: Disk quotas dquot_6.5.1
[   78.316533] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   78.316650] io scheduler noop registered
[   78.316652] io scheduler anticipatory registered
[   78.316654] io scheduler deadline registered
[   78.316670] io scheduler cfq registered (default)
[   78.316742] Boot video device is 0000:01:00.0
[   78.316930] isapnp: Scanning for PnP cards...
[   78.669882] isapnp: No Plug & Play device found
[   78.697596] Real Time Clock Driver v1.12ac
[   78.697710] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   78.697839] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   78.698079] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   78.698786] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   78.699116] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   78.699928] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   78.700167] input: Macintosh mouse button emulation as /class/input/input0
[   78.700305] PNP: No PS/2 controller found. Probing ports directly.
[   78.949428] serio: i8042 KBD port at 0x60,0x64 irq 1
[   78.949624] mice: PS/2 mouse device common for all mice
[   78.949752] EISA: Probing bus 0 at eisa.0
[   78.949788] EISA: Detected 0 cards.
[   78.949905] TCP cubic registered
[   78.949918] NET: Registered protocol family 1
[   78.949944] Using IPI No-Shortcut mode
[   78.950135]   Magic number: 11:71:105
[   78.950849] Freeing unused kernel memory: 364k freed
[   80.165941] AppArmor: AppArmor initialized<5>audit(1193274389.508:2):  type=1505 info="AppArmor initialized" pid=1189
[   80.371870] fuse init (API version 7.8)
[   80.378223] Failure registering capabilities with primary security module.
[   80.389364] ACPI: Fan [FAN] (on)
[   80.394214] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   80.395781] ACPI: Thermal Zone [THRM] (62 C)
[   81.206090] usbcore: registered new interface driver usbfs
[   81.206118] usbcore: registered new interface driver hub
[   81.206146] usbcore: registered new device driver usb
[   81.207045] USB Universal Host Controller Interface driver v3.0
[   81.207125] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   81.207139] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   81.207143] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   81.207341] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   81.207370] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000d800
[   81.207507] usb usb1: configuration #1 chosen from 1 choice
[   81.207539] hub 1-0:1.0: USB hub found
[   81.207547] hub 1-0:1.0: 2 ports detected
[   81.308848] SCSI subsystem initialized
[   81.314562] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   81.314576] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   81.314580] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   81.314605] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   81.314633] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000d000
[   81.314752] usb usb2: configuration #1 chosen from 1 choice
[   81.314779] hub 2-0:1.0: USB hub found
[   81.314788] hub 2-0:1.0: 2 ports detected
[   81.321244] libata version 2.21 loaded.
[   81.400960] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[   81.400964] e100: Copyright(c) 1999-2006 Intel Corporation
[   81.411345] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   81.411349] Copyright (c) 1999-2006 Intel Corporation.
[   81.414940] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   81.414955] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   81.414958] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   81.414988] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   81.415016] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
[   81.415121] usb usb3: configuration #1 chosen from 1 choice
[   81.415147] hub 3-0:1.0: USB hub found
[   81.415157] hub 3-0:1.0: 2 ports detected
[   81.467744] Floppy drive(s): fd0 is 1.44M
[   81.526575] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   81.526593] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   81.526597] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   81.526641] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   81.526683] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   81.526695] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xdd000000
[   81.559869] FDC 0 is a post-1991 82077
[   81.606346] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   81.606366] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   81.606522] usb usb4: configuration #1 chosen from 1 choice
[   81.606553] hub 4-0:1.0: USB hub found
[   81.606563] hub 4-0:1.0: 6 ports detected
[   81.710440] ata_piix 0000:00:1f.1: version 2.11
[   81.710462] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   81.710507] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   81.710624] scsi0 : ata_piix
[   81.710684] scsi1 : ata_piix
[   81.710786] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
[   81.710789] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
[   81.874662] ata1.00: ATA-5: WDC WD400BB-32CAA0, 16.06V16, max UDMA/100
[   81.874667] ata1.00: 78165360 sectors, multi 16: LBA 
[   81.890599] ata1.00: configured for UDMA/100
[   82.053444] ata2.01: ATA-7: ST3300831A, 3.03, max UDMA/100
[   82.053449] ata2.01: 586072368 sectors, multi 16: LBA48 
[   82.061430] ata2.01: configured for UDMA/100
[   82.061572] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-32CA 16.0 PQ: 0 ANSI: 5
[   82.062027] scsi 1:0:1:0: Direct-Access     ATA      ST3300831A       3.03 PQ: 0 ANSI: 5
[   82.063803] pata_pdc2027x 0000:02:02.0: version 0.9
[   82.063862] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 18 (level, low) -> IRQ 18
[   82.162918] pata_pdc2027x 0000:02:02.0: PLL input clock 2090150 kHz
[   82.162921] pata_pdc2027x: Invalid PLL input clock 2090150kHz, give up!
[   82.163431] scsi2 : pata_pdc2027x
[   82.163500] scsi3 : pata_pdc2027x
[   82.163527] ata3: PATA max UDMA/133 cmd 0xf88a17c0 ctl 0xf88a1fda bmdma 0xf88a1000 irq 18
[   82.163530] ata4: PATA max UDMA/133 cmd 0xf88a15c0 ctl 0xf88a1dda bmdma 0xf88a1008 irq 18
[   82.179211] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   82.179259] sd 0:0:0:0: [sda] Write Protect is off
[   82.179262] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   82.179287] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   82.179359] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   82.179370] sd 0:0:0:0: [sda] Write Protect is off
[   82.179373] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   82.179390] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   82.179396]  sda: sda1 sda2 sda3
[   82.216313] sd 0:0:0:0: [sda] Attached SCSI disk
[   82.216496] sd 1:0:1:0: [sdb] 586072368 512-byte hardware sectors (300069 MB)
[   82.216510] sd 1:0:1:0: [sdb] Write Protect is off
[   82.216512] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   82.216530] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   82.216585] sd 1:0:1:0: [sdb] 586072368 512-byte hardware sectors (300069 MB)
[   82.216596] sd 1:0:1:0: [sdb] Write Protect is off
[   82.216599] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   82.216616] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   82.216619]  sdb: sdb1
[   82.234213] sd 1:0:1:0: [sdb] Attached SCSI disk
[   82.239157] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   82.239303] sd 1:0:1:0: Attached scsi generic sg1 type 0
[   82.491645] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[   82.517313] e100: eth0: e100_probe: addr 0xda045000, irq 20, MAC addr 00:E0:81:52:55:1A
[   82.517418] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   82.543448] Attempting manual resume
[   82.543452] swsusp: Resume From Partition 8:3
[   82.543454] PM: Checking swsusp image.
[   82.543669] PM: Resume from disk failed.
[   82.768975] e1000: 0000:02:0a.0: e1000_probe: (PCI:33MHz:32-bit) 00:e0:81:52:55:19
[   82.804248] e1000: eth1: e1000_probe: Intel(R) PRO/1000 Network Connection
[   82.814825] kjournald starting.  Commit interval 5 seconds
[   82.814843] EXT3-fs: mounted filesystem with ordered data mode.
[   82.914917] usb 4-4: new high speed USB device using ehci_hcd and address 4
[   83.047594] usb 4-4: configuration #1 chosen from 1 choice
[   83.285953] usb 1-2: new full speed USB device using uhci_hcd and address 3
[   83.466349] usb 1-2: configuration #1 chosen from 1 choice
[   83.704873] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   83.877796] usb 2-1: configuration #1 chosen from 1 choice
[   83.880713] hub 2-1:1.0: USB hub found
[   83.883669] hub 2-1:1.0: 4 ports detected
[   84.196820] usb 2-1.2: new full speed USB device using uhci_hcd and address 3
[   84.341520] usb 2-1.2: configuration #1 chosen from 1 choice
[   84.547861] usb 2-1.3: new full speed USB device using uhci_hcd and address 4
[   84.649581] usb 2-1.3: not running at top speed; connect to a high speed hub
[   84.677615] usb 2-1.3: configuration #1 chosen from 1 choice
[   90.850317] Linux agpgart interface v0.102 (c) Dave Jones
[   90.854623] agpgart: Detected an Intel 845G Chipset.
[   90.857364] agpgart: AGP aperture is 64M @ 0xd0000000
[   90.905427] iTCO_vendor_support: vendor-support=0
[   90.955447] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   90.955768] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   90.955777] iTCO_wdt: No card detected
[   90.967981] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   90.970172] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   91.216932] intel_rng: FWH not detected
[   91.472754] ath_hal: module license 'Proprietary' taints kernel.
[   91.473543] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   92.285530] wlan: 0.8.4.2 (0.9.3.2)
[   92.298795] usbcore: registered new interface driver libusual
[   92.422914] usbcore: registered new interface driver hiddev
[   92.425785] input: Logitech USB Receiver as /class/input/input1
[   92.425841] input: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-1.2
[   92.428382] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: Fixing up Logitech keyboard report descriptor
[   92.429092] input: Logitech USB Receiver as /class/input/input2
[   92.429216] input,hiddev96: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1.2
[   92.429237] usbcore: registered new interface driver usbhid
[   92.429241] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   92.432093] input: PC Speaker as /class/input/input3
[   92.448070] parport_pc 00:09: reported by Plug and Play ACPI
[   92.448116] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   92.511133] Linux video capture interface: v2.00
[   92.549808] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   92.549814] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   92.559571] Initializing USB Mass Storage driver...
[   92.602928] scsi4 : SCSI emulation for USB Mass Storage devices
[   92.603530] usb-storage: device found at 4
[   92.603533] usb-storage: waiting for device to settle before scanning
[   92.603573] scsi5 : SCSI emulation for USB Mass Storage devices
[   92.603691] usb-storage: device found at 3
[   92.603693] usb-storage: waiting for device to settle before scanning
[   92.603716] scsi6 : SCSI emulation for USB Mass Storage devices
[   92.603784] usbcore: registered new interface driver usb-storage
[   92.603787] USB Mass Storage support registered.
[   92.603790] usb-storage: device found at 4
[   92.603791] usb-storage: waiting for device to settle before scanning
[   92.676606] ath_pci: 0.9.4.5 (0.9.3.2)
[   92.677022] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 18 (level, low) -> IRQ 18
[   93.313945] ath_rate_sample: 1.2 (0.9.3.2)
[   93.314237] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   93.314243] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   93.314253] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   93.314260] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   93.314264] wifi0: mac 7.9 phy 4.5 radio 5.6
[   93.314269] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   93.314270] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   93.314272] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   93.314274] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   93.314276] wifi0: Use hw queue 8 for CAB traffic
[   93.314277] wifi0: Use hw queue 9 for beacons
[   93.339987] wifi0: Atheros 5212: mem=0xda020000, irq=18
[   93.401452] ivtv:  ==================== START INIT IVTV ====================
[   93.401457] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
[   93.401564] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   93.402410] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 19 (level, low) -> IRQ 17
[   93.402422] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   94.072516] ivtv0: loaded v4l-cx2341x-enc.fw firmware (4158230096 bytes)
[   94.285545] ivtv0: Encoder revision: 0x02050032
[   94.285549] ivtv0: Recommended firmware version is 0x02060039.
[   94.348685] tveeprom 0-0050: Hauppauge model 26582, rev F0B2, serial# 9682292
[   94.348690] tveeprom 0-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[   94.348692] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   94.348695] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[   94.348697] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[   94.348700] tveeprom 0-0050: has no radio, has no IR receiver, has no IR transmitter
[   94.348703] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   94.375852] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   94.420227] cx25840 0-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   95.747277] usb 2-1.1: new full speed USB device using uhci_hcd and address 5
[   95.957533] usb 2-1.1: configuration #1 chosen from 1 choice
[   96.611803] Bluetooth: Core ver 2.11
[   96.612007] NET: Registered protocol family 31
[   96.612009] Bluetooth: HCI device and connection manager initialized
[   96.612013] Bluetooth: HCI socket layer initialized
[   96.730298] Bluetooth: HCI USB driver ver 2.9
[   96.742719] usbcore: registered new interface driver hci_usb
[   97.607028] usb-storage: device scan complete
[   97.607139] usb-storage: device scan complete
[   97.607194] usb-storage: device scan complete
[   97.645642] scsi 5:0:0:0: Direct-Access     Nikon    Digital Camera   1.00 PQ: 0 ANSI: 2
[   97.645678] scsi 6:0:0:0: CD-ROM            SONY     DVD RW DRU-830A  SS25 PQ: 0 ANSI: 0
[   97.645712] scsi 4:0:0:0: Direct-Access     Archos   PC Hard Drive    0316 PQ: 0 ANSI: 2
[   97.781291] sd 5:0:0:0: [sdc] 1991998 512-byte hardware sectors (1020 MB)
[   97.819550] sd 5:0:0:0: [sdc] Write Protect is off
[   97.819553] sd 5:0:0:0: [sdc] Mode Sense: 18 00 00 08
[   97.819555] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[   97.943985] sd 5:0:0:0: [sdc] 1991998 512-byte hardware sectors (1020 MB)
[   97.982263] sd 5:0:0:0: [sdc] Write Protect is off
[   97.982265] sd 5:0:0:0: [sdc] Mode Sense: 18 00 00 08
[   97.982267] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[   97.982274]  sdc:<6>cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   98.042014]  unknown partition table
[   98.044213] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[   98.044264] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   98.044367] scsi 6:0:0:0: Attached scsi generic sg3 type 5
[   98.051840] sd 4:0:0:0: [sdd] 312175080 512-byte hardware sectors (159834 MB)
[   98.055798] sd 4:0:0:0: [sdd] Write Protect is off
[   98.055801] sd 4:0:0:0: [sdd] Mode Sense: 0f 00 00 00
[   98.055803] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[   98.059121] sd 4:0:0:0: [sdd] 312175080 512-byte hardware sectors (159834 MB)
[   98.059898] sd 4:0:0:0: [sdd] Write Protect is off
[   98.059903] sd 4:0:0:0: [sdd] Mode Sense: 0f 00 00 00
[   98.059905] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[   98.059911]  sdd:sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[   98.185030] Uniform CD-ROM driver Revision: 3.20
[   98.185152] sr 6:0:0:0: Attached scsi CD-ROM sr0
[   98.285829] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   98.333899] tuner 0-0061: type set to 50 (TCL 2002N)
[   98.648234] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   98.648412] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   98.648590] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   98.648682] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   98.671623] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   98.671649] ivtv:  ====================  END INIT IVTV  ====================
[   98.671833] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 17 (level, low) -> IRQ 21
[   98.671859] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102
[  101.711138]  sdd1
[  101.724389] sd 4:0:0:0: [sdd] Attached SCSI removable disk
[  101.728887] sd 4:0:0:0: Attached scsi generic sg4 type 0
[  101.817808] lp0: using parport0 (interrupt-driven).
[  101.866041] Adding 2000084k swap on /dev/sda3.  Priority:-1 extents:1 across:2000084k
[  102.309585] EXT3 FS on sda2, internal journal
[  102.858407] kjournald starting.  Commit interval 5 seconds
[  102.858558] EXT3 FS on sda1, internal journal
[  102.858563] EXT3-fs: mounted filesystem with ordered data mode.
[  103.827415] No dock devices found.
[  104.059753] input: Power Button (FF) as /class/input/input4
[  104.064767] ACPI: Power Button (FF) [PWRF]
[  104.100995] input: Power Button (CM) as /class/input/input5
[  104.106100] ACPI: Power Button (CM) [PWRB]
[  106.072326] ppdev: user-space parallel port driver
[  106.266712] audit(1193274416.431:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4815 profile="/usr/sbin/cupsd"
[  106.355893] NET: Registered protocol family 10
[  106.356086] lo: Disabled Privacy Extensions
[  106.356390] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  106.382606] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  106.382611] apm: overridden by ACPI.
[  107.646268] Failure registering capabilities with primary security module.
[  107.809181] Bluetooth: L2CAP ver 2.8
[  107.809187] Bluetooth: L2CAP socket layer initialized
[  107.904767] Bluetooth: RFCOMM socket layer initialized
[  107.904893] Bluetooth: RFCOMM TTY layer initialized
[  107.904896] Bluetooth: RFCOMM ver 1.8
[  109.163817] [drm] Initialized drm 1.1.0 20060810
[  109.180643] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  109.184147] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[  111.294064] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  111.294214] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  111.294349] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[  111.554525] [drm] Setting GART location based on new memory map
[  111.554537] [drm] Loading R300 Microcode
[  111.554587] [drm] writeback test succeeded in 1 usecs
[  116.695649] ath0: no IPv6 routers present
[  180.705968] NET: Registered protocol family 17
[  200.132112] ath0: no IPv6 routers present
[  429.646399] cx25840 0-0044: 1x2 is not a valid size!
[  448.206505] cx25840 0-0044: 1x2 is not a valid size!
[  477.188437] cx25840 0-0044: 1x2 is not a valid size!
[  484.265069] cx25840 0-0044: 1x2 is not a valid size!
[  500.346322] cx25840 0-0044: 1x2 is not a valid size!
[  624.868905] usb 2-1.4: new full speed USB device using uhci_hcd and address 6
[  624.999681] usb 2-1.4: configuration #1 chosen from 1 choice
[  625.126038] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX) 
[  625.312543] usbcore: registered new interface driver gspca
[  625.312835] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[  625.373214] zc0301: V4L2 driver for ZC0301[P] Image Processor and Control Chip v1:1.07
[  625.374078] usbcore: registered new interface driver zc0301
[  639.883866] cx25840 0-0044: 1x2 is not a valid size!
[  684.279615] cx25840 0-0044: 1x2 is not a valid size!
[  690.121287] cx25840 0-0044: 1x2 is not a valid size!
[  690.144247] cx25840 0-0044: 1x2 is not a valid size!
[  728.100309] cx25840 0-0044: 1x2 is not a valid size!
keith@keith-desktop:~$ 

```

---

### Post by rsambuca on 2007-10-24
My tuner also switches between /dev/video0 and /dev/video1 every once in a while due to my webcam as well.  You can just change the vlc input on the pvr tab.

---

### Post by keithacole on 2007-10-24
well now its not working again, not on video0 or video1.. and i didnt reboot

---

### Post by rsambuca on 2007-10-24
Try typing this in a terminal and see if it gives you error messages:```
vlc pvr:// :pvr-device="/dev/video0"
```Also try the same command, but with video1

---

### Post by Robocoastie on 2007-10-25
I'm having the same problem except that when I do:

[INDENT]vlc pvr:// :pvr-device="/dev/video0"[/INDENT]

I do get a screen at least but no audio. Also in MythTV when I choose "watch tv" I get a blank screen.

I've given up on tv now, spent far too much time on it and am just going to transfer my tv card to my Vista Premium machine for recording then pull from it rather than other way around. But I'll keep my eye on this thread to see how it pans out, maybe I'll learn something from it I've missed.

Rob

---

### Post by RWC on 2007-10-25
I use vlc media player with the hauppauge 150 in gutsy - works great.

---

### Post by keithacole on 2007-10-25
and this is with a boot up with everything plugged in.. no work

```
keith@keith-desktop:~$ vlc pvr:// vr-device="/dev/video1"
VLC media player 0.8.6c Janus
[00000293] pvr access error: unknown ivtv driver version in use
[00000293] pvr access error: Called Close()
[00000290] main input error: no suitable access module for `pvr://'
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat vr-device=/dev/video1
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000302] main input error: no suitable access module for `vr-device=/dev/video1'
[00000281] main playlist: nothing to play
[00000281] main playlist: stopping playback
keith@keith-desktop:~$ vlc pvr:// vr-device="/dev/video0"
VLC media player 0.8.6c Janus
[00000293] pvr access error: unknown ivtv driver version in use
[00000293] pvr access error: Called Close()
[00000290] main input error: no suitable access module for `pvr://'
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat vr-device=/dev/video0
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000302] main input error: no suitable access module for `vr-device=/dev/video0'
[00000281] main playlist: nothing to play
[00000281] main playlist: stopping playback
keith@keith-desktop:~$ 

```

---

### Post by keithacole on 2007-10-25
i searched around and found a repo for ivtv, 

i got 404's when i tried for gutsy versions, so i went with feisty, here is the repo i used

```
# deb http://dl.ivtvdriver.org/ubuntu feisty firmware
# deb-src http://dl.ivtvdriver.org/ubuntu feisty firmware
```


when i used these drivers o got black and white video, but i had to do the same thing as before, not plug in the webcam until i was booted, thats why you will see the module errors in my dmesg above.. I BELEIVE

anyhow i commented out the repositories, removed ivtv, updated, then added them back. now i get color video again, but still not with the webcam plugged in.

i got an idea from irc about adding the module for the webcam to the blacklist, then using a script to bring it back after the hauppauge has been processed. however when i added 
zc0301 to the blacklist, kept the webcam in and rebooted, the hauppauage still did not show video. so the driver is not the issue. 

i would just go back to feisty, but gutsy is very smooth, and fixed issues with my ati9800SE and compiz-fusion. so until i get a fix, i will have to keep the webcam unplugged, then plug it back in after im booted.

---

### Post by rsambuca on 2007-10-25
> **keithacole said:**
> and this is with a boot up with everything plugged in.. no work

```
keith@keith-desktop:~$[COLOR="Red"] vlc pvr:// **p**vr-device="/dev/video1"[/COLOR]
VLC media player 0.8.6c Janus


```

You have a typo.  You are missing the 'p'

---

### Post by keithacole on 2007-10-27
wow, yea i dont know how that happepened, 

well when i use the command with the full "pvr" i get no action from vlc, and no report from terminal on what its doing... so i tossed in "-vv"

```
keith@keith-desktop:~$ vlc pvr:// pvr-device="/dev/video0" -vv
VLC media player 0.8.6c Janus
[00000001] main private debug: checking builtin modules
[00000001] main private debug: checking plugin modules
[00000001] main private debug: loading plugins cache file /home/keith/.vlc/cache/plugins-04041e.dat
[00000001] main private debug: recursively browsing `modules'
[00000001] main private debug: recursively browsing `/usr/lib/vlc'
[00000001] main private debug: recursively browsing `plugins'
[00000001] main private debug: module bank initialized, found 216 modules
[00000001] main private debug: opening config file /home/keith/.vlc/vlcrc
[00000001] main private debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU 
[00000001] main private debug: looking for memcpy module: 1 candidate
[00000001] main private debug: using memcpy module "memcpy"
[00000281] main playlist debug: waiting for thread completion
[00000281] main playlist debug: thread 3079850896 (playlist) created at priority 0 (playlist/playlist.c:184)
[00000282] main private debug: waiting for thread completion
[00000282] main private debug: thread 3071458192 (preparser) created at priority 0 (playlist/playlist.c:210)
[00000283] main interface debug: looking for interface module: 1 candidate
[00000283] main interface debug: using interface module "hotkeys"
[00000283] main interface debug: thread 3063065488 (interface) created at priority 0 (interface/interface.c:231)
[00000285] main interface debug: looking for interface module: 1 candidate
[00000285] main interface debug: using interface module "screensaver"
[00000285] main interface debug: thread 3054672784 (interface) created at priority 0 (interface/interface.c:231)
[00000281] main playlist debug: adding playlist item `pvr-device=/dev/video0' ( pvr-device=/dev/video0 )
[00000281] main playlist debug: adding playlist item `pvr://' ( pvr:// )
[00000287] main interface debug: looking for interface module: 5 candidates
[00000287] main interface debug: using interface module "wxwidgets"
[00000287] main interface debug: thread 3028548496 (manager) created at priority 0 (interface/interface.c:216)
[00000287] wxwidgets interface debug: Using last windows config '(-1,0,0,1920,1200)(0,655,245,425,88)(6,0,0,-1,150)'
[00000287] wxwidgets interface debug: id=0 p=(655,245) s=(425,88)
[00000287] wxwidgets interface debug: id=6 p=(0,0) s=(-1,150)
[00000281] main playlist debug: nothing requested, starting
[00000281] main playlist debug: creating new input thread
[00000290] main input debug: waiting for thread completion
[00000290] main input debug: thread 2971098000 (input) created at priority 0 (input/input.c:265)
[00000290] main input debug: creating statistics handler
[00000290] main input debug: `pvr://' gives access `pvr' demux `' path `'
[00000290] main input debug: creating demux: access='pvr' demux='' path=''
[00000292] main demuxer debug: looking for access_demux module: 0 candidates
[00000292] main demuxer warning: no access_demux module matched "pvr"
[00000290] main input debug: creating access 'pvr' path=''
[00000293] main access debug: looking for access2 module: 6 candidates
[00000293] pvr access debug: Using video device: /dev/video0.
[00000293] pvr access debug: ivtv driver version 01.00.00
[00000293] pvr access debug: this driver uses the v4l2 API
[00000293] main access debug: using access2 module "pvr"
[00000295] main private debug: pre-buffering...

```

it just hangs at the last line. perhaps it has something to do with the "cache" that it looks for? 

but now its not working at all anymore, not even if i plug the webcam in later. here are a few more commands i ran

```
keith@keith-desktop:~$ dmesg |grep Initialized[   89.762871] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[  106.676214] [drm] Initialized drm 1.1.0 20060810
[  106.696049] [drm] Initialized radeon 1.27.0 20060524 on minor 0
keith@keith-desktop:~$ lsmod | grep ivtv
ivtv                  134928  2 
i2c_algo_bit            7428  1 ivtv
cx2341x                13316  1 ivtv
tveeprom               16784  1 ivtv
i2c_core               26112  6 wm8775,cx25840,tuner,ivtv,i2c_algo_bit,tveeprom
videodev               29312  5 zc0301,gspca,ivtv
v4l2_common            18432  7 zc0301,wm8775,cx25840,tuner,ivtv,cx2341x,videodev
v4l1_compat            15364  2 ivtv,videodev

```

---

### Post by Robocoastie on 2007-10-28
> **RWC said:**
> I use vlc media player with the hauppauge 150 in gutsy - works great.

good for you. Revealing what you did different than us that made it work would actually be helpful though. Mine is now working in VLC but I don't know what I've different. Still no go in zapping, tvtime, or mythTV so it's real purpose - record scheduling is still not happening.

---

### Post by keithacole on 2007-10-29
I GOT IT WORKING AGAIN


here is what i did

```
sudo modprobe -r ivtv
```

i then downloaded the driver source from [here]("http://ivtvdriver.org/index.php/Main_Page"). i went with ivtv stable version 1.0.3, This release is for kernels >= 2.6.22.

i then compiled it via the readme.install instructions, and then everything worked perfectly again. 

i have not yet plugged my webcam back in, but now i can use vlc to view the capture, and ivtv-tune to change the channel

---

### Post by keithacole on 2007-10-29
ok, i rebooted and its not working again

so i did this

```
sudo modprobe -r ivtv && sudo modprobe ivtv
```

and it works, appearently this is what i have to do after EVERY reboot to get the pvr working

---

### Post by jacrider on 2007-10-29
I am in a similar situation.  I can't seem to get VLC to keep the settings for the device.  Each time I have to go set the capture device as /dev/video1.  I think my webcam is video0.

Next issue is how do I change channels?  I think I have lirc installed and I have built the .lirc key mapping file.  

Isn't there a means to change the channel with the keyboard or mouse?  I have been searching and searching.

Thanks.

---

### Post by rsambuca on 2007-10-30
> **jacrider said:**
> I am in a similar situation.  I can't seem to get VLC to keep the settings for the device.  Each time I have to go set the capture device as /dev/video1.  I think my webcam is video0.

Next issue is how do I change channels?  I think I have lirc installed and I have built the .lirc key mapping file.  

Isn't there a means to change the channel with the keyboard or mouse?  I have been searching and searching.

Thanks.

vlc by default will go to /dev/video0.  You can create a launcher to open it with /dev/video1.  Mine looks like this:

```
vlc pvr:// :pvr-device="/dev/video1"
```
Sorry, but I don't know about the remote.

---

### Post by jacrider on 2007-10-30
rsambuca:  Thanks.  This helps.  I still can't change channels.  I tried the terminal method I saw somewhere else, but it doesn't seem to work.

Anyone else out there who knows how to get the remote working?  A keyboard interface to change channels?

I don't really want MythTV.  This is just to bring up a window to watch briefly.

Thanks.

---

### Post by keithacole on 2007-10-30
you have to install the ivtv-utils to change the channel, if you had myth install you should have it, so try this


```
ivtv-tune -c #
``` 

replace # with your desired channel, i have a script that i use that does this for me, it just pops up a prompt that asks me what channel i want.

ok, so now we all agree that our webcams are being forced to /dev/video0 and that pushes our pvr to /dev/video1. how ever on my system i have unplugged the webcam until i get this situated.

i can just use the code from post #19 and have that run automatically when i boot, but i want to find out WHY the right module isnt being loaded.

---

### Post by rsambuca on 2007-10-30
> **jacrider said:**
> rsambuca:  Thanks.  This helps.  I still can't change channels.  I tried the terminal method I saw somewhere else, but it doesn't seem to work.

Anyone else out there who knows how to get the remote working?  A keyboard interface to change channels?

I don't really want MythTV.  This is just to bring up a window to watch briefly.

Thanks.

You can change channels using the terminal for video1 by using```
v4l2-ctl -c# -d /dev/video1
```

---

### Post by jacrider on 2007-10-30
rsambuca and keithacole:  Thanks for the responses.

Opening a terminal to change a channel doesn't seem that user friendly, do you think there would be a means to map those commands to the IR keys in lirc?

Thanks.

---

### Post by keithacole on 2007-10-30
> **jacrider said:**
> rsambuca and keithacole:  Thanks for the responses.

Opening a terminal to change a channel doesn't seem that user friendly, do you think there would be a means to map those commands to the IR keys in lirc?

Thanks.

i have a bash script, when i get home ill paste it here, but i like you, want to map the bash script to my multimedia keys.

---

### Post by jacrider on 2007-10-30
Thanks again, but I tried to change channels in the terminal, but rec'd this error.

I really need to change channels as the default channel is in Italian ... and my Italian is a bit rusty.

```
andrew@AndrewUbuntu:~$ ivtv-tune -c 8
ioctl VIDIOC_S_FREQUENCY failed
```

---

### Post by keithacole on 2007-10-30
did you build your ivtv stuff from the source i gave you?

---

### Post by rsambuca on 2007-10-30
> **jacrider said:**
> Thanks again, but I tried to change channels in the terminal, but rec'd this error.

I really need to change channels as the default channel is in Italian ... and my Italian is a bit rusty.

```
andrew@AndrewUbuntu:~$ ivtv-tune -c 8
ioctl VIDIOC_S_FREQUENCY failed
```

Did you see my previous post?  That method of changing channels won't work if the tuner is not video0.

---

### Post by radtek on 2007-11-04
Uhh, I got my pvr-150 working after few minutes. Months ago I had no luck at all even though the card seemed to be functioning. I did a NEW install of IVTV though. 

Now I get TV through VLC and I change the channels through the terminal. No prob, though it is a little cumbersome to have to use the terminal.

I wanted to use VLC anyway, even though IVTV (TV-time) looks freakin fantastic. I'm only assuming that IVTV's frontend doesn't support hauppage's pvr-150. Too bad, but I'm getting video where I had none after I had given up months ago. 

Not too keen on installing MythTV since I also had problems with it. If any one has been able to get TVtime to *actually work* as a stand-alone with the PVR-150 in Ubuntu 6.10 I'd love to know about it...

---

### Post by PokerJoker on 2007-11-04
> **radtek said:**
> Uhh, I got my pvr-150 working after few minutes. Months ago I had no luck at all even though the card seemed to be functioning. I did a NEW install of IVTV though. 

Now I get TV through VLC and I change the channels through the terminal. No prob, though it is a little cumbersome to have to use the terminal.

I wanted to use VLC anyway, even though IVTV (TV-time) looks freakin fantastic. I'm only assuming that IVTV's frontend doesn't support hauppage's pvr-150. Too bad, but I'm getting video where I had none after I had given up months ago. 

Not too keen on installing MythTV since I also had problems with it. If any one has been able to get TVtime to *actually work* as a stand-alone with the PVR-150 in Ubuntu 6.10 I'd love to know about it...

I had no probs in Feisty, nor Gutsy, though have to say, did a clean install instead of upgrade. I also use VLC (love this little big tool) and teminal. Tried myth but found it hard to get it working. 
So i'm curious to see if there are any other frontends around using ivtv.....

---

### Post by radtek on 2007-11-04
I found this nifty little script called CSMonkey.


[IMG]http://tvremote.sourceforge.net/images/tvremote.png[/IMG]

[[COLOR="DarkRed"]http://tvremote.sourceforge.net/index.php[/COLOR]]("http://tvremote.sourceforge.net/index.php")

Works pretty well even though I couldn't get this to work in terminal:

```
sh generateJar.sh
```


I just run the compressed file with java 5 runtime and it works for some reason.

---

### Post by keithacole on 2007-11-04
the generate jar code creates the remote, you can place your own buttons on there, for instance you can have a button that is the value of "77" so you dont have to hit "7" "7". l dont have it anymore so i cant tell you exactly where to look

---

### Post by End3r on 2007-11-08
I have been having similar problems with gutsy and my pvr-150.  It was primarily audio/ with flickers of video. (Once I was able to get video, but no audio.)   I found that if I "wiggled" the vlc window around I got a flash of picture which led me to suspect compiz as being the problem.  Sure enough, I get full picture/audio using metacity.

Anyone have an idea as to what may be causing the conflict?

---

### Post by rsambuca on 2007-11-08
What videocard and driver are you using?  There are definitely some bugs with the nvidia-glx-new driver, the worst being a bad memory leak, as well as video display problems.

---

### Post by End3r on 2007-11-08
ATI X800 with the 8.42.3 fglrx drivers
It's possible that that's where the bug lies I guess.

---

