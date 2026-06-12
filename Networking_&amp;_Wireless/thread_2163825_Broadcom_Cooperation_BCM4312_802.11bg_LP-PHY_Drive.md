---
title: "Broadcom Cooperation BCM4312 802.11b/g LP-PHY Driver"
date: 2013-07-19
forum: Networking &amp; Wireless
---

### Post by Prestigue on 2013-07-19
I have a Broadcom Cooperation BCM4312 802.11b/g LP-PHY wireless driver. Is there anyway to get the installation package for this? 
Note: 
I DO NOT have internet or an ether cord for the ubuntu laptop. I am on my other laptop and am hoping that I can just transfer the program using my USB

---

### Post by praseodym on 2013-07-19
Hi,

download this package and save it in "Downloads":

[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz)

Install it via:
```
sudo tar xvf ~/Downloads/2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot.

---

