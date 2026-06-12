---
title: "Problem with Internet connectivity"
date: 2011-06-20
forum: Networking &amp; Wireless
---

### Post by Vienen on 2011-06-20
Hello, I am new to UBUNTU. I installed the latest one alongside windows 7. I am having problem with the internet connectivity. i configured the static ip settings right i guess. Edited the Auto eth1 and assigned ipv4 settings manually and entered everything correctly.  

Address 192.168.xx.xx
Netmask 255.255.255.0
Gateway 192.168.xx.xxx
DNS Server xxx.xxx.xx.x, xxx.xxx.xx.x

Do i have to put MAC Address as well? Which is addressed as 'Network address' in Windows where i put this MAC. I have on board Realtek RTL8101E Family PCI-E Fast Ethernet NIC (NDIS 6.20) Network adapter. Do i have to install the driver?

---

### Post by Iowan on 2011-06-20
From a terminal (Applications>Accessories>Terminal) check and post (if possible/desired) results of **ifconfig -a** and **route -n**. These should show if the interface actually has the desired address - and if the gateway points to the proper place (presumably your router/modem).

---

### Post by Vienen on 2011-06-21
Its working now. :) The problem was with my older DNS. I changed it to Google Public DNS. But im posting the results of **ifconfig -a** and **route -n** anyway. Thanks.  

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

babu@babu-MS-7529:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1d:92:9c:05:c5  
          inet addr:192.168.xx.xx  Bcast:192.168.xx.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:92ff:fe9c:5c5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18606714 (18.6 MB)  TX bytes:1087834 (1.0 MB)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

babu@babu-MS-7529:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.xx.0    0.0.0.0         255.255.255.0   U     1      0         0 eth0
169.254.0.0      0.0.0.0         255.255.0.0      U     1000   0       0 eth0
0.0.0.0          192.168.xx.253   0.0.0.0          UG    0      0        0 eth0
babu@babu-MS-7529:~$ 

```

---

### Post by jazzplayermark on 2011-06-21
I'm new to ubuntu and having the same problem. Please post how you change your
'old dns'.
thanks

---

