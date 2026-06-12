---
title: "Kernel version and header mismatch during driver install"
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by bvande on 2010-05-24
I was trying to update my network card driver, and was going through the normal install when all of the sudden an error came up...

It says,
> "Check kernel header version (Kernel:2.6.32 != Header:2.6.32.11+drm33) [failed]"it goes on to say that due to the mismatch I won't be able to load the driver without the force option after its compilation finished.

> "This problem can be resolved by overwriting the current include/version.h (associated with kernel verison), with the include/version.h of the kernel version currently running.

BEWARE: OVERWRITE THE FILE ONLY IF YOU HAVE REALLY THE CORRECT HEADER FILE CORRESPONDING TO THE CURRENT RUNNING

If you know what you're doing and want to override this check, you can do so by setting IGNORE_HEADER_MISMATCH system variable: example, export IGNORE_HEADER_MISMATCH=1

or change the /usr/src/linux/include/linux/version.h to UTS_RELEASE '2.6.32-22-generic'

Installation of package failed"...

ok, so now I don't have a working network driver on my Ubuntu box :P What should I do to fix this problem and install the new driver? Would I be safe to do their recommended fix of changing either the global check or editing version.h?

---

### Post by bvande on 2010-05-24
I tried their global "work around," and I wasn't too surprised when it didn't work. Here's the log, maybe it has some clues (I didn't understand anything enough to make a fix)

Installation.log
> 
+++ Install mode: User
+++ Driver version: 10.61.3.3 (Jul-07-2008)
+++ Kernel version 2.6.32-22-generic
+++ smp_count=1
+++ cpu_number=1
+++ kernel_machine=i686
+++ Architecture: i386
+++ modpost available
+++ Unpack the sources
+++ ====================================
+++ tar xfv sk98lin.tar
2.4/
2.4/skdim.c
2.4/sky2.c
2.4/skethtool.c
2.4/Makefile
2.4/skge.c
2.4/h/
2.4/h/skdrv1st.h
2.4/h/skdrv2nd.h
2.4/skproc.c
2.6/
2.6/skdim.c
2.6/sky2.c
2.6/skethtool.c
2.6/Makefile
2.6/skge.c
2.6/h/
2.6/h/skdrv1st.h
2.6/h/skdrv2nd.h
2.6/skproc.c
common/
common/skgehwt.c
common/skgeasf.c
common/sk98lin.htm
common/skgeinit.c
common/sktwsi.c
common/skvpd.c
common/sky2le.c
common/sk98lin.4
common/skfops.c
common/skgespilole.c
common/skgeasfconv.c
common/skgemib.c
common/skaddr.c
common/skcsum.c
common/skgepnmi.c
common/vpdcheck.c
common/sklm80.c
common/skqueue.c
common/sktimer.c
common/skrlmt.c
common/skgespi.c
common/skxmac2.c
common/skgesirq.c
common/h/
common/h/sktypes.h
common/h/skpcidevid.h
common/h/skqueue.h
common/h/skrlmt.h
common/h/skgepnm2.h
common/h/skgeasfconv.h
common/h/skaddr.h
common/h/skdebug.h
common/h/mvyexhw.h
common/h/skgehw.h
common/h/skgehwt.h
common/h/skfops.h
common/h/sktimer.h
common/h/skgepnmi.h
common/h/skvpd.h
common/h/skgetwsi.h
common/h/skerror.h
common/h/sktwsi.h
common/h/skcsum.h
common/h/skversion.h
common/h/xmac_ii.h
common/h/sky2le.h
common/h/skgeasf.h
common/h/skgespi.h
common/h/skgeinit.h
common/h/skgesirq.h
common/h/lm80.h
common/h/skgedrv.h
common/sk98lin.txt
misc/
misc/Kconfig
misc/Configure.help

+++ Compile the driver
+++ ====================================
make: Entering directory `/usr/src/linux-headers-2.6.32-22'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.32-22/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.o
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:68:
include/linux/mmzone.h:18:26: error: linux/bounds.h: No such file or directory
include/linux/mmzone.h:258:5: warning: "MAX_NR_ZONES" is not defined
include/linux/mmzone.h:260:7: warning: "MAX_NR_ZONES" is not defined
include/linux/mmzone.h:262:7: warning: "MAX_NR_ZONES" is not defined
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:68:
include/linux/mmzone.h:300: error: â€˜MAX_NR_ZONESâ€™ undeclared here (not in a function)
In file included from /usr/src/linux-headers-2.6.32-22/arch/x86/include/asm/pci.h:4,
                 from include/linux/pci.h:1126,
                 from /tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/h/skdrv1st.h:58,
                 from /tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:83:
include/linux/mm.h:454:63: warning: "NR_PAGEFLAGS" is not defined
include/linux/mm.h:502:62: warning: "NR_PAGEFLAGS" is not defined
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c: In function â€˜sk98lin_init_deviceâ€™:
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:412: error: â€˜struct net_deviceâ€™ has no member named â€˜privâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:454: error: â€˜struct net_deviceâ€™ has no member named â€˜openâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:455: error: â€˜struct net_deviceâ€™ has no member named â€˜stopâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:456: error: â€˜struct net_deviceâ€™ has no member named â€˜get_statsâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:457: error: â€˜struct net_deviceâ€™ has no member named â€˜set_multicast_listâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:458: error: â€˜struct net_deviceâ€™ has no member named â€˜set_mac_addressâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:459: error: â€˜struct net_deviceâ€™ has no member named â€˜do_ioctlâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:460: error: â€˜struct net_deviceâ€™ has no member named â€˜change_mtuâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:463: error: â€˜struct net_deviceâ€™ has no member named â€˜poll_controllerâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:481: error: â€˜struct net_deviceâ€™ has no member named â€˜hard_start_xmitâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:483: error: â€˜struct net_deviceâ€™ has no member named â€˜pollâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:484: error: â€˜struct net_deviceâ€™ has no member named â€˜weightâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:487: error: â€˜struct net_deviceâ€™ has no member named â€˜hard_start_xmitâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:489: error: â€˜struct net_deviceâ€™ has no member named â€˜pollâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:490: error: â€˜struct net_deviceâ€™ has no member named â€˜weightâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:577: error: â€˜struct proc_dir_entryâ€™ has no member named â€˜ownerâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:603: error: â€˜struct net_deviceâ€™ has no member named â€˜privâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:609: error: â€˜struct net_deviceâ€™ has no member named â€˜hard_start_xmitâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:611: error: â€˜struct net_deviceâ€™ has no member named â€˜pollâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:612: error: â€˜struct net_deviceâ€™ has no member named â€˜weightâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:615: error: â€˜struct net_deviceâ€™ has no member named â€˜hard_start_xmitâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:617: error: â€˜struct net_deviceâ€™ has no member named â€˜pollâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:618: error: â€˜struct net_deviceâ€™ has no member named â€˜weightâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:626: error: â€˜struct net_deviceâ€™ has no member named â€˜openâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:627: error: â€˜struct net_deviceâ€™ has no member named â€˜stopâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:628: error: â€˜struct net_deviceâ€™ has no member named â€˜get_statsâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:629: error: â€˜struct net_deviceâ€™ has no member named â€˜set_multicast_listâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:630: error: â€˜struct net_deviceâ€™ has no member named â€˜set_mac_addressâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:631: error: â€˜struct net_deviceâ€™ has no member named â€˜do_ioctlâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:632: error: â€˜struct net_deviceâ€™ has no member named â€˜change_mtuâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:635: error: â€˜struct net_deviceâ€™ has no member named â€˜poll_controllerâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c: In function â€˜sk98lin_resumeâ€™:
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:1124: error: â€˜struct net_deviceâ€™ has no member named â€˜privâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c: In function â€˜sk98lin_suspendâ€™:
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:1202: error: â€˜struct net_deviceâ€™ has no member named â€˜privâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c: In function â€˜FreeResourcesâ€™:
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:1517: error: â€˜struct net_deviceâ€™ has no member named â€˜privâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:1518: error: â€˜struct net_deviceâ€™ has no member named â€˜privâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c: In function â€˜sk98lin_remove_deviceâ€™:
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:1699: error: â€˜struct net_deviceâ€™ has no member named â€˜privâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:1760: error: â€˜struct net_deviceâ€™ has no member named â€˜get_statsâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c: In function â€˜SkGeIsrâ€™:
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:2303: error: â€˜struct net_deviceâ€™ has no member named â€˜privâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:2315: error: implicit declaration of function â€˜netif_rx_schedule_prepâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:2318: error: implicit declaration of function â€˜__netif_rx_scheduleâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c: In function â€˜SkGeIsrOnePortâ€™:
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:2473: error: â€˜struct net_deviceâ€™ has no member named â€˜privâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c: In function â€˜SkGeOpenâ€™:
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:2593: error: â€˜struct net_deviceâ€™ has no member named â€˜privâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c: In function â€˜SkGeCloseâ€™:
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:2915: error: â€˜struct net_deviceâ€™ has no member named â€˜privâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:2958: error: â€˜struct net_deviceâ€™ has no member named â€˜privâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c: In function â€˜SkGeXmitâ€™:
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:3190: error: â€˜struct net_deviceâ€™ has no member named â€˜privâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c: In function â€˜SkGePollâ€™:
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:3249: error: â€˜struct net_deviceâ€™ has no member named â€˜privâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:3250: error: â€˜struct net_deviceâ€™ has no member named â€˜quotaâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:3250: warning: type defaults to â€˜intâ€™ in declaration of â€˜_min2â€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:3250: error: â€˜struct net_deviceâ€™ has no member named â€˜quotaâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:3271: error: â€˜struct net_deviceâ€™ has no member named â€˜quotaâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:3275: error: implicit declaration of function â€˜netif_rx_completeâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c: In function â€˜SkGeNetPollâ€™:
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:3304: error: â€˜struct net_deviceâ€™ has no member named â€˜privâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c: In function â€˜SkGeSetMacAddrâ€™:
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:4348: error: â€˜struct net_deviceâ€™ has no member named â€˜privâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c: In function â€˜SkGeSetRxModeâ€™:
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:4406: error: â€˜struct net_deviceâ€™ has no member named â€˜privâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c: In function â€˜SkGeChangeMtuâ€™:
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:4518: error: â€˜struct net_deviceâ€™ has no member named â€˜privâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c: In function â€˜SkGeStatsâ€™:
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:4641: error: â€˜struct net_deviceâ€™ has no member named â€˜privâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c: In function â€˜SkGeIoctlâ€™:
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:4946: error: â€˜struct net_deviceâ€™ has no member named â€˜privâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c: In function â€˜SkDrvEventâ€™:
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:6804: error: â€˜struct net_deviceâ€™ has no member named â€˜privâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c: In function â€˜SkDrvEnterDiagModeâ€™:
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:7096: error: â€˜struct net_deviceâ€™ has no member named â€˜privâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:7113: error: â€˜struct net_deviceâ€™ has no member named â€˜privâ€™
/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.c:7114: error: â€˜struct net_deviceâ€™ has no member named â€˜privâ€™
make[1]: *** [/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all/skge.o] Error 1
make: *** [_module_/tmp/Sk98IQanmArMQRCgXlmeLkSpn/all] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.32-22'
+++ Compiler error


---

### Post by puppywhacker on 2010-05-24
wow, lets do a few steps back.

which ethernet controller do you have in "lspci". Is it a marvell gigabit? where did you get the drivers from? where did you get the linux headers from?

The thing is that your compiling fails on the module skge which is a kernel module which already exists

```
/lib/modules/2.6.32-21-generic/kernel/drivers/net/skge.ko

```

doing a "modprobe skge" could already help.

I don't have your specific interface and it might be more complicated than just a modprobe, but I bet the free beer I just won, that this module doesn't need to be compiled unless you really really want to.

P.S you can read the man page from a terminal"man sk98lin" it has the full story for your card.

---

### Post by bvande on 2010-05-24
> which ethernet controller do you have in "lspci". Is it a marvell gigabit?
00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
> where did you get the drivers from?
[http://www.marvell.com/support.html](http://www.marvell.com/support.html) -> "88E8001 Search" -> Kernel 2.6.x Linux Driver Install Package for Yukon Devices	Linux 2.6 - Fedora	4/27/10	v10.85.3.3
> where did you get the linux headers from?
Whatever came with Ubuntu 10.04 standard install.

The "modprobe skge" fixed the ethernet driver temporarily (thanks), but, the performance is still aweful. It's a wired connection, and I have a 60mbps/40mbps internet connection and it's only performing at 1/10th its potential. I thought that by replacing the driver it would fix performance... ([http://www.speedtest.net/result/825019815.png](http://www.speedtest.net/result/825019815.png))

any other advice?

---

### Post by puppywhacker on 2010-05-25
hi, I have very little time today, you can probably provide options to manually set the speed of the interface. If you can modprobe I think you can add the module with update-ramfs to survive reboots. I still can't judge if you really need the newer kernel module from marvell, but I found a thread that solves your first problem, In general the modules Ubuntu ships with are the better solution, but if Marvell released a proper driver only a few months ago? then you may gain from compiling it yourself.

[http://swiss.ubuntuforums.org/showthread.php?t=1330283]("http://swiss.ubuntuforums.org/showthread.php?t=1330283")

to find the reason for the slow network I would use the following commands
dmesg
sudo mii-tool
sudo ethtool eth0

---

### Post by mathia on 2010-09-16
Hi,
please install the following driver as follows:
[http://www.marvell.com/support.html](http://www.marvell.com/support.html)  -> "88E8001 Search" -> Kernel 2.6.x Linux Driver Install Package for Yukon Devices	Linux 2.6 - Fedora v10.85.9.3

 $ sudo bash ./install.sh

and let me know if it works.

have a lot of fun ...:p

---

