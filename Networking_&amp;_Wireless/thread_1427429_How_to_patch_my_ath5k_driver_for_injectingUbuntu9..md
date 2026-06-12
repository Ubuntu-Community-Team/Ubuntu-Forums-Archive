---
title: "How to patch my ath5k driver for injecting/Ubuntu9.10"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by u`F`o on 2010-03-11
So this is my first thread and I hope to get some help from the Ubuntu Community ;) 
```

Acer Aspire 5520G with AMD Turion 64 /x2

```I'm a linux newbie (I'm using it since 6th of March/2010) and I want to get an injecting-ready driver for my AR5007EG wi-fi card ```
AR2425 Chipset
```. So I installed something called "compat-wireless", then there was some script for driver selecting, and I selected ath5k and this is the result: 
```
root@ufo-laptop:/home/ufo/Downloads/compat-wireless-2010-03-10#
river-select ath5k
Processing new driver-select request...
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/wireless/Makefile.bk
Backup exists: drivers/net/wireless/ath/Makefile.bk
Backup exists: net/wireless/Makefile.bk
Backup exists: drivers/net/Makefile.bk
Backup exists: drivers/ssb/Makefile.bk
Backup exists: drivers/misc/eeprom/Makefile.bk
root@ufo-laptop:/home/ufo/Downloads/compat-wireless-2010-03-10#
```What does this (above) mean? Does this mean that I already got those Backups, or it means that now is doing those backups?  
As far as I know (which isn't much) this compat-wireless should enable madwifi drivers, or I'm wrong? 
I've tested some kind of injection test 
```
root@ufo-laptop:/home/ufo# aireplay-ng -9 -b 00:22:B0:A1:FC:00 mon0
20:49:04  Trying broadcast probe requests...
20:49:04  Injection is working!
20:49:06  Found 2 APs

20:49:06  Trying directed probe requests...
20:49:06  00:22:B0:A1:FC:00 - channel: 6 - 'uFo's net'
20:49:08  Ping (min/avg/max): 1.186ms/75.596ms/92.845ms Power: -33.20
20:49:08  30/30: 100%

20:49:08  00:22:B0:91:A6:57 - channel: 6 - 'NASKO-PC_Network'
20:49:12  Ping (min/avg/max): 64.716ms/110.849ms/138.627ms Power: -92.17
20:49:12  30/30: 100%

``````
05:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
        Subsystem: AMBIT Microsystem Corp. Device 0428
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at f0400000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint, MSI 00
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Virtual Channel <?>
        Kernel driver in use: ath5k
        Kernel modules: ath_pci, ath5k

```I read some threads here in the forum for ath5k driver patching, but all I understood was just to add this compat-wireless and it'll do the rest. I don't think injecting is really working, no matter what the injection test shows. Today I've tried to crack my WEP network, but for 2 hours I got only about 1 000 IVs which as you know is insufficient. Everywhere I read they said that a successful WEP crack isn't taking more than 10 minutes and they are getting about 20 000+ IVs in this short period of time, but I can't. What should be wrong? A friend of mine, told me, that I must patch my wi-fi driver to get this job done. 10x for the help in advance :smile:

P.S.: Sorry for my English, I hope you'll understand me...

---

### Post by Nickelrw87 on 2010-09-12
i have same issue - totally lost...so this is a bump kinda lmfao

---

### Post by u`F`o on 2010-09-12
I have no progress at all since March this year... so** Nickelrw87 **buddy... I hope that you don't expect any progress too with this issue :(

---

