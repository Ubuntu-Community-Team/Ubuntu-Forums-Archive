---
title: "wireless and wired connectivity problem"
date: 2011-05-21
forum: Networking &amp; Wireless
---

### Post by filister on 2011-05-21
I want to connect to a device with static IP address 192.168.0.1 with a wire and to the internet through my wireless router. My router IP address is 192.168.1.1. my netstat output is the following 
```
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0

```
I edited the /etc/network/interfaces  
```

auto eth0 wlan0

iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

iface wlan0 inet static
address 192.168.1.10
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

# auto lo
# iface lo inet loopback

```
and when I am trying to restart my network:
```
/etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                                                                       RTNETLINK answers: No such process
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
SIOCDELRT: No such process
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
postconf: fatal: open /etc/postfix/main.cf: No such file or directory

```
and my new routing table is:
```

Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0

```
and I must to disable the eth0 interface in order to gain access to the internet. 
I guess I must change the routing table. Any guesses?

---

