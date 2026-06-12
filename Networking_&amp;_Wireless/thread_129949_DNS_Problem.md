---
title: "DNS Problem?"
date: 2006-02-15
forum: Networking &amp; Wireless
---

### Post by ManDevil on 2006-02-15
Without changing anything on my headless ubuntu PC (which I connect to using FreeNX), it seems like it can't access my ISP's DNS servers or is being blocked.  It was working fine since I installed it months ago and after a reboot suddenly I couldn't access any webpages or RSS feeds etc.

It is connected to the internet via combined modem/router, which I also have not changed the configuration of for ages and DNS seems to be working fine on my other PC's.

Any idea's why it would suddenly stop working on my ubuntu box?

---

### Post by ManDevil on 2006-02-15
Also, set the router as the DNS server in network configuration, on all PC's.

---

### Post by mips on 2006-02-15
Post output of the following files/commands here:
cat /etc/network/interface
cat /etc/resolv.conf
ifconfig -a
route -n

What are your networks IP & DNS settings ?

---

