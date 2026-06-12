---
title: "VPN Bonding with only 1 IP"
date: 2012-07-14
forum: Networking &amp; Wireless
---

### Post by Zerokuhl on 2012-07-14
Hi guys,

i am trying to get VPN bonding to work, the problem i am facing at the moment is that my Server (at the data center) only got one IP.

While i can get VPN bonding to work (with several tunnels) over only one connection i am unable to force out the second tunnel over my second connection.

I tried the "local IP" command in my openvpn client settings but to no avail...

I guess i could just buy additional IP addresses for every client but this seems silly when i should be able to do the same with with netfilter & ip route (Chapter 11, [http://lartc.org/lartc.pdf]("http://lartc.org/lartc.pdf"))

eth0 = cable modem
ppp0 = 3G Modem (10.64.64.64 is my ppp0 Gateway)

iptables -A PREROUTING -i eth0 -t mangle -p udp --dport 1337 -j MARK --set-mark 1
echo 201 bonding.out >> /etc/iproute2/rt_tables
ip rule add fwmark 1 table bonding.out
/sbin/ip route add default via 10.64.64.64 dev ppp0 table bonding.out

I also tried to test if it is working by rerouting port 80 traffic to my 3G Modem but i cant get that to work either. So i guess i must be doing something wrong.

Ubuntu 11.10
3.0.0-12-generic

Thanks :)

---

