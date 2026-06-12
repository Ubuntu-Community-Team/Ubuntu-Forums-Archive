---
title: "make error,D-link DWA-125 problem"
date: 2011-04-11
forum: Networking &amp; Wireless
---

### Post by khaj_vah on 2011-04-11
Hello everyone 

I am new user and i have a problem :

make -C tools
make[1]: Entering directory `/home/khajvah/2009_1204_RT3070_Linux_STA_v2.1.2.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/khajvah/2009_1204_RT3070_Linux_STA_v2.1.2.0/tools'
/home/khajvah/2009_1204_RT3070_Linux_STA_v2.1.2.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/khajvah/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/Makefile
make  -C  /lib/modules/2.6.35-28-generic/build SUBDIRS=/home/khajvah/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /home/khajvah/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.o
/home/khajvah/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitRecv’:
/home/khajvah/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:83: error: implicit declaration of function ‘usb_buffer_alloc’
/home/khajvah/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:83: warning: assignment makes pointer from integer without a cast
/home/khajvah/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:112: error: implicit declaration of function ‘usb_buffer_free’
make[2]: *** [/home/khajvah/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/khajvah/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [LINUX] Error 2
khajvah@khajvah-desktop:~/2009_1204_RT3070_Linux_STA_v2.1.2.0$ cd ..
khajvah@khajvah-desktop:~$ cp -r 2009_1204_RT3070_Linux_STA_v2.1.2.0 /etc
cp: cannot create directory `/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0': Permission denied
khajvah@khajvah-desktop:~$ sudo -s
root@khajvah-desktop:~# cd -r 2009_1204_RT3070_Linux_STA_v2.1.2.0/
bash: cd: -r: invalid option
cd: usage: cd [-L|-P] [dir]
root@khajvah-desktop:~# cp -r 2009_1204_RT3070_Linux_STA_v2.1.2.0 /etc
root@khajvah-desktop:~# cd /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/
root@khajvah-desktop:/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0# make
make -C tools
make[1]: Entering directory `/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/tools'
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/tools/bin2h
cp -f os/linux/Makefile.6 /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/Makefile
make  -C  /lib/modules/2.6.35-28-generic/build SUBDIRS=/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/crypt_md5.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/crypt_sha2.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/crypt_hmac.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.o
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.c:4408: warning: the frame size of 1572 bytes is larger than 1024 bytes
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_wep.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/action.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_data.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.o
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c: In function ‘RtmpRaDevCtrlInit’:
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c:3711: warning: passing argument 2 of ‘os_alloc_mem’ from incompatible pointer type
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/include/rtmp.h:5707: note: expected ‘UCHAR **’ but argument is of type ‘UCHAR *’
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_tkip.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_aes.o
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_aes.c:1338: warning: the frame size of 1092 bytes is larger than 1024 bytes
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_sync.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/eeprom.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_sanity.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_info.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_cfg.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_wpa.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/dfs.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/spectrum.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_timer.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rt_channel.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_profile.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_asic.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_cmd.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../sta/assoc.o
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../sta/assoc.c: In function ‘wext_notify_event_assoc’:
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../sta/assoc.c:1401: warning: pointer targets in passing argument 5 of ‘RtmpOSWrielessEventSend’ differ in signedness
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/include/rtmp.h:7051: note: expected ‘PUCHAR’ but argument is of type ‘char *’
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../sta/auth.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../sta/auth_rsp.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../sta/sync.o
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../sta/sync.c:657: warning: the frame size of 1252 bytes is larger than 1024 bytes
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../sta/sync.c:1435: warning: the frame size of 1312 bytes is larger than 1024 bytes
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../sta/sync.c:935: warning: the frame size of 1260 bytes is larger than 1024 bytes
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../sta/sync.c:525: warning: the frame size of 1064 bytes is larger than 1024 bytes
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../sta/sanity.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../sta/rtmp_data.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../sta/connect.o
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../sta/connect.c: In function ‘LinkDown’:
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../sta/connect.c:1976: warning: unused variable ‘Cancelled’
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../sta/connect.c:343: warning: the frame size of 1600 bytes is larger than 1024 bytes
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../sta/wpa.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/rt_linux.o
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/rt_linux.c: In function ‘send_monitor_packets’:
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/rt_linux.c:982: warning: the frame size of 1084 bytes is larger than 1024 bytes
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/rt_profile.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/sta_ioctl.o
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwencode’:
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/sta_ioctl.c:1842: warning: suggest parentheses around operand of ‘!’ or change ‘&’ to ‘&&’ or ‘!’ to ‘~’
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlRF’:
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/sta_ioctl.c:7235: warning: pointer targets in passing argument 1 of ‘strchr’ differ in signedness
/usr/src/linux-headers-2.6.35-28-generic/arch/x86/include/asm/string_32.h:27: note: expected ‘const char *’ but argument is of type ‘CHAR *’
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/sta_ioctl.c:7235: warning: pointer targets in assignment differ in signedness
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_iwaplist’:
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/sta_ioctl.c:1040: warning: the frame size of 1288 bytes is larger than 1024 bytes
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwmlme’:
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/sta_ioctl.c:2324: warning: the frame size of 1584 bytes is larger than 1024 bytes
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlRF’:
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/sta_ioctl.c:7371: warning: the frame size of 2328 bytes is larger than 1024 bytes
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlE2PROM’:
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/sta_ioctl.c:7187: warning: the frame size of 1348 bytes is larger than 1024 bytes
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlMAC’:
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/sta_ioctl.c:6989: warning: the frame size of 1344 bytes is larger than 1024 bytes
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/ba_action.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.o
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.c: In function ‘RTUSBWatchDog’:
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.c:743: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘ULONG’
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/rt_usb.o
  CC [M]  /etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.o
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitRecv’:
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:83: error: implicit declaration of function ‘usb_buffer_alloc’
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:83: warning: assignment makes pointer from integer without a cast
/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:112: error: implicit declaration of function ‘usb_buffer_free’
make[2]: *** [/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/etc/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [LINUX] Error 2




here is what i get after make command.
(i am trying to install driver for dwa-125 wireless adapter)
i have already  installed build-essentials and libc6-dev...
pls help me if u can this is very important for me...
(UBUNTU 10.10)

---

