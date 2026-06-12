---
title: "Problem with connetion sharing"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by alexshelkov on 2009-05-03
Hello.

I setup and install ubuntu server, and try share internet connection, but I have strange problem.

I have tow interfaces:
ppp0 (internet)
ath0 (wi-fi, work in master mode)

When computer connect by wi-fi to server it get ip setting by DHCP. I use iptable for sharing connetction. 

Some configs: 

This script start automatically: 
```
#!/bin/sh
IPT="/sbin/iptables"

# The network interface you will use
# WAN is the one connected to the internet
# LAN the one connected to your local network
WAN="ppp0"
LAN="ath0"
# First we need to clear up any existing firewall rules
# and chain which might have been created
$IPT -F
$IPT -F INPUT
$IPT -F OUTPUT
$IPT -F FORWARD
$IPT -F -t mangle
$IPT -F -t nat
$IPT -X

# Default policies: Drop any incoming packets
# accept the rest.
$IPT -P INPUT DROP
$IPT -P OUTPUT ACCEPT
$IPT -P FORWARD ACCEPT

# Masquerading will make machines from the LAN
# look like if they were the router
$IPT -t nat -A POSTROUTING -o $WAN -j MASQUERADE

# If you want to allow traffic to specific port to be
# forwarded to a machine from your LAN
# here we forward traffic to an HTTP server to machine 192.168.0.2
#$IPT -t nat -A PREROUTING -i $WAN -p tcp --dport 80 -j DNAT --to 192.168.0.2:80
#$IPT -A FORWARD -i $WAN -p tcp  --dport 80 -m state --state NEW -j ACCEPT
# For a whole range of port, use:
#$IPT -t nat -A PREROUTING -i $WAN -p tcp --dport 1200:1300 -j DNAT --to 192.168.0.2
#$IPT -A FORWARD -i $WAN -p tcp  --dport 1200:1300 -m state --state NEW -j ACCEPT

# Do not allow new or invalid connections to reach your internal network
$IPT -A FORWARD -i $WAN -m state --state NEW,INVALID -j DROP

# Accept any connections from the local machine
$IPT -A INPUT -i lo -j ACCEPT
# plus from your local network
$IPT -A INPUT -i $LAN -j ACCEPT

# Here we define a new chain which is going to handle
# packets we don't want to respond to
# limit the amount of logs to 10/min
$IPT -N Firewall
$IPT -A Firewall -m limit --limit 10/minute -j LOG --log-prefix "Firewall: "
$IPT -A Firewall -j DROP

# log those packets and inform the sender that the packet was rejected
$IPT -N Rejectwall
$IPT -A Rejectwall -m limit --limit 10/minute -j LOG --log-prefix "Rejectwall: "
$IPT -A Rejectwall -j REJECT
# use the following instead if you want to simulate that the host is not reachable
# for fun though
#$IPT -A Rejectwall -j REJECT  --reject-with icmp-host-unreachable

# here we create a chain to deal with unlegitimate packets
# and limit the number of alerts to 10/min
# packets will be drop without informing the sender
$IPT -N Badflags
$IPT -A Badflags -m limit --limit 10/minute -j LOG --log-prefix "Badflags: "
$IPT -A Badflags -j DROP

# A list of well known combination of Bad TCP flags
# we redirect those to the Badflags chain
# which is going to handle them (log and drop)
$IPT -A INPUT -p tcp --tcp-flags ACK,FIN FIN -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ACK,PSH PSH -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ACK,URG URG -j Badflags
$IPT -A INPUT -p tcp --tcp-flags FIN,RST FIN,RST -j Badflags
$IPT -A INPUT -p tcp --tcp-flags SYN,FIN SYN,FIN -j Badflags
$IPT -A INPUT -p tcp --tcp-flags SYN,RST SYN,RST -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ALL ALL -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ALL NONE -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ALL FIN,PSH,URG -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ALL SYN,FIN,PSH,URG -j Badflags
$IPT -A INPUT -p tcp --tcp-flags ALL SYN,RST,ACK,FIN,URG -j Badflags

# Accept certain icmp message, drop the others
# and log them through the Firewall chain
# 0 => echo reply
$IPT -A INPUT -p icmp --icmp-type 0 -j ACCEPT
# 3 => Destination Unreachable
$IPT -A INPUT -p icmp --icmp-type 3 -j ACCEPT
# 11 => Time Exceeded
$IPT -A INPUT -p icmp --icmp-type 11 -j ACCEPT
# 8 => Echo
# avoid ping flood
$IPT -A INPUT -p icmp --icmp-type 8 -m limit --limit 1/second -j ACCEPT
$IPT -A INPUT -p icmp -j Firewall

# Accept ssh connections from the Internet
# $IPT -A INPUT -i $WAN -p tcp --dport 22 -j ACCEPT
# or only accept from a certain ip
#$IPT -A INPUT -i $WAN -s 125.124.123.122 -p tcp --dport 22 -j ACCEPT

# Accept related and established connections
$IPT -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Drop netbios from the outside, no log, just drop
$IPT -A INPUT -p udp --sport 137 --dport 137 -j DROP

# Finally, anything which was not allowed yet
# is going to go through our Rejectwall rule
$IPT -A INPUT -j Rejectwall
```Here is interfaces config: 
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Onboard ethernet controller
# auto eth0
# iface eth0 inet static
#    address 192.168.1.1
#    netmask 255.255.0.0

# Wi-fi card setup
auto ath0
iface ath0 inet static
    hostapd -B /etc/hostapd/hostapd.conf
    address 192.168.0.3
    netmask 255.255.255.0
    madwifi-base wifi0
    madwifi-mode ap

# PPPoE connection 
auto eth0
iface eth0 inet manual

auto dsl-provider
iface dsl-provider inet ppp
    re-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
    pon dsl-provider

```And all work almost ideal except one thing: I can't get access to some site form remote computers(computers in local network).

Now I find 3 sites(maybe there is more):
mail.ru
microsoft.com
yahoo.com

When I try get access to them from **server**(w3m mail.ru or w3m microsoft.com) all works. But when I open browser and try open this site on **remote computer** (I have 3 and test at them all) they don't opens.

```

On remote:
Tracing route to yahoo.com [209.131.36.159]
over a maximum of 30 hops:

  1     3 ms     1 ms     1 ms  SFAM [192.168.0.3]
  2     2 ms     1 ms     1 ms  10.254.254.254
  3     6 ms     4 ms    56 ms  rt4.net208.omkc.ru [217.25.208.141]
  4     4 ms     2 ms     4 ms  rt5.omkc.ru [217.25.208.1]
  5     2 ms     2 ms     2 ms  rt1.omkc.ru [217.25.208.161]
  6     2 ms     2 ms     2 ms  ge0-1-168.ll-omk.zsttk.ru [81.1.224.33]
  7     3 ms     6 ms     1 ms  omk15.transtelecom.net [217.150.37.34]
  8   101 ms   102 ms   102 ms  lnn11-ge500.501.transtelecom.net [195.66.224.212]
  9   107 ms   107 ms   110 ms  ge-1-1-0.pat1.the.yahoo.com [195.66.224.129]
 10   180 ms   181 ms   181 ms  so-2-1-0-pat1.nyc.yahoo.com [66.196.65.13]
 11   182 ms   195 ms   181 ms  ge-3-0-0.pat2.nyc.yahoo.com [216.115.111.66]
 12   199 ms   193 ms   197 ms  so-6-1-0.pat1.che.yahoo.com [216.115.101.158]
 13   250 ms   250 ms   250 ms  as1.pat1.dnx.yahoo.com [216.115.96.34]
 14   248 ms     *      247 ms  as0.pat1.sjc.yahoo.com [216.115.101.149]
 15   295 ms   290 ms   248 ms  ae1-p170.msr2.sp1.yahoo.com [216.115.107.85]
 16   255 ms   244 ms   245 ms  te-9-1.bas-a1.sp1.yahoo.com [209.131.32.21]
 17   294 ms   246 ms   293 ms  b1.www.vip.sp1.yahoo.com [209.131.36.159]
``````

On remote:
Pinging yahoo.com [209.191.93.53] with 32 bytes of data:
Reply from 209.191.93.53: bytes=32 time=218ms TTL=54
Reply from 209.191.93.53: bytes=32 time=217ms TTL=54
Reply from 209.191.93.53: bytes=32 time=217ms TTL=54
Reply from 209.191.93.53: bytes=32 time=218ms TTL=54
```
All other site works (google.com, ununtu.com, skype.com, **developer.yahoo.com **etc) both from server and from remote.

I really don't know why it is heppend, but I am sure that problem in server config. Please help.

Ask additional info if needed.

---

