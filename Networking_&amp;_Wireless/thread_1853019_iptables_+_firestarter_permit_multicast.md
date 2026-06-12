---
title: "iptables + firestarter permit multicast"
date: 2011-10-01
forum: Networking &amp; Wireless
---

### Post by voodoosound on 2011-10-01
Hi,
 im using natty and tried to stream RTP with VLC. 
if firestarter is aktivated, no multicast packet is sent, if i disable it it works properly.

i tried out some iptable rules without effort.
does anyone know which rules to add to get multicast streaming to work?

thanks
Ck

---

### Post by psrdotcom on 2011-10-01
I think, if you have any network filter, then VLC Multicast won't work ..

---

### Post by voodoosound on 2011-10-01
i cant believe this, 
because i use other multicast programs like ptpd2 having the same problem.

this would mean iptables/netfilter are not capable of handling multicast packets.

---

### Post by voodoosound on 2011-10-01
i found out!

possible soulution is:

sudo iptables -L INPUT
sudo iptables -R INPUT [position in list] -p all -s base-address.mcast.net/8 -j ACCEPT
sudo iptables -R INPUT [position in list] -p all -d base-address.mcast.net/8 -j ACCEPT

sudo iptables -L OUTPUT
sudo iptables -R OUTPUT [position in list] -p all -s base-address.mcast.net/8 -j ACCEPT
sudo iptables -R OUTPUT [position in list] -p all -d base-address.mcast.net/8 -j ACCEPT

now its working!

---

