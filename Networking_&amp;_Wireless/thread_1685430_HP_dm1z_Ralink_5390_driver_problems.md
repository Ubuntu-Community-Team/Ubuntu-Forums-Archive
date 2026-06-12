---
title: "HP dm1z Ralink 5390 driver problems"
date: 2011-02-10
forum: Networking &amp; Wireless
---

### Post by stubbsPY on 2011-02-10
There are a number of us that have the new HP dm1z-3000 laptop, which has a Ralink 5390 card. None of us have been successful in getting the card to work, even when downloading the driver from Ralink and compiling ourselves. 

Note that this is all on 64-bit; I've heard the odd success story on a 32-bit OS, but not for this specific machine.

I've tried the instructions in this thread:
[http://ubuntuforums.org/showthread.php?p=10441038#post10441038]("http://ubuntuforums.org/showthread.php?p=10441038#post10441038")

Several of us with the dm1z posted in there, including outputs of what happens when the driver is accessed. I also tried it on Natty Alpha 2, but can't get past login with networking enabled. It hangs so fast I can't even get to a real console to see what's going on.

Any ideas?

---

### Post by spaceharrier on 2011-02-11
I got a response back from Ralink technical support, having sent them the details in the other thread. They're attempting to reproduce the issue. Hopefully they'll be able to shed some prompt light on it.

---

### Post by mr_raider on 2011-02-12
Thanks for the effort. I just ordered my dm1z.  may have to resort to transplanting the broadcom 4322 from my current HP dv2 of the problem can't be resolved.

I noticed the windows driver reports it as ralink 5390, not 539f.

Is there a chane the problem could be related to the new Hudson Southbridge and PCI-E config?

---

### Post by mr_raider on 2011-02-12
Here is some hope:

[http://www.phoronix.com/scan.php?page=news_item&px=OTA5MA](http://www.phoronix.com/scan.php?page=news_item&px=OTA5MA)

---

### Post by spaceharrier on 2011-02-12
> **mr_raider said:**
> Here is some hope:

[http://www.phoronix.com/scan.php?page=news_item&px=OTA5MA](http://www.phoronix.com/scan.php?page=news_item&px=OTA5MA)

That does look promising. I'm not a driver writer but all those 5390-specific definitions look like just the sort of thing that might be almost the same across chips, but not quite leading to sort of behavior we've been seeing with the existing driver.

(I've also ordered a cheapo USB adapter to use under Linux while this is getting figured out.)

---

### Post by ricardon on 2011-02-12
Hi,

My two cents: Here[ http://ubuntuforums.org/showpost.php?p=10452987&postcount=42]("http://ubuntuforums.org/showpost.php?p=10452987&postcount=42") are some steps that worked for me on making my Ralink 5390 on my HP G62 laptop. Even though I am using 32-bit Maverick, I think these steps could work on 64-bit as well, as I was seeing the same issues reported in that thread (able to build and install but unable to connect to any network).

---

### Post by mrmagos on 2011-02-13
> **mr_raider said:**
> Here is some hope:

[http://www.phoronix.com/scan.php?page=news_item&px=OTA5MA](http://www.phoronix.com/scan.php?page=news_item&px=OTA5MA)

Quite promising, but a bit too late to be included in kernel 2.6.38, not to mention that the version of rt2x00 included with the kernel is a couple months behind. Possibly some hope for a backport, but unlikely I'd guess. We may have to wait for the next kernel (or later), or pull from the project's git tree and build ourselves.

---

### Post by spaceharrier on 2011-02-14
> **ricardon said:**
> Hi,

My two cents: Here[ http://ubuntuforums.org/showpost.php?p=10452987&postcount=42]("http://ubuntuforums.org/showpost.php?p=10452987&postcount=42") are some steps that worked for me on making my Ralink 5390 on my HP G62 laptop. Even though I am using 32-bit Maverick, I think these steps could work on 64-bit as well, as I was seeing the same issues reported in that thread (able to build and install but unable to connect to any network).

This worked for me on my dm1z under 10.10 64-bit. Nice work. I've also posted confirmation in the other thread.

I actually got an email from Ralink tech support a couple of hours ago pointing to your posting as a possible solution.

---

### Post by mrmagos on 2011-02-14
> **ricardon said:**
> Hi,

My two cents: Here[ http://ubuntuforums.org/showpost.php?p=10452987&postcount=42]("http://ubuntuforums.org/showpost.php?p=10452987&postcount=42") are some steps that worked for me on making my Ralink 5390 on my HP G62 laptop. Even though I am using 32-bit Maverick, I think these steps could work on 64-bit as well, as I was seeing the same issues reported in that thread (able to build and install but unable to connect to any network).

I can confirm that this solution works under Natty x64 as well. Thanks a bunch.

---

### Post by dig-it74 on 2011-02-16
I got the card to work on open networks but with anything from wep-wpa2 will not connect. I have the hp dm1 3000 5390. I have not gotten a reply from RAlink on this issue.

---

### Post by headlice on 2011-03-06
> **ricardon said:**
> Hi,

My two cents: Here[ http://ubuntuforums.org/showpost.php?p=10452987&postcount=42]("http://ubuntuforums.org/showpost.php?p=10452987&postcount=42") are some steps that worked for me on making my Ralink 5390 on my HP G62 laptop. Even though I am using 32-bit Maverick, I think these steps could work on 64-bit as well, as I was seeing the same issues reported in that thread (able to build and install but unable to connect to any network).

I am having a problem applying the patches.  This is what I get:

```
$ patch -p0 < rt5390sta-2.4.0.4-config.patch

patching file Makefile
Hunk #1 FAILED at 286.
Hunk #2 FAILED at 333.
2 out of 2 hunks FAILED -- saving rejects to file Makefile.rej
patching file os/linux/config.mk
Hunk #1 FAILED at 108.
1 out of 1 hunk FAILED -- saving rejects to file os/linux/config.mk.rej
```

what is going on?

This is what is in the .rej file:

```
--- os/linux/config.mk.orig     2010-12-17 20:13:52.000000000 +0100
+++ os/linux/config.mk  2010-12-17 20:15:48.000000000 +0100
@@ -108,10 +108,10 @@
 HAS_GREENAP_SUPPORT=n

 #Support MAC80211 LINUX-only function
-HAS_CFG80211_SUPPORT=y
+HAS_CFG80211_SUPPORT=n

 #Support RFKILL hardware block/unblock LINUX-only function
-HAS_RFKILL_HW_SUPPORT=y
+HAS_RFKILL_HW_SUPPORT=n


 #Support Restore Credential back to profile
```

---

### Post by mrmagos on 2011-03-09
You need to run the command from the directory that the source and makefiles are in, and give a relative path to the patches.

As an aside (and I posted this in the other thread too), has anyone had success pairing bluetooth devices whith this card? Syslog shows that it goes into discovery, but it won't pick up any discoverable devices.

---

### Post by palimmo on 2011-03-20
> **mrmagos said:**
> I can confirm that this solution works under Natty x64 as well. Thanks a bunch.

Can you (mrmagos and spaceharrier) confirm that it works good?
Do you never lose the connection as someone reported in the other thread?

Thank you!

(I have a HP G62 and I'm going to install Ubuntu asap)

---

### Post by palimmo on 2011-03-24
> **palimmo said:**
> Can you (mrmagos and spaceharrier) confirm that it works good?
Do you never lose the connection as someone reported in the other thread?

Thank you!

(I have a HP G62 and I'm going to install Ubuntu asap)

Nothing? 
:(

---

### Post by stubbsPY on 2011-03-24
I've had it working for a few weeks, no issues with dropped connections. Seems to work at least as well as Windows now.

---

### Post by adamis on 2011-03-25
Any chance one of you that has already applied the patches and gotten the code to compile correctly could make a zip file of the patched source code available? 

Patching code may not be a very difficult task but there are many of us that don't have much experience with the process. A link would be greatly appreciated.

---

### Post by adamis on 2011-04-01
For anyone else that doesn't want to take on the challenge of patching these files, I have uploaded a patched version of the RT5390 drivers to my web-server. The patches are the ones that are from the opensuse server that have been mentioned previously in this thread. You can access them here.

[http://barkmunchers.com/dm1z/RT.tar.gz](http://barkmunchers.com/dm1z/RT.tar.gz)[]("http://barkmunchers.com/dm1z/RT.tar.gz") 

Note that, when I applied the patches, I renamed the patch files to numerical file names to make it easier to run the patch commands. I only mention this because when you extract the files, you will see something like 1.patch, 2.patch, etc... instead of the long file names that the patch files were originally named. Since the files have already patched, there is no need to anything with these files.

---

### Post by en4ian on 2011-04-05
> **adamis said:**
> For anyone else that doesn't want to take on the challenge of patching these files, I have uploaded a patched version of the RT5390 drivers to my web-server. The patches are the ones that are from the opensuse server that have been mentioned previously in this thread. You can access them here.

[http://barkmunchers.com/dm1z/RT.tar.gz](http://barkmunchers.com/dm1z/RT.tar.gz)[]("http://barkmunchers.com/dm1z/RT.tar.gz") 

Note that, when I applied the patches, I renamed the patch files to numerical file names to make it easier to run the patch commands. I only mention this because when you extract the files, you will see something like 1.patch, 2.patch, etc... instead of the long file names that the patch files were originally named. Since the files have already patched, there is no need to anything with these files.

So I download your files and all that is left to do is the following?

7. Copy manually the kernel module to your modules directory.
sudo cp ./os/linux/rt5390sta.ko /lib/modules/2.6.35-25-generic/kernel/drivers/net/wireless/

8. Edit /etc/modules to add the line 'rt5390sta'

9. Reboot and find your network SSID. It may be possible that you need to restart the network manager with 'sudo restart network-manager'

Also what if I don't have 2.6.35-25-generic? I have -22 and -28?

---

### Post by en4ian on 2011-04-08
This still isn't working for me and after I install drivers for the 5390 my system hangs whenever I click the wireless icon. 

How is this solved when so many people seem to still be having trouble?

Also that patching thing makes no sense. Can someone write it for a complete linux noob.

---

### Post by cynninge on 2011-04-10
> **en4ian said:**
> This still isn't working for me and after I install drivers for the 5390 my system hangs whenever I click the wireless icon. 

How is this solved when so many people seem to still be having trouble?

Also that patching thing makes no sense. Can someone write it for a complete linux noob.

are you sure you're using the correct driver for your hardware? 

this works perfectly on the dm1z with the device id Ralink Device 539f

maybe you have something slightly different in your box

check with lspci

---

### Post by adamis on 2011-04-10
The instructions listed in the link from earlier posts I found have typos. Below are some corrected instructions that hopefully should get you on your way... 

1. Download the file contained at this link: [http://barkmunchers.com/dm1z/RT.tar.gz](http://barkmunchers.com/dm1z/RT.tar.gz)

2. Extract the files to a directory. Then open a console, navigate to the directory that you extracted the files to then run the following commands:

[PHP]sudo make
sudo make install
sudo mkdir -p /etc/Wireless/RT5390STA
sudo cp RT5390STA.dat /etc/Wireless/RT5390STA/RT5390STA.dat
sudo cp ./os/linux/rt5390sta.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt5390sta.ko[/PHP]

Note that for the last command above I used the option <uname -r>. This will copy the files to the current running kernel version. Make sure you are running the kernel that you wish to get the wireless running on...

Now edit /etc/modules to add the line 'rt5390sta' at the end

Then run:

[PHP]sudo depmod -a
reboot[/PHP]

That should get you on your way. Hopefully that I didn't add in any typos myself.

**Edit** fixed the <uname -r> with `uname -r`, Thanks frospeh for catching the error!

---

### Post by palimmo on 2011-04-14
> **adamis said:**
> The instructions listed in the link from earlier posts I found have typos. Below are some corrected instructions that hopefully should get you on your way... 

1. Download the file contained at this link: [http://barkmunchers.com/dm1z/RT.tar.gz](http://barkmunchers.com/dm1z/RT.tar.gz)

2. Extract the files to a directory. Then open a console, navigate to the directory that you extracted the files to then run the following commands:

[PHP]sudo make
sudo make install
sudo mkdir -p /etc/Wireless/RT5390STA
sudo cp RT5390STA.dat /etc/Wireless/RT5390STA/RT5390STA.dat
sudo cp ./os/linux/rt5390sta.ko /lib/modules/<uname -r>/kernel/drivers/net/wireless/rt5390sta.ko[/PHP]

Note that for the last command above I used the option <uname -r>. This will copy the files to the current running kernel version. Make sure you are running the kernel that you wish to get the wireless running on...

Now edit /etc/modules to add the line 'rt5390sta' at the end

Then run:

[PHP]sudo depmod -a
reboot[/PHP]

That should get you on your way. Hopefully that I didn't add in any typos myself.

Very interesting.

But when I run the command 
*sudo make install*
I receive an error
[I]
/home/tamburello/RT/RT2860STA.dat": File or directory doesn't exist[/I]

:confused:


```
tamburello@tamburello-HP-G62-Notebook-PC:~$ cd RT
tamburello@tamburello-HP-G62-Notebook-PC:~/RT$ sudo make
[sudo] password for tamburello: 
make -C tools
make[1]: ingresso nella directory "/home/tamburello/RT/tools"
gcc -g bin2h.c -o bin2h
make[1]: uscita dalla directory "/home/tamburello/RT/tools"
/home/tamburello/RT/tools/bin2h
cp -f os/linux/Makefile.6 /home/tamburello/RT/os/linux/Makefile
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/home/tamburello/RT/os/linux modules
make[1]: ingresso nella directory "/usr/src/linux-headers-2.6.38-8-generic"
  CC [M]  /home/tamburello/RT/os/linux/../../common/crypt_md5.o
  CC [M]  /home/tamburello/RT/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/tamburello/RT/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/tamburello/RT/os/linux/../../common/crypt_aes.o
/home/tamburello/RT/os/linux/../../common/crypt_aes.c: In function ‘WscEncryptData’:
/home/tamburello/RT/os/linux/../../common/crypt_aes.c:1522:1: warning: the frame size of 1424 bytes is larger than 1024 bytes
/home/tamburello/RT/os/linux/../../common/crypt_aes.c: In function ‘WscDecryptData’:
/home/tamburello/RT/os/linux/../../common/crypt_aes.c:1592:1: warning: the frame size of 1424 bytes is larger than 1024 bytes
/home/tamburello/RT/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/tamburello/RT/os/linux/../../common/crypt_aes.c:2265:1: warning: the frame size of 1648 bytes is larger than 1024 bytes
/home/tamburello/RT/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_UNWRAP’:
/home/tamburello/RT/os/linux/../../common/crypt_aes.c:2348:1: warning: the frame size of 1136 bytes is larger than 1024 bytes
  CC [M]  /home/tamburello/RT/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/tamburello/RT/os/linux/../../common/mlme.o
/home/tamburello/RT/os/linux/../../common/mlme.c: In function ‘InitLookupTable’:
/home/tamburello/RT/os/linux/../../common/mlme.c:635:2: warning: missing braces around initializer
/home/tamburello/RT/os/linux/../../common/mlme.c:635:2: warning: (near initialization for ‘WordStruct.field’)
/home/tamburello/RT/os/linux/../../common/mlme.c: In function ‘MlmeResetRalinkCounters’:
/home/tamburello/RT/os/linux/../../common/mlme.c:1047:2: warning: cast from pointer to integer of different size
/home/tamburello/RT/os/linux/../../common/mlme.c:1047:2: warning: cast from pointer to integer of different size
/home/tamburello/RT/os/linux/../../common/mlme.c: In function ‘BssTableSetEntry’:
/home/tamburello/RT/os/linux/../../common/mlme.c:6019:39: warning: operation on ‘Tab->BssOverlapNr’ may be undefined
/home/tamburello/RT/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/tamburello/RT/os/linux/../../common/mlme.c:6380:1: warning: the frame size of 1728 bytes is larger than 1024 bytes
  CC [M]  /home/tamburello/RT/os/linux/../../common/cmm_wep.o
  CC [M]  /home/tamburello/RT/os/linux/../../common/action.o
  CC [M]  /home/tamburello/RT/os/linux/../../common/cmm_data.o
  CC [M]  /home/tamburello/RT/os/linux/../../common/rtmp_init.o
/home/tamburello/RT/os/linux/../../common/rtmp_init.c: In function ‘NICInitAsicFromEEPROM’:
/home/tamburello/RT/os/linux/../../common/rtmp_init.c:1558:9: warning: unused variable ‘EfuseData’
  CC [M]  /home/tamburello/RT/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/tamburello/RT/os/linux/../../common/cmm_aes.o
  CC [M]  /home/tamburello/RT/os/linux/../../common/cmm_sync.o
  CC [M]  /home/tamburello/RT/os/linux/../../common/eeprom.o
  CC [M]  /home/tamburello/RT/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/tamburello/RT/os/linux/../../common/cmm_info.o
  CC [M]  /home/tamburello/RT/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/tamburello/RT/os/linux/../../common/cmm_wpa.o
/home/tamburello/RT/os/linux/../../common/cmm_wpa.c: In function ‘PeerPairMsg4Action’:
/home/tamburello/RT/os/linux/../../common/cmm_wpa.c:1109:11: warning: unused variable ‘group_cipher’
/home/tamburello/RT/os/linux/../../common/cmm_wpa.c: In function ‘PeerGroupMsg2Action’:
/home/tamburello/RT/os/linux/../../common/cmm_wpa.c:1454:11: warning: unused variable ‘group_cipher’
  CC [M]  /home/tamburello/RT/os/linux/../../common/dfs.o
  CC [M]  /home/tamburello/RT/os/linux/../../common/spectrum.o
  CC [M]  /home/tamburello/RT/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/tamburello/RT/os/linux/../../common/rt_channel.o
  CC [M]  /home/tamburello/RT/os/linux/../../common/cmm_profile.o
  CC [M]  /home/tamburello/RT/os/linux/../../common/cmm_asic.o
/home/tamburello/RT/os/linux/../../common/cmm_asic.c: In function ‘AsicSwitchChannel’:
/home/tamburello/RT/os/linux/../../common/cmm_asic.c:1243:15: warning: comparison of distinct pointer types lacks a cast
/home/tamburello/RT/os/linux/../../common/cmm_asic.c:1384:17: warning: comparison of distinct pointer types lacks a cast
/home/tamburello/RT/os/linux/../../common/cmm_asic.c:1392:17: warning: comparison of distinct pointer types lacks a cast
/home/tamburello/RT/os/linux/../../common/cmm_asic.c:1403:16: warning: comparison of distinct pointer types lacks a cast
/home/tamburello/RT/os/linux/../../common/cmm_asic.c: In function ‘AsicEnableIbssSync’:
/home/tamburello/RT/os/linux/../../common/cmm_asic.c:5431:11: warning: unused variable ‘beaconLen’
/home/tamburello/RT/os/linux/../../common/cmm_asic.c: In function ‘AsicAddPairwiseKeyEntry’:
/home/tamburello/RT/os/linux/../../common/cmm_asic.c:6159:9: warning: unused variable ‘CipherAlg’
  CC [M]  /home/tamburello/RT/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/tamburello/RT/os/linux/../../sta/assoc.o
  CC [M]  /home/tamburello/RT/os/linux/../../sta/auth.o
  CC [M]  /home/tamburello/RT/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/tamburello/RT/os/linux/../../sta/sync.o
/home/tamburello/RT/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/tamburello/RT/os/linux/../../sta/sync.c:755:1: warning: the frame size of 1328 bytes is larger than 1024 bytes
/home/tamburello/RT/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/tamburello/RT/os/linux/../../sta/sync.c:1085:1: warning: the frame size of 1408 bytes is larger than 1024 bytes
/home/tamburello/RT/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/tamburello/RT/os/linux/../../sta/sync.c:571:1: warning: the frame size of 1088 bytes is larger than 1024 bytes
/home/tamburello/RT/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/tamburello/RT/os/linux/../../sta/sync.c:1755:1: warning: the frame size of 1472 bytes is larger than 1024 bytes
  CC [M]  /home/tamburello/RT/os/linux/../../sta/sanity.o
  CC [M]  /home/tamburello/RT/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/tamburello/RT/os/linux/../../sta/connect.o
/home/tamburello/RT/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/tamburello/RT/os/linux/../../sta/connect.c:314:1: warning: the frame size of 1776 bytes is larger than 1024 bytes
  CC [M]  /home/tamburello/RT/os/linux/../../sta/wpa.o
  CC [M]  /home/tamburello/RT/os/linux/../../sta/ags.o
  CC [M]  /home/tamburello/RT/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/tamburello/RT/os/linux/../../sta/frq_cal.o
/home/tamburello/RT/os/linux/../../sta/frq_cal.c: In function ‘FrequencyCalibration’:
/home/tamburello/RT/os/linux/../../sta/frq_cal.c:214:18: warning: comparison of distinct pointer types lacks a cast
/home/tamburello/RT/os/linux/../../sta/frq_cal.c:227:18: warning: comparison of distinct pointer types lacks a cast
/home/tamburello/RT/os/linux/../../sta/frq_cal.c:242:18: warning: comparison of distinct pointer types lacks a cast
/home/tamburello/RT/os/linux/../../sta/frq_cal.c:264:18: warning: comparison of distinct pointer types lacks a cast
/home/tamburello/RT/os/linux/../../sta/frq_cal.c:277:18: warning: comparison of distinct pointer types lacks a cast
/home/tamburello/RT/os/linux/../../sta/frq_cal.c:292:18: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/tamburello/RT/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/tamburello/RT/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/tamburello/RT/os/linux/../../os/linux/sta_ioctl.o
/home/tamburello/RT/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_iwaplist’:
/home/tamburello/RT/os/linux/../../os/linux/sta_ioctl.c:592:1: warning: the frame size of 1280 bytes is larger than 1024 bytes
/home/tamburello/RT/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwmlme’:
/home/tamburello/RT/os/linux/../../os/linux/sta_ioctl.c:1962:1: warning: the frame size of 1696 bytes is larger than 1024 bytes
/home/tamburello/RT/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlMAC’:
/home/tamburello/RT/os/linux/../../os/linux/sta_ioctl.c:5835:1: warning: the frame size of 1360 bytes is larger than 1024 bytes
/home/tamburello/RT/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlE2PROM’:
/home/tamburello/RT/os/linux/../../os/linux/sta_ioctl.c:6034:1: warning: the frame size of 1376 bytes is larger than 1024 bytes
  CC [M]  /home/tamburello/RT/os/linux/../../os/linux/rt_linux.o
/home/tamburello/RT/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:
/home/tamburello/RT/os/linux/../../os/linux/rt_linux.c:636:23: warning: assignment makes integer from pointer without a cast
/home/tamburello/RT/os/linux/../../os/linux/rt_linux.c: In function ‘update_os_packet_info’:
/home/tamburello/RT/os/linux/../../os/linux/rt_linux.c:658:15: warning: assignment makes integer from pointer without a cast
/home/tamburello/RT/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:
/home/tamburello/RT/os/linux/../../os/linux/rt_linux.c:679:15: warning: assignment makes integer from pointer without a cast
/home/tamburello/RT/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevDetach’:
/home/tamburello/RT/os/linux/../../os/linux/rt_linux.c:1701:38: warning: initialization discards qualifiers from pointer target type
/home/tamburello/RT/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/tamburello/RT/os/linux/../../os/linux/rt_linux.c:1738:38: warning: initialization discards qualifiers from pointer target type
  CC [M]  /home/tamburello/RT/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /home/tamburello/RT/os/linux/../../common/ba_action.o
/home/tamburello/RT/os/linux/../../common/ba_action.c: In function ‘convert_reordering_packet_to_preAMSDU_or_802_3_packet’:
/home/tamburello/RT/os/linux/../../common/ba_action.c:1568:2: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/tamburello/RT/os/linux/../../common/cmm_mac_pci.o
  CC [M]  /home/tamburello/RT/os/linux/../../common/cmm_data_pci.o
  CC [M]  /home/tamburello/RT/os/linux/../../common/ee_prom.o
  CC [M]  /home/tamburello/RT/os/linux/../../common/ee_efuse.o
  CC [M]  /home/tamburello/RT/os/linux/../../common/rtmp_mcu.o
/home/tamburello/RT/os/linux/../../common/rtmp_mcu.c: In function ‘RtmpAsicSendCommandToMcu’:
/home/tamburello/RT/os/linux/../../common/rtmp_mcu.c:463:4: warning: passing argument 3 of ‘pci_read_config_word’ from incompatible pointer type
include/linux/pci.h:736:19: note: expected ‘u16 *’ but argument is of type ‘INT *’
/home/tamburello/RT/os/linux/../../common/rtmp_mcu.c:482:4: warning: passing argument 3 of ‘pci_read_config_word’ from incompatible pointer type
include/linux/pci.h:736:19: note: expected ‘u16 *’ but argument is of type ‘INT *’
  CC [M]  /home/tamburello/RT/os/linux/../../common/rt_rf.o
  CC [M]  /home/tamburello/RT/os/linux/../../chips/rt30xx.o
  CC [M]  /home/tamburello/RT/os/linux/../../chips/rt3090.o
  CC [M]  /home/tamburello/RT/os/linux/../../chips/rt33xx.o
  CC [M]  /home/tamburello/RT/os/linux/../../chips/rt3390.o
  CC [M]  /home/tamburello/RT/os/linux/../../chips/rt5390.o
  CC [M]  /home/tamburello/RT/os/linux/../../os/linux/rt_pci_rbus.o
  CC [M]  /home/tamburello/RT/os/linux/../../os/linux/rt_rbus_pci_util.o
  CC [M]  /home/tamburello/RT/os/linux/../../os/linux/pci_main_dev.o
/home/tamburello/RT/os/linux/../../os/linux/pci_main_dev.c: In function ‘rt2860_probe’:
/home/tamburello/RT/os/linux/../../os/linux/pci_main_dev.c:305:13: warning: assignment discards qualifiers from pointer target type
  CC [M]  /home/tamburello/RT/os/linux/../../common/rt_ate.o
/home/tamburello/RT/os/linux/../../common/rt_ate.c: In function ‘DO_RACFG_CMD_IO_READ_BULK’:
/home/tamburello/RT/os/linux/../../common/rt_ate.c:454:44: warning: cast to pointer from integer of different size
/home/tamburello/RT/os/linux/../../common/rt_ate.c: In function ‘ATETxPwrHandler’:
/home/tamburello/RT/os/linux/../../common/rt_ate.c:1802:45: warning: unused variable ‘CfgOfTxPwrCtrlOverMAC’
/home/tamburello/RT/os/linux/../../common/rt_ate.c: In function ‘ATEAsicSwitchChannel’:
/home/tamburello/RT/os/linux/../../common/rt_ate.c:5076:15: warning: comparison of distinct pointer types lacks a cast
/home/tamburello/RT/os/linux/../../common/rt_ate.c:5230:16: warning: comparison of distinct pointer types lacks a cast
/home/tamburello/RT/os/linux/../../common/rt_ate.c:5007:21: warning: unused variable ‘RFValue2’
/home/tamburello/RT/os/linux/../../common/rt_ate.c:5002:16: warning: unused variable ‘RFRegTable’
/home/tamburello/RT/os/linux/../../common/rt_ate.c:5001:43: warning: unused variable ‘R4’
/home/tamburello/RT/os/linux/../../common/rt_ate.c:5001:17: warning: unused variable ‘R3’
/home/tamburello/RT/os/linux/../../common/rt_ate.c:5001:9: warning: unused variable ‘R2’
/home/tamburello/RT/os/linux/../../common/rt_ate.c: In function ‘Set_ATE_TSSI_CALIBRATION_Proc’:
/home/tamburello/RT/os/linux/../../common/rt_ate.c:7564:5: warning: passing argument 3 of ‘eFuseWrite’ from incompatible pointer type
/home/tamburello/RT/include/rtmp.h:5889:10: note: expected ‘PUSHORT’ but argument is of type ‘UCHAR *’
/home/tamburello/RT/os/linux/../../common/rt_ate.c:7477:42: warning: unused variable ‘ChannelPower’
/home/tamburello/RT/os/linux/../../common/rt_ate.c:7649:5: warning: passing argument 3 of ‘eFuseWrite’ from incompatible pointer type
/home/tamburello/RT/include/rtmp.h:5889:10: note: expected ‘PUSHORT’ but argument is of type ‘UCHAR *’
/home/tamburello/RT/os/linux/../../common/rt_ate.c: In function ‘Set_ATE_READ_EXTERNAL_TSSI_Proc’:
/home/tamburello/RT/os/linux/../../common/rt_ate.c:8011:9: warning: passing argument 3 of ‘eFuseWrite’ from incompatible pointer type
/home/tamburello/RT/include/rtmp.h:5889:10: note: expected ‘PUSHORT’ but argument is of type ‘UCHAR *’
/home/tamburello/RT/os/linux/../../common/rt_ate.c:7965:18: warning: unused variable ‘EEPTemp’
/home/tamburello/RT/os/linux/../../common/rt_ate.c: In function ‘Set_ATE_TSSI_CALIBRATION_Proc’:
/home/tamburello/RT/os/linux/../../common/rt_ate.c:7477:9: warning: ‘BbpData’ may be used uninitialized in this function
/home/tamburello/RT/os/linux/../../common/rt_ate.c:7584:17: warning: ‘BbpData’ may be used uninitialized in this function
/home/tamburello/RT/os/linux/../../common/rt_ate.c: In function ‘RTATEGetTssiByChannel’:
/home/tamburello/RT/os/linux/../../common/rt_ate.c:7708:8: warning: ‘BbpData’ may be used uninitialized in this function
/home/tamburello/RT/os/linux/../../common/rt_ate.c: In function ‘Set_ATE_READ_EXTERNAL_TSSI_Proc’:
/home/tamburello/RT/os/linux/../../common/rt_ate.c:7964:28: warning: ‘BbpData’ may be used uninitialized in this function
  CC [M]  /home/tamburello/RT/os/linux/../../common/misc.o
  LD [M]  /home/tamburello/RT/os/linux/rt5390sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/tamburello/RT/os/linux/rt5390sta.mod.o
  LD [M]  /home/tamburello/RT/os/linux/rt5390sta.ko
make[1]: uscita dalla directory "/usr/src/linux-headers-2.6.38-8-generic"
tamburello@tamburello-HP-G62-Notebook-PC:~/RT$ sudo make install
make -C /home/tamburello/RT/os/linux -f Makefile.6 install
mkdir: impossibile creare la directory "/etc/Wireless": File già esistente
make[1]: ingresso nella directory "/home/tamburello/RT/os/linux"
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/tamburello/RT/RT2860STA.dat /etc/Wireless/RT2860STA/.
cp: impossibile eseguire stat di "/home/tamburello/RT/RT2860STA.dat": File o directory non esistente
make[1]: *** [install] Errore 1
make[1]: uscita dalla directory "/home/tamburello/RT/os/linux"
make: *** [install] Errore 2
tamburello@tamburello-HP-G62-Notebook-PC:~/RT$ 

```

---

### Post by ioaniro on 2011-04-14
> **palimmo said:**
> Very interesting.

But when I run the command 
*sudo make install*
I receive an error
[I]
/home/tamburello/RT/RT2860STA.dat": File or directory doesn't exist[/I]

:confused:



It worked for me but you just need to

cp RT2860STACard.dat ./RT2860STA.dat

At least that's what got me past that error and the card works fine now.

---

### Post by palimmo on 2011-04-14
Thank you...

Proceeding, I receive another error:
*bash: uname: File or directory doesn't exist*

argh!

---

### Post by palimmo on 2011-04-14
I solved it! 
Instead of
uname -r
I used my own kernel.

And it works!

In these days I'll check if the connection is steady!

One final doubt:
Do I have to follow this procedure everytime I install a new kernel... or not?


thank you!!

---

### Post by ioaniro on 2011-04-14
> **palimmo said:**
> Thank you...

Proceeding, I receive another error:
*bash: uname: File or directory doesn't exist*

argh!

Yes I forgot about that. You have to run uname -r command and then replace the output in the command mentioned in the original post. So the output goes as the directory instead of the <uname -r>

---

### Post by ioaniro on 2011-04-14
> **palimmo said:**
> I solved it! 
Instead of
uname -r
I used my own kernel.

And it works!

In these days I'll check if the connection is steady!

One final doubt:
Do I have to follow this procedure everytime I install a new kernel... or not?


thank you!!

Hehe, I just wrote that. no idea if we have to do this every time but would be nice to know so I can save the commands in a text file for later :-). But maybe in the next releases our card will be supported out of the box...

---

### Post by palimmo on 2011-04-14
> **ioaniro said:**
> Hehe, I just wrote that. no idea if we have to do this every time but would be nice to know so I can save the commands in a text file for later :-). But maybe in the next releases our card will be supported out of the box...

We hope so ;)

---

### Post by froseph on 2011-04-15
> **adamis said:**
> 
[PHP]sudo make
sudo make install
sudo mkdir -p /etc/Wireless/RT5390STA
sudo cp RT5390STA.dat /etc/Wireless/RT5390STA/RT5390STA.dat
sudo cp ./os/linux/rt5390sta.ko /lib/modules/<uname -r>/kernel/drivers/net/wireless/rt5390sta.ko[/PHP]

Note that for the last command above I used the option <uname -r>. This will copy the files to the current running kernel version. Make sure you are running the kernel that you wish to get the wireless running on...

.

If you use backticks instead of quotes, you will get the desired result, i.e.


[PHP]sudo cp ./os/linux/rt5390sta.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt5390sta.ko[/PHP]

Cheers,
froseph

---

### Post by palimmo on 2011-04-15
> **froseph said:**
> If you use backticks instead of quotes, you will get the desired result, i.e.


[PHP]sudo cp ./os/linux/rt5390sta.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt5390sta.ko[/PHP]

Cheers,
froseph

So... are you suggesting me to try with backtips?
Do you think I need to start with the procedure from the beginning or it's enough from 

*sudo cp ./os/linux/rt5390sta.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt5390sta.ko  *

?

Thanks in advance!

---

### Post by adamis on 2011-04-15
Thanks frospeh for catching the error, I edited my original post with the back ticks so people wouldn't continue to encounter the same error.

---

### Post by Redblade20XX on 2011-04-15
Hey everyone,

I've got the dm1z with the rt5390 chip. This might seem off topic but I would like to know if anyone has power management issues with the dm1z. I mean I've lost allot of battery power when I shutdown the computer and leave it for a day (about 10%) with any ubuntu variant. I think that the chip still draws power when the system is off because when I use the ethernet port (which lights on if used) and shut down the computer, the port is still active (the light is still on). Note this is all with just the battery plugged in. So if anyone can validate this, I would be thankful.

Thanks
-Red

---

### Post by palimmo on 2011-04-16
> **adamis said:**
> Thanks frospeh for catching the error, I edited my original post with the back ticks so people wouldn't continue to encounter the same error.

Will I need to run that command each time I install a new kernel?

Thank you!

---

### Post by albedoa on 2011-04-17
> **adamis said:**
> The instructions listed in the link from earlier posts I found have typos. Below are some corrected instructions that hopefully should get you on your way...

Registered to thank you. I was one of the people suffering from hard system freezes, and this fixed the problem!

---

### Post by adamis on 2011-04-18
To answer the question about new kernels, yes, you will have to do these commands each time your kernel gets updated. On the plus side, once you understand the procedures, it is much easier to do the second time.

Supposedly, the 2.6.39 kernel will have fully working drivers for this chip-set which will fix the issue permanently.

---

### Post by froseph on 2011-04-20
> **palimmo said:**
> Will I need to run that command each time I install a new kernel?

Thank you!

Until they fix the issue in the installed kernel, you'll need to run the command(s) every time. Each installed kernel version it's own directory for kernel modules (drivers).

froseph

---

### Post by i_grok on 2011-04-26
The power/battery issue mentioned by RedBlade is discussed further here:
[http://ubuntuforums.org/showthread.php?t=1729782](http://ubuntuforums.org/showthread.php?t=1729782)


Just to re-iterate, here is what I did to get wifi working on my 32-bit install:

[https://build.opensuse.org/package/binaries?package=rt5390sta&project=driver%3Awireless&repository=11.4-update](https://build.opensuse.org/package/binaries?package=rt5390sta&project=driver%3Awireless&repository=11.4-update)

You'll see 64-bit (x86_64) and 32-bit (i586) packages listed. Download the openSUSE driver package - the source RPM, not the binary package:
rt5390sta-2.4.0.4-6.2.src.rpm

Open your web browser's download directory and double-click the src RPM. Extract all files into a new directory named openSUSE_rt5390sta_driver

**Open a terminal and sudo to root:**
```
sudo su -
cd openSUSE_rt5390sta_driver
tar jxvf 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO.tar.bz2
cd 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/
patch -p0 < ../rt5390sta-2.4.0.4-config.patch
patch -p0 < ../rt5390sta-2.4.0.4-WPA-mixed.patch
patch -p0 < ../rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch
patch -p0 < ../rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch 
patch -p0 < ../rt5390sta-2.4.0.4-return_nonvoid_function.patch
patch -p0 < ../rt5390sta-2.4.0.4-reduce_debug_output.patch
mv RT2860STA.dat RT5390STA.dat
vi os/linux/config.mk
```

**Change HAS_ANTENNA_DIVERSITY_SUPPORT to:**
HAS_ANTENNA_DIVERSITY_SUPPORT=y

```
make
mkdir -p /etc/Wireless/RT5390STA
cp  RT5390STA.dat /etc/Wireless/RT5390STA/
cp -i os/linux/rt5390sta.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/
echo rt5390sta >> /etc/modules
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
depmod -a
```

---

### Post by red4our on 2011-04-29
Hi, just wanted to thank all the contributors to this thread (and especially i_grok's post) for all their help. After weeks of pfaffing around and trying various solutions, my machine is finally up and running with wireless - woohoo!!! Thanks again.

---

### Post by palimmo on 2011-04-30
> **adamis said:**
> The instructions listed in the link from earlier posts I found have typos. Below are some corrected instructions that hopefully should get you on your way... 

1. Download the file contained at this link: [http://barkmunchers.com/dm1z/RT.tar.gz](http://barkmunchers.com/dm1z/RT.tar.gz)

2. Extract the files to a directory. Then open a console, navigate to the directory that you extracted the files to then run the following commands:

[PHP]sudo make
sudo make install
sudo mkdir -p /etc/Wireless/RT5390STA
sudo cp RT5390STA.dat /etc/Wireless/RT5390STA/RT5390STA.dat
sudo cp ./os/linux/rt5390sta.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt5390sta.ko[/PHP]

Note that for the last command above I used the option <uname -r>. This will copy the files to the current running kernel version. Make sure you are running the kernel that you wish to get the wireless running on...

Now edit /etc/modules to add the line 'rt5390sta' at the end

Then run:

[PHP]sudo depmod -a
reboot[/PHP]

That should get you on your way. Hopefully that I didn't add in any typos myself.

**Edit** fixed the <uname -r> with `uname -r`, Thanks frospeh for catching the error!

Hi guys!

I thought I solved the problem with this solution but...sometimes  the connection goes down... in particular during skype video-chat... and this is very annoying.

Do you have any idea?

Thank you very much!

---

### Post by palimmo on 2011-05-05
> **palimmo said:**
> Hi guys!

I thought I solved the problem with this solution but...sometimes  the connection goes down... in particular during skype video-chat... and this is very annoying.

Do you have any idea?

Thank you very much!

Nothing? :(

---

### Post by adamis on 2011-05-07
Sorry, I don't seem to be having any issues like you are having. My wireless connection has been pretty stable. I am not even sure if the type of data being sent over the link will necessarily have an impact on your connection dropping or not. 

The only thing I could suggest is that you try these applications when you are right next to your wireless router and see if it's a reception problem. The lower the signal the laptop receives, the slower the data rate that the wifi will transmit at. For data intensive applications, this may cause the connectivity issues you are experiencing.

It's just a shot in the dark though...

---

### Post by ronthedon on 2011-05-12
> **adamis said:**
> The instructions listed in the link from earlier posts I found have typos. Below are some corrected instructions that hopefully should get you on your way... 

1. Download the file contained at this link: [http://barkmunchers.com/dm1z/RT.tar.gz](http://barkmunchers.com/dm1z/RT.tar.gz)

2. Extract the files to a directory. Then open a console, navigate to the directory that you extracted the files to then run the following commands:

[PHP]sudo make
sudo make install
sudo mkdir -p /etc/Wireless/RT5390STA
sudo cp RT5390STA.dat /etc/Wireless/RT5390STA/RT5390STA.dat
sudo cp ./os/linux/rt5390sta.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt5390sta.ko[/PHP]

Note that for the last command above I used the option <uname -r>. This will copy the files to the current running kernel version. Make sure you are running the kernel that you wish to get the wireless running on...

Now edit /etc/modules to add the line 'rt5390sta' at the end

Then run:

[PHP]sudo depmod -a
reboot[/PHP]

That should get you on your way. Hopefully that I didn't add in any typos myself.

**Edit** fixed the <uname -r> with `uname -r`, Thanks frospeh for catching the error!

One minor hiccup there bud! there is no need for the sudo make install, its fine without that. make install will just do the rest of the steps but instead do it with rt2860sta.dat. Rest is fine, I got my wifi working thanx to you! and downloading the kde-config-touchpad from synaptic for proper touchpad support! 

Cheers!

---

### Post by Praetor77 on 2011-07-21
I am on a dm1z Ralink 539f.

I tried 11.04 with 2.6.38, 39 and 3.0 kernels. Now I am on 10.10 32bits with 2.6.35 kernel,, and still the same problems.

I follow these instructiosn and everyhting seems to work. Then when I turn off my router and turn it on again, it jsut wont connect.

I had the hidden SSID proble, set it to broadcast SSID. I am trying to connect to a WPA2 router with no success at all, although I connected perfectly 10 mins ago.

---

### Post by devguy on 2011-07-22
The official Linux 3.0 kernel has been released.  According to the driver [changelog]("http://kernelnewbies.org/Linux_3.0_DriverArch#head-ad274d1f8464164f80c4ec951c7801905a248bb4"), the RT53xx wireless cards should be enabled by default.  However, the DM1z has a type RT5390f version that has not been enabled in the release candidates.  I gave up waiting and went back to Maverick with the patches, but can someone check if the stock 3.0 kernel has the wireless drivers enabled by default now?

---

### Post by juanfi on 2011-07-23
Hi to all,


I am still having problems. I have a dm1-3210us, with the 539f card as shown by lspci. I installed Ubuntu amd64 11.04, and the Ralink 2.4.0.4 driver with the openSUSE patches (including the amd64 gcc warning). Everything compiles nicely, but when mounting the rt5390sta module, it complains:

> [  361.038335] rt5390 0000:02:00.0: setting latency timer to 64
[  361.038840] <-- RTMPAllocAdapterBlock, Status=0
[  361.053800] KH: Use High Memory for Beacon
[  361.057618] <-- RTMPAllocTxRxRingMemory, Status=0
[  361.061947] ERROR!!! RTMPReadParametersHook failed, Status[=0x00000001]
[  361.077736] KH: Use High Memory for Beacon
[  361.081492] <-- RTMPAllocTxRxRingMemory, Status=0
[  361.092773] ERROR!!! RTMPReadParametersHook failed, Status[=0x00000001]

I get the wlan0 device, but it does not do anything. Trying iwlist wlan0 scanning does not return any network.

Any help would be appreciated!

Best,
Juan

---

### Post by wastedtime-fr on 2011-08-12
> **devguy said:**
> The official Linux 3.0 kernel has been released.  According to the driver [changelog]("http://kernelnewbies.org/Linux_3.0_DriverArch#head-ad274d1f8464164f80c4ec951c7801905a248bb4"),  the RT53xx wireless cards should be enabled by default.  However, the  DM1z has a type RT5390f version that has not been enabled in the release  candidates.  I gave up waiting and went back to Maverick with the  patches, but can someone check if the stock 3.0 kernel has the wireless  drivers enabled by default now?
Hello, I'm using this card on my HP DM1Z 3130 and I just had to add the correct pciid in the kernel sources. I checked and it is included in 3.0.1, not before.
This compile a module called rt2800pci which works just fine (and has been since kernel 2.6.39) for me.
in the file /usr/src/linux/drivers/net/wireless/rt2x00/rt2800pci.c , find the PCI_DEVICE(0x1814 , 0x5390) line and either duplicate it and change to 539f or change directly without duplicating.
Then, compile kernel (and activate experimental drivers for 5390 cards), and you're done.

---

### Post by adamis on 2011-08-28
Hi all, just wanted to let you know that the latest mainline kernel 3.1 rc3 (search for mainline kernel ppa) has the wireless working right out of the box. Kubuntu 11.10 alpha 3 on the otherhand has issues with it that causes the kdeinit4 to crash on startup. Note that Kubuntu 11.10 alpha 3 actually comes with kernel 3.0.0.9 I think. You would need to download the mainline kernel 3.1 from the mainline kernel ppa (google "mainline kernel ppa" to find it).

What I was finally able to figure out is that if you install the alpha release of Kubuntu 11.10 rc3, install the latest 3.1 mainline kernel, and then go into synaptic and select "Mark all Updates" and let it do it's thing. After all of the updating is done, reboot the system. This time, you shouldn't get a popup crash notification for kdeinit4 when you log in. However, you may get a crash notification in the system tray but you should be able to ignore it. 

Now, click on the network manager icon in the system tray. You may get a message along the lines of "We need NetworkManger verision...". Click on the wireless adapter just above the message and it should now show all of the access points available. Click on the one you want, enter your creditionals and you should be good to go.

It is nice to see that progress has been made in getting this open source driver into the kernel. I haven't tested the functionality much but I am writing this post from the connection. 

Cheers!

---

### Post by kateiacy on 2011-09-02
I just ran Ubuntu 11.10 Beta-1 desktop off a flash drive on my dm1z.  It immediately recognized the wireless card and connected to my network as soon as I entered the password.  Yippee!

---

### Post by nm_geo on 2011-09-02
> **kateiacy said:**
> I just ran Ubuntu 11.10 Beta-1 desktop off a flash drive on my dm1z.  It immediately recognized the wireless card and connect to my network as soon as I entered the password.  Yippee!

What kernel kateiacy?

---

### Post by kateiacy on 2011-09-03
The kernel in 11.10 beta-1 is 3.0.3.

---

### Post by bedorlan on 2011-09-04
Thanks! 
works perfectly with debian linux 3.0
hp pavilion dm1, amd vision e350

---

