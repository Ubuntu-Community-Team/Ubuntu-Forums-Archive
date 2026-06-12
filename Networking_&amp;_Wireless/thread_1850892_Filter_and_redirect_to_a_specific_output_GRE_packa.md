---
title: "Filter and redirect to a specific output GRE packages"
date: 2011-09-27
forum: Networking &amp; Wireless
---

### Post by ranieri85 on 2011-09-27
Hello,

I have a server that I use as firewall and VPN (pptpd) server. On it, I have two internet connection and one lan connection. One of internet connection has fixed ip address and support VPN connections. The other one, has some ports blocks and has dynamic ip address, it can't support vpn connection.

I'll call my internet connection that supports VPN as ITN_1, and my another connection that don't support as ITN_2... My LAN connection, I'll call it as LAN_1.

I'm facing the following problem... If I enable both internet connections on my server, users can't connect in the VPN, because for some reason, probably, the server is redirecting some packages to ITN_2 (that doesn't support VPN connections)...

My idea is let ITN_2 just to internet trafic for LAN_1, so users that are accessing websites, ftp, will use the ITN_2, and users that are trying to connection to my VPN will use ITN_1.

I'm trying to do this with the following iptables rules:

```

#!/bin/bash

echo 1 >  /proc/sys/net/ipv4/ip_forward

# flush all tables
iptables -t nat -F
iptables -t mangle -F
iptables -F

# delete all user defined chains
iptables -t nat -X
iptables -t mangle -X
iptables -X

# nat rules
iptables -t nat -P PREROUTING ACCEPT
iptables -t nat -P POSTROUTING ACCEPT
iptables -t nat -P OUTPUT ACCEPT

iptables -t nat -A POSTROUTING -s 172.16.0.0/255.255.0.0 ! -d 172.16.0.0/255.255.0.0 -o eth0 -j MASQUERADE
iptables -t nat -A POSTROUTING -s 172.16.0.0/255.255.0.0 ! -d 172.16.0.0/255.255.0.0 -o eth1 -j MASQUERADE

# filter rules
iptables -P INPUT DROP
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

iptables -t filter -A INPUT -p icmp -j ACCEPT
iptables -t filter -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A INPUT -m tcp -p tcp -s 172.16.0.0/255.255.0.0 -d 172.16.2.1 --dport 22 -j ACCEPT

# Allow PPTP traffic
iptables -t filter -A INPUT -p tcp -m tcp --dport 1723 -j ACCEPT
iptables -t filter -A INPUT -p gre -j ACCEPT

# Mark GRE (VPN) packages
iptables -t mangle -A PREROUTING -p gre -j MARK --set-mark 65

```To share the internet connection, I'm using the following script

```

#!/bin/bash
IP_VIRTUA=`ifconfig eth1 | grep "inet addr" | cut -d : -f2 | cut -d ' ' -f1 | tr ' ' '\r'`
MASK_VIRTUA=`ifconfig eth1 | grep "inet addr" | cut -d : -f4 | cut -d ' ' -f1 | tr ' ' '\r'`
GTW_VIRTUA=`whatmask ${IP_VIRTUA}/${MASK_VIRTUA} | grep "First" | cut -d : -f2 | cut -c2-`

IP_AJATO=`ifconfig eth0 | grep "inet addr" | cut -d : -f2 | cut -d ' ' -f1 | tr ' ' '\r'`
MASK_AJATO=`ifconfig eth0 | grep "inet addr" | cut -d : -f4 | cut -d ' ' -f1 | tr ' ' '\r'`
GTW_AJATO=`whatmask ${IP_AJATO}/${MASK_AJATO} | grep "First" | cut -d : -f2 | cut -c2-`

#Delete all default routes created by DHCP and network start
ip route show table main | grep ^default | while read LINE ; do
        ip route del default
done

#Create default route to ITN_2
ip route add default via ${GTW_VIRTUA}

# Redirect maked GRE packages to AJATO table
ip rule add fwmark 65 table AJATO

# Create route to AJATO table to redirect trafic to ITN_1 
ip route add default dev eth0 table AJATO

```After do this, LAN users can access internet using ITN_2 without problems, all trafic is going out to ITN_2, but VPN connections can't complete.

If I deactive ITN_2 and use only ITN_1, users can connect in VPN without problems.

Am I missing some rule or doing something wrong?

I really appreciate any help.

Thanks

---

