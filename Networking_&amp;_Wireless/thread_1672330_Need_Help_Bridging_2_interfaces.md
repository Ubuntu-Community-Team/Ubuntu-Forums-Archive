---
title: "Need Help Bridging 2 interfaces"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by sky5564 on 2011-01-20
so what i am trying to do is connect my xbox360 through one of my spare ethernet interfaces on my computer running ubuntu 10.10,

so far i did these steps below 

```
sudo ifconfig eth0 down
sudo ifconfig eth1 down
sudo brctl addbr bridge0
sudo brctl addif bridge0 eth0
sudo brctl addif bridge0 eth1
sudo ifconfig bridge0 192.168.2.100 netmask 255.255.255.0
sudo ifconfig eth0 192.168.2.50 netmask 255.255.255.0
sudo ifconfig eth1 192.168.2.102 netmask 255.255.255.0
sudo iptables -A FORWARD --in-interface eth1 --out-interface eth0 --source 192.168.2.0/255.255.255.0 -m state --state NEW -j ACCEPT
sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
```

this crates a bridge and bridges the 2 interfaces to the bridg0 but when i try to connect with my xbox360 it says it cant find the DNS server?

i tried doing it automatically but it wont get the setting automatically.

my router/gateway is at 192.168.2.254

---

