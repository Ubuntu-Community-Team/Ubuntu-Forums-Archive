---
title: "Wireless not working under 12.04 / Lenovo B560 laptop"
date: 2012-10-12
forum: Networking &amp; Wireless
---

### Post by amssb on 2012-10-12
Hi, 

I cannot get the wireless working on my new  Lenovo B560 laptop with Ubuntu 12.04.

Fn+F5 doesn't do anything.

rfkill list all shows:
```
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```and lspci -nnk | grep -iA2 net shows:
```
03:00.0 Ethernet controller [0200]: Atheros Communications AR8131 Gigabit Ethernet [1969:1063] (rev c0)
    Subsystem: Lenovo Device [17aa:3956]
    Kernel driver in use: atl1c
--
04:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Lenovo Device [17aa:30a1]
    Kernel driver in use: ath9k
```Please help!
Thanks!

---

### Post by chili555 on 2012-10-12
How about this little switch?

---

### Post by amssb on 2012-10-13
> **chili555 said:**
> How about this little switch?
Wow! That was it! Thank you very much for your help!

---

