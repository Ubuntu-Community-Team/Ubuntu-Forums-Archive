---
title: "eth0 and tun 0. IPtables allow VPN"
date: 2013-03-18
forum: Networking &amp; Wireless
---

### Post by djevlen on 2013-03-18
HI

Im trying to make a firewall working with openvpn. there is only one interface eth0, but when openvpn connects it gets virtual interface tun0.
What im trying to achieve is that the computer must not connect to internet through eth0 unless vpn is up. If i block eth0 completely then i it doesnt work because tun0 also use eth0..And i cant figure out how to solve it..When you see the iptables rules you see right away that i have no idea of what im doing here, i#ve lost the track of it :(. pls help edit the rules so it works. Here is what i've been experimenting:

*filter
# Policy
:INPUT DROP
:OUTPUT DROP
# Allow local host
-A INPUT -i lo -j ACCEPT
-A OUTPUT -o lo -j ACCEPT
# LAN
#-A INPUT -s 192.168.1.0/24 -j ACCEPT
#-A OUTPUT -d 192.168.1.0/24 -j ACCEPT
# iface eth0
-A INPUT -i eth0 -j ACCEPT
-A OUTPUT -o eth0 -j ACCEPT
# iface tun0
-A INPUT -i tun0 -j ACCEPT
-A OUTPUT -o tun0 -j ACCEPT

# sikker noget lort :(
#-A INPUT -i tun0 -s 10.8.2.166 -p udp --sport 4672 -m state --state NEW,ESTABLISHED -j ACCEPT
#-A OUTPUT -o tun0 -d 10.8.2.166 -p udp --dport 4672 -m state --state NEW,ESTABLISHED -j ACCEPT
#-A INPUT -i tun0 -s 10.8.2.166 -p tcp --sport 49402 -m state --state NEW,ESTABLISHED -j ACCEPT
#-A OUTPUT -o tun0 -d 10.8.2.166 -p tcp --dport 49402 -m state --state NEW,ESTABLISHED -j ACCEPT
-A INPUT -i tun0 -j ACCEPT
-A OUTPUT -o tun0 -j ACCEPT


# OPENVPN
-A INPUT -s 10.8.2.166 -p udp --sport 4672 -m state --state NEW,ESTABLISHED -j ACCEPT
-A OUTPUT -d 10.8.2.166 -p udp --dport 4672 -m state --state NEW,ESTABLISHED -j ACCEPT
# TORRENT
-A INPUT -s 10.8.2.166 -p tcp --sport 49402 -m state --state NEW,ESTABLISHED -j ACCEPT
-A OUTPUT -d 10.8.2.166 -p tcp --dport 49402 -m state --state NEW,ESTABLISHED -j ACCEPT
COMMIT

---

