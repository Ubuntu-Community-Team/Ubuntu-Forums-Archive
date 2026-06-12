---
title: "Monitor mode not supported"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by cisco2009 on 2009-02-10
Hi

I have a question about my Broadcom Corporation BCM4310 USB Controller. Last week i have tried a lot op times to connect the wireless internet. After two days it works very good. I have done this with ndiswrapper.
Only one thing not , when i am working in shel hi give me the next error "MONITOR MODE NOT SUPPORTED" Can somebody tell me how it comes ?

I want to connect the wireless internet without ndiswrapper is that possible ?

Excuses for my bad language control

in advance thanks

---

### Post by kevdog on 2009-02-10
ndiswrapper does not support monitor mode as you well know.  I know for a fact that the b43 does not support the USB 4310.  I'm not sure if the Broadcom STA (wl) driver supports 4310, however wl can not do Monitor Mode either.  

I think you may be out of luck with this chipset.  Ayuthia may be able to give you the definitive answer, but I think you are in a pickle!

---

### Post by Ayuthia on 2009-02-10
The 4310 card is actually the 4312 card (14e4:4315 chipset) which can only use the wl module or ndiswrapper.  Sorry.

For the Broadcom modules monitor modes work with only b43 with the proprietary firmware or open-source (WPA only. WEP is not supported yet).

---

### Post by cisco2009 on 2009-02-11
octl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead. Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either


Do you know what this means ?

---

