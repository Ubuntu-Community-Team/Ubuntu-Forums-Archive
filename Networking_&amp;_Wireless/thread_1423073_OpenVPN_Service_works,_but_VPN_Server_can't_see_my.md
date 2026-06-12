---
title: "OpenVPN Service works, but VPN Server can't see my local network"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by joubertdj on 2010-03-06
Dear community,

I have set up my OpenVPN configuration in such a way that I can log in from remotely (via the Internet) to my local network. However, as I am very lazy (problem one), I only want users to use one set of certificates, but forcing them to log in with their own username and password that is on an LDAP server somewhere within my local network.

My problem (the real problem) is this, if the VPN service is running on the VPN-Server then I cannot "see" my local network for any LDAP queries from my VPN-Server... when I shutdown OpenLDAP and reconfigure my interfaces file, then obviously it works ... I narrowed my "problem", according to myself, down to the "routing table". My configuration is as follows:

internet - <eth1> VPN-Server <eth0> - local network - <eth0> LDAP-Server

my interfaces file is:

```

auto lo eth2 eth0 eth1 br0

 # Loopback device

 iface lo inet loopback 

 # Internet interface
 iface eth1 inet static
   address 10.50.82.5
   netmask 255.255.255.224
   broadcast 10.50.82.31
   gateway 10.50.82.1
   dns-nameservers 10.50.16.21 10.50.16.22
   pre-up echo 1 > /proc/sys/net/ipv4/ip_forward
   up /sbin/iptables -t nat -A POSTROUTING -o $IFACE -j MASQUERADE
   down /sbin/iptables -t nat -F
   post-down echo 0 > /proc/sys/net/ipv4/ip_forward
 
 # WAN interface
 iface eth0 inet static
   address 192.168.1.249
   netmask 255.255.255.0
   network 192.168.1.0
   broadcast 192.168.1.255
   post-up route add -net 192.168.1.0/24 gw 192.168.1.1


 # OpenVPN interface
 iface br0 inet manual
   up openvpn --mktun --dev tap0
   up ifconfig eth0 0.0.0.0 promisc up
   up ifconfig tap0 0.0.0.0 promisc up
   up brctl addbr br0
   up brctl setfd br0 0
   up brctl stp br0 off
   up brctl addif br0 eth0
   up brctl addif br0 tap0
   up ifconfig br0 192.168.1.249 netmask 255.255.255.0 up
   up route add -net 192.168.1.0/24 gw 192.168.1.1
   down ifconfig br0 down
   down brctl delif br0 tap0
   down brctl delif br0 eth0
   down brctl delbr br0
   down openvpn --rmtun --dev tap0
   down ifconfig eth0 192.168.1.249 netmask 255.255.255.0 broadcast 192.168.1.255 network 192.168.1.0
   down route add -net 192.168.1.0/24 gw 192.168.1.1


```

like i said, the VPN function works fine, but their has to be a user within my VPN-Server else I can't use my LDAP-Server, because I can't "see" my network ... from within my VPN-Server

Please help me, it will really make my frustration level a bit better ...

---

### Post by joubertdj on 2010-03-09
... I am bumping this topic as I did not even get a single hint ... anybody?

---

