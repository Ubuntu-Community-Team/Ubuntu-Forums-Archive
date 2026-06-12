---
title: "Wrong primary interface"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by xinit on 2009-05-19
Hi all!

I'm experiencing something strange after upgrading from 8.10 to 9.04. I have the following /etc/network/interfaces:

auto lo
iface lo inet loopback

[FONT=Courier New]auto eth0
iface eth0 inet static
        address 82.xxx.xxx.106
        netmask 255.255.255.248
        network 82.xxx.xxx.104
        broadcast 82.xxx.xxx.111
        gateway 82.xxx.xxx.105

auto eth0:0
iface eth0:0 inet static
        address 82.xxx.xxx.107
        netmask 255.255.255.248

auto eth0:1
iface eth0:1 inet static
        address 82.xxx.xxx.108
        netmask 255.255.255.248[/FONT]

After booting, for some reason eth0:0 appears to be my primary interface:

# ip a s
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:22:64:f2:4c:8c brd ff:ff:ff:ff:ff:ff
    inet 82.xxx.xxx.107/29 brd 82.xxx.xxx.111 scope global eth0:0
    inet 82.xxx.xxx.106/29 brd 82.xxx.xxx.111 scope global secondary eth0
    inet 82.xxx.xxx.108/29 brd 82.xxx.xxx.111 scope global secondary eth0:1
    inet6 fe80::222:64ff:fef2:4c8c/64 scope link 
       valid_lft forever preferred_lft forever

ifconfig however seems to show something different:

#ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:22:64:f2:4c:8c  
          inet addr:82.xxx.xxx.106  Bcast:82.xxx.xxx.111  Mask:255.255.255.248
          inet6 addr: fe80::222:64ff:fef2:4c8c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2704656 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3981060 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:556802350 (556.8 MB)  TX bytes:4404958990 (4.4 GB)
          Interrupt:16 

eth0:0    Link encap:Ethernet  HWaddr 00:22:64:f2:4c:8c  
          inet addr:82.xxx.xxx.107  Bcast:82.xxx.xxx.111  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

eth0:1    Link encap:Ethernet  HWaddr 00:22:64:f2:4c:8c  
          inet addr:82.xxx.xxx.108  Bcast:82.xxx.xxx.111  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 


Outgoing traffic gets 82.xxx.xxx.107 as the source, since eth0 (and thus .106) are secondary. 

Does anyone know what's causing this?

---

