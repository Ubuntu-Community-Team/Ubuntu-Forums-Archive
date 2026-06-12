---
title: "iproute2 / source port routing broken in Ubuntu 10.04?"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by TomaszC on 2010-09-12
I've been using source port routing on several Linux systems (i.e. Debian Lenny) without problems.

However, I can't get it to work with Ubuntu 10.04, despite using exactly the same setup as on Debian:


in /etc/iproute2/rt_tables:

1       http


ip route add default via 10.4.0.1 dev tun0 table http
ip rule add from all fwmark 1 table http 
iptables -t mangle -A OUTPUT -p tcp --sport 80 -j MARK --set-mark 1


With this setup, webserver queries would be answered over tun0 interface.

But not on Ubuntu 10.04. I see it doesn't even generate outgoing packages (as checked with tcpdump on all interfaces).

Is there anything changed/different on Ubuntu 10.04? Does anyone has it working?

---

