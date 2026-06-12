---
title: "Xbox ICS - NAT strict"
date: 2009-08-21
forum: Networking &amp; Wireless
---

### Post by brk3 on 2009-08-21
I've googled and googled, and read the same threads and guides to death, I just can't get this to work.

I've tried every combination of iptables commands and firestarter, and every time the xbox network test is reporting strict NAT.

I'll post my settings here and what I've tried, if someone could make a suggestion that would be great.

_Xbox settings:_
Static IP: 192.168.0.2
DNS: opendns servers
Gateway: 255.255.255.0

_Ubuntu settings:_
ppp0 is the interface to the internet - dhcp
eth0 is the nic connected to the xbox - static - 192.168.0.1

_iptables script:_
ifconfig eth0 192.168.0.1
echo "1" > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o ppp0 -s 192.168.0.0/24 -j MASQUERADE
iptables -t nat -A PREROUTING -i ppp0 -p tcp --dport 3074 -j DNAT --to-destination 192.168.0.2
iptables -t nat -A PREROUTING -i ppp0 -p udp -m multiport --dports 88,3074 -j DNAT --to-destination 192.168.0.2
iptables -A FORWARD -i wlan0 -d 192.168.0.2 -p tcp --dport 3074 -j ACCEPT
iptables -A FORWARD -i wlan0 -d 192.168.0.2 -p udp -m multiport --dports 88,3074 -j ACCEPT

_firestarter settings:_
As described in guides, sharing ppp0 to eth0, with rules added for the port forwarding.

I've also tried ipmasq, dnsmasq, and linux-igd.  Most of the methods get the 360 to connect to live, but like I said, the NAT is strict every time :confused:

Edit:
Im beginning to think this is because Im using a 3 broadband dongle, and they have the ports blocked on their end.  If anyone has any more info on this Id still love to hear it though.

Edit 2:
Got it working, turned out my 3 mobile internet had the ports blocked.  Changing the APN from Three Ireland to 3Internet worked,

---

