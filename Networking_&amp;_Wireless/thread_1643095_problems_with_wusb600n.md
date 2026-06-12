---
title: "problems with wusb600n"
date: 2010-12-11
forum: Networking &amp; Wireless
---

### Post by Sketchworks on 2010-12-11
ok so i bet if i really search hard enough id figure this out but hey im tired of looking.... ok so i have a linksys wusb600n and im running ubuntu 10.10 and when i boot up the wireless works for like ten min then disconnects... if i suspend or reboot it'll work again for another 10 min but im soooo tired of having to do that.. so my question is pretty obvious, how do i fix it so it stays on? need step by step cuz yeah linux noob....

---

### Post by Sketchworks on 2010-12-11
update.... iv gone to [http://ubuntuforums.org/showthread.php?t=972060](http://ubuntuforums.org/showthread.php?t=972060) and im not exactly sure what im doing here ive tryed messing aroun but yeah no luck... help me please...

---

### Post by Sketchworks on 2010-12-11
this is where im stuck...
sketchworks@oldpile:~/Desktop$ cd WUSB600N
sketchworks@oldpile:~/Desktop/WUSB600N$ sudo make
[sudo] password for sketchworks: 
make -C tools
make[1]: Entering directory `/home/sketchworks/Desktop/WUSB600N/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/sketchworks/Desktop/WUSB600N/tools'
/home/sketchworks/Desktop/WUSB600N/tools/bin2h
cp -f os/linux/Makefile.6 /home/sketchworks/Desktop/WUSB600N/os/linux/Makefile
make  -C  /lib/modules/2.6.35-23-generic/build SUBDIRS=/home/sketchworks/Desktop/WUSB600N/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic'
  CC [M]  /home/sketchworks/Desktop/WUSB600N/os/linux/../../common/md5.o
  CC [M]  /home/sketchworks/Desktop/WUSB600N/os/linux/../../common/mlme.o
/home/sketchworks/Desktop/WUSB600N/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/sketchworks/Desktop/WUSB600N/os/linux/../../common/mlme.c:4259: warning: the frame size of 1572 bytes is larger than 1024 bytes
  CC [M]  /home/sketchworks/Desktop/WUSB600N/os/linux/../../common/rtmp_wep.o
  CC [M]  /home/sketchworks/Desktop/WUSB600N/os/linux/../../common/action.o
  CC [M]  /home/sketchworks/Desktop/WUSB600N/os/linux/../../common/cmm_data.o
/home/sketchworks/Desktop/WUSB600N/os/linux/../../common/cmm_data.c: In function ‘RTMP_FillTxBlkInfo’:
/home/sketchworks/Desktop/WUSB600N/os/linux/../../common/cmm_data.c:713: warning: label ‘FillTxBlkErr’ defined but not used
  CC [M]  /home/sketchworks/Desktop/WUSB600N/os/linux/../../common/rtmp_init.o
  CC [M]  /home/sketchworks/Desktop/WUSB600N/os/linux/../../common/rtmp_tkip.o
  CC [M]  /home/sketchworks/Desktop/WUSB600N/os/linux/../../common/cmm_sync.o
  CC [M]  /home/sketchworks/Desktop/WUSB600N/os/linux/../../common/eeprom.o
  CC [M]  /home/sketchworks/Desktop/WUSB600N/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/sketchworks/Desktop/WUSB600N/os/linux/../../common/cmm_info.o
  CC [M]  /home/sketchworks/Desktop/WUSB600N/os/linux/../../common/cmm_wpa.o
/home/sketchworks/Desktop/WUSB600N/os/linux/../../common/cmm_wpa.c: In function ‘AES_GTK_KEY_WRAP’:
/home/sketchworks/Desktop/WUSB600N/os/linux/../../common/cmm_wpa.c:836: warning: the frame size of 1092 bytes is larger than 1024 bytes
  CC [M]  /home/sketchworks/Desktop/WUSB600N/os/linux/../../common/dfs.o
  CC [M]  /home/sketchworks/Desktop/WUSB600N/os/linux/../../common/spectrum.o
  CC [M]  /home/sketchworks/Desktop/WUSB600N/os/linux/../../sta/assoc.o
  CC [M]  /home/sketchworks/Desktop/WUSB600N/os/linux/../../sta/aironet.o
  CC [M]  /home/sketchworks/Desktop/WUSB600N/os/linux/../../sta/auth.o
  CC [M]  /home/sketchworks/Desktop/WUSB600N/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/sketchworks/Desktop/WUSB600N/os/linux/../../sta/sync.o
/home/sketchworks/Desktop/WUSB600N/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/sketchworks/Desktop/WUSB600N/os/linux/../../sta/sync.c:1393: warning: the frame size of 1312 bytes is larger than 1024 bytes
/home/sketchworks/Desktop/WUSB600N/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/sketchworks/Desktop/WUSB600N/os/linux/../../sta/sync.c:934: warning: the frame size of 1252 bytes is larger than 1024 bytes
/home/sketchworks/Desktop/WUSB600N/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/sketchworks/Desktop/WUSB600N/os/linux/../../sta/sync.c:675: warning: the frame size of 1256 bytes is larger than 1024 bytes
/home/sketchworks/Desktop/WUSB600N/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/sketchworks/Desktop/WUSB600N/os/linux/../../sta/sync.c:533: warning: the frame size of 1064 bytes is larger than 1024 bytes
  CC [M]  /home/sketchworks/Desktop/WUSB600N/os/linux/../../sta/sanity.o
  CC [M]  /home/sketchworks/Desktop/WUSB600N/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/sketchworks/Desktop/WUSB600N/os/linux/../../sta/connect.o
/home/sketchworks/Desktop/WUSB600N/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/sketchworks/Desktop/WUSB600N/os/linux/../../sta/connect.c:351: warning: the frame size of 1600 bytes is larger than 1024 bytes
  CC [M]  /home/sketchworks/Desktop/WUSB600N/os/linux/../../sta/wpa.o
/home/sketchworks/Desktop/WUSB600N/os/linux/../../sta/wpa.c: In function ‘CCKMPRF’:
/home/sketchworks/Desktop/WUSB600N/os/linux/../../sta/wpa.c:1848: warning: the frame size of 1044 bytes is larger than 1024 bytes
  CC [M]  /home/sketchworks/Desktop/WUSB600N/os/linux/../../os/linux/rt_linux.o
/home/sketchworks/Desktop/WUSB600N/os/linux/../../os/linux/rt_linux.c: In function ‘send_monitor_packets’:
/home/sketchworks/Desktop/WUSB600N/os/linux/../../os/linux/rt_linux.c:1043: warning: the frame size of 1084 bytes is larger than 1024 bytes
  CC [M]  /home/sketchworks/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.o
/home/sketchworks/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.c: In function ‘RTMPReadParametersHook’:
/home/sketchworks/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.c:928: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/sketchworks/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.c:929: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/sketchworks/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/sketchworks/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/sketchworks/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.c:1593: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/sketchworks/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.c:1594: error: ‘struct task_struct’ has no member named ‘fsgid’
make[2]: *** [/home/sketchworks/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.o] Error 1
make[1]: *** [_module_/home/sketchworks/Desktop/WUSB600N/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
make: *** [LINUX] Error 2
sketchworks@oldpile:~/Desktop/WUSB600N$ 



what do i do now?

---

