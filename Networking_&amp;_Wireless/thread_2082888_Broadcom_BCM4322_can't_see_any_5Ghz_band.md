---
title: "Broadcom BCM4322 can't see any 5Ghz band"
date: 2012-11-10
forum: Networking &amp; Wireless
---

### Post by cocoa117 on 2012-11-10
Hi, I have a HP TouchSmart TX2 laptop with have Broadcom BCM4322 wifi card. On this machine with Win7 I can use dual band 5Ghz wifi with my router. 

Now I am using STA driver from Broadcom at version 5.1. I installed using this method
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_STA_drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_STA_drivers)

Now, I can see the wifi card support 5Ghz band, with following command
sudo iwlist eth1 channel
eth1      20 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Channel:1

But in the network-manager-> wifi list -> I can't see my 5Ghz wifi network. 

Does anyone why and how this can be solved?

I know with Ubuntu 10.10, my 5Ghz wifi network worked fine.

---

### Post by cocoa117 on 2012-11-10
My bad, just realised my router's wifi channel was set to something not listed in the supported range. Now changed it to 44, the 5Ghz network showing in my network list. Yes!!!

---

