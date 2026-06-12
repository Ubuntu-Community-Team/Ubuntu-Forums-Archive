---
title: "Enabling multicast between two applications"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by ajwharton on 2009-07-21
I am using my desktop installation of 9.04 to test a server application stack from another development group. The applications are on one machine and talk to each other via multicast. Although this works on their target OS (RHEL), when I follow the same instructions -- "sudo route -n add -net 224.0.0.0 netmask 240.0.0.0 dev eth0" -- I still cannot get the applications to talk to each other.

I disabled the firewall (that is assuming that "ufw disable" actually disables iptables) and still nothing. There is very little available on the net, despite my considerable google-fu.

Help me Obi-Wan!

In case this was a loopback (lo) device issue, I enabled the same route on lo and on eth0.

[FONT=Courier New]ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:23:7d:e7:15:51  
          inet addr:172.19.167.54  Bcast:172.19.167.255  Mask:255.255.255.0
          inet6 addr: fe80::223:7dff:fee7:1551/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16015 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9554 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:7960147 (7.9 MB)  TX bytes:1817277 (1.8 MB)
          Memory:db300000-db320000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MULTICAST  MTU:16436  Metric:1
          RX packets:174 errors:0 dropped:0 overruns:0 frame:0
          TX packets:174 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7765 (7.7 KB)  TX bytes:7765 (7.7 KB)


route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.54.0     0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.12.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
172.19.167.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0
10.186.160.0    0.0.0.0         255.255.252.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
224.0.0.0       0.0.0.0         240.0.0.0       U     0      0        0 lo
224.0.0.0       0.0.0.0         240.0.0.0       U     0      0        0 eth0
0.0.0.0         172.19.167.1    0.0.0.0         UG    0      0        0 eth0[/FONT]

---

