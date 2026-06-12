---
title: "wifi adapter not working after upgrade to 11.10"
date: 2012-11-02
forum: Networking &amp; Wireless
---

### Post by cve009 on 2012-11-02
I have been struggling with this and not making any progress and would like some suggestions from the forums knowledgeable about Ubuntu.  I read many threads about wifi adapter issues and tried to proactively answer the common questions.  I hope that did not make this thread too long.

Issue:
The wireless network adapter worked fine using 11.04.
After upgrading to 11.10, I seem to have no wireless device.  The PC shows no signs of searching for a wifi signal.  And of course, I have no network connectivity.

I believe I already have what I need.  Possibly something is in the wrong location.  But it worked on 11.04, so I think I just need to set it up in a way that 11.10 understands.  I did try reinstalling the old driver and installing a new driver (notes below).  That did not help.

iwconfig shows no wireless devices.
lsusb shows the ASUS device which is plugged into a USB port:
 Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
lspci shows the Realtek driver which is the original driver:
 01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

$ sudo modprobe rtl8192cu swenc=1
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Error inserting rtl8192cu (/lib/modules/3.0.0-26-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko): Unknown symbol in module, or unknown parameter (see dmesg)

$ modinfo rtl8192cu
filename:       /lib/modules/3.0.0-26-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
srcversion:     6CDAA0F2DC1FD3297EBA8A6
alias:          usb:v7392p7822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p330Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3309d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0056d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v3359p13D3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v3358p13D3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7811d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20F4p648Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3308d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v103Cp1629d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0EB0p9071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0052d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8189d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8188d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE033d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp1102d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8754d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8176d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8170d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8191d*dc*dsc*dp*ic*isc*ip*
depends:        rtlwifi,mac80211,rtl8192c-common
vermagic:       3.0.0-26-generic SMP mod_unload modversions 686 

$ sudo modprobe -r rtl8192cu
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.


Try to reinstall old driver:
$ pwd
/home/eyster/drivers/rtl8192_8188CU_linux_v3.0.2164.20110715
$ sudo su -c "make 8192cu.ko"
make: *** No rule to make target `8192cu.ko'.  Stop.
$ sudo su -c make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.0.0-26-generic/build M=/home/eyster/drivers/rtl8192_8188CU_linux_v3.0.2164.20110715  modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-26-generic'
  CC [M]  /home/eyster/drivers/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.o
In file included from /home/eyster/drivers/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.c:24:0:
/home/eyster/drivers/rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_service.h:49:29: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/home/eyster/drivers/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/home/eyster/drivers/rtl8192_8188CU_linux_v3.0.2164.20110715] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-26-generic'
make: *** [modules] Error 2

Try to install new driver:
$ pwd
/home/eyster/drivers/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715
$ sudo su -c make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.0.0-26-generic/build M=/home/eyster/drivers/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715  modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-26-generic'
  CC [M]  /home/eyster/drivers/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.o
In file included from /home/eyster/drivers/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.c:24:0:
/home/eyster/drivers/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_service.h:49:29: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/home/eyster/drivers/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/home/eyster/drivers/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-26-generic'
make: *** [modules] Error 2

---

### Post by cve009 on 2012-11-04
Not one suggestion or question in 2 days.  I must be in serious trouble.

---

### Post by cve009 on 2012-11-12
FYI,
I resolved this by installing a new driver:
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105

I don't know if these threads can be marked as "resolved", but this one is.
thx

---

