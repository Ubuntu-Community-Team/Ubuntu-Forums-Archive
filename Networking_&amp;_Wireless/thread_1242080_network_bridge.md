---
title: "network bridge"
date: 2009-08-16
forum: Networking &amp; Wireless
---

### Post by ForMar on 2009-08-16
OS: Ubuntu 8.10 Server PPC

I am attempting to turn the above computer in to a router. I am attempting the make a network bridge between its wlan which is running in ad-hoc and the eth. My problem is that from what I know bridges require that the ports (eth0) cannot have a ip address assigned to it. But i need eth0 to be dynamically assigned an ip from comcast since it is directly connect to the modem. Is there a way to do this using a bridge. Or do I need to use iptables? either way pointing me in the right direction would be much appreciated!

---

### Post by arthur.m on 2009-08-16
Hi, you need to enable netword forwarding.


echo 1 > /proc/sys/net/ipv4/ip_forward

regards,

Arthur

---

### Post by aesis05401 on 2009-08-16
You can dhclient the bridge itself, but this is not your only concern.  I saw another poster reference this link in another thread:[http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server]("http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server")

If the link is helpful pls post back with that info so I will know to recommend it to others ;)

---

