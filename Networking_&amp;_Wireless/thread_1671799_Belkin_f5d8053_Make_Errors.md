---
title: "Belkin f5d8053 Make Errors"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by chaozuper on 2011-01-20
Hi, I've been trying to follow this tutorial:

[http://ubuntuforums.org/showthread.php?t=1382798&highlight=F5D8053](http://ubuntuforums.org/showthread.php?t=1382798&highlight=F5D8053)

to get my Belkin F5D8053 Wireless Adapter working. I get so far as using the "make" command, but then encounter an error. This is the full terminal results:

> eric@ericonpenguin:~/2010_0709_RT2870_Linux_STA_v2.4.0.1$ make
make -C tools
make[1]: Entering directory `/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools'
/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools/bin2h
cp -f os/linux/Makefile.6 /home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/Makefile
make -C /lib/modules/2.6.35-24-generic/build SUBDIRS=/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-24-generic'
  CC [M]  /home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o
/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocUsbBulkBufStruct’:
/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:52: error: implicit declaration of function ‘usb_buffer_alloc’
/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:52: warning: assignment makes pointer from integer without a cast
/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeUsbBulkBufStruct’:
/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:78: error: implicit declaration of function ‘usb_buffer_free’
/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:234: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:241: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:278: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitTransmit’:
/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:507: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:566: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:596: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:610: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:628: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘UCHAR **’
make[2]: *** [/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/eric/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
make: *** [LINUX] Error 2
I'm using Ubuntu 10.10. Any help would be greatly appreciated as I really want to get my ubuntu computer online! thanks.

---

### Post by PCNetSpec on 2011-03-06
Kernels >= 2.6.35 will fail to compile (make) the driver because the driver makes use of the functions **usb_buffer_alloc()** and **usb_buffer_free()** which were renamed in kernel 2.6.35 

For a fix, see the red [COLOR="Red"]EDIT[/COLOR] in this posting:
[http://linuxforums.org.uk/hardware-compatibility/ralink-rt2870-based-usb-wireless-n-adapters-(ubuntu)/](http://linuxforums.org.uk/hardware-compatibility/ralink-rt2870-based-usb-wireless-n-adapters-(ubuntu)/)


Or, I've uploaded a pre-modified version of the driver that WILL compile on kernels >= 2.6.35 here:
[2010_0709_RT2870_Linux_STA_v2.4.0.1.tar.bz2](http://bit.ly/eZHx0J)

---

