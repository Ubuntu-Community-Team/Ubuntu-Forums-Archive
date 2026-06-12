---
title: "NetworkManager Applet 0.7.0 shows duplicates of NICs"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by jahshuah on 2009-01-20
On my Ubuntu 8.10 install (all the latest patches/updates applied), my NM applet displays duplicates of the two NICs I have installed in my laptop.  I have one 10/100/1000 NIC and an Intel wireless card.  However, NM shows three of each interfaces when I click on it--a total of six interfaces.

How can I tell NM that I only have the two and to display them instead of duplicates.  Also, why would NM show duplicates of the network cards?

Thanks in advance for the help.

---

### Post by jakon on 2009-01-30
There seems to be a bug in network-manager, it is reported here: [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/286500/](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/286500/)
It's a strange issue, but otherwise harmless AFAICS.

---

