---
title: "NFS DHCP fails to boot liveCD on multiple NIC"
date: 2012-07-24
forum: Networking &amp; Wireless
---

### Post by klqn on 2012-07-24
I setup a PXE boot server for a diskless PC (clients) to boot via PXE server, it works when a PC with 1 NIC.  However, when a PC with multiple NICs installed and one port connected to the switch and the other NICs are NOT connected, I got the following error during PXE boot:

IP-Config:eth0 hardware addresss 00:01:02:03:04:05 mtu 1500 DHCP RARP
IP-Config:eth1 hardware addresss 00:01:02:03:04:06 mtu 1500 DHCP RARP

these errors repeat every 5 seconds and never boot.  However, when I connect all the NICs cable to the switch - everything working OK.  Do anyone have a solution for this?  I have been reading and searching for this issue and I found the following info:
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/182940](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/182940)

---

