---
title: "Squid transparent fail. Please help !!!"
date: 2011-02-28
forum: Networking &amp; Wireless
---

### Post by alex noria on 2011-02-28
Hi:
 
With manual proxy on the client browsers work well, but the transparent proxy fails :
 
eth0:1 INTERNET
eth0 LAN
 
# /etc/network/interfaces
 
auto lo
iface lo inet loopback
 
auto eth0
iface eth0 inet static
address 192.168.2.1
netmask 255.255.255.0
 
auto eth0:1
iface eth0:1 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254
dns-nameservers 192.168.1.254
 
# /etc/squid/squid.conf
 
http_port 192.168.2.1:8080 transparent
 
# /etc/init.d/iptables.cf
 
# myFilter 
 
echo 0 > /proc/sys/net/ipv4/ip_forward
 
iptables -F
iptables -X
iptables -Z
iptables -F -t nat
iptables -X -t nat
iptables -Z -t nat
iptables -F -t mangle
iptables -X -t mangle
iptables -Z -t mangle
iptables -F -t filter
iptables -X -t filter
iptables -Z -t filter
 
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -t nat -P PREROUTING ACCEPT
iptables -t nat -P POSTROUTING ACCEPT
 
iptables -A INPUT -i eth0 -j ACCEPT
iptables -t nat -A POSTROUTING -s 192.168.2.0/24 -o 192.168.1.100 -j MASQUERADE
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 8080
iptables -A FORWARD -i eth0 -j ACCEPT
iptables -A FORWARD -s 192.168.2.0/24 -p tcp --dport 80 -j ACCEPT
 
# Turn on IP Forwarding
 
echo 1 > /proc/sys/net/ipv4/ip_forward
 
Please help !!! I am now quite desperate to get this problem fixed. Appreciate all the help. Thanks
 
best regards

---

