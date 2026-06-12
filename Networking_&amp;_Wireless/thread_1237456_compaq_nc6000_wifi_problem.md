---
title: "compaq nc6000 wifi problem"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by racingbrett on 2009-08-11
Hi all

Im in need of some advice, iv just installed the latest version of ubuntu on a hp nc6000 and all is working great apart from my wifi, I dont trust the internal card much as although it was recognized it doesn't see the networks (i saw networks 3 times in 6 hours of trying) i managed to find a tutorial on getting it working with ndiswrapper but that didnt seem to do anything, i also tried the madwifi drivers and this was when the wifi would light up but in 6 hours i only saw networks maybe 3 times. Anyway iv given up on the internal wifi (i questioned its functionalism before with windows) and iv switched to a PCMCIA Dlink DWL-G650 this seems to work fine, i see the networks and i can connect up to my router however i cant get online, its like theres no internet on the router, which has been proved otherwise by connecting another device up and accessing the internet. From what i have read these cards should work out the box so im lost as to why i cant access the internet with it. Any advice or tips on what to do would be greatly appreciated.

Cheers Brett:guitar:

---

### Post by racingbrett on 2009-08-11
really nobody cares to answer? c'on guys I need wireless on this freakin' laptop
cheers

---

### Post by rustybronco on 2009-08-21
A hp/compaq NC6000 works perfect with 8.04 and 9.04. no problems with the internal wireless card.

Trust me, I have 5 of them...

is the bluetooth icon showing up on your panel? if it's not, wireless also will be off. the wireless only works when the bluetooth icon is showing.

if it isn't showing, push the wireless button... 

my wireless info...
```
*-network:0             
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wifi0
       version: 01
       serial: 00:11:85:1c:37:b6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.101 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
```

---

