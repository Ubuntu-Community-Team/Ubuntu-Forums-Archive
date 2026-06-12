---
title: "help me....can't install RT2870"
date: 2013-01-01
forum: Networking &amp; Wireless
---

### Post by walpurgis on 2013-01-01
i tried with this instruction
[http://ubuntuforums.org/showthread.php?t=1310569](http://ubuntuforums.org/showthread.php?t=1310569)
but it's blocked at "make"

make[2]: *** [/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/chen/desktop/RT2870/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2

```

root@ubuntu:/home/chen/desktop/RT2870# make
make -C tools
make[1]: Entering directory `/home/chen/desktop/RT2870/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/chen/desktop/RT2870/tools'
/home/chen/desktop/RT2870/tools/bin2h
cp -f os/linux/Makefile.6 /home/chen/desktop/RT2870/os/linux/Makefile
make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/chen/desktop/RT2870/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/crypt_md5.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/crypt_aes.o
/home/chen/desktop/RT2870/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/chen/desktop/RT2870/os/linux/../../common/crypt_aes.c:2265: warning: the frame size of 1100 bytes is larger than 1024 bytes
/home/chen/desktop/RT2870/os/linux/../../common/crypt_aes.c: In function ‘WscDecryptData’:
/home/chen/desktop/RT2870/os/linux/../../common/crypt_aes.c:1592: warning: the frame size of 1356 bytes is larger than 1024 bytes
/home/chen/desktop/RT2870/os/linux/../../common/crypt_aes.c: In function ‘WscEncryptData’:
/home/chen/desktop/RT2870/os/linux/../../common/crypt_aes.c:1522: warning: the frame size of 1356 bytes is larger than 1024 bytes
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/mlme.o
/home/chen/desktop/RT2870/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/chen/desktop/RT2870/os/linux/../../common/mlme.c:6100: warning: the frame size of 1720 bytes is larger than 1024 bytes
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/cmm_wep.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/action.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/cmm_data.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/rtmp_init.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/cmm_aes.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/cmm_sync.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/eeprom.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/cmm_info.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/dfs.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/spectrum.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/rt_channel.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/cmm_profile.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/cmm_asic.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../sta/assoc.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../sta/auth.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../sta/sync.o
/home/chen/desktop/RT2870/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/chen/desktop/RT2870/os/linux/../../sta/sync.c:1764: warning: the frame size of 1308 bytes is larger than 1024 bytes
/home/chen/desktop/RT2870/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/chen/desktop/RT2870/os/linux/../../sta/sync.c:1094: warning: the frame size of 1296 bytes is larger than 1024 bytes
/home/chen/desktop/RT2870/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/chen/desktop/RT2870/os/linux/../../sta/sync.c:764: warning: the frame size of 1264 bytes is larger than 1024 bytes
/home/chen/desktop/RT2870/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/chen/desktop/RT2870/os/linux/../../sta/sync.c:581: warning: the frame size of 1064 bytes is larger than 1024 bytes
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../sta/sanity.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../sta/connect.o
/home/chen/desktop/RT2870/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/chen/desktop/RT2870/os/linux/../../sta/connect.c:355: warning: the frame size of 1748 bytes is larger than 1024 bytes
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../sta/wpa.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../sta/ags.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../os/linux/sta_ioctl.o
/home/chen/desktop/RT2870/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwencode’:
/home/chen/desktop/RT2870/os/linux/../../os/linux/sta_ioctl.c:1479: warning: suggest parentheses around operand of ‘!’ or change ‘&’ to ‘&&’ or ‘!’ to ‘~’
/home/chen/desktop/RT2870/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_iwaplist’:
/home/chen/desktop/RT2870/os/linux/../../os/linux/sta_ioctl.c:599: warning: the frame size of 1284 bytes is larger than 1024 bytes
/home/chen/desktop/RT2870/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwmlme’:
/home/chen/desktop/RT2870/os/linux/../../os/linux/sta_ioctl.c:1979: warning: the frame size of 1652 bytes is larger than 1024 bytes
/home/chen/desktop/RT2870/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlE2PROM’:
/home/chen/desktop/RT2870/os/linux/../../os/linux/sta_ioctl.c:6035: warning: the frame size of 1348 bytes is larger than 1024 bytes
/home/chen/desktop/RT2870/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlMAC’:
/home/chen/desktop/RT2870/os/linux/../../os/linux/sta_ioctl.c:5836: warning: the frame size of 1344 bytes is larger than 1024 bytes
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../os/linux/rt_linux.o
/home/chen/desktop/RT2870/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevDetach’:
/home/chen/desktop/RT2870/os/linux/../../os/linux/rt_linux.c:1694: warning: initialization discards qualifiers from pointer target type
/home/chen/desktop/RT2870/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/chen/desktop/RT2870/os/linux/../../os/linux/rt_linux.c:1731: warning: initialization discards qualifiers from pointer target type
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../os/linux/rt_main_dev.o
/home/chen/desktop/RT2870/os/linux/../../os/linux/rt_main_dev.c: In function ‘MainVirtualIF_close’:
/home/chen/desktop/RT2870/os/linux/../../os/linux/rt_main_dev.c:117: warning: unused variable ‘Cancelled’
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/ba_action.o
  CC [M]  /home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.o
/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocUsbBulkBufStruct’:
/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.c:52: error: implicit declaration of function ‘usb_buffer_alloc’
/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.c:52: warning: assignment makes pointer from integer without a cast
/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeUsbBulkBufStruct’:
/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.c:78: error: implicit declaration of function ‘usb_buffer_free’
/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.c:234: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.c:241: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.c:278: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitTransmit’:
/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.c:507: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.c:566: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.c:596: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.c:610: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.c:628: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘UCHAR **’
make[2]: *** [/home/chen/desktop/RT2870/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/chen/desktop/RT2870/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2


```

---

### Post by sanderj on 2013-01-01
Why do you want to follow a 3 years advice? The original source page [http://ubunturt2870.pbworks.com/w/page/8928776/FrontPage](http://ubunturt2870.pbworks.com/w/page/8928776/FrontPage) says Ubuntu 9.04 has support built in.

So:
Which Ubuntu do you run?
What does "lsusb" say? (Assuming you have a USB device)

---

### Post by walpurgis on 2013-01-01
ubuntu 10.10

lsusb:
Bus 003 Device 002: ID 1c4f:3000 SiGma Micro Micro USB Web Camera
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 012: ID 05e3:0512 Genesys Logic, Inc. 
Bus 001 Device 011: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 010: ID 1241:1166 Belkin MI-2150 Trust Mouse
Bus 001 Device 009: ID 058f:6390 Alcor Micro Corp. USB 2.0-IDE bridge
Bus 001 Device 004: ID 1a40:0101 TERMINUS TECHNOLOGY INC. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 1a40:0201 TERMINUS TECHNOLOGY INC. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by sanderj on 2013-01-01
> **walpurgis said:**
> ubuntu 10.10


Why such an old Ubuntu version? It's not supported anymore (see [http://en.wikipedia.org/wiki/Ubuntu_(operating_system)#Releases](http://en.wikipedia.org/wiki/Ubuntu_(operating_system)#Releases) )

Advice: Use Ubuntu 12.10.

---

### Post by walpurgis on 2013-01-04
i tried 12.10....
and its same error

---

### Post by sanderj on 2013-01-04
> **walpurgis said:**
> i tried 12.10....
and its same error

Same error? Are you trying the "make" procedure? If so, I would think that's not necessary in Ubuntu 12.10.

So, do this:

If possbile: unplug wifi module, and put it in again.
Then type "dmesg | tail" and post the output here.

---

