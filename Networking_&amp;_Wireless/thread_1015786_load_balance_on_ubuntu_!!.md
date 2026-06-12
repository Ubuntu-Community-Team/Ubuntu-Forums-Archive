---
title: "load balance on ubuntu !!"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by ismaeel.abuamsha on 2008-12-19
i'm using ubuntu 8.04 Gusty , i've installed freeradius 1.17 with chilli v1.0
my 
eth0 --> chillispot interface 
eth1 --> first dhcp router ( 172.30.0.1)
eth2--> second dchp router (172.30.1.1 )

1) I want to adjust chilli.iptables and interfaces file  to append load balance with eth1 and eth2 interfaces 

2) i've access points such as edmax which provide one mac address for all users on it. i want to make a simultanous use of the same mac address . i've adjust /raddb/sql.conf to append simultanous use but chilli can give one ip address for on user connect to the AP.

3) compare between chillispot and pppoe ? which best for wireless network and for internet cafe ? 

a lot of thanks .

my chilli.iptables firewall .
[COLOR="Red"]#
# Firewall script for ChilliSpot
# A Wireless LAN Access Point Controller
#
# Uses $EXTIF (eth0) as the external interface (Internet or intranet) and
# $INTIF (eth1) as the internal interface (access points).
#
#
# SUMMARY
# * All connections originating from chilli are allowed.
# * Only ssh is allowed in on external interface.
# * Nothing is allowed in on internal interface.
# * Forwarding is allowed to and from the external interface, but disallowed
#   to and from the internal interface.
# * NAT is enabled on the external interface.

IPTABLES="/sbin/iptables"
EXTIF="eth1"
# here i want to add EXTIF= "eth2" and adjust the rules .
INTIF="eth0"
[COLOR="SeaGreen"]# this added to /etc/network/interfaces
#ip route add default scope global nexthop via 172.30.0.1 dev #eth1 weight 1 \
#        nexthop via 172.30.1.1 dev eth2 weight 1
[/COLOR]
#Flush all rules
$IPTABLES -F 
$IPTABLES -F -t nat
$IPTABLES -F -t mangle

#Set default behaviour
$IPTABLES -P INPUT DROP
$IPTABLES -P FORWARD ACCEPT
$IPTABLES -P OUTPUT ACCEPT

#Allow related and established on all interfaces (input)
$IPTABLES -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

#Allow releated, established and ssh on $EXTIF. Reject everything else.
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 --syn -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -j REJECT

#Allow related and established from $INTIF. Drop everything else.
$IPTABLES -A INPUT -i $INTIF -j DROP

#Allow http and https on other interfaces (input).
#This is only needed if authentication server is on same server as chilli
$IPTABLES -A INPUT -p tcp -m tcp --dport 80 --syn -j ACCEPT
$IPTABLES -A INPUT -p tcp -m tcp --dport 443 --syn -j ACCEPT

#Allow 3990 on other interfaces (input).
$IPTABLES -A INPUT -p tcp -m tcp --dport 3990 --syn -j ACCEPT

#Allow ICMP echo on other interfaces (input).
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -j ACCEPT

#Allow everything on loopback interface.
$IPTABLES -A INPUT -i lo -j ACCEPT

# Drop everything to and from $INTIF (forward)
# This means that access points can only be managed from ChilliSpot
$IPTABLES -A FORWARD -i $INTIF -j DROP
$IPTABLES -A FORWARD -o $INTIF -j DROP

#Enable NAT on output device
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE[/COLOR]

---

