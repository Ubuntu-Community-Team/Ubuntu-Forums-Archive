---
title: "accept incoming connections, dual wan?"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by thefix0r on 2011-01-06
Ok Im not interested in load balancing or failover, I just want my box to respond to traffic on both wans from the outside world. I assume this is a simple iptables configuration?

I can of course access services on both wan ports over the lan, but not from the internet, I can change gateways manually and it will respond on one gateway or the other, but not both at the same time as I would like.

Heres my setup and any suggestions would be great.


auto lo eth0 eth1 eth2

iface lo inet loopback  
iface eth1 inet static      <-------------wan 1 gw 10.10.1.1
    address 10.10.1.105
    netmask 255.0.0.0


iface eth2 inet static     <--------------wan 2 gw 172.16.0.1
    address 172.16.0.105
    netmask 255.255.255.0
    gateway 172.16.0.1

iface eth0 inet static
        address 192.168.5.1  <--------dhcp server for lan
        netmask 255.255.255.0
        broadcast 192.168.5.255
        
-----------------------------------------------------------------
root@ubuntu:~# ip route
192.168.5.0/24 dev eth0  proto kernel  scope link  src 192.168.5.1
172.16.0.0/24 dev eth2  proto kernel  scope link  src 172.16.0.105
10.0.0.0/8 dev eth1  proto kernel  scope link  src 10.10.1.105
default via 172.16.0.1 dev eth2  metric 100
------------------------------------------------------------------

root@ubuntu:~# iptables -L -v
Chain INPUT (policy ACCEPT 586K packets, 402M bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain FORWARD (policy ACCEPT 2289 packets, 216K bytes)
 pkts bytes target     prot opt in     out     source               destination
    1    60 ACCEPT     all  --  eth0   eth1    192.168.5.0/24       anywhere            ctstate N          EW
38406 7164K ACCEPT     all  --  any    any     anywhere             anywhere            ctstate R          ELATED,ESTABLISHED

Chain OUTPUT (policy ACCEPT 656K packets, 432M bytes)
 pkts bytes target     prot opt in     out     source               destination

---

### Post by thefix0r on 2011-01-06
primetime bump

---

### Post by thefix0r on 2011-01-06
showtime bump

---

