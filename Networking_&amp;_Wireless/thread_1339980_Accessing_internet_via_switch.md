---
title: "Accessing internet via switch"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by nithinkk on 2009-11-28
Hi

I have direct internet connection(IP 192.168.0.207) in eth0(host machine). I have set up a static IP 10.1.2.1 in eth1 to share internet to other systems. eth1 is connected to a switch from which other machines are connected.

The command "route -n" in the main machine yields

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.183.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
10.2.1.0        192.168.0.207   255.255.255.0   UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
172.16.237.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eth1
0.0.0.0         192.168.0.200   0.0.0.0         UG    100    0        0 eth0

For the machine connected from the switch(client machine), I set up  a static IP(10.1.2.6) and added gateway as follows :
sudo route add default gw 10.1.2.1

I am able to access internet in the host machine but can't acces internet in client machines. Please help!!!

---

### Post by nithinkk on 2009-11-28
Ubuntu documentation helps..
I referred

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) 

and got my network ok!!! :)

---

### Post by Iowan on 2009-11-28
Is problem [SOLVED]?
(Thread Tools) :p

---

