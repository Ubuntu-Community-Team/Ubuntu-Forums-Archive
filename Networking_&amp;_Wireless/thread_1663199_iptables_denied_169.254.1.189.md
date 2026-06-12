---
title: "iptables denied: 169.254.1.189"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by linuxnewbieuser on 2011-01-09
greetings,

i'm using ubuntu version 9.04 and iptables version 1.4.1.1. My rules are working correctly,
although when i look in /var/log/syslog i see an iptables denied message from my ip (192.168.10.5) address to
a 169.254.1.189 address. I'm not really sure what is going on. Anyone else experience this ? Thanks.

---

### Post by dandnsmith on 2011-01-09
169.254.x.y is an odd address, commonly found when there is a need to assign an address automatically, but there is no proper DHCP server.

I only see these from Windows PCs, and have no idea where yours came from.
I don't think this address range is 'routable'.

---

