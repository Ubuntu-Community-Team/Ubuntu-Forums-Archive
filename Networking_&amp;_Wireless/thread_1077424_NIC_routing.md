---
title: "NIC routing"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by omax on 2009-02-22
Hi guys!

I have two different wireless NIC's in my setup, each assigned with an internal ip from DHCP.

Is there any way to route traffic through the different cards? Say bittorrent traffic (assigned to a small range of ports) on wlan0 and all other type of traffic on ath0.

Is this possible, perhaps with iptables? Or is there any bittorrent client that allows me to select interface.

AFAIK, the kernel will shuffle traffic through the card with the lowest metric. But how can I change that I want all the other traffic on another card?

Help much appreciated!
omax

---

### Post by omax on 2009-02-24
Bump.

Guys, this must be do-able. It'd be ridiculous if it wasn't. But I need some advice.

---

### Post by mpokrywka on 2009-02-24
As for bittorrent clients: rtorrent has command line parameter (-b a.b.c.d) or ~/.rtorrent.rc setting (bind = a.b.c.d)

Overall this is nontrivial config, so you have to know what you are doing:
[LIST=1]
[*]if both interfaces has addresses from same subnet you have to turn off **rp_filter** to make sure that packets received by "second" NIC won't be filtered (echo 0 > /proc/sys/net/ipv4/conf/wifi0/rp_filter)
[*]to send traffic through non-default route you will have to:
a) mark OUTPUT traffic - you can use source port,protocol,dest ip,port etc:
iptables -t mangle -A OUTPUT -p tcp --sport 6881:6999 -j MARK --set-mark 0xb
b) add routing table[1] with default route using "second" device[2] and add rule that will direct packets with appropriate fwmark to that table[3]:
[1] echo "10 backup-route" >> /etc/iproute2/rt_tables
[2] ip route add default dev wlan0 table backup-route
[3] ip rule add fwmark 0xb lookup backup-route pref 1000

when interface goes down or address changes, route may be deleted (ip route show table backup-route) - pt.[2] may need to be repeated
[/LIST]

---

### Post by omax on 2009-04-01
Thank you for your reply! Your input is highly appreciated.

But I was wondering, I'm changing my set of plans and I want the two networkcards to be connected to two different accesspoints, thus two different subnets and ISP's.

There really is not a lot of usable information about this around. Possible? Easy?

---

### Post by superprash2003 on 2009-04-01
[http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

---

