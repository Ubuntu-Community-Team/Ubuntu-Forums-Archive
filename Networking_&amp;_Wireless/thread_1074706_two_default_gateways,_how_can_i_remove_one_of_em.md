---
title: "two default gateways, how can i remove one of em?"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by malanco on 2009-02-19
hi guys, i installed ubuntu server, and also installed on it vmware server 2 , i have 2 nics, one wireless and one eth, let me explain a little bit what i want, i want the eth nic to be the bridge for the vm's to my internal network, and it is working fine, and i want my wlan to be my gateway to internet, i know you can only have one default gateway, but when i give a "netstat -rn" i get to defaults gateways, the same but in both nics, how can i remove the gateway from the eth nic?, thanks!!

root@Agustin:/etc/network# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.36.0    0.0.0.0         255.255.255.0   U         0 0          0 vmnet8
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
192.168.26.0    0.0.0.0         255.255.255.0   U         0 0          0 vmnet1
192.168.122.0   0.0.0.0         255.255.255.0   U         0 0          0 vnet0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG        0 0          0 wlan0
0.0.0.0         192.168.2.1     0.0.0.0         UG        0 0          0 eth0

---

