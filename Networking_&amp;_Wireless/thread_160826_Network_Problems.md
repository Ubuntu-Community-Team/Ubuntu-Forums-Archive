---
title: "Network Problems"
date: 2006-04-15
forum: Networking &amp; Wireless
---

### Post by ra008 on 2006-04-15
Hi, I have a USB ADSl modem (nas0)( Speedtouch 330), The modem is working. I also have a networkcard eth0(100.100.100.1) that is connected to my other computer. The problem is I tried to share my internet connection with this script. But after that I can use the internet in the computert 1 and share files with computer 2  but computer 2 can only share files with computer 1. I can do ping [www.anything.anything](www.anything.anything) in computer 2 but I can open ONLY [www.google.com](www.google.com) all the other websites will start to load then stop some times the title will show. Please Help me!

#!/bin/bash

IPT='/sbin/iptables'
NET_IFACE='ppp0'
LAN_IFACE='eth0'
LAN_RANGE='100.100.100.0/24'

/sbin/modprobe ip_conntrack
/sbin/modprobe ipt_MASQUERADE
/sbin/modprobe ipt_LOG
/sbin/modprobe iptable_nat

echo 1 > /proc/sys/net/ipv4/ip_forward

echo 1 > /proc/sys/net/ipv4/ip_dynaddr



$IPT -F
$IPT -Z
$IPT -t nat -F
$IPT -t filter -P FORWARD DROP

$IPT -t filter -A INPUT -i lo -s 0/0 -d 0/0 -j ACCEPT
$IPT -t filter -A OUTPUT -o lo -s 0/0 -d 0/0 -j ACCEPT

$IPT -t filter -A INPUT -i $LAN_IFACE -m state --state NEW -j ACCEPT
$IPT -t filter -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

$IPT -t filter -A FORWARD -d 0/0 -s $LAN_RANGE -o $NET_IFACE -j ACCEPT
$IPT -t filter -A FORWARD -d $LAN_RANGE -s 0/0 -i $NET_IFACE -j ACCEPT
$IPT -t nat -A POSTROUTING -o $NET_IFACE -j MASQUERADE
$IPT -t filter -A INPUT -s $LAN_RANGE -d 0/0 -j ACCEPT
$IPT -t filter -A OUTPUT -s $LAN_RANGE -d 0/0 -j ACCEPT
$IPT -t filter -A OUTPUT -p icmp -s $LAN_RANGE -d 0/0 -j ACCEPT

---

