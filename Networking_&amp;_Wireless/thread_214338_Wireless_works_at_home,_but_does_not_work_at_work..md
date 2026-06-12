---
title: "Wireless works at home, but does not work at work."
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by Serenader on 2006-07-12
I have this weird problem with wireless on Dapper. I am using the bcm43xx driver for my Broadcom wireless card and I use wifi-radar to connect to the wireless. It connects fine at my home. But, at work it sees the network, but it can't get an ip address. Does anyone have a similar problem. I tried network-manager, nm-applet and gtkwifi and none of them work. Only wifi-radar works.

My /etc/network/interfaces file has the following lines

iface eth1 inet dhcp
wireless-essid apname
wireless-key s:0000000000
auto eth1

where apname is my home network name.

Any help would be really appreciated.

Thanks.

---

### Post by Serenader on 2006-07-12
Does anyone think that ndiswrapper is better than the new bcm43xx driver.](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

