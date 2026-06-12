---
title: "ip address"
date: 2006-04-26
forum: Networking &amp; Wireless
---

### Post by utUtu on 2006-04-26
I noticed in my X/Ubuntu Dapper box, the ifconfig now display a different ip address from before, maybe around Fligth 6??.  It used to be the ip address is like my router's, i.e. 192.168.1.1xx.  Now I get something like 169.254.214.247.  Any idea where this came from?  

Also I looked at the gui Networking tools, and I see the old and the new one as assigned to eth0.

In Kubuntu Dapper, ifconfig and the gui tools show only the 192.168.1.1xx for eth0.

BTW, these 3 systems are in different partitions in the same box.

Appreciate any help.  Thanks.

---

### Post by kingmonkey on 2006-04-26
does anything not work?
doesnt matter if you have different partitions because you have one network card with one mac address. maybe your dapper is using static ip rather than dynamic.

---

### Post by utUtu on 2006-04-26
Thanks but  that's what I was trying to say - they used the same hardware, DHCP.  But anyway I figured it out.  At first I suspected my new toy XAMPP, but it turned out to be the ZeroConf.

---

