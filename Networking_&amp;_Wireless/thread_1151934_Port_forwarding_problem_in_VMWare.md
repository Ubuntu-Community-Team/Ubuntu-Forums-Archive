---
title: "Port forwarding problem in VMWare"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by Wobbert on 2009-05-07
Hi there.

I was wondering if anyone could help me with my port forwarding. I have a configuration that works on an old Redhat-machine but when I try to do the same thing in Ubuntu, running on VMWare it doesn't work.

I have eth0 as my external NIC and eth1 as internal and I'm doing something in the line of..

iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to 192.168.1.11:80
iptables -A INPUT -p tcp -i eth0 --destination 192.168.1.11 -m state --state NEW,ESTABLISHED,RELATED --dport 80 -j ACCEPT

..but it doesn't work.. The timeout is however significantly longer when I add these rules, like 15 seconds or so when I connect to this computer on port 80. Otherwise the connection seems to be refused.

iptables -L shows

Chain INPUT
ACCEPT   tcp -- anywhere       192.168.1.11    state NEW, RELATED,ESTABLISHED tcp dpt:www

Can anyone help me with this?

Kind regards.

/Wobbert

---

