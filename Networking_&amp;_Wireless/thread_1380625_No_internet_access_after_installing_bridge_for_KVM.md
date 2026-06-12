---
title: "No internet access after installing bridge for KVM"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by jimezam on 2010-01-13
I recently installed a bridge (br0) over eth0 to let the KVM virtual machines access directly the LAN.  They work just fine but now the server (host) cannot access Internet.

Checking I found that it has double gateways on the route table using both interfaces: eth0 and br0.  I think that is the problem, but I cannot find why it happens and where to fix it because this tables seems to be filled automatically at boot time.

This is my route table:

```
jimezam@ivy:~$ route 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 br0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 br0
```This is how I created the bridge:

```
jimezam@ivy:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0
```And this is my current interface information:

```
jimezam@ivy:~$ ifconfig
br0       Link encap:Ethernet  HWaddr 00:24:21:b6:12:11  
          inet addr:192.168.1.99  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:21ff:feb6:1211/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15410 (15.4 KB)  TX bytes:12655 (12.6 KB)

eth0      Link encap:Ethernet  HWaddr 00:24:21:b6:12:11  
          inet addr:192.168.1.99  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:21ff:feb6:1211/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18180 (18.1 KB)  TX bytes:14419 (14.4 KB)
 
```I think I need a way to remove the double 'default' entry (the eth0 one ?) on the routing table but I don´t know how.  I am running out ideas, I hope you could help me.

Thank you,

jimezam.

---

