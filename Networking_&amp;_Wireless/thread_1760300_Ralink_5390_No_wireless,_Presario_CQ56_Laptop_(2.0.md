---
title: "Ralink 5390 No wireless, Presario CQ56 Laptop (2.0)"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by Xinu38 on 2011-05-16
I need help, first off...i have done this 4 times. just downloaded ubuntu 11.04 from windows 7 a few hours ago. everything is identical to this thread all the way up to the code i posted where i get errors. 
[http://ubuntuforums.org/showthread.php?t=1751685](http://ubuntuforums.org/showthread.php?t=1751685)

no matter what i did, i could not get rt5390sta to show up in my additional drivers. i followed it step by step, all the terminal results came out the same as samzystrange's results. downloaded the patches from [https://build.opensuse.org/package/f...ver%3Awireless]("https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless") and followed the instructions by chilli555 as close as i can, but here is my results.

```
stoke@Stoke:~$ patch -p0 < rt5390sta-2.4.0.4-config.patch 
bash: rt5390sta-2.4.0.4-config.patch: No such file or directory
stoke@Stoke:~$ patch -p0 < rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch 
bash: rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch: No such file or directory
stoke@Stoke:~$ patch -p0 < rt5390sta-2.4.0.4-reduce_debug_output.patch 
bash: rt5390sta-2.4.0.4-reduce_debug_output.patch: No such file or directory
stoke@Stoke:~$ patch -p0 < rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch 
bash: rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch: No such file or directory
stoke@Stoke:~$ patch -p0 < rt5390sta-2.4.0.4-return_nonvoid_function.patch 
bash: rt5390sta-2.4.0.4-return_nonvoid_function.patch: No such file or directory
stoke@Stoke:~$ patch -p0 < rt5390sta-2.4.0.4-WPA-mixed.patch 
bash: rt5390sta-2.4.0.4-WPA-mixed.patch: No such file or directory
stoke@Stoke:~$ sudo su 
root@Stoke:/home/stoke# cp RT2860STA.dat RT5390STA.dat
cp: cannot stat `RT2860STA.dat': No such file or directory
root@Stoke:/home/stoke# mkdir -p /etc/Wireless/RT5390STA
root@Stoke:/home/stoke# cp RT5390STA.dat /etc/Wireless/RT5390STA
cp: cannot stat `RT5390STA.dat': No such file or directory
root@Stoke:/home/stoke# make clean
make: *** No rule to make target `clean'.  Stop.
root@Stoke:/home/stoke# make
make: *** No targets specified and no makefile found.  Stop.
root@Stoke:/home/stoke# make install
make: *** No rule to make target `install'.  Stop.
root@Stoke:/home/stoke# modprobe rt5390sta
FATAL: Module rt5390sta not found.
root@Stoke:/home/stoke# exit^C
root@Stoke:/home/stoke# 
 
```i have the same exact computer as samzystrange as well, 64 bit, just...i am lost on what to do now.  thanks in advanced. I havnt had Ubuntu since 10.04 release, and im sure i am missing something that is so stupid, imma smack my head after this thread. im just hitting a blocking point and my experience can not figure this out.

---

### Post by chili555 on 2011-05-16
> stoke@Stoke:[COLOR="Red"]**~**[/COLOR]$ patch -p0 < rt5390sta-2.4.0.4-config.patch 
bash: rt5390sta-2.4.0.4-config.patch: No such file or directoryYou are not missing something stupid; you are missing something that's easy for experienced Ubuntians and is a part of command line lore. It's hard to get right away for noobs.

See that little ~ up there? That indicates you are in your /home/stoke directory. That is NOT where the 5390 files and patches are. If you put the patches in the same directory as the driver you downloaded and extracted, namely 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO, then do:```
cd 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
sudo su
patch etc.
```See post #24 here: [http://ubuntuforums.org/showthread.php?t=1740963&highlight=5390&page=3](http://ubuntuforums.org/showthread.php?t=1740963&highlight=5390&page=3)

---

### Post by Xinu38 on 2011-05-16
well...stupid was the wrong word, a simple mistake lol. but ya, it did what it was supposed to do this time, rebooted, still no driver, still no wireless.

---

### Post by chili555 on 2011-05-16
Please run and post:```
sudo modprobe rt5390sta
dmesg | grep 539
```Thanks.

---

### Post by Xinu38 on 2011-05-16
done

```
stoke@Stoke:~$ sudo modprobe rt5390sta
[sudo] password for stoke: 
FATAL: Module rt5390sta not found.
stoke@Stoke:~$ dmesg | grep 539
[    0.223666] pci 0000:02:00.0: [1814:5390] type 0 class 0x000280
[    0.265390] usbcore: registered new interface driver hub
stoke@Stoke:~$ 

```

---

### Post by chili555 on 2011-05-16
> FATAL: Module rt5390sta not found.It looks like your compile didn't go so well. Please retrace your steps:```
cd 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
sudo su
make clean
make
make install
modprobe rt5390sta
exit
```Are there any errors?

---

### Post by Xinu38 on 2011-05-16
```
stoke@Stoke:~$ cd 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
stoke@Stoke:~/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO$ sudo su
root@Stoke:/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO# make clean
cp -f os/linux/Makefile.6 os/linux/Makefile
make -C os/linux clean
make[1]: Entering directory `/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux'
rm -f ../../common/*.o
rm -f ../../common/.*.{cmd,flags,d}
rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
rm -f ../../os/linux/.*.{cmd,flags,d}
rm -fr ../../os/linux/.tmp_versions
rm -f ../../os/linux/Module.symvers
rm -f ../../os/linux/Module.markers
rm -f ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.{cmd,flags,d}
rm -f ../../sta/*.o
rm -f ../../sta/.*.{cmd,flags,d}
make[1]: Leaving directory `/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux'
rm -rf os/linux/Makefile
root@Stoke:/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO# make
make -C tools
make[1]: Entering directory `/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/tools'
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/Makefile
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_md5.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_aes.o
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_aes.c: In function ‘WscEncryptData’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_aes.c:1522:1: warning: the frame size of 1424 bytes is larger than 1024 bytes
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_aes.c: In function ‘WscDecryptData’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_aes.c:1592:1: warning: the frame size of 1424 bytes is larger than 1024 bytes
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_aes.c:2265:1: warning: the frame size of 1648 bytes is larger than 1024 bytes
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_UNWRAP’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_aes.c:2348:1: warning: the frame size of 1152 bytes is larger than 1024 bytes
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/mlme.o
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/mlme.c: In function ‘InitLookupTable’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/mlme.c:635:2: warning: missing braces around initializer
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/mlme.c:635:2: warning: (near initialization for ‘WordStruct.field’)
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/mlme.c: In function ‘MlmeResetRalinkCounters’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/mlme.c:1047:2: warning: cast from pointer to integer of different size
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/mlme.c:1047:2: warning: cast from pointer to integer of different size
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/mlme.c: In function ‘BssTableSetEntry’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/mlme.c:6019:39: warning: operation on ‘Tab->BssOverlapNr’ may be undefined
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/mlme.c:6380:1: warning: the frame size of 1744 bytes is larger than 1024 bytes
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_wep.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/action.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_data.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_init.o
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_init.c: In function ‘NICInitAsicFromEEPROM’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_init.c:1558:9: warning: unused variable ‘EfuseData’
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_aes.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_sync.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/eeprom.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_info.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/dfs.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/spectrum.o
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/spectrum.c:1966:3: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_channel.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_profile.o
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_profile.c: In function ‘RTMPSetProfileParameters’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_profile.c:1436:4: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘ULONG’
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.o
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c: In function ‘AsicSwitchChannel’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:1243:15: warning: comparison of distinct pointer types lacks a cast
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:1384:17: warning: comparison of distinct pointer types lacks a cast
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:1392:17: warning: comparison of distinct pointer types lacks a cast
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:1403:16: warning: comparison of distinct pointer types lacks a cast
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c: In function ‘AsicAdjustTxPower’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:4977:6: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:4984:6: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:4990:6: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:5055:5: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:5060:5: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:5064:5: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:5071:5: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:5076:5: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:5080:5: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:5087:5: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:5092:5: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_asic.c:5096:5: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/assoc.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/auth.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.o
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.c:755:1: warning: the frame size of 1344 bytes is larger than 1024 bytes
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.c:1085:1: warning: the frame size of 1424 bytes is larger than 1024 bytes
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.c:571:1: warning: the frame size of 1088 bytes is larger than 1024 bytes
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sync.c:1755:1: warning: the frame size of 1472 bytes is larger than 1024 bytes
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sanity.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/connect.o
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/connect.c:314:1: warning: the frame size of 1792 bytes is larger than 1024 bytes
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/wpa.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/ags.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/frq_cal.o
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/frq_cal.c: In function ‘FrequencyCalibration’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/frq_cal.c:214:18: warning: comparison of distinct pointer types lacks a cast
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/frq_cal.c:227:18: warning: comparison of distinct pointer types lacks a cast
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/frq_cal.c:242:18: warning: comparison of distinct pointer types lacks a cast
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/frq_cal.c:264:18: warning: comparison of distinct pointer types lacks a cast
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/frq_cal.c:277:18: warning: comparison of distinct pointer types lacks a cast
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../sta/frq_cal.c:292:18: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/ba_action.o
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/ba_action.c: In function ‘convert_reordering_packet_to_preAMSDU_or_802_3_packet’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/ba_action.c:1568:2: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_mac_pci.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_data_pci.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/ee_prom.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/ee_efuse.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_mcu.o
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_mcu.c: In function ‘RtmpAsicSendCommandToMcu’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_mcu.c:463:4: warning: passing argument 3 of ‘pci_read_config_word’ from incompatible pointer type
include/linux/pci.h:736:19: note: expected ‘u16 *’ but argument is of type ‘INT *’
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_mcu.c:482:4: warning: passing argument 3 of ‘pci_read_config_word’ from incompatible pointer type
include/linux/pci.h:736:19: note: expected ‘u16 *’ but argument is of type ‘INT *’
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_rf.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../chips/rt30xx.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../chips/rt3090.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../chips/rt33xx.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../chips/rt3390.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../chips/rt5390.o
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.o
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c: In function ‘DO_RACFG_CMD_IO_READ_BULK’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:454:44: warning: cast to pointer from integer of different size
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c: In function ‘ATETxPwrHandler’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:1802:45: warning: unused variable ‘CfgOfTxPwrCtrlOverMAC’
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c: In function ‘ATEAsicSwitchChannel’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:5076:15: warning: comparison of distinct pointer types lacks a cast
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:5230:16: warning: comparison of distinct pointer types lacks a cast
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:5007:21: warning: unused variable ‘RFValue2’
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:5002:16: warning: unused variable ‘RFRegTable’
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:5001:43: warning: unused variable ‘R4’
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:5001:17: warning: unused variable ‘R3’
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:5001:9: warning: unused variable ‘R2’
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c: In function ‘Set_ATE_TSSI_CALIBRATION_Proc’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7564:5: warning: passing argument 3 of ‘eFuseWrite’ from incompatible pointer type
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/include/rtmp.h:5889:10: note: expected ‘PUSHORT’ but argument is of type ‘UCHAR *’
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7477:42: warning: unused variable ‘ChannelPower’
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7649:5: warning: passing argument 3 of ‘eFuseWrite’ from incompatible pointer type
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/include/rtmp.h:5889:10: note: expected ‘PUSHORT’ but argument is of type ‘UCHAR *’
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c: In function ‘GetPowerDeltaFromTssiRatio’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7801:2: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘LONG’
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7830:2: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘LONG’
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c: In function ‘Set_ATE_READ_EXTERNAL_TSSI_Proc’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:8011:9: warning: passing argument 3 of ‘eFuseWrite’ from incompatible pointer type
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/include/rtmp.h:5889:10: note: expected ‘PUSHORT’ but argument is of type ‘UCHAR *’
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7965:18: warning: unused variable ‘EEPTemp’
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c: In function ‘Set_ATE_TSSI_CALIBRATION_Proc’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7477:9: warning: ‘BbpData’ may be used uninitialized in this function
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7584:17: warning: ‘BbpData’ may be used uninitialized in this function
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c: In function ‘RTATEGetTssiByChannel’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7708:8: warning: ‘BbpData’ may be used uninitialized in this function
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c: In function ‘Set_ATE_READ_EXTERNAL_TSSI_Proc’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rt_ate.c:7964:28: warning: ‘BbpData’ may be used uninitialized in this function
  CC [M]  /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.o
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:679:2: warning: ‘enum tx_power_setting’ declared inside parameter list
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:679:2: warning: its scope is only this definition or declaration, which is probably not what you want
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:678:29: error: parameter 2 (‘Type’) has incomplete type
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:676:12: warning: function declaration isn’t a prototype
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:1355:2: warning: initialization from incompatible pointer type
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:1378:2: warning: initialization from incompatible pointer type
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:1379:2: warning: initialization from incompatible pointer type
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:1380:2: warning: initialization from incompatible pointer type
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:1381:2: warning: initialization from incompatible pointer type
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:1388:2: warning: initialization from incompatible pointer type
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c: In function ‘CFG80211_SupBandInit’:
/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:2594:2: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
make[2]: *** [/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.o] Error 1
make[1]: *** [_module_/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [LINUX] Error 2
root@Stoke:/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO# make install
make -C /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5390sta.ko /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/
install: cannot stat `rt5390sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux'
make: *** [install] Error 2
root@Stoke:/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO# modprobe rt5390sta
FATAL: Module rt5390sta not found.
root@Stoke:/home/stoke/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO# exit
```

looks like the errors are at the very end.

---

### Post by chili555 on 2011-05-16
> os/linux/../../os/linux/cfg80211.o] Error 1In the file os/linux/config.mk, please change HAS_CFG80211_SUPPORT=n to =y. Then try again.

For future reference, an error anywhere in the process MUST be fixed in order for the module to build and work. If you encounter an error at 'make,' any further steps will be useless. Stop, fix the error and then proceed.

---

### Post by Xinu38 on 2011-05-16
noted, ill  let you know the results here in a few.

edit: actually it was already set to =y

#Support MAC80211 LINUX-only function 
HAS_CFG80211_SUPPORT=y

---

### Post by Xinu38 on 2011-05-16
also found these here. should i switch the y's to n's?

ifeq ($(HAS_CFG80211_SUPPORT),y) 
WFLAGS += -DRT_CFG80211_SUPPORT

---

### Post by chili555 on 2011-05-16
> **Xinu38 said:**
> also found these here. should i switch the y's to n's?

ifeq ($(HAS_CFG80211_SUPPORT),y) 
WFLAGS += -DRT_CFG80211_SUPPORTNo.

---

### Post by chili555 on 2011-05-16
> **Xinu38 said:**
> noted, ill  let you know the results here in a few.

edit: actually it was already set to =y

#Support MAC80211 LINUX-only function 
HAS_CFG80211_SUPPORT=yTry it =n then.

Sorry, off to bed. I'll check in tomorrow. This has been 14 hours on the forum...yawn...

---

### Post by Xinu38 on 2011-05-16
ya ill mess around with it, i appreciate the last minute help. later

---

### Post by Xinu38 on 2011-05-16
> **chili555 said:**
> Try it =n then.

Sorry, off to bed. I'll check in tomorrow. This has been 14 hours on the forum...yawn...


that is exactly what it was. everything is working flawless now.   you are awesome, i appreciate all the tips and help.

---

### Post by chili555 on 2011-05-17
Woo hoo! Glad to hear it's working now.

---

### Post by Xinu38 on 2011-05-17
yes, i must thank you, glad you were able to continue the help from the previous threads. i went to bed happy :P

---

### Post by gavroche76 on 2011-06-27
Thank you [chili555]("http://ubuntuforums.org/member.php?u=35909") that worked for me too.:popcorn:

---

### Post by Sable Drakon on 2011-07-29
Are these drivers going to be making an appearance in 11.10? It'd be nice to be able to blast Win7 off my notebook, same model as the OP, and have Linux working right out of the box.

---

