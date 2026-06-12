---
title: "squid server installation problem"
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by Ashishkhandelwal on 2010-01-28
I have installed squid proxy server at server side so that all PCs connected to the server will access internet through it.I have made changes in squid.conf file also.I have added these two lines:-
acl localnet src 192.168.0.167 192.168.0.0-192.168.0.250/255.255.255.0
http_access allow localnet
But all the PCs connected to LAN are not able to connect to internet.I am using correct gateway IP at all PCs.

I have created a script as per instructions given on internet.That script is as following:-

INTIF="eth1"
EXTIF="eth2"
EXTIP="192.168.0.167"
/sbin/depmod -a
/sbin/modprobe ip_tables
/sbin/modprobe ip_conntrack
/sbin/modprobe ip_conntrack_ftp
/sbin/modprobe ip_conntrack_irc
/sbin/modprobe iptable_nat
/sbin/modprobe ip_nat_ftp
echo "1" > /proc/sys/net/ipv4/ip_forward
echo "1" > /proc/sys/net/ipv4/ip_dynaddr
iptables -P INPUT ACCEPT
iptables -F INPUT 
iptables -P OUTPUT ACCEPT
iptables -F OUTPUT 
iptables -P FORWARD DROP
iptables -F FORWARD 
iptables -t nat -F
iptables -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
iptables -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE

Now when i am running this script at server side then all the PCs connected to LAN are able to access internet although squid service is stopped.But i only want all the PCs should access internet through SQUID so that i can track their record and manage them.What is the solution of my problem???What changes should i need to do.Is my problem related to firewall or iptables as i have no idea regarding them.Please solve my issue.

---

