---
title: "installation of RT8169 LAN card using driver cd"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by skumarisation on 2009-12-20
installed ubuntu on windows. LAN card (RT 8169) working fine with XP Pro. ubuntu not recognising this HW as in MAC addr field it is showing all 0's. I have driver cd for the card which is  having LINUX folder. Now pl suggest how to install it. please its urgent.
rgds
skumar:(

---

### Post by chili555 on 2009-12-20
I don't believe you need the drivers from the CD as the driver is already included in your Ubuntu install. Please open a terminal and do:```
sudo modprobe r8169
ifconfig
```Do you see an ethernet interface, *eth0*, perhaps? Can you now click on the Network Manager icon and connect?

---

