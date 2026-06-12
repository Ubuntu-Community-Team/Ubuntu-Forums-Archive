---
title: "Wired Interface Missing"
date: 2009-07-23
forum: Networking &amp; Wireless
---

### Post by mbender on 2009-07-23
Hey.  I just installed Ubuntu 9.04 from Wubi on a brand new Acer Aspire One netbook.  Everything works fine except the wired network interface is missing.  I did some searching and modified my /etc/network/interfaces file to include eth0/1 but that didn't work.  Here's the output for ifconfig (dmesg | grep eth returns nothing ):

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:2c:5e:94:a7  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2cff:fe5e:94a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:762 errors:0 dropped:0 overruns:0 frame:0
          TX packets:870 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:884995 (884.9 KB)  TX bytes:161705 (161.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-2C-5E-94-A7-34-61-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Here's what /etc/network/interfaces looks like:

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

Any ideas?

Mike

---

### Post by superprash2003 on 2009-07-24
post output of
1)sudo /etc/init.d/networking restart
2)lshw -C network

---

