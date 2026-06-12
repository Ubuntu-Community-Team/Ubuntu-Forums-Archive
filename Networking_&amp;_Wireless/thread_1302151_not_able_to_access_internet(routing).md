---
title: "not able to access internet(routing)"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by anupindi007 on 2009-10-26
Hi,
I am not able to access  Internet from pc through server but able to access internet form server.

Not able to ping from PC to  dns server(10.10.10.1)/www.google.com/ 72.14.213.105) but able to do so from server(192.168.80.1 eth1).  

   #netstat -rn
Kernel IP routing table
Destination         Gateway      -           Genmask                 Flags   MSS Window  irtt Iface
(192.168.80.0 )   - (0.0     0.0.0.0)  -                255.255.255.0    U              0 0          0 eth1
(10.10.10.0)              - (0.0.0.0)                   - 255.255.255.0    U              0 0          0 eth0
(169.254.0.0)        - (0.0.0.0)                    - 255.255.0.0           U              0 0          0 eth0
(0.0.0.0)                                - (10.10.10.1)           -  0.0.0.0                 UG            0 0          0 eth0

#cat /etc/resolv.conf 
nameserver 10.10.10.1


#cat /etc/network/interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.80.1
netmask 255.255.255.0


#cat /etc/dhcp3/dhcpd.conf
subnet 192.168.80.0 netmask 255.255.255.0{
range 192.168.80.2 192.168.80.99;
default-lease-time 86400;
option routers 192.168.80.1;
option domain-name-servers 10.10.10.1;
max-lease-time 60480;
}

#cat /etc/default/dhcp3-server 
INTERFACES="eth1"

---

### Post by Iowan on 2009-10-26
What is the next upstream machine - 10.10.10.1? 
I suspect that should also in be the "option routers" line.
(I've been wrong before...)

---

### Post by anupindi007 on 2009-10-27
> **Iowan said:**
> What is the next upstream machine - 10.10.10.1? 
I suspect that should also in be the "option routers" line.
(I've been wrong before...)

Thanks for your reply and please find the requested info:

MyPC--->Router---> Server( internal ip =192.168.80.1 and external IP connected to)  ---> 10.10.10.1 DNS server/router/firewall.)---> internet

- From Server I am able to browse internet.
- from MyPC to Server(internal ip) able to ping but not able to ping any external sites or DNS server.

---

