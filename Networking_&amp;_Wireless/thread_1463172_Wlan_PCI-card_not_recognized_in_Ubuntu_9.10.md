---
title: "Wlan PCI-card not recognized in Ubuntu 9.10"
date: 2010-04-26
forum: Networking &amp; Wireless
---

### Post by mvanderlaen on 2010-04-26
Dear readers,

**I recently installed Ubuntu 9.10 on my computer. The computer was delivered with a pre-installed 54 Mbit WLAN PCI-card. Unfortunately Ubuntu only recognizes the 2 LAN-gates and not the WLAN PCI-card. What to do?**

After I installed Ubuntu 9.10, the computer did recognize the WLAN PCI-card and I was able to access Internet using the wireless connection. After I restarted the computer next day, the PCI-card did not show in the list of internet connections (accept for the two LAN-gates).

Together with the PC came a driver-CD (Planex, GW-DS54GR). This CD only contains Windows drivers, no Linux/Ubuntu. I’ve tried to install the Windows drivers using NDISWrapper but unfortunately no success on that either.

**Could any of you guys tell me how to make sure Ubuntu recognizes my WLAN PCI-card?**

This is the data I received while entering LSPCI in my Terminal-screen:
Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)


Many thanks!

Regards,
Michiel

---

### Post by chili555 on 2010-04-26
Does it come to life if you open a terminal and do:```
sudo modprobe rtl8180
```When you tried ndiswrapper, did you blacklist the native driver? If this makes the card appear make it permanent with:```
sudo su
echo rtl8180 >> /etc/modules
exit
```

---

