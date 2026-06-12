---
title: "Having trouble installing a ASUS n13 wireless adaptop"
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by sn6uv on 2011-02-21
Hi, recently I bought a an Asus n13 usb wireless adaptor. It came with the linux drivers installed and some brief instructions, but make failed and I don't know why. I am running ubuntu 10.10 (64bit) and gcc version 4.4.5. Can any one help me?

The error messages from make 
```

[angus@angus-laptop 2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13]$ sudo make
make -C tools
make[1]: Entering directory `/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/tools'
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/tools/bin2h
cp -f os/linux/Makefile.6 /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/Makefile
make  -C  /lib/modules/2.6.35-25-generic/build SUBDIRS=/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/crypt_md5.o
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/mlme.o
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/mlme.c:4406: warning: the frame size of 1584 bytes is larger than 1024 bytes
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_wep.o
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/action.o
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_data.o
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/rtmp_init.o
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/rtmp_init.c: In function ‘RtmpRaDevCtrlInit’:
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/rtmp_init.c:3710: warning: passing argument 2 of ‘os_alloc_mem’ from incompatible pointer type
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/include/rtmp.h:5687: note: expected ‘UCHAR **’ but argument is of type ‘UCHAR *’
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_aes.o
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_aes.c:1338: warning: the frame size of 1136 bytes is larger than 1024 bytes
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_sync.o
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/eeprom.o
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_info.o
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/dfs.o
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/spectrum.o
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/spectrum.c:1899: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/rt_channel.o
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_profile.o
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_asic.o
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/assoc.o
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/assoc.c: In function ‘wext_notify_event_assoc’:
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/assoc.c:1401: warning: pointer targets in passing argument 5 of ‘RtmpOSWrielessEventSend’ differ in signedness
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/include/rtmp.h:7025: note: expected ‘PUCHAR’ but argument is of type ‘char *’
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/auth.o
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.o
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.c:651: warning: the frame size of 1360 bytes is larger than 1024 bytes
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.c:1429: warning: the frame size of 1456 bytes is larger than 1024 bytes
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.c:929: warning: the frame size of 1392 bytes is larger than 1024 bytes
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.c:525: warning: the frame size of 1088 bytes is larger than 1024 bytes
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sanity.o
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/connect.o
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/connect.c: In function ‘LinkDown’:
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/connect.c:1975: warning: unused variable ‘Cancelled’
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/connect.c:343: warning: the frame size of 1632 bytes is larger than 1024 bytes
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/wpa.o
  CC [M]  /home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.o
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c: In function ‘duplicate_pkt’:
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:525: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/usr/src/linux-headers-2.6.35-25-generic/arch/x86/include/asm/string_64.h:58: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:527: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/usr/src/linux-headers-2.6.35-25-generic/arch/x86/include/asm/string_64.h:58: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:588: warning: assignment makes integer from pointer without a cast
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c: In function ‘update_os_packet_info’:
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:610: warning: assignment makes integer from pointer without a cast
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:630: warning: assignment makes integer from pointer without a cast
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c: In function ‘send_monitor_packets’:
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:837: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1510: error: ‘struct net_device’ has no member named ‘open’
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1511: error: ‘struct net_device’ has no member named ‘stop’
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1512: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1513: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1519: error: ‘struct net_device’ has no member named ‘get_stats’
/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1553: error: ‘struct net_device’ has no member named ‘validate_addr’
make[2]: *** [/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/angus/bin/drivers/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make: *** [LINUX] Error 2

```

---

### Post by nickbodd on 2011-03-01
same problem... Cant compile either. I tried with other versions as well, but cant get anything to compile.

---

### Post by mfpockets on 2011-03-19
Try to download newest driver off Asus site.

[http://www.asus.com/product.aspx?P_ID=UI3ejenXyxqQTIcJ&templete=2](http://www.asus.com/product.aspx?P_ID=UI3ejenXyxqQTIcJ&templete=2)

I bought this product yesterday and got it to work with the above driver.it compiled but when installing it looks for file name 3070 but the file is name 2870.  Change the filename (i forget the exact file to change, but run sudo make install after compiling and look for the error line that says file doesnt exist and rename that file then it worked fine

---

### Post by flash63 on 2011-03-19
Edit and delete.

---

