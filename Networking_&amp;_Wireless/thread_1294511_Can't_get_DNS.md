---
title: "Can't get DNS"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by mibadt on 2009-10-18
Hi,
My Mint 7 (Ubuntu 9.04 variant) fails to get DNS and thus can't browse, whereas the **same PC can easily browse in XP** (dual boot) under the same network configuration.

Network configuration: 

2 PCs (a: Dual boot Mint 7/XP;  b: Win 7) on a LAN together with a router (Edimax 6204WG) which also provides DHCP to LAN clients and a cable modem.

Mint PC (a) configuration:
 edited /etc/dhcp3/dhclient.conf to include the following DNS servers (all tested to be working):
***prepend domain-name-servers 192.115.106.31, 62.219.186.7, 194.90.1.5, 212.143.212.143, 127.0.0.1;***

I can **ping explicitly** from Mint box (e.g., ping 87.248.113.14 which happens to be Yahoo) but can't ping [www.yahoo.com](www.yahoo.com) (and others).  

Rebooting all elements (modem, router, Mint) didn't change anything.

As said I can browse from same PC under XP and second Win 7 PC.

Please advise!

Thanks

Michael Badt

---

### Post by coffeeaddict22 on 2009-10-18
There's a nice page on getting networking running [here.  ]("http://www.linuxjournal.com/content/troubleshooting-network-problems")
Post back if you need more help.

---

### Post by mibadt on 2009-10-18
Thanks,

I'll look at it.

---

