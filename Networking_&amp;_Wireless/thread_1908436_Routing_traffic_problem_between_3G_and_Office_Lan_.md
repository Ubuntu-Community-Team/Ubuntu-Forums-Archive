---
title: "Routing traffic problem between 3G and Office Lan Network"
date: 2012-01-13
forum: Networking &amp; Wireless
---

### Post by jao_madn on 2012-01-13
Hi, 

I would like to ask some networking solution regarding my work LAN and 3G usb network problem. I want to route my internet traffic to the 3G network and sometimes connect to some of my work network for ssh to configure some workstation or print something. Currently my problem is i can't connect to the office network if i used internet using the 3G network setting the default gateway 10.64.64.64, all internal LAN connection lost(ping, telnet ssh, ftp etc). Even if i set the default gateway to the LAN as long as 3G network is available or connected

Here are some of the steps i taken and unsuccesful:
1. Only 3G or LAN:
3G Only with internet connection
```
    Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 ppp0
0.0.0.0         10.64.64.64   0.0.0.0         UG        0 0          0 ppp0
```
LAN only with ping/office connection
```
    Kernel IP routing table
 Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
 192.168.173.0   0.0.0.0         255.255.255.0   U         0 0          0 eth0
 169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
 0.0.0.0         192.168.173.254   0.0.0.0         UG        0 0          0 eth0
```

2. Connected/plug 3G and LAN
 with internet no lan connection
```
    Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
192.168.173.0   0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         10.64.64.64   0.0.0.0         UG        0 0          0 ppp0
```
No internet no lan connection
```
    Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
192.168.173.0   0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.173.254   0.0.0.0         UG        0 0          0 eth0

with internet but NO LAN
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
 10.64.64.64     0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
 192.168.173.0   192.168.173.254         255.255.255.0   UG         0 0          0 eth0
192.168.173.0   0.0.0.0         255.255.255.0   U         0 0          0 eth0
 169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
 0.0.0.0         10.64.64.64   0.0.0.0         UG        0 0          0 ppp0

```


I laso Tried this furom [http://ubuntuforums.org/showthread.php?t=1313845](http://ubuntuforums.org/showthread.php?t=1313845) and doesn't work
```
route del default route del -net 192.168.173.0 netmask 255.255.255.0 dev eth0 route add -net 192.168.173.0 netmask 255.0.0.0 dev eth0 
or (route add -net 192.168.173.0 netmask 255.0.0.0 gw 192.168.173.254 eth0) route add default gw 10.10.10.64 dev ppp0
```

Does iptables also the culprit but using only the lan no usb 3G networks and no iptables configure, the LAN works

Im using Ubuntu 10.04

---

