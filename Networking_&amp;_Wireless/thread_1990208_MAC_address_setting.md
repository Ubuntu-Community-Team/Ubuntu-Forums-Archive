---
title: "MAC address setting"
date: 2012-05-29
forum: Networking &amp; Wireless
---

### Post by rocking on 2012-05-29
Hi

My laptop's serial number and mac address has been erased from BIOS. I guess it happened after installing Broadcom STA Wireless Driver.

Now for connecting internet using LAN connection, I am using following commands everytime after boot-up.

sudo ifconfig eth0 down
sudo ifconfig eth0  hw ether AA:BB:CC:DD:EE:FF
sudo ifconfig eth0 up.

How to set mac address permanently in Ubuntu 10.04. ?

---

