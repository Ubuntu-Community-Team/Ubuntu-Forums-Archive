---
title: "Linksys WUSB600N v2 in 64 bit Ubuntu 10.10"
date: 2010-10-07
forum: Networking &amp; Wireless
---

### Post by baz.g on 2010-10-07
hi,

I have seen lots of posts around about this adapter and tried them in 10.04 and worked perfectly, now giving 10.10 rc a run and it doesnt want to play

i have tried with version 2.3.0.0 of the driver and the latest (2.4.something) they both result in the same error:

```

thegrantfamily@ubuntu:~/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2$ sudo makemake -C tools
make[1]: Entering directory `/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools'
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools/bin2h
cp -f os/linux/Makefile.6 /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/Makefile
make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_md5.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_aes.o
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_aes.c:2265: warning: the frame size of 1664 bytes is larger than 1024 bytes
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_UNWRAP’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_aes.c:2348: warning: the frame size of 1168 bytes is larger than 1024 bytes
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_aes.c: In function ‘WscDecryptData’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_aes.c:1592: warning: the frame size of 1408 bytes is larger than 1024 bytes
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_aes.c: In function ‘WscEncryptData’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_aes.c:1522: warning: the frame size of 1408 bytes is larger than 1024 bytes
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/mlme.o
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/mlme.c: In function ‘MlmeResetRalinkCounters’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/mlme.c:895: warning: cast from pointer to integer of different size
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/mlme.c:895: warning: cast from pointer to integer of different size
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/mlme.c:6112: warning: the frame size of 1728 bytes is larger than 1024 bytes
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_wep.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/action.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_data.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/rtmp_init.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_aes.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_sync.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/eeprom.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_info.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/dfs.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/spectrum.o
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/spectrum.c:1977: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/rt_channel.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_profile.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_asic.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/assoc.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/auth.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.o
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.c:1764: warning: the frame size of 1456 bytes is larger than 1024 bytes
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.c:1094: warning: the frame size of 1440 bytes is larger than 1024 bytes
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.c:764: warning: the frame size of 1376 bytes is larger than 1024 bytes
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.c:581: warning: the frame size of 1088 bytes is larger than 1024 bytes
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sanity.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/connect.o
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/connect.c:356: warning: the frame size of 1776 bytes is larger than 1024 bytes
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/wpa.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/ags.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/sta_ioctl.o
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwencode’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/sta_ioctl.c:1484: warning: suggest parentheses around operand of ‘!’ or change ‘&’ to ‘&&’ or ‘!’ to ‘~’
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_iwaplist’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/sta_ioctl.c:604: warning: the frame size of 1296 bytes is larger than 1024 bytes
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwmlme’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/sta_ioctl.c:1984: warning: the frame size of 1696 bytes is larger than 1024 bytes
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlMAC’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/sta_ioctl.c:5853: warning: the frame size of 1376 bytes is larger than 1024 bytes
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlE2PROM’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/sta_ioctl.c:6052: warning: the frame size of 1376 bytes is larger than 1024 bytes
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.o
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c: In function ‘duplicate_pkt’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c:477: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/usr/src/linux-headers-2.6.35-22-generic/arch/x86/include/asm/string_64.h:58: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c:479: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/usr/src/linux-headers-2.6.35-22-generic/arch/x86/include/asm/string_64.h:58: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c:629: warning: assignment makes integer from pointer without a cast
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c: In function ‘update_os_packet_info’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c:651: warning: assignment makes integer from pointer without a cast
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c:672: warning: assignment makes integer from pointer without a cast
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c: In function ‘send_monitor_packets’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c:945: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevDetach’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c:1694: warning: initialization discards qualifiers from pointer target type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c:1731: warning: initialization discards qualifiers from pointer target type
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_main_dev.o
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_main_dev.c: In function ‘MainVirtualIF_close’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_main_dev.c:117: warning: unused variable ‘Cancelled’
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/ba_action.o
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/ba_action.c: In function ‘convert_reordering_packet_to_preAMSDU_or_802_3_packet’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/ba_action.c:1553: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/dls.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.o
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocUsbBulkBufStruct’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:52: error: implicit declaration of function ‘usb_buffer_alloc’
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:52: warning: assignment makes pointer from integer without a cast
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeUsbBulkBufStruct’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:78: error: implicit declaration of function ‘usb_buffer_free’
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:234: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:241: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:278: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitTransmit’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:507: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:566: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:596: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:610: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:628: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘UCHAR **’
make[2]: *** [/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2
thegrantfamily@ubuntu:~/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2$ sudo makemake -C tools
make[1]: Entering directory `/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools'
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools/bin2h
cp -f os/linux/Makefile.6 /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/Makefile
make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.o
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocUsbBulkBufStruct’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:52: error: implicit declaration of function ‘usb_buffer_alloc’
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:52: warning: assignment makes pointer from integer without a cast
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeUsbBulkBufStruct’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:78: error: implicit declaration of function ‘usb_buffer_free’
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:234: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:241: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:278: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitTransmit’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:507: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:566: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:596: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:610: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:628: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘UCHAR **’
make[2]: *** [/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2
thegrantfamily@ubuntu:~/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2$ sudo modprobe rt3572sta
FATAL: Module rt3572sta not found.

```

any ideas please? :)

---

### Post by beau6282 on 2010-10-07
can't speak much on this bud but I'm running ubuntu 10.04 and the same wireless card WUSB600N v2.  
I have been having problems with it for days. finally got it working with this code.

echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0079" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf

Im sorry if it i can help more because I really have no idea what it does. But it made my card work fine so just give it a shot

this code loads it at startup
echo rt2870sta | sudo tee -a /etc/modules
this code  to work on plug-in
# UDEV-Rule for wusb-100v2 ID 1737:0078 SUBSYSTEM=="usb", SYSFS{idVendor}=="1737", SYSFS{idProduct}=="0078", RUN+="/sbin/modprobe rt2870sta"
hope this help man. if not good luck

---

### Post by rhill on 2010-10-13
I had the same problem today when I upgraded to 10.10. Here is the solution:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165/comments/77](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165/comments/77):

> Per this post, related to a different Ralink chipset:
[http://art.ubuntuforums.org/showpost.php?p=9778612&postcount=108](http://art.ubuntuforums.org/showpost.php?p=9778612&postcount=108)
It appears that usb_buffer_alloc and usb_buffer_free, which the driver calls on, were renamed to usb_alloc_coherent and usb_free_coherent (respectively) in kernel 2.6.35.

In order to get the driver to compile, edit ../include/os/rt_linux.h and change all instances of "usb_buffer_alloc" to "usb_alloc_coherent" and all instances of "usb_buffer_free" to "usb_free_coherent". From what I can tell, there is only once occurrence of each, on lines 1077 and 1078, respectively.

Make sure you've made the usual changes (enabling WPA Supplicant support in ../os/linux/config.mk and adding the USB ID to ../common/rtusb_dev_id.c) and the driver should compile, install and modprobe just fine.

I also had to blacklist the rt2800 modules as the OS was trying to use them instead. If ifconfig/iwconfig show the device as "wlan0" then it's most likely trying to use the rt2800 module. If the device is shown as "ra0" the rt3572sta module should be in use.

This worked for me. To recapitulate for anybody else who is trying to have a WUSB600N Rev.2 to work with Ubuntu Maverick Meerkat, here are all the steps:

1. Download RT3572USB v. 2.4.0.2 from [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

2. Extract the content

3. Edit common/rtusb_dev_id.c, and add:
```
{USB_DEVICE(0x1737,0x0079)}, /* WUSB600Nv2 */
```
between #ifdef RT35xx and #endif (should be between line 109 and 120.) Save and close the file.

4. Edit os/linux/config.mk, and set HAS_WPA_SUPPLICANT, HAS_NATIVE_WPA_SUPPLICANT_SUPPORT and HAS_QOS_DLS_SUPPORT to "y". Save and close.

5. Edit include/os/rt_linux.h, and change

"usb_buffer_alloc" to "usb_alloc_coherent"
"usb_buffer_free" to "usb_free_coherent"

Save and close.

6. Sudo edit /etc/modprobe.d/blacklist.conf, and add

```
# to ensure my rt3572usb gets loaded
blacklist rt2800usb
```
Save and close.

Then you can build your driver and install it ("make", then "sudo make install"). This worked for me.

---

### Post by alliance1975 on 2010-10-13
God bless you rhill.

---

### Post by ibizatunes on 2010-10-26
work like a charm, in ubuntu 10.10 x64
tip for getting this to work for newbies
***use a search function to find the files in the extracted .tar.br2 file***
Use the search function to find the edit aswell

"usb_buffer_alloc" to "usb_alloc_coherent"
"usb_buffer_free" to "usb_free_coherent"
ONLY CHANGE that text that extactly the same, if it has other text infront leave only!

then
make 
you need to do from the command line 
cd ~/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2
(if that is where you extract it)
then run make
then sudo make install

---

### Post by randiroo76073 on 2010-10-26
> **rhill said:**
>  This worked for me.

Well bless your peapickin heart rhill, that did the trick for me just fine !
Running 10.04[64 bit] with kernel 2.6.36.1 generic

@ ibizatunes:
Why would you want to run "make" as sudo, doesn't make sense.

---

### Post by six-geek on 2010-11-03
Thanks for the installation guide.
I edited all config files but I got a failure message during the compiling process. After I executed the command **make** i got the following output:

```
$ make
make -C tools
make[1]: Betrete Verzeichnis '/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools'
gcc -g bin2h.c -o bin2h
make[1]: Verlasse Verzeichnis '/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools'
/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools/bin2h
cp -f os/linux/Makefile.6 /home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/Makefile
make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.o
/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocUsbBulkBufStruct’:
/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:52: error: implicit declaration of function ‘usb_alloc_coheren’
/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:52: warning: assignment makes pointer from integer without a cast
/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:234: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:241: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:278: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitTransmit’:
/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:507: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:566: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:596: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:610: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:628: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘UCHAR **’
make[2]: *** [/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.o] Fehler 1
make[1]: *** [_module_/home/six/Downloads/treiber/linksys/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Fehler 2
```

So I could not install the driver. I have absolutely no idea why the failure occurs. 

I'm using kubuntu 10.10 (amd64) with kernel 2.6.35-22-generic and all system updates.

Does someone have a clue for me?

---

### Post by jshuford on 2010-11-05
> **rhill said:**
> I had the same problem today when I upgraded to 10.10. Here is the solution:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165/comments/77](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165/comments/77):



This worked for me. To recapitulate for anybody else who is trying to have a WUSB600N Rev.2 to work with Ubuntu Maverick Meerkat, here are all the steps:

1. Download RT3572USB v. 2.4.0.2 from [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

2. Extract the content

3. Edit common/rtusb_dev_id.c, and add:
```
{USB_DEVICE(0x1737,0x0079)}, /* WUSB600Nv2 */
```between #ifdef RT35xx and #endif (should be between line 109 and 120.) Save and close the file.

4. Edit os/linux/config.mk, and set HAS_WPA_SUPPLICANT, HAS_NATIVE_WPA_SUPPLICANT_SUPPORT and HAS_QOS_DLS_SUPPORT to "y". Save and close.

5. Edit include/os/rt_linux.h, and change

"usb_buffer_alloc" to "usb_alloc_coherent"
"usb_buffer_free" to "usb_free_coherent"

Save and close.

6. Sudo edit /etc/modprobe.d/blacklist.conf, and add

```
# to ensure my rt3572usb gets loaded
blacklist rt2800usb
```Save and close.

Then you can build your driver and install it ("make", then "sudo make install"). This worked for me.

Thank you...

---

### Post by ltpg97 on 2010-11-05
For those having issues with v1 open a terminal and type: 

sudo gedit /etc/modprobe.d/blacklist.conf 

At the end of the file, add three lines
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib 

Proofread carefully, save and close gedit. Reboot.

---

### Post by anmg on 2010-12-29
I downloaded firmware from this page [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
**Firmware RT28XX/RT30XX USB series (RT2870/RT2770/RT3572/RT3070)**
unziped **rt2870.bin** to **/lib/firware** and replaced existing file

Plug WUSB600N, blue led is on
now instead of "Firmware is not installed" I have this in logs
batterfly kernel: [ 2807.458107] usb 2-1.8: new high speed USB device using ehci_hcd and address 9
batterfly kernel: [ 2807.868904] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by ihc100 on 2011-02-04
I am on ubuntu 10.10 AMD64

Ralink now has RT3572 v2.5.0.0

Played with it for a few hours:
new firmware - compile
old firmware - compile etc.
tried every combination, compiled and installed fine but the 600n v2 would not connect.

Still had driver v2.3.0.0 on a usb stick with the system firmware and the changes mentioned above, wireless works very good.

Perhaps this helps somebody.

---

### Post by joshuaje1 on 2011-02-23
HELLO!

Could someone kindly send me RT3572USB v. 2.4.0.2!?!?!?!?!

The ralinktech site doesn't have that driver anymore, and I'm getting errors when trying to "make" using 2.5.0.0


```
joshua@jsys:~/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)$ make
make -C tools
make[1]: Entering directory `/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)/tools'
/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)/tools/bin2h
/bin/sh: Syntax error: word unexpected (expecting ")")
make: *** [build_tools] Error 2
joshua@jsys:~/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)$ sudo make install
make -C /home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)/os/linux -f Makefile.6 install
/bin/sh: Syntax error: "(" unexpected
make: *** [install] Error 2

```

---

### Post by dabbi2000 on 2011-03-14
Ubuntu 32bit on 10.10, got the latest 
2010_1215_RT3572_Linux_STA_v2.5.0.0

drivers, made all modifications, even changed
"usb_buffer_alloc" to "usb_alloc_coherent"
"usb_buffer_free" to "usb_free_coherent"

as described. No blue light. Can see SSID but cannot connect even with no wireless security setting on router. Works out of the box with Vista.


Just got this so I haven't tried earlier driver versions but from what I have Googled others are having problems too with the 2.5.x.x versions.


Will this be solved in 11.04?

---

### Post by arilds on 2011-03-22
I have a variation of the problem.  My wireless connection links up fine using WUSB600N and Ubuntu 10.10 64 bit, and it works for the longest time.

Occasionally I will lose the connection, but I can get it going again by restarting my computer.

I have used the software that came with Ubuntu when I installed it, and the only annoyance is that the connection drops occasionally.  I have not compiled in any other drivers into the kernel, as my problem is minor.

Has anyone seen this flavor of the issue?

---

### Post by Jockboy98295 on 2011-04-11
Thank you. This install worked perfectly. I had done this before but this time downloaded the wrong driver. lol. oh well. all is good now. Hope this all will help everyone else as much as it helped me. This install was on a fresh ubuntu 10.10 install and a sony vaio E series. btw for all of you with a sony just remember that the wireless switch on the front of the computer will control the availability of ALL wireless networks, regardless of weather the adapter is a WUSB600N or the factory installed PCI card. Good luck.:P


oops sorry. this was placed in the wrong location. will relocate.

---

### Post by Jockboy98295 on 2011-04-11
Thank you rhill. Thank you. This install worked perfectly. I had done this before but this time downloaded the wrong driver. lol. oh well. all is good now. Hope this all will help everyone else as much as it helped me. This driver install was on a fresh ubuntu 10.10 os install and a sony vaio E series. btw for all of you with a sony just remember that the wireless switch on the front of the computer will control the availability of ALL wireless networks, regardless of weather the adapter is a WUSB600N or the factory installed PCI card. Good luck.:P

---

### Post by anmg on 2011-04-30
Ubuntu 11.04 released
the device is still not working out of box :(

I have tried sveral times to get it working. still can not do this.

---

### Post by eythian on 2011-05-11
> **anmg said:**
> Ubuntu 11.04 released
the device is still not working out of box :(

Has anyone had any success with this on Natty? I just picked up one, and can get it to see access points, but it's prone to Oopsing the kernel and causing things to break when I use the method described here.

---

### Post by anmg on 2011-05-12
> **eythian said:**
> Has anyone had any success with this on Natty? 

I have done according to this thread [http://www.linuxquestions.org/questions/linux-wireless-networking-41/linksys-wusb600n-driver-and-dlink-dwl-ag132-driver-622449/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/linksys-wusb600n-driver-and-dlink-dwl-ag132-driver-622449/)

It start working after disconnecting the web cam.
Led is not working.
And I'm not sure that the result is stable as I use it seldom.

---

### Post by eythian on 2011-05-12
> **anmg said:**
> I have done according to this thread It start working after disconnecting the web cam.
Led is not working.
And I'm not sure that the result is stable as I use it seldom.

I should've mentioned, but this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165/comments/85](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165/comments/85)
made it work for me in natty. It's stable and effective. Sometimes takes a little time to connect the first time, but nothing too bad.

LEDs are working properly, the connection is reliable, etc.

---

### Post by bogyit on 2011-05-18
> **joshuaje1 said:**
> HELLO!

Could someone kindly send me RT3572USB v. 2.4.0.2!?!?!?!?!

The ralinktech site doesn't have that driver anymore, and I'm getting errors when trying to "make" using 2.5.0.0


```
joshua@jsys:~/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)$ make
make -C tools
make[1]: Entering directory `/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)/tools'
/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)/tools/bin2h
/bin/sh: Syntax error: word unexpected (expecting ")")
make: *** [build_tools] Error 2
joshua@jsys:~/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)$ sudo make install
make -C /home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)/os/linux -f Makefile.6 install
/bin/sh: Syntax error: "(" unexpected
make: *** [install] Error 2

```

This error depends on the directory name, at the end there is a blank space "...DPO (2)" that makes the compiler brake, just rename the directory and you will be able to do make and make install. I know because I had the same issue.

---

### Post by rbeede on 2011-09-28
I have Ubuntu 10.10 64-bit.
Tried the 2.5.0.0 version driver from RA
blacklisted the rt2800
Plugged in USB device
Entire machine locked up.  Hard to hard reset it.

I'm going to try the 2.4 driver (not available from RA) care of [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165/comments/85](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165/comments/85)

---

### Post by rbeede on 2011-09-28
This worked after I did blacklisted the following:

blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2870sta


Unfortunately I have a second wireless device that needs the rt2xxx modules.  I'm going to play around with diff of 2.4 and 2.5 as well as the order of the device ids to see if blacklisting can be avoided all together.

---

### Post by rbeede on 2011-09-28
I haven't had much luck with loading wireless devices that use both the ra34 and ra2x modules.

---

### Post by anmg on 2011-11-29
At last RaLink published source code of driver for Linksys WUSB600N v2
[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

donload archive for **RT5572 USB** dated 11/22/2011 version 2.5.0.0
device id is already there
> #ifdef RT35xx
	{USB_DEVICE(0x148F,0x3572)}, /* Ralink 3572 */
	{USB_DEVICE(0x1740,0x9801)}, /* EnGenius 3572 */
	{USB_DEVICE(0x0DF6,0x0041)}, /* Sitecom 3572 */
	{USB_DEVICE(0x0DF6,0x0042)},
	{USB_DEVICE(0x04BB,0x0944)}, /* I-O DATA 3572 */
	{USB_DEVICE(0x1690,0x0740)}, /* 3572 */
	{USB_DEVICE(0x1690,0x0744)}, /* 3572 */
	{USB_DEVICE(0x5A57,0x0284)}, /* Zinwell 3572 */
	{USB_DEVICE(0x167B,0x4001)}, /* 3572 */
	{USB_DEVICE(0x0930,0x0A07)}, /* TOSHIBA */
	{USB_DEVICE(0x1690,0x0761)}, /* Askey */
	{USB_DEVICE(0x13B1,0x002F)}, /* Cisco LinkSys AE1000 */
	[COLOR="Red"]{USB_DEVICE(0x1737,0x0079)}, /* Cisco LinkSys WUSB600N */[/COLOR]
	{USB_DEVICE(0x148F,0x3573)}, /* Ralink 3573 */
	{USB_DEVICE(0x1690,0x0764)}, /* 3572 */
#endif /* RT35xx */


Just compile and check. I can not at the moment

---

