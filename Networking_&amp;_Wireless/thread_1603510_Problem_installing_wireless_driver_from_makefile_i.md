---
title: "Problem installing wireless driver from makefile in maverick"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by Renegade13 on 2010-10-22
I have a linksys AE 1000 wireless N usb card. which is a simi9lar model to the WUSB600N.
On lucid I was able to install the driver via a make file I had got from a website. and had absolutley no problems with it.
 
the i made the change to 10.10 maverick and im getting an install error, that i never got on 10.04.
 
this is the error
 
[EMAIL="renegade@renegade-desktop:~$"]renegade@renegade-desktop:~$[/EMAIL] cd wireless
[EMAIL="renegade@renegade-desktop:~/wireless$"]renegade@renegade-desktop:~/wireless$[/EMAIL] sudo make
[sudo] password for renegade: 
make -C tools
make[1]: Entering directory `/home/renegade/wireless/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/renegade/wireless/tools'
/home/renegade/wireless/tools/bin2h
cp -f os/linux/Makefile.6 /home/renegade/wireless/os/linux/Makefile
make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/renegade/wireless/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/renegade/wireless/os/linux/../../common/crypt_md5.o
  CC [M]  /home/renegade/wireless/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/renegade/wireless/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/renegade/wireless/os/linux/../../common/crypt_aes.o
/home/renegade/wireless/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/renegade/wireless/os/linux/../../common/crypt_aes.c:2265: warning: the frame size of 1664 bytes is larger than 1024 bytes
/home/renegade/wireless/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_UNWRAP’:
/home/renegade/wireless/os/linux/../../common/crypt_aes.c:2348: warning: the frame size of 1168 bytes is larger than 1024 bytes
/home/renegade/wireless/os/linux/../../common/crypt_aes.c: In function ‘WscDecryptData’:
/home/renegade/wireless/os/linux/../../common/crypt_aes.c:1592: warning: the frame size of 1408 bytes is larger than 1024 bytes
/home/renegade/wireless/os/linux/../../common/crypt_aes.c: In function ‘WscEncryptData’:
/home/renegade/wireless/os/linux/../../common/crypt_aes.c:1522: warning: the frame size of 1408 bytes is larger than 1024 bytes
  CC [M]  /home/renegade/wireless/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/renegade/wireless/os/linux/../../common/mlme.o
/home/renegade/wireless/os/linux/../../common/mlme.c: In function ‘MlmeResetRalinkCounters’:
/home/renegade/wireless/os/linux/../../common/mlme.c:895: warning: cast from pointer to integer of different size
/home/renegade/wireless/os/linux/../../common/mlme.c:895: warning: cast from pointer to integer of different size
/home/renegade/wireless/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/renegade/wireless/os/linux/../../common/mlme.c:6112: warning: the frame size of 1728 bytes is larger than 1024 bytes
  CC [M]  /home/renegade/wireless/os/linux/../../common/cmm_wep.o
  CC [M]  /home/renegade/wireless/os/linux/../../common/action.o
  CC [M]  /home/renegade/wireless/os/linux/../../common/cmm_data.o
  CC [M]  /home/renegade/wireless/os/linux/../../common/rtmp_init.o
  CC [M]  /home/renegade/wireless/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/renegade/wireless/os/linux/../../common/cmm_aes.o
  CC [M]  /home/renegade/wireless/os/linux/../../common/cmm_sync.o
  CC [M]  /home/renegade/wireless/os/linux/../../common/eeprom.o
  CC [M]  /home/renegade/wireless/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/renegade/wireless/os/linux/../../common/cmm_info.o
  CC [M]  /home/renegade/wireless/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/renegade/wireless/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/renegade/wireless/os/linux/../../common/dfs.o
  CC [M]  /home/renegade/wireless/os/linux/../../common/spectrum.o
/home/renegade/wireless/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/renegade/wireless/os/linux/../../common/spectrum.c:1977: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/renegade/wireless/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/renegade/wireless/os/linux/../../common/rt_channel.o
  CC [M]  /home/renegade/wireless/os/linux/../../common/cmm_profile.o
  CC [M]  /home/renegade/wireless/os/linux/../../common/cmm_asic.o
  CC [M]  /home/renegade/wireless/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/renegade/wireless/os/linux/../../sta/assoc.o
  CC [M]  /home/renegade/wireless/os/linux/../../sta/auth.o
  CC [M]  /home/renegade/wireless/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/renegade/wireless/os/linux/../../sta/sync.o
/home/renegade/wireless/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/renegade/wireless/os/linux/../../sta/sync.c:1764: warning: the frame size of 1456 bytes is larger than 1024 bytes
/home/renegade/wireless/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/renegade/wireless/os/linux/../../sta/sync.c:1094: warning: the frame size of 1440 bytes is larger than 1024 bytes
/home/renegade/wireless/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/renegade/wireless/os/linux/../../sta/sync.c:764: warning: the frame size of 1376 bytes is larger than 1024 bytes
/home/renegade/wireless/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/renegade/wireless/os/linux/../../sta/sync.c:581: warning: the frame size of 1088 bytes is larger than 1024 bytes
  CC [M]  /home/renegade/wireless/os/linux/../../sta/sanity.o
  CC [M]  /home/renegade/wireless/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/renegade/wireless/os/linux/../../sta/connect.o
/home/renegade/wireless/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/renegade/wireless/os/linux/../../sta/connect.c:356: warning: the frame size of 1776 bytes is larger than 1024 bytes
  CC [M]  /home/renegade/wireless/os/linux/../../sta/wpa.o
  CC [M]  /home/renegade/wireless/os/linux/../../sta/ags.o
  CC [M]  /home/renegade/wireless/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/renegade/wireless/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/renegade/wireless/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/renegade/wireless/os/linux/../../os/linux/sta_ioctl.o
/home/renegade/wireless/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwencode’:
/home/renegade/wireless/os/linux/../../os/linux/sta_ioctl.c:1484: warning: suggest parentheses around operand of ‘!’ or change ‘&’ to ‘&&’ or ‘!’ to ‘~’
/home/renegade/wireless/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_iwaplist’:
/home/renegade/wireless/os/linux/../../os/linux/sta_ioctl.c:604: warning: the frame size of 1296 bytes is larger than 1024 bytes
/home/renegade/wireless/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwmlme’:
/home/renegade/wireless/os/linux/../../os/linux/sta_ioctl.c:1984: warning: the frame size of 1696 bytes is larger than 1024 bytes
/home/renegade/wireless/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlMAC’:
/home/renegade/wireless/os/linux/../../os/linux/sta_ioctl.c:5853: warning: the frame size of 1376 bytes is larger than 1024 bytes
/home/renegade/wireless/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlE2PROM’:
/home/renegade/wireless/os/linux/../../os/linux/sta_ioctl.c:6052: warning: the frame size of 1376 bytes is larger than 1024 bytes
  CC [M]  /home/renegade/wireless/os/linux/../../os/linux/rt_linux.o
/home/renegade/wireless/os/linux/../../os/linux/rt_linux.c: In function ‘duplicate_pkt’:
/home/renegade/wireless/os/linux/../../os/linux/rt_linux.c:477: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/usr/src/linux-headers-2.6.35-22-generic/arch/x86/include/asm/string_64.h:58: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/renegade/wireless/os/linux/../../os/linux/rt_linux.c:479: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/usr/src/linux-headers-2.6.35-22-generic/arch/x86/include/asm/string_64.h:58: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/renegade/wireless/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:
/home/renegade/wireless/os/linux/../../os/linux/rt_linux.c:629: warning: assignment makes integer from pointer without a cast
/home/renegade/wireless/os/linux/../../os/linux/rt_linux.c: In function ‘update_os_packet_info’:
/home/renegade/wireless/os/linux/../../os/linux/rt_linux.c:651: warning: assignment makes integer from pointer without a cast
/home/renegade/wireless/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:
/home/renegade/wireless/os/linux/../../os/linux/rt_linux.c:672: warning: assignment makes integer from pointer without a cast
/home/renegade/wireless/os/linux/../../os/linux/rt_linux.c: In function ‘send_monitor_packets’:
/home/renegade/wireless/os/linux/../../os/linux/rt_linux.c:945: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
/home/renegade/wireless/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevDetach’:
/home/renegade/wireless/os/linux/../../os/linux/rt_linux.c:1694: warning: initialization discards qualifiers from pointer target type
/home/renegade/wireless/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/renegade/wireless/os/linux/../../os/linux/rt_linux.c:1731: warning: initialization discards qualifiers from pointer target type
  CC [M]  /home/renegade/wireless/os/linux/../../os/linux/rt_main_dev.o
/home/renegade/wireless/os/linux/../../os/linux/rt_main_dev.c: In function ‘MainVirtualIF_close’:
/home/renegade/wireless/os/linux/../../os/linux/rt_main_dev.c:117: warning: unused variable ‘Cancelled’
  CC [M]  /home/renegade/wireless/os/linux/../../common/ba_action.o
/home/renegade/wireless/os/linux/../../common/ba_action.c: In function ‘convert_reordering_packet_to_preAMSDU_or_802_3_packet’:
/home/renegade/wireless/os/linux/../../common/ba_action.c:1553: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/renegade/wireless/os/linux/../../sta/dls.o
  CC [M]  /home/renegade/wireless/os/linux/../../common/cmm_mac_usb.o
/home/renegade/wireless/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocUsbBulkBufStruct’:
/home/renegade/wireless/os/linux/../../common/cmm_mac_usb.c:52: error: implicit declaration of function ‘usb_buffer_alloc’
/home/renegade/wireless/os/linux/../../common/cmm_mac_usb.c:52: warning: assignment makes pointer from integer without a cast
/home/renegade/wireless/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeUsbBulkBufStruct’:
/home/renegade/wireless/os/linux/../../common/cmm_mac_usb.c:78: error: implicit declaration of function ‘usb_buffer_free’
/home/renegade/wireless/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/renegade/wireless/os/linux/../../common/cmm_mac_usb.c:234: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/renegade/wireless/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/renegade/wireless/os/linux/../../common/cmm_mac_usb.c:241: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/renegade/wireless/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/renegade/wireless/os/linux/../../common/cmm_mac_usb.c:278: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/renegade/wireless/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/renegade/wireless/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitTransmit’:
/home/renegade/wireless/os/linux/../../common/cmm_mac_usb.c:507: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/renegade/wireless/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/renegade/wireless/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/renegade/wireless/os/linux/../../common/cmm_mac_usb.c:566: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/renegade/wireless/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/renegade/wireless/os/linux/../../common/cmm_mac_usb.c:596: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/renegade/wireless/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/renegade/wireless/os/linux/../../common/cmm_mac_usb.c:610: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/renegade/wireless/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/renegade/wireless/os/linux/../../common/cmm_mac_usb.c:628: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/renegade/wireless/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘UCHAR **’
make[2]: *** [/home/renegade/wireless/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/renegade/wireless/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2

 
 
 
could someone help me out here?

---

### Post by mizunoX on 2010-10-23
See post #221 here:  [http://ubuntuforums.org/showthread.php?t=960642&highlight=rt2870&page=23](http://ubuntuforums.org/showthread.php?t=960642&highlight=rt2870&page=23)

Make the changes to rt_linux.h that Zaruman lists, then try to make it again.  It worked for me.

---

