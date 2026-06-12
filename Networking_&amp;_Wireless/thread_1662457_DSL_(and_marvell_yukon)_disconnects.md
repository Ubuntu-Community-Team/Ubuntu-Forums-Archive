---
title: "DSL (and marvell yukon) disconnects"
date: 2011-01-08
forum: Networking &amp; Wireless
---

### Post by snisarg on 2011-01-08
I am very new to linux, and am using Ubuntu 10.10 on a Sony vaio with Marvell Yukon 88E8056.
Everytime I try to connect using DSL, it tries connecting for a second and then gives me 'wired network disconnected.' On trying several times, i MAY get connected to the internet. [Sometimes it connects at the first try and sometimes never and i have to restart and try again.] Even after i disconnect and try to reconnect, the same problem persists, and i have to go through the process of trying to reconnect again and again.
The same connection connects correctly in windows 7.

---

### Post by snisarg on 2011-01-08
somebody please help.
its frustrating to keep clicking on the connection continuously just to connect to the internet

---

### Post by mathia on 2011-01-09
Hi,
please install the following ethernet driver as follows:
[http://www.marvell.com/support.html](http://www.marvell.com/support.html)  -> "88E8056 Search" -> Kernel 2.6.x Linux Driver Install Package for Yukon Devices	Linux 2.6 - v10.85.9.3

 $ sudo bash ./install.sh

and let me know if it works.

have a lot of fun ...:razz:

---

### Post by snisarg on 2011-01-10
thank you for your reply.
i downloaded the driver you specified, (says fedora though) and executed install.sh
here is the problem.

nisarg@nisarg-VPCEB14EN:~/DriverInstall$ sudo bash ./install.sh

Installation script for sk98lin driver.
Version 10.85.9.3 (Aug-13-2010)
(C)Copyright 2003-2010 Marvell(R).
====================================================
Add to your trouble-report the logfile install.log
which is located in the  DriverInstall directory.
====================================================


1) installation	      3) generate makefile
2) generate patch     4) exit
Choose your favorite installation method: 1
Please read this carefully!

This script will automatically compile and load the sk98lin
driver on your host system. Before performing both compilation
and loading, it is necessary to shutdown any device using the
sk98lin kernel module and to unload the old sk98lin kernel 
module. This script will do this automatically per default.
 
Please plug a card into your machine. Without a card we aren't
able to check the full driver functionality.

Do you want proceed? (y/N) y
IMPORTANT INFORMATION!

We found an alternative driver for your Marvell product on this system.
The alternative driver is _NOT_ directly supported by Marvell and does not
include all features provided by your device. If you want to use the
sk98lin driver developed by Marvell, you may choose either to deactivate
or remove the alternative driver.

[PRESS ANY KEY FOR FURTHER INSTRUCTIONS]
Do nothing:
  - The sk98lin will be installed
  NOTE: It may happen that the alternative driver will be loaded on 
  the next boot process. In this case the Marvell driver _WON'T_ be
  loaded.

Deactivate driver:
  - The alternative driver will be renamed to _skge.ko or _sky2.ko
  - All references in the /etc/modprobe.conf file will be changed to
    the sk98lin driver
  - The alternative driver will be unloaded
  - The sk98lin driver will be installed

Remove driver (recommended):
  - The alternative driver will be removed from your system
  - All references in the /etc/modprobe.conf file will be changed to
    the sk98lin driver
  - The alternative driver will be unloaded
  - The sk98lin driver will be installed


1) Do nothing
2) Deactivate diver
3) Remove driver
Action: 1

Create tmp dir (/tmp/Sk98IKhWBERcfmrpHDEmDiApf)                      [   OK   ]
Check user id (0)                                                    [   OK   ]
Check kernel version (2.6.35-24-generic)                             [   OK   ]
Check kernel symbol file (/proc/kallsyms)                            [   OK   ]
Check kernel type (SMP)                                              [   OK   ]
Check number of CPUs (4)                                             [   OK   ]
Check architecture (found)                                           [   OK   ]
Set architecture (i386)                                              [   OK   ]
Check compiler (/usr/bin/gcc)                                        [   OK   ]
Check mcmodel flags (none)                                           [   OK   ]
Check module support (/sbin/insmod)                                  [   OK   ]
Check make (/usr/bin/make)                                           [   OK   ]
Check kernel gcc version (4.4.5) (Kernel:4.4.5 == gcc:4.4.5)         [   OK   ]
Check sk98lin driver availability (not loaded)                       [   OK   ]
Check kernel header files (/lib/modules/2.6.35-24-generic/build)     [   OK   ]
Check sources for .config file (/lib/modules/2.6.35-24-generic/build/[   OK   ]
Copy and check .config file (done)                                   [   OK   ]
Check the mem address space (highmem)                                [   OK   ]
Change IOMMU (disabled)                                              [   OK   ]
Create new .config file (done)                                       [   OK   ]
Execute: make oldconfig (done)                                       [   OK   ]
Check modpost availability (available)                               [   OK   ]
Unpack the sources (done)                                            [   OK   ]
Check firmware availability (done)                                   [   OK   ]
Check kernel header version (not recognized)                         [  warn  ]
Check kernel functions (Changed: nothing)                            [   OK   ]
Compile the kernel (error)                                           [ failed ]

An error has occurred during the compile proces which prevented 
the installation from completing.                              
Take a look at the log file install.log for more informations.  
Installation of package failed.



--------------------
i have even tried deactivating and removing the driver options as well, but the error happens at 'compile the kernel' all the time. Any solution?

---

### Post by PatchesTheCaveman on 2011-01-10
You need the kernel headers package to compile that driver.  If you can get a working Internet connection, you can run this command to install it:
```
sudo apt-get install kernel-headers-$(uname -r)
```

If you cannot, you need to run this command:
```
uname -r
```
to figure out your kernel version and download the appropriate *kernel-headers* package from [http://archive.ubuntu.com/ubuntu/pool/main/l/linux](http://archive.ubuntu.com/ubuntu/pool/main/l/linux)

---

### Post by snisarg on 2011-01-11
Thank you.
i tried what you said, i will give you the complete result if you can isolate a cause.
first, the terminal....
============================================
nisarg@nisarg-VPCEB14EN:~$ sudo apt-get install kernel-headers-$(uname -r)
[sudo] password for nisarg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package kernel-headers-2.6.35-24-generic
E: Couldn't find any package by regex 'kernel-headers-2.6.35-24-generic'
nisarg@nisarg-VPCEB14EN:~$
=================================================

then i went to the link
nisarg@nisarg-VPCEB14EN:~$ uname -r
2.6.35-24-generic
-on the web site : 
linux-headers-2.6.35-24-generic-pae_2.6.35-24.42_i386.deb	
linux-headers-2.6.35-24-generic_2.6.35-24.42_amd64.deb
linux-headers-2.6.35-24-generic_2.6.35-24.42_i386.deb
--------------
i selected the last one, hoping it is the most appropriate one.
after download, when i double-click, in ubuntu software center, it ask me if i want to 'REINSTALL'.Meaning its already installed?!? I haven't proceeded, in case it caused some other problems. 

I am sorry if i have am asking something stupid, but i am really new.

---

### Post by PatchesTheCaveman on 2011-01-11
So that wasn't your problem then.  In that case you'll need to post the content of the *install.log* file in the driver install directory.

---

### Post by snisarg on 2011-01-12
install.log, as requested
---------------------------------------------------------------

+++ Install mode: User
+++ Driver version: 10.85.9.3 (Aug-13-2010)
+++ Kernel version 2.6.35-24-generic
+++ smp_count=1
+++ cpu_number=4
+++ kernel_machine=i686
+++ Architecture: i386
+++ modpost available
+++ Unpack the sources
+++ ====================================
+++ tar xfv sk98lin.tar
2.6/
2.6/sky2.c
2.6/skethtool.c
2.6/skproc.c
2.6/Makefile
2.6/skge.c
2.6/h/
2.6/h/skdrv1st.h
2.6/h/skdrv2nd.h
2.6/skdim.c
common/
common/skaddr.c
common/fwos.c
common/skgeinit.c
common/skgehwt.c
common/skspi.c
common/sk98lin.htm
common/fwapp.c
common/sktimer.c
common/fwhci.c
common/fwptrn.c
common/flashfun.c
common/fwfunctions.c
common/skgemib.c
common/vpdcheck.c
common/skvpd.c
common/skpflash.c
common/sky2le.c
common/fwimage.c
common/fwoids.c
common/skgesirq.c
common/sk98lin.4
common/fwmain.c
common/sktwsi.c
common/skgepnmi.c
common/sklm80.c
common/skgespilole.c
common/skxmac2.c
common/sk98lin.txt
common/h/
common/h/sktimer.h
common/h/fwimage.h
common/h/sktypes.h
common/h/fwptrn.h
common/h/skdebug.h
common/h/skaddr.h
common/h/skversion.h
common/h/skgeasfapi.h
common/h/lm80.h
common/h/skvpd.h
common/h/skgetwsi.h
common/h/skgeinit.h
common/h/skgesirq.h
common/h/skpflash.h
common/h/skqueue.h
common/h/fwoids.h
common/h/skcsum.h
common/h/skgepnm2.h
common/h/skspi.h
common/h/fwapp.h
common/h/skpcidevid.h
common/h/fwos.h
common/h/mvyexhw.h
common/h/sktwsi.h
common/h/fwmain.h
common/h/xmac_ii.h
common/h/fwhci.h
common/h/skgehw.h
common/h/skgedrv.h
common/h/sky2le.h
common/h/skgepnmi.h
common/h/flash.h
common/h/fwcommon.h
common/h/skgehwt.h
common/h/skerror.h
common/skqueue.c
common/skgeasfapi.c
common/skcsum.c
misc/
misc/Kconfig
misc/Configure.help

+++ Compile the driver
+++ ====================================
make: Entering directory `/usr/src/linux-headers-2.6.35-24-generic'
make -C /lib/modules/2.6.35-24-generic/build \
	KBUILD_SRC=/usr/src/linux-headers-2.6.35-24-generic \
	KBUILD_EXTMOD="/tmp/Sk98IhXeqAWRDccZLFebKKhFr/all" -f /usr/src/linux-headers-2.6.35-24-generic/Makefile \
	
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/Sk98IhXeqAWRDccZLFebKKhFr/all/.tmp_versions ; rm -f /tmp/Sk98IhXeqAWRDccZLFebKKhFr/all/.tmp_versions/*
make -f /usr/src/linux-headers-2.6.35-24-generic/scripts/Makefile.build obj=/tmp/Sk98IhXeqAWRDccZLFebKKhFr/all
   rm -f /tmp/Sk98IhXeqAWRDccZLFebKKhFr/all/built-in.o; ar rcs /tmp/Sk98IhXeqAWRDccZLFebKKhFr/all/built-in.o
  cc -Wp,-MD,/tmp/Sk98IhXeqAWRDccZLFebKKhFr/all/.skge.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.4.5/include -I/usr/src/linux-headers-lbm- -I/usr/src/linux-headers-2.6.35-24-generic/arch/x86/include -Iinclude  -I/usr/src/linux-headers-2.6.35-24-generic/include -include include/generated/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.35-24-generic/ubuntu/include   -I/tmp/Sk98IhXeqAWRDccZLFebKKhFr/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack   -I/tmp/Sk98IhXeqAWRDccZLFebKKhFr/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(skge)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)"  -c -o /tmp/Sk98IhXeqAWRDccZLFebKKhFr/all/.tmp_skge.o /tmp/Sk98IhXeqAWRDccZLFebKKhFr/all/skge.c
  cc -Wp,-MD,/tmp/Sk98IhXeqAWRDccZLFebKKhFr/all/.sky2.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.4.5/include -I/usr/src/linux-headers-lbm- -I/usr/src/linux-headers-2.6.35-24-generic/arch/x86/include -Iinclude  -I/usr/src/linux-headers-2.6.35-24-generic/include -include include/generated/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.35-24-generic/ubuntu/include   -I/tmp/Sk98IhXeqAWRDccZLFebKKhFr/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack   -I/tmp/Sk98IhXeqAWRDccZLFebKKhFr/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(sky2)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)"  -c -o /tmp/Sk98IhXeqAWRDccZLFebKKhFr/all/.tmp_sky2.o /tmp/Sk98IhXeqAWRDccZLFebKKhFr/all/sky2.c
  cc -Wp,-MD,/tmp/Sk98IhXeqAWRDccZLFebKKhFr/all/.skethtool.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.4.5/include -I/usr/src/linux-headers-lbm- -I/usr/src/linux-headers-2.6.35-24-generic/arch/x86/include -Iinclude  -I/usr/src/linux-headers-2.6.35-24-generic/include -include include/generated/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.35-24-generic/ubuntu/include   -I/tmp/Sk98IhXeqAWRDccZLFebKKhFr/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack   -I/tmp/Sk98IhXeqAWRDccZLFebKKhFr/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(skethtool)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)"  -c -o /tmp/Sk98IhXeqAWRDccZLFebKKhFr/all/.tmp_skethtool.o /tmp/Sk98IhXeqAWRDccZLFebKKhFr/all/skethtool.c
  cc -Wp,-MD,/tmp/Sk98IhXeqAWRDccZLFebKKhFr/all/.sky2le.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.4.5/include -I/usr/src/linux-headers-lbm- -I/usr/src/linux-headers-2.6.35-24-generic/arch/x86/include -Iinclude  -I/usr/src/linux-headers-2.6.35-24-generic/include -include include/generated/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.35-24-generic/ubuntu/include   -I/tmp/Sk98IhXeqAWRDccZLFebKKhFr/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack   -I/tmp/Sk98IhXeqAWRDccZLFebKKhFr/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(sky2le)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)"  -c -o /tmp/Sk98IhXeqAWRDccZLFebKKhFr/all/.tmp_sky2le.o /tmp/Sk98IhXeqAWRDccZLFebKKhFr/all/sky2le.c
/tmp/Sk98IhXeqAWRDccZLFebKKhFr/all/skge.c: In function ‘SkGeSetRxMode’:
/tmp/Sk98IhXeqAWRDccZLFebKKhFr/all/skge.c:4497: error: ‘struct net_device’ has no member named ‘mc_list’
/tmp/Sk98IhXeqAWRDccZLFebKKhFr/all/skge.c:4498: error: ‘struct net_device’ has no member named ‘mc_count’
/tmp/Sk98IhXeqAWRDccZLFebKKhFr/all/skge.c:4498: error: dereferencing pointer to incomplete type
/tmp/Sk98IhXeqAWRDccZLFebKKhFr/all/skge.c:4500: error: dereferencing pointer to incomplete type
make[2]: *** [/tmp/Sk98IhXeqAWRDccZLFebKKhFr/all/skge.o] Error 1
make[2]: *** Waiting for unfinished jobs....
  set -e ; perl /usr/src/linux-headers-2.6.35-24-generic/scripts/recordmcount.pl "i386" "little" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/Sk98IhXeqAWRDccZLFebKKhFr/all/sky2le.o";
  set -e ; perl /usr/src/linux-headers-2.6.35-24-generic/scripts/recordmcount.pl "i386" "little" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/Sk98IhXeqAWRDccZLFebKKhFr/all/skethtool.o";
  set -e ; perl /usr/src/linux-headers-2.6.35-24-generic/scripts/recordmcount.pl "i386" "little" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/Sk98IhXeqAWRDccZLFebKKhFr/all/sky2.o";
make[1]: *** [_module_/tmp/Sk98IhXeqAWRDccZLFebKKhFr/all] Error 2
make: *** [sub-make] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
+++ Compiler error

---

### Post by PatchesTheCaveman on 2011-01-12
Hmm.  Let's take a look at a few things.  Run:
```
lspci -vnn
nm-tool
```

and copy/paste the output.

---

### Post by snisarg on 2011-01-12
please note : this is after i gained a connection to the internet(after several tries)
----------------------------------------------------------

nisarg@nisarg-VPCEB14EN:~$ lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0045] (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: e0000000-f00fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f5e0a000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05) (prog-if 20 [EHCI])
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f5e08000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at f5e00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f4a00000-f5dfffff
	Prefetchable memory behind bridge: 00000000bc100000-00000000bc2fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: f3600000-f49fffff
	Prefetchable memory behind bridge: 00000000bc300000-00000000bc4fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f2200000-f35fffff
	Prefetchable memory behind bridge: 00000000bc500000-00000000bc6fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: f0200000-f21fffff
	Prefetchable memory behind bridge: 00000000bc700000-00000000bc8fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05) (prog-if 20 [EHCI])
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f5e07000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05) (prog-if 01 [AHCI 1.0])
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 46
	I/O ports at e070 [size=8]
	I/O ports at e060 [size=4]
	I/O ports at e050 [size=8]
	I/O ports at e040 [size=4]
	I/O ports at e020 [size=32]
	Memory at f5e06000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: medium devsel, IRQ 4
	Memory at f5e05000 (64-bit, non-prefetchable) [size=256]
	I/O ports at e000 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series] [1002:68e0] (prog-if 00 [VGA controller])
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0, IRQ 49
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f0020000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at d000 [size=256]
	Expansion ROM at f0000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

01:00.1 Audio device [0403]: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series] [1002:aa68]
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0, IRQ 48
	Memory at f0040000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e017]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f4a00000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

03:00.0 SD Host controller [0805]: Ricoh Co Ltd Device [1180:e822]
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f3602000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

03:00.1 System peripheral [0880]: Ricoh Co Ltd Device [1180:e230]
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0, IRQ 4
	Memory at f3601000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:00.4 SD Host controller [0805]: Ricoh Co Ltd Device [1180:e822]
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f3600000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8059 PCI-E Gigabit Ethernet Controller [11ab:4381] (rev 11)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at f2220000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at a000 [size=256]
	Expansion ROM at f2200000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

3f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0

3f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0

3f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0

3f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0

3f:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0

3f:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)
	Subsystem: Sony Corporation Device [104d:9071]
	Flags: bus master, fast devsel, latency 0


--------------------------------------------------------------
nisarg@nisarg-VPCEB14EN:~$ nm-tool

NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        78:DD:08:CB:38:B1

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [DSL connection 1] ---------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        54:42:49:0E:5B:F7

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         111.91.108.188
    Prefix:          32 (255.255.255.255)
    Gateway:         115.117.29.245

    DNS:             8.8.8.8
    DNS:             8.8.4.4

---

### Post by PatchesTheCaveman on 2011-01-12
Try updating the built-in network card drivers.  Run the following command:
```
gksudo software-properties-gtk
```
and check the "Unsupported updates (backports)" box if it isn't already selected.

Then run:
```
sudo apt-get install linux-backports-modules-net-$(lsb_release -cs)-generic
```

---

### Post by mathia on 2011-01-12
Hi Snisarg,
sorry for delay. I was in vacation for few days.
You use the linux kernel version 2.6.35. The sk98lin driver v10.85.9.3 does not support this kernel. Here is the workaround:

1) use ./install.sh -> 3) generate makefile -> follow the commands on display:
$ export ...
$ make ...
it will fail.
2) in DriverInstall/src/skge.c file do as follows:
Replace the lines with (-) to (+)

-            struct dev_mc_list    *pMcList;*/
+           struct netdev_hw_addr    *ha;[INDENT] int            i; 
............

            ("Number of MC entries: %d ", dev->mc_count)); 
         
-       pMcList = dev->mc_list; 
-        for (i=0; i<dev->mc_count; i++, pMcList = pMcList->next) { 
-            SkAddrMcAdd(pAC, pAC->IoBase, PortIdx, 
-                (SK_MAC_ADDR*)pMcList->dmi_addr, 0); 
-            SK_DBG_MSG(NULL, SK_DBGMOD_DRV, SK_DBGCAT_DRV_MCA, 
-                ("%02x:%02x:%02x:%02x:%02x:%02x\n", 
-                pMcList->dmi_addr[0], 
-                pMcList->dmi_addr[1], 
-                pMcList->dmi_addr[2], 
-                pMcList->dmi_addr[3], 
-                pMcList->dmi_addr[4], 
-                pMcList->dmi_addr[5])); 
-        }

+        i=0; 
+        netdev_for_each_mc_addr (ha, dev){ 
+            SkAddrMcAdd(pAC, pAC->IoBase, PortIdx, 
+                (SK_MAC_ADDR*)ha->addr, 0); 
+            SK_DBG_MSG(NULL, SK_DBGMOD_DRV, SK_DBGCAT_DRV_MCA, 
+                ("%02x:%02x:%02x:%02x:%02x:%02x\n")); 
+            i++; 
+        } 
 
        SkAddrMcUpdate(pAC, pAC->IoBase, PortIdx)

3) use make command again to bulid the driver (sk98lin.ko)
4) load the driver with:
$ insmod src/sk98lin.ko

Please let me know if it works.
[/INDENT]

---

### Post by snisarg on 2011-01-13
Thank you for your replies...

can you please explain the process of 'make' and even the next step. I really don't know how to use the terminal commands.

---

### Post by snisarg on 2011-01-13
@PatchesTheCaveman

i did what you requested and it worked successfully.
-------------------------------------------------------------
nisarg@nisarg-VPCEB14EN:~$ gksudo software-properties-gtk
nisarg@nisarg-VPCEB14EN:~$ sudo apt-get install linux-backports-modules-net-$(lsb_release -cs)-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-backports-modules-net-2.6.35-24-generic
The following NEW packages will be installed:
  linux-backports-modules-net-2.6.35-24-generic
  linux-backports-modules-net-maverick-generic
0 upgraded, 2 newly installed, 0 to remove and 39 not upgraded.
Need to get 82.6kB of archives.
After this operation, 274kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main linux-backports-modules-net-2.6.35-24-generic i386 2.6.35-24.15 [77.5kB]
Get:2 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main linux-backports-modules-net-maverick-generic i386 2.6.35.24.28 [5,092B]
Fetched 82.6kB in 7s (10.5kB/s)                                                
Selecting previously deselected package linux-backports-modules-net-2.6.35-24-generic.
(Reading database ... 148327 files and directories currently installed.)
Unpacking linux-backports-modules-net-2.6.35-24-generic (from .../linux-backports-modules-net-2.6.35-24-generic_2.6.35-24.15_i386.deb) ...
Selecting previously deselected package linux-backports-modules-net-maverick-generic.
Unpacking linux-backports-modules-net-maverick-generic (from .../linux-backports-modules-net-maverick-generic_2.6.35.24.28_i386.deb) ...
Setting up linux-backports-modules-net-2.6.35-24-generic (2.6.35-24.15) ...
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic
Setting up linux-backports-modules-net-maverick-generic (2.6.35.24.28) ...
nisarg@nisarg-VPCEB14EN:~$
--------------------------------------------------------

so now what? is it done?

---

### Post by PatchesTheCaveman on 2011-01-14
Yeah.  Reboot and see if it's any better.  If not you will need to try mathia's solution.

---

### Post by snisarg on 2011-01-14
Okay. I can now safely say my problem is solved!
thank you for helping me considering you had to explain even the baby steps to me in detail.
however, i have tried both your suggestions, so i cannot say what exactly helped(ie, what the prolbems was exactly and how was it solved.) For those who have such similar problems, just try both :)
thank you once again.

---

