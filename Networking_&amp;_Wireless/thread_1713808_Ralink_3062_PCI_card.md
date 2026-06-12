---
title: "Ralink 3062 PCI card"
date: 2011-03-24
forum: Networking &amp; Wireless
---

### Post by catlover2 on 2011-03-24
Hello, I recently did my first custom computer build, and a ralink 3062 card was part of it.
The reviews on newegg looked like a safe bet, but it is not working  "Out of the box".

i tried this driver:[http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMj](http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMj)

but the readme is a bit over my head.

Thanks, Catlover

---

### Post by MooPi on 2011-03-24
This is my tutorial on this driver. Don't be fooled by the different number of the chip as they are both covered by this driver. If you have issues just let us know. You'll need this driver from Ralink as the one in the tutorial is dated: [http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMjVzYjJGa09USXlNek15TlRReE9TNTBaM285UFQxRVVFOWZVbFF6TlRZeVh6TTFPVEpmTXpBMk1sOU1hVzUxZUZOVVFWOVdNaTQwTGpFdU1WOHlNREV3TVRJeE53PT1D]("http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMjVzYjJGa09USXlNek15TlRReE9TNTBaM285UFQxRVVFOWZVbFF6TlRZeVh6TTFPVEpmTXpBMk1sOU1hVzUxZUZOVVFWOVdNaTQwTGpFdU1WOHlNREV3TVRJeE53PT1D")
My tutorial link:
[http://ubuntuforums.org/showthread.php?t=1608095]("http://ubuntuforums.org/showthread.php?t=1608095")

---

### Post by catlover2 on 2011-03-24
thanks, but it does not work. here is the output of make and make install:
```
reed@Reeds-Custom-Computer:~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo make
make -C tools
make[1]: Entering directory `/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools/bin2h
cp -f os/linux/Makefile.6 /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/Makefile
make -C /lib/modules/2.6.35-28-generic/build SUBDIRS=/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_md5.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.o
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c: In function &#8216;AES_GTK_KEY_WRAP&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c:2265: warning: the frame size of 1664 bytes is larger than 1024 bytes
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c: In function &#8216;AES_GTK_KEY_UNWRAP&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c:2348: warning: the frame size of 1168 bytes is larger than 1024 bytes
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c: In function &#8216;WscDecryptData&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c:1592: warning: the frame size of 1408 bytes is larger than 1024 bytes
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c: In function &#8216;WscEncryptData&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c:1522: warning: the frame size of 1408 bytes is larger than 1024 bytes
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/mlme.o
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/mlme.c: In function &#8216;MlmeResetRalinkCounters&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/mlme.c:867: warning: cast from pointer to integer of different size
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/mlme.c:867: warning: cast from pointer to integer of different size
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_wep.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/action.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_data.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_init.o
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_init.c: In function &#8216;NICInitAsicFromEEPROM&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_init.c:1391: warning: format &#8216;%x&#8217; expects type &#8216;unsigned int&#8217;, but argument 3 has type &#8216;ULONG&#8217;
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_aes.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_sync.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/eeprom.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_info.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/dfs.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/spectrum.o
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/spectrum.c: In function &#8216;PeerMeasureReportAction&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/spectrum.c:1966: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217;
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rt_channel.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_profile.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_asic.o
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_asic.c: In function &#8216;AsicBBPAdjust&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_asic.c:924: warning: the frame size of 1888 bytes is larger than 1024 bytes
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/assoc.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/auth.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/sync.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/sanity.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/connect.o
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/connect.c: In function &#8216;InitChannelRelatedValue&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/connect.c:3058: warning: the frame size of 1120 bytes is larger than 1024 bytes
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/wpa.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/ags.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/sta_ioctl.o
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/sta_ioctl.c: In function &#8216;rt_ioctl_iwaplist&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/sta_ioctl.c:596: warning: the frame size of 1296 bytes is larger than 1024 bytes
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/sta_ioctl.c: In function &#8216;RTMPIoctlE2PROM&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/sta_ioctl.c:6043: warning: the frame size of 1376 bytes is larger than 1024 bytes
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/sta_ioctl.c: In function &#8216;RTMPIoctlMAC&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/sta_ioctl.c:5844: warning: the frame size of 1408 bytes is larger than 1024 bytes
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linuxreed@Reeds-Custom-Computer:~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo modprobe rt3562sta
reed@Reeds-Custom-Computer:~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo ifconfig ra0 inet up
ra0: ERROR while getting interface flags: No such device
reed@Reeds-Custom-Computer:~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ 
.o
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linux.c: In function &#8216;duplicate_pkt&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linux.c:482: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast
/usr/src/linux-headers-2.6.35-28-generic/arch/x86/include/asm/string_64.h:58: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217;
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linux.c:484: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast
/usr/src/linux-headers-2.6.35-28-generic/arch/x86/include/asm/string_64.h:58: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217;
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linux.c: In function &#8216;ClonePacket&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linux.c:634: warning: assignment makes integer from pointer without a cast
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linux.c: In function &#8216;update_os_packet_info&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linux.c:656: warning: assignment makes integer from pointer without a cast
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linux.c: In function &#8216;wlan_802_11_to_802_3_packet&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linux.c:677: warning: assignment makes integer from pointer without a cast
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linux.c: In function &#8216;send_monitor_packets&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linux.c:950: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217;
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSNetDevDetach&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linux.c:1699: warning: initialization discards qualifiers from pointer target type
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSNetDevAttach&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linux.c:1736: warning: initialization discards qualifiers from pointer target type
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_main_dev.o
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_main_dev.c: In function &#8216;MainVirtualIF_close&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_main_dev.c:118: warning: unused variable &#8216;Cancelled&#8217;
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_main_dev.c: In function &#8216;WriteDatThread&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_main_dev.c:1250: warning: &#8216;return&#8217; with no value, in function returning non-void
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/ba_action.o
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/ba_action.c: In function &#8216;convert_reordering_packet_to_preAMSDU_or_802_3_packet&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/ba_action.c:1558: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.o
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c: In function &#8216;RTMPResetTxRxRingMemory&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:36: warning: unused variable &#8216;num&#8217;
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c: In function &#8216;RTMPFreeTxRxRingMemory&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:119: warning: unused variable &#8216;IrqFlags&#8217;
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:118: warning: unused variable &#8216;pPacket&#8217;
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:117: warning: unused variable &#8216;pTxD&#8217;
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:116: warning: unused variable &#8216;pTxRing&#8217;
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:115: warning: unused variable &#8216;j&#8217;
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:115: warning: unused variable &#8216;index&#8217;
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c: In function &#8216;RTMPAllocTxRxRingMemory&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:447: warning: unused variable &#8216;BufBaseVa&#8217;
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:446: warning: unused variable &#8216;BufBasePaLow&#8217;
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:445: warning: unused variable &#8216;BufBasePaHigh&#8217;
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:432: warning: unused variable &#8216;pPacket&#8217;
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:431: warning: unused variable &#8216;pDmaBuf&#8217;
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:430: warning: unused variable &#8216;pTxRing&#8217;
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:428: warning: unused variable &#8216;pRxD&#8217;
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:427: warning: unused variable &#8216;pTxD&#8217;
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:425: warning: unused variable &#8216;RingBaseVa&#8217;
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:424: warning: unused variable &#8216;RingBasePaLow&#8217;
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:423: warning: unused variable &#8216;RingBasePaHigh&#8217;
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:489: warning: &#8216;index&#8217; may be used uninitialized in this function
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_data_pci.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_mcu.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/ee_prom.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/ee_efuse.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rt_rf.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../chips/rt30xx.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../chips/rt35xx.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_pci_rbus.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_rbus_pci_util.o
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/pci_main_dev.o
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/pci_main_dev.c: In function &#8216;rt2860_probe&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/pci_main_dev.c:320: warning: assignment discards qualifiers from pointer target type
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/misc.o
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/misc.c: In function &#8216;RTMPHwCoexSwitch&#8217;:
/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/misc.c:963: warning: format &#8216;%x&#8217; expects type &#8216;unsigned int&#8217;, but argument 6 has type &#8216;ULONG&#8217;
  CC [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../chips/rt3592cb.o
  LD [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.o
see include/linux/module.h for more information
  CC      /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.mod.o
  LD [M]  /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
cp -f /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.ko /tftpboot
reed@Reeds-Custom-Computer:~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo make install
make -C /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3562sta.ko /lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.35-28-generic
make[1]: Leaving directory `/home/reed/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
reed@Reeds-Custom-Computer:~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$
```and:

```
reed@Reeds-Custom-Computer:~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo modprobe rt3562sta
reed@Reeds-Custom-Computer:~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo ifconfig ra0 inet up
ra0: ERROR while getting interface flags: No such device
reed@Reeds-Custom-Computer:~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ 

```

thanks!

---

### Post by MooPi on 2011-03-24
Reboot !

---

### Post by catlover2 on 2011-03-24
reboot after what?
i'm still getting:
```
reed@Reeds-Custom-Computer:~$ sudo ifconfig ra0 inet up
[sudo] password for reed: 
ra0: ERROR while getting interface flags: No such device
reed@Reeds-Custom-Computer:~$ 


 
```

after a reboot

---

### Post by MooPi on 2011-03-24
Can you give me the results of this command from terminal```
lsmod
```

---

### Post by catlover2 on 2011-03-24
```
reed@Reeds-Custom-Computer:~$ lsmod
Module                  Size  Used by
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_atihdmi     3079  1 
snd_hda_codec_realtek   300173  1 
snd_hda_intel          26147  2 
snd_hda_codec         100951  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
rt3562sta            1047226  0 
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    64181  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
arc4                    1497  4 
rt2800pci              10528  0 
rt2800lib              32002  1 rt2800pci
rt2x00usb              11316  1 rt2800lib
rt2x00pci               6993  1 rt2800pci
soundcore               1240  1 snd
rtl8187                53994  0 
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
crc_ccitt               1699  1 rt2800pci
i2c_piix4              10047  0 
rt2x00lib              31575  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
xhci_hcd               60496  0 
led_class               3393  2 rtl8187,rt2x00lib
k10temp                 3535  0 
fglrx                2523725  37 
mac80211              267099  4 rt2x00usb,rt2x00pci,rtl8187,rt2x00lib
cfg80211              170485  3 rtl8187,rt2x00lib,mac80211
eeprom_93cx6            1789  2 rt2800pci,rtl8187
psmouse                62080  0 
edac_core              46822  0 
edac_mce_amd            9387  0 
serio_raw               4910  0 
shpchp                 34910  0 
lp                     10201  0 
asus_atk0110           12987  0 
parport                37032  3 parport_pc,ppdev,lp
firewire_sbp2          15033  2 
usbhid                 42030  0 
hid                    84710  1 usbhid
firewire_ohci          24839  0 
r8169                  42254  0 
pata_atiixp             4405  0 
mii                     5261  1 r8169
firewire_core          54327  2 firewire_sbp2,firewire_ohci
ahci                   22210  4 
crc_itu_t               1739  1 firewire_core
libahci                26148  1 ahci
reed@Reeds-Custom-Computer:~$ 
 
```

---

### Post by MooPi on 2011-03-24
Your going to need to blacklist some modules that are interfering . Open /etc/modprobe.d/blacklist.conf  with your choice of text editor. For example sake I'll select gedit
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
At the end of the file add these lines
```
# blacklist for rt3562sta
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2800usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2x00usb
```
Just for kicks could you give me the results in terminal for ```
lspci
```

---

### Post by catlover2 on 2011-03-25
Awesome! After blacklisting those modules, it connected without a hitch!

Thanks alot!

Catlover



Edit:
In case you were wondering:
```
reed@Reeds-Custom-Computer:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: ASUSTeK Computer Inc. RS880 PCI to PCI bridge (int gfx)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4250]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
04:06.0 Network controller: RaLink Device 3062
04:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
reed@Reeds-Custom-Computer:~$ 

```

---

### Post by MooPi on 2011-03-25
Super glad it worked out :)

---

### Post by jackllewellynbrown on 2011-10-12
Thank you so much for this, I had the same problem. It worked at first, but I just ran updates, rebooted and now it's not picking up any wireless networks, its gone back to how it was before. Anything I'm missing?

---

### Post by jackllewellynbrown on 2011-10-12
Hi, solved my problem by compiling the driver again. Thanks again.

---

