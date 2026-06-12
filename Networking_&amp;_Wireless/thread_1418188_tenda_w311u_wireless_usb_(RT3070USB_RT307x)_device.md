---
title: "tenda w311u wireless usb (RT3070USB RT307x) device problem"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by XxDARKXx on 2010-02-28
i have download RT3070USB RT307x device for ubuntu 9.10
cd /home/anas/rt3
and
sudo make
and 
sudo make install

```
anas@ubuntu:~$ cd /home/anas/rt3
anas@ubuntu:~/rt3$ sudo make
make -C tools
make[1]: Entering directory `/home/anas/rt3/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/anas/rt3/tools'
/home/anas/rt3/tools/bin2h
cp -f os/linux/Makefile.6 /home/anas/rt3/os/linux/Makefile
make -C /lib/modules/2.6.31-14-generic/build  SUBDIRS=/home/anas/rt3/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/anas/rt3/os/linux/../../common/crypt_md5.o
  CC [M]  /home/anas/rt3/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/anas/rt3/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/anas/rt3/os/linux/../../common/crypt_aes.o
/home/anas/rt3/os/linux/../../common/crypt_aes.c: In function  ‘AES_GTK_KEY_WRAP’:
/home/anas/rt3/os/linux/../../common/crypt_aes.c:2265: warning: the  frame size of 1100 bytes is larger than 1024 bytes
/home/anas/rt3/os/linux/../../common/crypt_aes.c: In function  ‘WscDecryptData’:
/home/anas/rt3/os/linux/../../common/crypt_aes.c:1592: warning: the  frame size of 1364 bytes is larger than 1024 bytes
/home/anas/rt3/os/linux/../../common/crypt_aes.c: In function  ‘WscEncryptData’:
/home/anas/rt3/os/linux/../../common/crypt_aes.c:1522: warning: the  frame size of 1364 bytes is larger than 1024 bytes
  CC [M]  /home/anas/rt3/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/anas/rt3/os/linux/../../common/mlme.o
/home/anas/rt3/os/linux/../../common/mlme.c: In function  ‘BssTableSortByRssi’:
/home/anas/rt3/os/linux/../../common/mlme.c:4683: warning: the frame  size of 1720 bytes is larger than 1024 bytes
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_wep.o
  CC [M]  /home/anas/rt3/os/linux/../../common/action.o
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_data.o
  CC [M]  /home/anas/rt3/os/linux/../../common/rtmp_init.o
/home/anas/rt3/os/linux/../../common/rtmp_init.c: In function  ‘NICInitAsicFromEEPROM’:
/home/anas/rt3/os/linux/../../common/rtmp_init.c:2488: warning: unused  variable ‘RFValue’
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_aes.o
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_sync.o
  CC [M]  /home/anas/rt3/os/linux/../../common/eeprom.o
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_info.o
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/anas/rt3/os/linux/../../common/dfs.o
  CC [M]  /home/anas/rt3/os/linux/../../common/spectrum.o
  CC [M]  /home/anas/rt3/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/anas/rt3/os/linux/../../common/rt_channel.o
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_profile.o
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_asic.o
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/anas/rt3/os/linux/../../sta/assoc.o
/home/anas/rt3/os/linux/../../sta/assoc.c: In function  ‘MlmeAssocReqAction’:
/home/anas/rt3/os/linux/../../sta/assoc.c:377: warning: unused variable  ‘pInfo’
/home/anas/rt3/os/linux/../../sta/assoc.c:374: warning: unused variable  ‘infoPos’
  CC [M]  /home/anas/rt3/os/linux/../../sta/auth.o
  CC [M]  /home/anas/rt3/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/anas/rt3/os/linux/../../sta/sync.o
/home/anas/rt3/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/anas/rt3/os/linux/../../sta/sync.c:1736: warning: the frame size  of 1316 bytes is larger than 1024 bytes
/home/anas/rt3/os/linux/../../sta/sync.c: In function  ‘PeerBeaconAtJoinAction’:
/home/anas/rt3/os/linux/../../sta/sync.c:1079: warning: the frame size  of 1264 bytes is larger than 1024 bytes
/home/anas/rt3/os/linux/../../sta/sync.c: In function  ‘PeerBeaconAtScanAction’:
/home/anas/rt3/os/linux/../../sta/sync.c:773: warning: the frame size of  1268 bytes is larger than 1024 bytes
/home/anas/rt3/os/linux/../../sta/sync.c: In function  ‘MlmeStartReqAction’:
/home/anas/rt3/os/linux/../../sta/sync.c:589: warning: the frame size of  1064 bytes is larger than 1024 bytes
  CC [M]  /home/anas/rt3/os/linux/../../sta/sanity.o
  CC [M]  /home/anas/rt3/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/anas/rt3/os/linux/../../sta/connect.o
/home/anas/rt3/os/linux/../../sta/connect.c: In function  ‘CntlOidScanProc’:
/home/anas/rt3/os/linux/../../sta/connect.c:351: warning: the frame size  of 1748 bytes is larger than 1024 bytes
  CC [M]  /home/anas/rt3/os/linux/../../sta/wpa.o
  CC [M]  /home/anas/rt3/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/anas/rt3/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/anas/rt3/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/anas/rt3/os/linux/../../os/linux/sta_ioctl.o
/home/anas/rt3/os/linux/../../os/linux/sta_ioctl.c: In function  ‘rt_ioctl_siwencode’:
/home/anas/rt3/os/linux/../../os/linux/sta_ioctl.c:1481: warning:  suggest parentheses around operand of ‘!’ or change ‘&’ to  ‘&&’ or ‘!’ to ‘~’
/home/anas/rt3/os/linux/../../os/linux/sta_ioctl.c: In function  ‘RTMPIoctlRF’:
/home/anas/rt3/os/linux/../../os/linux/sta_ioctl.c:6219: warning: the  frame size of 2328 bytes is larger than 1024 bytes
/home/anas/rt3/os/linux/../../os/linux/sta_ioctl.c: In function  ‘RTMPIoctlE2PROM’:
/home/anas/rt3/os/linux/../../os/linux/sta_ioctl.c:6035: warning: the  frame size of 1348 bytes is larger than 1024 bytes
/home/anas/rt3/os/linux/../../os/linux/sta_ioctl.c: In function  ‘RTMPIoctlMAC’:
/home/anas/rt3/os/linux/../../os/linux/sta_ioctl.c:5837: warning: the  frame size of 1344 bytes is larger than 1024 bytes
/home/anas/rt3/os/linux/../../os/linux/sta_ioctl.c: In function  ‘rt_ioctl_iwaplist’:
/home/anas/rt3/os/linux/../../os/linux/sta_ioctl.c:606: warning: the  frame size of 1288 bytes is larger than 1024 bytes
/home/anas/rt3/os/linux/../../os/linux/sta_ioctl.c: In function  ‘rt_ioctl_siwmlme’:
/home/anas/rt3/os/linux/../../os/linux/sta_ioctl.c:1979: warning: the  frame size of 1588 bytes is larger than 1024 bytes
  CC [M]  /home/anas/rt3/os/linux/../../os/linux/rt_linux.o
/home/anas/rt3/os/linux/../../os/linux/rt_linux.c: In function  ‘RtmpOSTaskAttach’:
/home/anas/rt3/os/linux/../../os/linux/rt_linux.c:1283: warning: passing  argument 1 of ‘kthread_create’ from incompatible pointer type
include/linux/kthread.h:7: note: expected ‘int (*)(void *)’ but argument  is of type ‘RTMP_OS_TASK_CALLBACK’
/home/anas/rt3/os/linux/../../os/linux/rt_linux.c: In function  ‘RtmpOSNetDevDetach’:
/home/anas/rt3/os/linux/../../os/linux/rt_linux.c:1614: warning:  initialization discards qualifiers from pointer target type
/home/anas/rt3/os/linux/../../os/linux/rt_linux.c: In function  ‘RtmpOSNetDevAttach’:
/home/anas/rt3/os/linux/../../os/linux/rt_linux.c:1653: warning:  initialization discards qualifiers from pointer target type
/home/anas/rt3/os/linux/../../os/linux/rt_linux.c:1653: warning: ISO C90  forbids mixed declarations and code
  CC [M]  /home/anas/rt3/os/linux/../../os/linux/rt_main_dev.o
/home/anas/rt3/os/linux/../../os/linux/rt_main_dev.c: In function  ‘RtmpOSIRQRequest’:
/home/anas/rt3/os/linux/../../os/linux/rt_main_dev.c:951: warning:  unused variable ‘net_dev’
  CC [M]  /home/anas/rt3/os/linux/../../common/ba_action.o
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_mac_usb.o
  CC [M]  /home/anas/rt3/os/linux/../../common/rtusb_io.o
  CC [M]  /home/anas/rt3/os/linux/../../common/rtusb_bulk.o
  CC [M]  /home/anas/rt3/os/linux/../../common/rtusb_data.o
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_data_usb.o
  CC [M]  /home/anas/rt3/os/linux/../../common/ee_prom.o
  CC [M]  /home/anas/rt3/os/linux/../../common/ee_efuse.o
  CC [M]  /home/anas/rt3/os/linux/../../common/rtmp_mcu.o
  CC [M]  /home/anas/rt3/os/linux/../../chips/rt30xx.o
  CC [M]  /home/anas/rt3/os/linux/../../common/rt_rf.o
  CC [M]  /home/anas/rt3/os/linux/../../chips/rt3070.o
  CC [M]  /home/anas/rt3/os/linux/../../common/rtusb_dev_id.o
  CC [M]  /home/anas/rt3/os/linux/../../os/linux/rt_usb.o
  CC [M]  /home/anas/rt3/os/linux/../../os/linux/rt_usb_util.o
  CC [M]  /home/anas/rt3/os/linux/../../os/linux/usb_main_dev.o
  LD [M]  /home/anas/rt3/os/linux/rt3070sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in  /home/anas/rt3/os/linux/rt3070sta.o
see include/linux/module.h for more information
  CC      /home/anas/rt3/os/linux/rt3070sta.mod.o
  LD [M]  /home/anas/rt3/os/linux/rt3070sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
cp -f /home/anas/rt3/os/linux/rt3070sta.ko /tftpboot
anas@ubuntu:~/rt3$ sudo make install 
make -C /home/anas/rt3/os/linux -f Makefile.6 install
make[1]: Entering directory `/home/anas/rt3/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
cp /home/anas/rt3/RT3070STA.dat /etc/Wireless/RT3070STA/.
cp: cannot stat `/home/anas/rt3/RT3070STA.dat': No such file or  directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/anas/rt3/os/linux'
make: *** [install] Error 2
anas@ubuntu:~/rt3$
```

---

### Post by chili555 on 2010-02-28
> cp: cannot stat `/home/anas/rt3/RT3070STA.dat': No such file or  directorySo, do you have a RT3070STA.dat file? When I built this, I ended up with a file RT2870STA.dat. I suggest you do:```
cp RT2870STA.dat RT3070STA.dat
sudo make install
```Any errors this time?

---

### Post by XxDARKXx on 2010-02-28
Yes i have it 
```
anas@ubuntu:~/rt3$ cp RT2870STA.dat RT3070STA.dat
anas@ubuntu:~/rt3$ sudo make
make -C tools
make[1]: Entering directory `/home/anas/rt3/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/anas/rt3/tools'
/home/anas/rt3/tools/bin2h
cp -f os/linux/Makefile.6 /home/anas/rt3/os/linux/Makefile
make -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/anas/rt3/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/anas/rt3/os/linux/../../common/crypt_md5.o
  CC [M]  /home/anas/rt3/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/anas/rt3/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/anas/rt3/os/linux/../../common/crypt_aes.o
/home/anas/rt3/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/anas/rt3/os/linux/../../common/crypt_aes.c:2265: warning: the frame size of 1100 bytes is larger than 1024 bytes
/home/anas/rt3/os/linux/../../common/crypt_aes.c: In function ‘WscDecryptData’:
/home/anas/rt3/os/linux/../../common/crypt_aes.c:1592: warning: the frame size of 1364 bytes is larger than 1024 bytes
/home/anas/rt3/os/linux/../../common/crypt_aes.c: In function ‘WscEncryptData’:
/home/anas/rt3/os/linux/../../common/crypt_aes.c:1522: warning: the frame size of 1364 bytes is larger than 1024 bytes
  CC [M]  /home/anas/rt3/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/anas/rt3/os/linux/../../common/mlme.o
/home/anas/rt3/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/anas/rt3/os/linux/../../common/mlme.c:4683: warning: the frame size of 1720 bytes is larger than 1024 bytes
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_wep.o
  CC [M]  /home/anas/rt3/os/linux/../../common/action.o
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_data.o
  CC [M]  /home/anas/rt3/os/linux/../../common/rtmp_init.o
/home/anas/rt3/os/linux/../../common/rtmp_init.c: In function ‘NICInitAsicFromEEPROM’:
/home/anas/rt3/os/linux/../../common/rtmp_init.c:2488: warning: unused variable ‘RFValue’
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_aes.o
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_sync.o
  CC [M]  /home/anas/rt3/os/linux/../../common/eeprom.o
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_info.o
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/anas/rt3/os/linux/../../common/dfs.o
  CC [M]  /home/anas/rt3/os/linux/../../common/spectrum.o
  CC [M]  /home/anas/rt3/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/anas/rt3/os/linux/../../common/rt_channel.o
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_profile.o
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_asic.o
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/anas/rt3/os/linux/../../sta/assoc.o
/home/anas/rt3/os/linux/../../sta/assoc.c: In function ‘MlmeAssocReqAction’:
/home/anas/rt3/os/linux/../../sta/assoc.c:377: warning: unused variable ‘pInfo’
/home/anas/rt3/os/linux/../../sta/assoc.c:374: warning: unused variable ‘infoPos’
  CC [M]  /home/anas/rt3/os/linux/../../sta/auth.o
  CC [M]  /home/anas/rt3/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/anas/rt3/os/linux/../../sta/sync.o
/home/anas/rt3/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/anas/rt3/os/linux/../../sta/sync.c:1736: warning: the frame size of 1316 bytes is larger than 1024 bytes
/home/anas/rt3/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/anas/rt3/os/linux/../../sta/sync.c:1079: warning: the frame size of 1264 bytes is larger than 1024 bytes
/home/anas/rt3/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/anas/rt3/os/linux/../../sta/sync.c:773: warning: the frame size of 1268 bytes is larger than 1024 bytes
/home/anas/rt3/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/anas/rt3/os/linux/../../sta/sync.c:589: warning: the frame size of 1064 bytes is larger than 1024 bytes
  CC [M]  /home/anas/rt3/os/linux/../../sta/sanity.o
  CC [M]  /home/anas/rt3/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/anas/rt3/os/linux/../../sta/connect.o
/home/anas/rt3/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/anas/rt3/os/linux/../../sta/connect.c:351: warning: the frame size of 1748 bytes is larger than 1024 bytes
  CC [M]  /home/anas/rt3/os/linux/../../sta/wpa.o
  CC [M]  /home/anas/rt3/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/anas/rt3/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/anas/rt3/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/anas/rt3/os/linux/../../os/linux/sta_ioctl.o
/home/anas/rt3/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwencode’:
/home/anas/rt3/os/linux/../../os/linux/sta_ioctl.c:1481: warning: suggest parentheses around operand of ‘!’ or change ‘&’ to ‘&&’ or ‘!’ to ‘~’
/home/anas/rt3/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlRF’:
/home/anas/rt3/os/linux/../../os/linux/sta_ioctl.c:6219: warning: the frame size of 2328 bytes is larger than 1024 bytes
/home/anas/rt3/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlE2PROM’:
/home/anas/rt3/os/linux/../../os/linux/sta_ioctl.c:6035: warning: the frame size of 1348 bytes is larger than 1024 bytes
/home/anas/rt3/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlMAC’:
/home/anas/rt3/os/linux/../../os/linux/sta_ioctl.c:5837: warning: the frame size of 1344 bytes is larger than 1024 bytes
/home/anas/rt3/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_iwaplist’:
/home/anas/rt3/os/linux/../../os/linux/sta_ioctl.c:606: warning: the frame size of 1288 bytes is larger than 1024 bytes
/home/anas/rt3/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwmlme’:
/home/anas/rt3/os/linux/../../os/linux/sta_ioctl.c:1979: warning: the frame size of 1588 bytes is larger than 1024 bytes
  CC [M]  /home/anas/rt3/os/linux/../../os/linux/rt_linux.o
/home/anas/rt3/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSTaskAttach’:
/home/anas/rt3/os/linux/../../os/linux/rt_linux.c:1283: warning: passing argument 1 of ‘kthread_create’ from incompatible pointer type
include/linux/kthread.h:7: note: expected ‘int (*)(void *)’ but argument is of type ‘RTMP_OS_TASK_CALLBACK’
/home/anas/rt3/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevDetach’:
/home/anas/rt3/os/linux/../../os/linux/rt_linux.c:1614: warning: initialization discards qualifiers from pointer target type
/home/anas/rt3/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/anas/rt3/os/linux/../../os/linux/rt_linux.c:1653: warning: initialization discards qualifiers from pointer target type
/home/anas/rt3/os/linux/../../os/linux/rt_linux.c:1653: warning: ISO C90 forbids mixed declarations and code
  CC [M]  /home/anas/rt3/os/linux/../../os/linux/rt_main_dev.o
/home/anas/rt3/os/linux/../../os/linux/rt_main_dev.c: In function ‘RtmpOSIRQRequest’:
/home/anas/rt3/os/linux/../../os/linux/rt_main_dev.c:951: warning: unused variable ‘net_dev’
  CC [M]  /home/anas/rt3/os/linux/../../common/ba_action.o
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_mac_usb.o
  CC [M]  /home/anas/rt3/os/linux/../../common/rtusb_io.o
  CC [M]  /home/anas/rt3/os/linux/../../common/rtusb_bulk.o
  CC [M]  /home/anas/rt3/os/linux/../../common/rtusb_data.o
  CC [M]  /home/anas/rt3/os/linux/../../common/cmm_data_usb.o
  CC [M]  /home/anas/rt3/os/linux/../../common/ee_prom.o
  CC [M]  /home/anas/rt3/os/linux/../../common/ee_efuse.o
  CC [M]  /home/anas/rt3/os/linux/../../common/rtmp_mcu.o
  CC [M]  /home/anas/rt3/os/linux/../../chips/rt30xx.o
  CC [M]  /home/anas/rt3/os/linux/../../common/rt_rf.o
  CC [M]  /home/anas/rt3/os/linux/../../chips/rt3070.o
  CC [M]  /home/anas/rt3/os/linux/../../common/rtusb_dev_id.o
  CC [M]  /home/anas/rt3/os/linux/../../os/linux/rt_usb.o
  CC [M]  /home/anas/rt3/os/linux/../../os/linux/rt_usb_util.o
  CC [M]  /home/anas/rt3/os/linux/../../os/linux/usb_main_dev.o
  LD [M]  /home/anas/rt3/os/linux/rt3070sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/anas/rt3/os/linux/rt3070sta.o
see include/linux/module.h for more information
  CC      /home/anas/rt3/os/linux/rt3070sta.mod.o
  LD [M]  /home/anas/rt3/os/linux/rt3070sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
cp -f /home/anas/rt3/os/linux/rt3070sta.ko /tftpboot
anas@ubuntu:~/rt3$ sudo make install
make -C /home/anas/rt3/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/anas/rt3/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
cp /home/anas/rt3/RT3070STA.dat /etc/Wireless/RT3070STA/.
install -d /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3070sta.ko /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.31-14-generic
make[1]: Leaving directory `/home/anas/rt3/os/linux'
anas@ubuntu:~/rt3$ 


```

---

### Post by chili555 on 2010-02-28
> anas@ubuntu:~/rt3$ sudo make install
make -C /home/anas/rt3/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/anas/rt3/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
cp /home/anas/rt3/RT3070STA.dat /etc/Wireless/RT3070STA/.
install -d /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3070sta.ko /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.31-14-generic
make[1]: Leaving directory `/home/anas/rt3/os/linux'
No errors. Sounds like you are fine. After you modprobed the rt3070sta module, did your wireless device spring to life?

---

### Post by XxDARKXx on 2010-02-28
_No i cant see any _wireless

---

### Post by chili555 on 2010-02-28
With the device inserted, please let me see:```
lsusb
```I wonder if there is another driver that is more appropriate than rt3070sta.

---

### Post by XxDARKXx on 2010-02-28
```
anas@ubuntu:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse
Bus 007 Device 002: ID 03f0:4c11 Hewlett-Packard PSC 1500 series
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0644:0200 TEAC Corp. 
Bus 002 Device 003: ID 148f:3070 Ralink Technology, Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

---

### Post by chili555 on 2010-02-28
Looks correct to me. Let's take a look at:```
sudo modprobe rt3070sta
iwconfig
dmesg | grep -e rt2 -e rt3
```Thanks.

---

### Post by XxDARKXx on 2010-02-28
```
anas@ubuntu:~$ sudo modprobe rt3070sta
[sudo] password for anas: 
WARNING: /etc/modprobe.d/blacklist.conf line 56: ignoring bad line starting with 'rt2800usb'
anas@ubuntu:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=7 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

anas@ubuntu:~$ dmesg | grep -e rt2 -e rt3
[   16.349099] Registered led device: rt2800usb-phy0::radio
[   16.349122] Registered led device: rt2800usb-phy0::assoc
[   16.349144] Registered led device: rt2800usb-phy0::quality
[   16.349526] usbcore: registered new interface driver rt2800usb
[   16.695175] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   16.700888] usbcore: registered new interface driver rt2870
[   16.856685] rt3070sta: module is from the staging directory, the quality is unknown, you have been warned.
[   16.862798] Error: Driver 'rt2870' is already registered, aborting...
[   16.862804] usbcore: error -17 registering interface     driver rt2870
[   43.922747] rt2800usb 2-3:1.0: firmware: requesting rt2870.bin
[   93.043817] rt3070sta: module is from the staging directory, the quality is unknown, you have been warned.
[   93.048705] Error: Driver 'rt2870' is already registered, aborting...
[   93.048711] usbcore: error -17 registering interface     driver rt2870
anas@ubuntu:~$ 


```
Tanks for your help ;)

---

### Post by chili555 on 2010-02-28
Well, there are some interesting issues here. Let's take them in order. First:> WARNING:   line 56: ignoring bad line starting with 'rt2800usb'Please edit /etc/modprobe.d/blacklist.conf and make sure the line reads:```
blacklist rt2800usb
```And, as long as you are in there, add another line:```
blacklist rt2870sta
```Proofread carefully, save and close your text editor. Next, remove the device and do:```
sudo rmmod -f rt2870sta
```Re-insert the device and do:```
dmesg | grep -e rt2 -e rt3
```We'll look at any entries after 93.048 to see if we have cured the errors. Thanks.

---

### Post by eeBus on 2010-04-05
I'm currently testing 10.04 beta 1 on a Lenovo S10-2 netbook.

All I did was to edit the /etc/modules files and add rt2870sta to the end of file.

I disabled the built-in wireless adapter. Rebooted with the Tenda W311U plugged in an it works a treat! 

Hope this helps.

---

### Post by TheStreetSpirit on 2010-05-01
hi. i followed all the steps and it appears that the w311u is working. Except that under my wireless networks everything is duplicated AKA there are the networks under ralink 802.11 n and networks under wlan1rename. it will connect to both or one but internet works. solutions?

---

### Post by TheStreetSpirit on 2010-05-02
could someone please help me with this? they seem to be battling for control of the wireless.

---

### Post by madberry on 2010-05-06
You need to switch off the on-board wireless of the laptop and the battle will stop....

[mad]Berry van der Linden
[http://madberry.org](http://madberry.org)
[http://fantasy-rpg.com](http://fantasy-rpg.com)

---

