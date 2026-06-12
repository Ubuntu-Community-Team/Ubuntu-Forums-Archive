---
title: "ubuntu Vlan`s"
date: 2011-04-27
forum: Networking &amp; Wireless
---

### Post by krlos7 on 2011-04-27
Hi all forum, I have one server with 2 network interface card eth0 and eth1. eth1 local network and eth0 internet. eth1 connect FastEthernet0/24 with switchport mode trunk. i have two pc1 FastEthernet0/10 vlan 10 and pc2 FastEthernet0/20 vlan 20. I want make ping only pc1 eth1 server and pc2 only ping eth1:1 server for example. I can't connect every pc to server--

How i can configure the server?

My Config 
/etc/network/interfaces server
auto eht1
iface eth1 inet static
address 10.10.10.10
netmask 255.255.255.0

auto eht1:1
iface eth1:1 inet static
address 10.10.20.20
netmask 255.255.255.0

Config /etc/network/interfaces pc1
auto eht0
iface eth0 inet static
address 10.10.10.11
netmask 255.255.255.0

Config /etc/network/interfaces pc2
auto eht0
iface eth0 inet static
address 10.10.20.21
netmask 255.255.255.0


Switch cisco 2950
Interface FastEthernet0/10
Swichport access vlan 10
Swichport mode access

Interface FastEthernet0/20
Swichport access vlan 20
Swichport mode access

Interface FastEthernet0/24
Swichport mode trunk

Thank`s in advance!

---

### Post by psusi on 2011-04-27
You have only configured two IP addresses on the interface, not set up vlans.  See:

[http://wiki.debian.org/NetworkConfiguration#Howto_use_vlan_.28dot1q.2C_802.1q.2C_trunk.29_.28Etch.2C_Lenny.29](http://wiki.debian.org/NetworkConfiguration#Howto_use_vlan_.28dot1q.2C_802.1q.2C_trunk.29_.28Etch.2C_Lenny.29)

---

### Post by krlos7 on 2011-05-02
> **psusi said:**
> You have only configured two IP addresses on the interface, not set up vlans.  See:

[http://wiki.debian.org/NetworkConfiguration#Howto_use_vlan_.28dot1q.2C_802.1q.2C_trunk.29_.28Etch.2C_Lenny.29](http://wiki.debian.org/NetworkConfiguration#Howto_use_vlan_.28dot1q.2C_802.1q.2C_trunk.29_.28Etch.2C_Lenny.29)

thaks Psusi, I can now make ping of all vlan, but how i wanted only vlan 10 with vlan10 of server vlan 20 with vlan20 server. Now i ping pc1 to vlan 10 and 20. pc2 vlan 10 and 20. My example is only pc 1 ping vlan10 and pc 2 only ping vlan20.

My Config 
/etc/network/interfaces server
auto vlan10
iface vlan10 inet static
address 10.10.10.10
netmask 255.255.255.0
mtu 1500
vlan_raw_device_eth1

auto vlan20
iface vlan20 inet static
address 10.10.20.20
netmask 255.255.255.0
mtu 1500
vlan_raw_device_eth1

Config /etc/network/interfaces pc1
auto eht0
iface eth0 inet static
address 10.10.10.11
netmask 255.255.255.0

Config /etc/network/interfaces pc2
auto eht0
iface eth0 inet static
address 10.10.20.21
netmask 255.255.255.0

thanks guys.

---

### Post by lz1dsb on 2011-05-02
> **krlos7 said:**
>  My example is only pc 1 ping vlan10 and pc 2 only ping vlan20.
Do mean that you want to be able only to have access from pc 1 to vlan10 and from pc 2 to vlan 20?
If this is the case you just need to remove the default gateway on both PCs and than they won't be able to access any foreign IP subnets...

---

### Post by krlos7 on 2011-05-03
> **lz1dsb said:**
> Do mean that you want to be able only to have access from pc 1 to vlan10 and from pc 2 to vlan 20?
If this is the case you just need to remove the default gateway on both PCs and than they won't be able to access any foreign IP subnets...

ok thanks lz1dsb its work!

---

### Post by lz1dsb on 2011-05-03
Cool! Happy networking :guitar:

---

