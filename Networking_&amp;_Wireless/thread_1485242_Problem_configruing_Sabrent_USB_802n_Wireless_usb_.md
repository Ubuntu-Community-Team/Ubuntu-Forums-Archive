---
title: "Problem configruing Sabrent USB 802n Wireless usb adapter"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by azteka22 on 2010-05-16
Hello, I recently bought a Sabrent USB-802N wireless adapter for my computer, but before I bought it I looked it up online to see if this adapter was ubuntu friendly. On the box it said it was compatible with linux and on line it said people have gotten it to work on ubuntu. However I am having some problems configuring it to be detected and working propery on my Ubuntu 10.04 linux machine. 

I followed all the instructions on the README. I changed the config to set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y' on os/linux/config.mk but when I run the make 
I keep getting this error:

```
 vick@vick-desktop:~/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0$ sudo make
make -C tools
make[1]: Entering directory `/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.32-22-generic/build SUBDIRS=/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/md5.o
  CC [M]  /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/mlme.o
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/mlme.c:4259: warning: the frame size of 1572 bytes is larger than 1024 bytes
  CC [M]  /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtmp_wep.o
  CC [M]  /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/action.o
  CC [M]  /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_data.o
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_data.c: In function ‘RTMP_FillTxBlkInfo’:
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_data.c:713: warning: label ‘FillTxBlkErr’ defined but not used
  CC [M]  /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtmp_tkip.o
  CC [M]  /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_sync.o
  CC [M]  /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/eeprom.o
  CC [M]  /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_info.o
  CC [M]  /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_wpa.o
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_wpa.c: In function ‘AES_GTK_KEY_WRAP’:
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_wpa.c:836: warning: the frame size of 1092 bytes is larger than 1024 bytes
  CC [M]  /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/dfs.o
  CC [M]  /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/spectrum.o
  CC [M]  /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/assoc.o
  CC [M]  /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/aironet.o
  CC [M]  /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/auth.o
  CC [M]  /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sync.o
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sync.c:1393: warning: the frame size of 1312 bytes is larger than 1024 bytes
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sync.c:934: warning: the frame size of 1252 bytes is larger than 1024 bytes
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sync.c:675: warning: the frame size of 1256 bytes is larger than 1024 bytes
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sync.c:533: warning: the frame size of 1064 bytes is larger than 1024 bytes
  CC [M]  /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sanity.o
  CC [M]  /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/connect.o
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/connect.c:351: warning: the frame size of 1600 bytes is larger than 1024 bytes
  CC [M]  /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/wpa.o
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/wpa.c: In function ‘CCKMPRF’:
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/wpa.c:1848: warning: the frame size of 1044 bytes is larger than 1024 bytes
  CC [M]  /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_linux.o
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘send_monitor_packets’:
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_linux.c:1043: warning: the frame size of 1084 bytes is larger than 1024 bytes
  CC [M]  /home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.o
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c: In function ‘RTMPReadParametersHook’:
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:928: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:929: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:1593: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:1594: error: ‘struct task_struct’ has no member named ‘fsgid’
make[2]: *** [/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.o] Error 1
make[1]: *** [_module_/home/vick/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [LINUX] Error 2


```also do i need to install the wpa_supplicant? I have it downloaded but i have not installed it or compiled it yet.

USB adapter: Sabrent USB-802N
Driver: Ralink Technology rt2870.o
Ubuntu: 10.04 32 bit

any ideas? Please help 

Thanks in advance!

---

### Post by azteka22 on 2010-05-16
Problem solved thx anyway

---

### Post by skalra63 on 2010-05-18
...so how did you solve the problem?

---

### Post by azteka22 on 2010-05-18
browsing around Ubuntu Forums I found someone who had this particular problem as me but with a different USB. There solution was to add 4 entries in the blacklist.conf and apparently it worked like a charm.. here is the link: 

[http://ubuntuforums.org/showthread.php?t=1435271&highlight=148f:3070](http://ubuntuforums.org/showthread.php?t=1435271&highlight=148f:3070)

---

