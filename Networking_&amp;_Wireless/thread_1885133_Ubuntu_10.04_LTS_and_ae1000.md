---
title: "Ubuntu 10.04 LTS and ae1000"
date: 2011-11-22
forum: Networking &amp; Wireless
---

### Post by mjvernon on 2011-11-22
I installed Ubuntu 10.04 LTS  yesterday, I followed several different guide to get me Linksys AE1000 to work.  I downloaded a file that had all the changes to the ./common/rtusb_dev_id.c, ./os/linux/config.mk, and to ./include/os/rt_linux.h files and have gone through and verified the changes are correct..  I then ran "sudo apt-get install build-essential linux-headers-generic" it runs fine, but when I use the make command I am still getting errors.  
I would appreciate any help.


mjvernon@mjvernon-desktop:~/Downloads/linksys_ae1000_linux_driver_mod$ make
make -C tools
make[1]: Entering directory `/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/tools'
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/tools/bin2h
cp -f os/linux/Makefile.6 /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/Makefile
make -C /lib/modules/2.6.32-33-generic/build SUBDIRS=/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-33-generic'
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/crypt_md5.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/crypt_aes.o
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/crypt_aes.c:2265: warning: the frame size of 1100 bytes is larger than 1024 bytes
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/crypt_aes.c: In function ‘WscDecryptData’:
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/crypt_aes.c:1592: warning: the frame size of 1364 bytes is larger than 1024 bytes
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/crypt_aes.c: In function ‘WscEncryptData’:
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/crypt_aes.c:1522: warning: the frame size of 1364 bytes is larger than 1024 bytes
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/mlme.o
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/mlme.c:6112: warning: the frame size of 1720 bytes is larger than 1024 bytes
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_wep.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/action.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_data.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/rtmp_init.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_aes.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_sync.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/eeprom.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_info.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/dfs.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/spectrum.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/rt_channel.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_profile.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_asic.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../sta/assoc.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../sta/auth.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../sta/sync.o
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../sta/sync.c:1764: warning: the frame size of 1308 bytes is larger than 1024 bytes
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../sta/sync.c:1094: warning: the frame size of 1300 bytes is larger than 1024 bytes
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../sta/sync.c:764: warning: the frame size of 1268 bytes is larger than 1024 bytes
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../sta/sync.c:581: warning: the frame size of 1064 bytes is larger than 1024 bytes
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../sta/sanity.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../sta/connect.o
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../sta/connect.c:356: warning: the frame size of 1748 bytes is larger than 1024 bytes
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../sta/wpa.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../sta/ags.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/ba_action.o
  CC [M]  /home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.o
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocUsbBulkBufStruct’:
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.c:52: error: implicit declaration of function ‘usb_alloc_coherent’
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.c:52: warning: assignment makes pointer from integer without a cast
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeUsbBulkBufStruct’:
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.c:78: error: implicit declaration of function ‘usb_free_coherent’
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.c:234: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.c:241: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.c:278: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitTransmit’:
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.c:507: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.c:566: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.c:596: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.c:610: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.c:628: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘UCHAR **’
make[2]: *** [/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/mjvernon/Downloads/linksys_ae1000_linux_driver_mod/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-33-generic'
make: *** [LINUX] Error 2

---

### Post by Paddy Landau on 2011-11-29
I see no one has answered you, so let's see if we can at least get you started.

It seems that 10.04 does not have the driver that you need for your wireless.

As a first step, I would download the lasted version of Ubuntu (11.10), burn it to a CD or, preferably, to a USB stick. Boot from the Live CD (or USB), choose to try Ubuntu (not install), and see whether or not you can connect to the Internet.

If you can, then 11.10 has a driver that works, so install 11.10 over 10.04 (be sure to first back up any data you might have saved).

If you still cannot access the Internet, tell us *exactly* what happens when you try to connect -- in other words, what tells you that it is not working?

---

### Post by mjvernon on 2011-12-11
I upgraded to 11.10, installed the drivers and now it works. Thanks

---

