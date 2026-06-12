---
title: "Wireless not working in dual boot (except in Windows)"
date: 2011-10-11
forum: Networking &amp; Wireless
---

### Post by briandeyoung on 2011-10-11
**Re: wireless not working (dual boot Windows 7) It works in windows.** 			
 			 			 		   		 		 		Are you up for another connection problem?  I have an ASUS dual boot UbuntuStudio / Windows 7 that cannot connect wirelessly.

I tried to turn the power off like in the HP machine.  It didn't work.

Here is what I get:
jeikemeijer@ubuntustudioasus:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux ubuntustudioasus 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
jeikemeijer@ubuntustudioasus:~$ nm -tool
nm: 'a.out': No such file
jeikemeijer@ubuntustudioasus:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0083]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1305]
    Kernel driver in use: iwlagn
--
04:00.5 Ethernet controller [0200]: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller [197b:0250] (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1905]
    Kernel driver in use: jme
jeikemeijer@ubuntustudioasus:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:eek:ff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:ff
          
jeikemeijer@ubuntustudioasus:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
jeikemeijer@ubuntustudioasus:~$ sudo iwlist scan
[sudo] password for jeikemeijer: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

jeikemeijer@ubuntustudioasus:~$ lsmod | grep iwl
iwlagn                333716  0 
iwlcore               167502  1 iwlagn
mac80211              294370  2 iwlagn,iwlcore
cfg80211              178528  3 iwlagn,iwlcore,mac80211
jeikemeijer@ubuntustudioasus:~$ dmesg | egrep 'iwl|firm|wlan0'
[   12.730461] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   12.730465] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   12.730540] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.730551] iwlagn 0000:02:00.0: setting latency timer to 64
[   12.730592] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   12.751208] iwlagn 0000:02:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   12.751211] iwlagn 0000:02:00.0: Device SKU: 0X9
[   12.751213] iwlagn 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   12.751226] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   12.751306] iwlagn 0000:02:00.0: irq 46 for MSI/MSI-X
[   12.797418] iwlagn 0000:02:00.0: loaded firmware version 128.50.3.1 build 13488
[   12.803294] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   12.819153] elantech: assuming hardware version 2, firmware version 4.1.2
jeikemeijer@ubuntustudioasus:~$ 


Thanks again!

---

### Post by briandeyoung on 2011-10-19
Everything seems to be working now.  I had a friend work on it for a while.  Network manager was causing the problems.  Now Network manager works, and everything is logical after that.

Thanks!

I will post what was done when I better understand it.

---

