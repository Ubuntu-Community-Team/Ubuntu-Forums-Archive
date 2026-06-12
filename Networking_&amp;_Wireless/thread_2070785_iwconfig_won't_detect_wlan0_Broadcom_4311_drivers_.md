---
title: "iwconfig won't detect wlan0 Broadcom 4311 drivers installed"
date: 2012-10-13
forum: Networking &amp; Wireless
---

### Post by adfgvx on 2012-10-13
Hello,

I have a 32 bit Dell Vostro 1000 computer with a Broadcom 4311 wireless card (Ubuntu 12.04 installed), and iwconfig and ifconfig do not detect wlan0. I installed b43-fwcutter and firmware-b43-installer, activated the driver using Additional Drivers, and restarted the computer, but the computer still won't detect wlan0. The output of "rfkill list all" is:
```
0: dell-wifi: Wireless LAN
   Soft blocked: no
   Hard blocked: no
```
Does anyone have any suggestions?

Thank you.

---

### Post by chili555 on 2012-10-13
Please open a terminal and run and post:```
lspci -nn | grep 0280
lsmod | grep -e wl -e b43
dmesg | grep -e wl -e b43
```Thanks.

---

