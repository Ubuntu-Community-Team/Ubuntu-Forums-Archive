---
title: "pseudo bridge and proxy arp"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by lukaskinder on 2010-08-08
Hello
Im trying to to make pseudo bridge between virtual interface (here i_wlan0) and real interface (here wlan0)  to route all packets from i_wlan0 to wlan0 and vice versa without affecting all packets on ip level ( I based on [http://www.linux.com/learn/docs/ldp/418-Adv-Routing-HOWTO#LARTC.BRIDGING](http://www.linux.com/learn/docs/ldp/418-Adv-Routing-HOWTO#LARTC.BRIDGING) ).
[COLOR="Red"]Step by step what I do:[/COLOR]
1. Add two table to /etc/iproute2/rt_tables:
1 wlan0-to-i_wlan0
2 i_wlan0-to-wlan0

2. Next in terminal :
tunctl -t i_wlan0

ifconfig i_wlan0 0.0.0.0 promisc up
ifconfig wlan0 0.0.0.0 promisc up

echo 1 > /proc/sys/net/ipv4/conf/i_wlan0/proxy_arp
echo 1 > /proc/sys/net/ipv4/conf/wlan0/proxy_arp
echo 1 > /proc/sys/net/ipv4/ip_forward

ip route add table 1 to default dev i_wlan0
ip route add table 2 to default dev wlan0

ip rule add iif wlan0 pref 1 table 1
ip rule add iif i_wlan0 pref 2 table 2

[COLOR="red"]I'm checking if my pseudo bridge works.[/COLOR]

I don't know if mode "promisc" is necessary but pseudo bridge should works now. I turn on capturing on both interfaces:

tcpdump -nn -i wlan0
tcpdump -nn -i i_wlan0

Virtual interface i_wlan0 is connected through real bridge to virtual machine which is configured with ip address 10.125.11.1 (255.255.255.0). And I try from this virtual machine ping a host, e.g.:

ping 10.125.11.112

And I except that for both interfaces (wlan0 and i_wlan0) tcpdump shows something like that:

 13:30:32.862430 IP 10.125.11.1 > 10.125.11.112: ICMP echo request, id 2048, seq 1888, length 64

[COLOR="Red"]Unfortunately[/COLOR] only in interface i_wlan0 it looks similar. On interface wlan0 tcpdump shows:

13:25:49.702915 ARP, Request who-has 10.125.11.112 tell 0.0.0.0, length 28

[COLOR="red"]So proxy arp dont works for interface wlan0 ?? Is my thinking ok? [/COLOR]Please help. Why it is happening like that.

Ps. route command don't show anything
ip rule shows
# ip rule
0:	from all lookup local 
1:	from all iif i_wlan1 lookup wlan0-to-i_wlan0 
2:	from all iif i_wlan0 lookup i_wlan0-to-wlan0 
32766:	from all lookup main 
32767:	from all lookup default

---

