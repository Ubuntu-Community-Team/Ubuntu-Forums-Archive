---
title: "set up a 3.5g HSDPA connection share"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by cloudone on 2008-12-21
My Huawei USB modem is connected to the computer running Intrepid, and the 3.5g connection works perfectly. I want to create a share with the rest of my computers hooked to a wireless router.

I connected a LAN cable from my computer to the WAN port of the router, and tried to set up a network bridge. I edited /etc/network/interfaces as follows:
> auto lo
iface lo inet loopback

auto wmaster0
iface wmaster0 inet dhcp
prep-up iptables-restore < /etc/iptables.conf

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
    address 192.168.0.110
    network 192.168.0.1
    netmask 255.255.255.0
    broadcast 192.168.0.255
ifconfig:
> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:b7:8b:4b:ef  
          inet6 addr: fe80::215:b7ff:fe8b:4bef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:35400 (35.4 KB)  TX bytes:468 (468.0 B)
          Memory:ffce0000-ffd00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1560 (1.5 KB)  TX bytes:1560 (1.5 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.240.154.202  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:3034 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2723 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3022354 (3.0 MB)  TX bytes:413962 (413.9 KB)

iwconfig:
> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:b7:8b:4b:ef  
          inet6 addr: fe80::215:b7ff:fe8b:4bef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:35400 (35.4 KB)  TX bytes:468 (468.0 B)
          Memory:ffce0000-ffd00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1560 (1.5 KB)  TX bytes:1560 (1.5 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.240.154.202  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:3034 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2723 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3022354 (3.0 MB)  TX bytes:413962 (413.9 KB)

I would like the wireless router to act as a DHCP server. But apparently this does not work.

Can any kind souls give me some guidance?

---

### Post by cloudone on 2008-12-21
bump.........

I tried sharing on Windows XP using ICS, and it worked. There's a display of Internet gateway on Connections.

How should I do that in Ubuntu?

---

