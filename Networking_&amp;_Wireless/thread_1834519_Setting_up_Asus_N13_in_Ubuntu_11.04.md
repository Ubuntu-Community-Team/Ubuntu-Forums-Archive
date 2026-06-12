---
title: "Setting up Asus N13 in Ubuntu 11.04"
date: 2011-08-27
forum: Networking &amp; Wireless
---

### Post by Hadriel18 on 2011-08-27
Hey guys,
I'm not the greatest with linux in general, I mean I know my way around it okay but theres still a ton to learn, and 11.04 is the first version to work on my custom PC without messing up after I update it so I'm left with natty. Anyway I bought my PC with an Asus U8B-N13 Wireless adapter. The disc it came with has the program to install the drivers in Windows, Mac, and Linux, but the Linux drivers need to be compile and I'm yet to have luck doing so. I've tried to somewhat follow an older guide here: [http://ubuntuforums.org/showthread.php?t=1444746](http://ubuntuforums.org/showthread.php?t=1444746) but I made it as far as extracting the .tgz, then running the make command and got a couple errors. Here is that attempt:

```
dom@NZXT:~$ cd Desktop
dom@NZXT:~/Desktop$ tar -xvzf DPO_RT3070_LinuxSTA_V2.3.0.2_20100422.tgz 
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/iwpriv_usage.txt
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/LICENSE ralink-firmware.txt
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/Makefile
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/README_STA_usb
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/RT2870STA.dat
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/RT2870STACard.dat
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta_ate_iwpriv_usage.txt
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/chips/
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/chips/rt3070.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/chips/rt30xx.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/chips/rt3593.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/action.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/ba_action.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/br_ftph.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/client_wds.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_aes.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_asic.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_cfg.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_cmd.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_data.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_data_usb.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_info.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_mac_usb.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_profile.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_sanity.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_sync.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_tkip.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_wep.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_wpa.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/crypt_aes.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/crypt_arc4.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/crypt_hmac.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/crypt_md5.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/crypt_sha2.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/dfs.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/eeprom.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/ee_efuse.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/ee_prom.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/mlme.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/mrgtmp0
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/netif_block.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/rt2870.bin
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/rtmp_init.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/rtmp_init_inf.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/rtmp_mcu.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/rtmp_timer.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/rtusb_bulk.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/rtusb_data.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/rtusb_dev_id.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/rtusb_io.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/rt_channel.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/rt_rf.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/spectrum.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/vr_ikans.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/action.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/ap.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/cfg80211.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/cfg80211extr.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/chlist.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/client_wds.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/client_wds_cmm.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/crypt_aes.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/crypt_arc4.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/crypt_hmac.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/crypt_md5.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/crypt_sha2.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/dfs.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/dot11i_wpa.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/eeprom.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/firmware.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/link_list.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/mlme.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/netif_block.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/oid.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rtmp.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rtmp_chip.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rtmp_cmd.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rtmp_def.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rtmp_dot11.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rtmp_iface.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rtmp_mcu.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rtmp_os.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rtmp_timer.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rtmp_type.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rtusb_io.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rt_ate.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rt_config.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/spectrum.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/spectrum_def.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/sta_cfg.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/vr_ikans.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/wpa.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/wpa_cmm.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/os/
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/os/rt_linux.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/iface/
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/iface/rtmp_usb.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/chip/
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/chip/mac_usb.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/chip/rt3070.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/chip/rt30xx.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/chip/rt3593.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/chip/rtmp_mac.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/chip/rtmp_phy.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/cfg80211.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/config.mk
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/Makefile.4
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/Makefile.6
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/modules.order
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/rt_ate.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/rt_linux.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/rt_main_dev.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/rt_profile.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/rt_usb.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/rt_usb_util.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/sta_ioctl.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/usb_main_dev.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/vr_ikans.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta/
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta/assoc.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta/auth.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta/auth_rsp.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta/connect.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta/dls.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta/rtmp_ckipmic.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta/rtmp_data.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta/sanity.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta/sta_cfg.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta/sync.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta/wpa.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/tools/
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/tools/bin2h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/tools/bin2h.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/tools/Makefile
dom@NZXT:~/Desktop$ cd DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/
dom@NZXT:~/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422$ sudo su
[sudo] password for dom: 
root@NZXT:/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422# make
make -C tools
make[1]: Entering directory `/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/tools'
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/tools/bin2h
cp -f os/linux/Makefile.6 /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/Makefile
make -C /lib/modules/2.6.38-11-generic/build SUBDIRS=/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/crypt_md5.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/crypt_aes.o
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/crypt_aes.c: In function ‘WscEncryptData’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/crypt_aes.c:1522:1: warning: the frame size of 1424 bytes is larger than 1024 bytes
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/crypt_aes.c: In function ‘WscDecryptData’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/crypt_aes.c:1592:1: warning: the frame size of 1424 bytes is larger than 1024 bytes
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/crypt_aes.c:2265:1: warning: the frame size of 1648 bytes is larger than 1024 bytes
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_UNWRAP’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/crypt_aes.c:2348:1: warning: the frame size of 1152 bytes is larger than 1024 bytes
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/mlme.o
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/mlme.c: In function ‘MlmeResetRalinkCounters’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/mlme.c:828:2: warning: cast from pointer to integer of different size
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/mlme.c:828:2: warning: cast from pointer to integer of different size
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/mlme.c: In function ‘BssTableSetEntry’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/mlme.c:4322:39: warning: operation on ‘Tab->BssOverlapNr’ may be undefined
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/mlme.c:4683:1: warning: the frame size of 1728 bytes is larger than 1024 bytes
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_wep.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/action.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_data.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/rtmp_init.o
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/rtmp_init.c: In function ‘NICInitAsicFromEEPROM’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/rtmp_init.c:2488:10: warning: unused variable ‘RFValue’
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_aes.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_sync.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/eeprom.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_info.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/dfs.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/spectrum.o
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/spectrum.c:1977:3: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/rt_channel.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_profile.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_asic.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/assoc.o
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/assoc.c: In function ‘MlmeAssocReqAction’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/assoc.c:377:11: warning: unused variable ‘pInfo’
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/assoc.c:374:18: warning: unused variable ‘infoPos’
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/auth.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/sync.o
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/sync.c:1079:1: warning: the frame size of 1376 bytes is larger than 1024 bytes
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/sync.c:773:1: warning: the frame size of 1360 bytes is larger than 1024 bytes
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/sync.c:589:1: warning: the frame size of 1088 bytes is larger than 1024 bytes
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/sync.c:1736:1: warning: the frame size of 1456 bytes is larger than 1024 bytes
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/sanity.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/connect.o
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/connect.c:351:1: warning: the frame size of 1776 bytes is larger than 1024 bytes
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/wpa.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.o
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwencode’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.c:1481:3: warning: suggest parentheses around operand of ‘!’ or change ‘&’ to ‘&&’ or ‘!’ to ‘~’
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_iwaplist’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.c:606:1: warning: the frame size of 1280 bytes is larger than 1024 bytes
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwmlme’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.c:1979:1: warning: the frame size of 1632 bytes is larger than 1024 bytes
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlMAC’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.c:5837:1: warning: the frame size of 1360 bytes is larger than 1024 bytes
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlE2PROM’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.c:6035:1: warning: the frame size of 1376 bytes is larger than 1024 bytes
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlRF’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.c:6219:1: warning: the frame size of 2336 bytes is larger than 1024 bytes
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.o
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.c: In function ‘duplicate_pkt’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.c:407:3: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/usr/src/linux-headers-2.6.38-11-generic/arch/x86/include/asm/string_64.h:58:7: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.c:409:3: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/usr/src/linux-headers-2.6.38-11-generic/arch/x86/include/asm/string_64.h:58:7: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.c:559:23: warning: assignment makes integer from pointer without a cast
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.c: In function ‘update_os_packet_info’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.c:581:15: warning: assignment makes integer from pointer without a cast
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.c:602:15: warning: assignment makes integer from pointer without a cast
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.c: In function ‘send_monitor_packets’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.c:875:9: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSTaskAttach’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.c:1283:24: warning: passing argument 1 of ‘kthread_create’ from incompatible pointer type
include/linux/kthread.h:7:21: note: expected ‘int (*)(void *)’ but argument is of type ‘RTMP_OS_TASK_CALLBACK’
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevDetach’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.c:1614:38: warning: initialization discards qualifiers from pointer target type
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.c:1653:38: warning: initialization discards qualifiers from pointer target type
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.c:1653:2: warning: ISO C90 forbids mixed declarations and code
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_main_dev.o
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_main_dev.c: In function ‘RtmpOSIRQRequest’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_main_dev.c:951:21: warning: unused variable ‘net_dev’
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/ba_action.o
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/ba_action.c: In function ‘convert_reordering_packet_to_preAMSDU_or_802_3_packet’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/ba_action.c:1562:2: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_mac_usb.o
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitRecv’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_mac_usb.c:83:3: error: implicit declaration of function ‘usb_buffer_alloc’
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_mac_usb.c:83:30: warning: assignment makes pointer from integer without a cast
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_mac_usb.c:112:4: error: implicit declaration of function ‘usb_buffer_free’
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitTransmit’:
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_mac_usb.c:219:4: warning: cast to pointer from integer of different size
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_mac_usb.c:306:4: warning: cast to pointer from integer of different size
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_mac_usb.c:324:3: warning: cast to pointer from integer of different size
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_mac_usb.c:341:3: warning: cast to pointer from integer of different size
/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_mac_usb.c:357:3: warning: cast to pointer from integer of different size
make[2]: *** [/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
make: *** [LINUX] Error 2
```I should mention that for now I'm using my old Wireless adapter which works just fine, but it's only Wireless G and my new one is N and I'd rather only have to use one(the Asus one).

After I ran make I decided to run lsusb and heres that results:
```
root@NZXT:/home/dom/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422# lsusb
Bus 007 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 004: ID 13b1:0020 Linksys WUSB54GC v1 802.11g Adapter [Ralink RT73]
Bus 001 Device 006: ID 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter

```(I removed any unnecessary lines from the readout and left anything wireless even though they may not matter i.e bluetooth and my mouse)

Mainly looking at the "ASUSTek Computer, Inc. 801.11n Network Adapter" the Linksys is the adapter I'm using to connect to my router(I don't have an ethernet cable long enough to connect to it)
When I click on the Network Connections icon at the top, it shows the networks from my Linksys adapter and also shows 
"Wireless Network (Ralink 802.11n WLAN)
device not ready (firmware missing)"

Attached is the .tgz file that came with the disc.(I had to change the extension to .tar to upload it, change it back to .tgz)

All help is greatly appreciated :]

---

### Post by thorner on 2011-08-27
I am running the same version of ubuntu, but never got the N13 to run above 54Mb/s "g" speeds.

to get it running at all, i suggest you remove your WUSB54GL and use the blacklist technique found [here]("https://help.ubuntu.com/community/WifiDocs/Device/Asus%20USB-N13_Natty%2011.04")

That got my N13 running well under 11.04 (albeit at only 54Mb/s)

---

### Post by Hadriel18 on 2011-08-27
Wouldn't it support the higher speeds if I were to use the files given on the disc? I'd rather have full performance on my adapter.

However I must say thank you for the response and link.

---

### Post by thorner on 2011-08-27
Yes, theoretically, the files on the disc, or the latest drivers available on the ASUS [website]("http://ca.asus.com/en/Networks/Wireless_Adapters/USBN13/#download") should support 802.11n, but I couldn't get it to work, and found no help here. I decided to run cat5e through my walls instead.

Good luck, I hope someone with more knowledge/experience can help you achieve "n" speed.

---

### Post by thorner on 2011-08-27
I believe there is also a version [2.4.0.1]("http://www.ralinktech.com/support.php?s=2") of the driver too. I couldn't compile that one on my machine.
Maybe you could have more luck with it...

---

### Post by Hadriel18 on 2011-08-27
> **thorner said:**
> I decided to run cat5e through my walls instead.
  I'm considering doing something similar, but don't exactly have enough money to buy a long enough one haha. thanks though

---

### Post by thorner on 2011-08-27
monoprice.com my friend.
[100ft]("http://www.monoprice.com/products/product.asp?c_id=102&cp_id=10208&cs_id=1020814&p_id=147&seq=1&format=2") of cat5e for under $12 (shipping to NJ would be about $7)

---

### Post by praseodym on 2011-08-27
Did you try the compilation with "sudo make" instead of "make", only? Or the classic debian-style:

```
sudo su
make
make install
exit
```and reboot.

---

### Post by chili555 on 2011-08-27
I'm not at all sure that N speeds are possible with this driver and 64-bit. If you'd like to try, get the later version linked and be sure to blacklist rt2800usb:```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
exit
```I'll subscribe to the thread and help you if you get stuck.

---

### Post by chili555 on 2011-08-27
> **praseodym said:**
> Did you try the compilation with "sudo make" instead of "make", only? Or the classic debian-style:

```
sudo su
make
make install
exit
```and reboot.It's not going to compile because of:> error: implicit declaration of function ‘usb_buffer_alloc’The version on the disk is too old for his kernel.

---

### Post by Hadriel18 on 2011-09-01
sorry for the late response, i thought i was subscribed to the thread, but I guess not. I am trying at this point with the newer version which from what I found is [2.5.02]("http://www.ralinktech.com/support.php?s=2"). I'll take the advice of everyone and blacklist the other one. I'm assuming rt2800usb is my linksys adapter, however. should all this not work for whatever reason, what would be the command to undo the blacklist?


And as a further thought, as soon as I can get my Asus adapter working in linux, I'll have no need to keep the Linksys adapter plugged in, so would I still have to blacklist it if I remove it?

---

### Post by chili555 on 2011-09-01
> I'm assuming rt2800usb is my linksys adapter,No. Your Linksys uses rt73usb.> And as a further thought, as soon as I can get my Asus adapter working in linux, I'll have no need to keep the Linksys adapter plugged in, so would I still have to blacklist it if I remove it? You still must blacklist rt2800usb. It tries but conflicts with your USB-N13 and needs to be kicked out in any event.

If you remove the Linksys and reboot, doesn't the N13 work as expected?

---

### Post by praseodym on 2011-09-01
Hi,

try driver version 2.4.0.1 according to this thread:

[http://forum.ubuntuusers.de/post/2809590/](http://forum.ubuntuusers.de/post/2809590/)

---

### Post by Hadriel18 on 2011-09-01
> **chili555 said:**
> No. Your Linksys uses rt73usb.You still must blacklist rt2800usb. It tries but conflicts with your USB-N13 and needs to be kicked out in any event.

If you remove the Linksys and reboot, doesn't the N13 work as expected?

Okay, I'm not home right now, but i will be soon so I'll hop on and try it out. And no removing the linksys won't make the n13 work as normal because I still have to compile and install the firmware for it

And as perthe other comment I'm going to try 2.5.0.2 since it's newer, rather than 2.4.0.1. If the newer one doesn't work then I'll try 2401 for sure

---

### Post by Hadriel18 on 2011-09-03
Well I went ahead and followed what you said, I blacklisted the rt2800usb and I compiled and installed the 2.5.0.2 version, unplugged my Linksys adapter and replaced it with the Asus one and rebooted and it works, however liek you guys said, the top speed is 54mb/s which I guess I'll deal with. but thanks a bunch guys :]

---

### Post by Tonyr63 on 2011-09-05
Hi

Is that it, the ASUS N13 USB wireless adapter can only work in Ubuntu 11.04 at 54 MB "G" speed?  :???:

I have one of these suckers and it works with 10.10 at 270MB however i was only able to get 54 MB on my ASUS PR031 F series laptop.

I tried using my ASUS N13 USB Wireless card with my ASUS PR031F  laptop with Ubuntu 10.10 expecting it to be automatically detected but  this was not the case.  I am using Kernal 2.6.35.30 and had heard that  the N13 is supported in newer kernals.


 I run the usual Make , make install instructions along with the rules  files and blacklisting the rt2800 and when I restarted the computer the N13 fired into life with  its indicator lights flashing actively however it only connects at 54 MB.

 

I  expected that if I switch off the internal Intel wireless card I could  use the N13 to get the higher speeds but it will not connect.
 I tried all 3 different RT2870 drivers 2.1.1.2, 2.1.2.0 & 2.3.0.2  and putting in Sym links from RT3070 to RT 2870 and nothing makes any  difference.
 

I noticed that it only works if I have the internal wireless Inter adapter turned on and it looks like both connect.


I expected to turn off the internal adapter via the switch on the front of the laptop and use the USB N13 at higher speed however with the internal wireless turned off the USB one does not show any activity either.


 The question I have is how do you use a USB "N" series wireless on a laptop on a laptop with Ubuntu and get the "N" speed performance.  Is this possible?

---

### Post by praseodym on 2011-09-05
Hi,

you have to modify the file /etc/Wireless/RT28[COLOR="Red"]7[/COLOR]0STA/RT28[COLOR="Red"]7[/COLOR]0STA.dat

according to this entries for your specific country settings

[http://wiki.ubuntuusers.de/wlan/ralink#RT2860STA-und-Draft-N](http://wiki.ubuntuusers.de/wlan/ralink#RT2860STA-und-Draft-N)

You may want to translate the page. The file rt28[COLOR="Red"]7[/COLOR]0sta.dat is for USB-devices, the according file /etc/Wireless/RT28[COLOR="Red"]6[/COLOR]0STA/RT28[COLOR="Red"]6[/COLOR]0STA.dat for PCI-devices. Otherwise Draft-N doesnt work properly.

---

