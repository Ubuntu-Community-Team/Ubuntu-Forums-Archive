---
title: "Ubuntu 9.10 Belkin F5D8053 won't work."
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by The-Wise-Man on 2009-10-31
I have tried many steps to get this adapter running. As of right now I am using a old Wireless G to connect. There seems to be so many of these posts that have no ending. Anyway I was installing the Ranlink rt2870 driver which I believe was the Native Linux driver to get this thing running. Here is My terminal outcome.

sudo make
make -C tools
make[1]: Entering directory `/home/casey/driver/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/casey/driver/tools'
/home/casey/driver/tools/bin2h
cp -f os/linux/Makefile.6 /home/casey/driver/os/linux/Makefile
make  -C  /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/casey/driver/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/casey/driver/os/linux/../../common/crypt_md5.o
  CC [M]  /home/casey/driver/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/casey/driver/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/casey/driver/os/linux/../../common/mlme.o
/home/casey/driver/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/casey/driver/os/linux/../../common/mlme.c:4406: warning: the frame size of 1584 bytes is larger than 1024 bytes
  CC [M]  /home/casey/driver/os/linux/../../common/cmm_wep.o
  CC [M]  /home/casey/driver/os/linux/../../common/action.o
  CC [M]  /home/casey/driver/os/linux/../../common/cmm_data.o
  CC [M]  /home/casey/driver/os/linux/../../common/rtmp_init.o
/home/casey/driver/os/linux/../../common/rtmp_init.c: In function ‘RtmpRaDevCtrlInit’:
/home/casey/driver/os/linux/../../common/rtmp_init.c:3710: warning: passing argument 2 of ‘os_alloc_mem’ from incompatible pointer type
/home/casey/driver/include/rtmp.h:5687: note: expected ‘UCHAR **’ but argument is of type ‘UCHAR *’
  CC [M]  /home/casey/driver/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/casey/driver/os/linux/../../common/cmm_aes.o
/home/casey/driver/os/linux/../../common/cmm_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/casey/driver/os/linux/../../common/cmm_aes.c:1338: warning: the frame size of 1136 bytes is larger than 1024 bytes
  CC [M]  /home/casey/driver/os/linux/../../common/cmm_sync.o
  CC [M]  /home/casey/driver/os/linux/../../common/eeprom.o
  CC [M]  /home/casey/driver/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/casey/driver/os/linux/../../common/cmm_info.o
  CC [M]  /home/casey/driver/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/casey/driver/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/casey/driver/os/linux/../../common/dfs.o
  CC [M]  /home/casey/driver/os/linux/../../common/spectrum.o
/home/casey/driver/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/casey/driver/os/linux/../../common/spectrum.c:1899: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/casey/driver/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/casey/driver/os/linux/../../common/rt_channel.o
  CC [M]  /home/casey/driver/os/linux/../../common/cmm_profile.o
  CC [M]  /home/casey/driver/os/linux/../../common/cmm_asic.o
  CC [M]  /home/casey/driver/os/linux/../../sta/assoc.o
/home/casey/driver/os/linux/../../sta/assoc.c: In function ‘wext_notify_event_assoc’:
/home/casey/driver/os/linux/../../sta/assoc.c:1401: warning: pointer targets in passing argument 5 of ‘RtmpOSWrielessEventSend’ differ in signedness
/home/casey/driver/include/rtmp.h:7025: note: expected ‘PUCHAR’ but argument is of type ‘char *’
  CC [M]  /home/casey/driver/os/linux/../../sta/auth.o
  CC [M]  /home/casey/driver/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/casey/driver/os/linux/../../sta/sync.o
/home/casey/driver/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/casey/driver/os/linux/../../sta/sync.c:651: warning: the frame size of 1360 bytes is larger than 1024 bytes
/home/casey/driver/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/casey/driver/os/linux/../../sta/sync.c:1429: warning: the frame size of 1456 bytes is larger than 1024 bytes
/home/casey/driver/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/casey/driver/os/linux/../../sta/sync.c:929: warning: the frame size of 1392 bytes is larger than 1024 bytes
/home/casey/driver/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/casey/driver/os/linux/../../sta/sync.c:525: warning: the frame size of 1088 bytes is larger than 1024 bytes
  CC [M]  /home/casey/driver/os/linux/../../sta/sanity.o
  CC [M]  /home/casey/driver/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/casey/driver/os/linux/../../sta/connect.o
/home/casey/driver/os/linux/../../sta/connect.c: In function ‘LinkDown’:
/home/casey/driver/os/linux/../../sta/connect.c:1975: warning: unused variable ‘Cancelled’
/home/casey/driver/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/casey/driver/os/linux/../../sta/connect.c:343: warning: the frame size of 1632 bytes is larger than 1024 bytes
  CC [M]  /home/casey/driver/os/linux/../../sta/wpa.o
  CC [M]  /home/casey/driver/os/linux/../../os/linux/rt_linux.o
/home/casey/driver/os/linux/../../os/linux/rt_linux.c: In function ‘duplicate_pkt’:
/home/casey/driver/os/linux/../../os/linux/rt_linux.c:525: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/string_64.h:58: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/casey/driver/os/linux/../../os/linux/rt_linux.c:527: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/string_64.h:58: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/casey/driver/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:
/home/casey/driver/os/linux/../../os/linux/rt_linux.c:588: warning: assignment makes integer from pointer without a cast
/home/casey/driver/os/linux/../../os/linux/rt_linux.c: In function ‘update_os_packet_info’:
/home/casey/driver/os/linux/../../os/linux/rt_linux.c:610: warning: assignment makes integer from pointer without a cast
/home/casey/driver/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:
/home/casey/driver/os/linux/../../os/linux/rt_linux.c:630: warning: assignment makes integer from pointer without a cast
/home/casey/driver/os/linux/../../os/linux/rt_linux.c: In function ‘send_monitor_packets’:
/home/casey/driver/os/linux/../../os/linux/rt_linux.c:837: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
/home/casey/driver/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/casey/driver/os/linux/../../os/linux/rt_linux.c:1510: error: ‘struct net_device’ has no member named ‘open’
/home/casey/driver/os/linux/../../os/linux/rt_linux.c:1511: error: ‘struct net_device’ has no member named ‘stop’
/home/casey/driver/os/linux/../../os/linux/rt_linux.c:1512: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/casey/driver/os/linux/../../os/linux/rt_linux.c:1513: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/casey/driver/os/linux/../../os/linux/rt_linux.c:1519: error: ‘struct net_device’ has no member named ‘get_stats’
/home/casey/driver/os/linux/../../os/linux/rt_linux.c:1553: error: ‘struct net_device’ has no member named ‘validate_addr’
make[2]: *** [/home/casey/driver/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/casey/driver/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [LINUX] Error 2
casey@casey-desktop:~/driver$ 
:popcorn:

I also tried the Ndiswrapper approach I have "rt2807.cat, rt2807.inf, and rt2870.sys" which I thought should have the windows wireless driver thing to work. but it didn't. Any help with this is greatly appreciated.

---

