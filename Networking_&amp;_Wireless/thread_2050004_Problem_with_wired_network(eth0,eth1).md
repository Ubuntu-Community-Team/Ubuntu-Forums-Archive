---
title: "Problem with wired network(eth0,eth1)"
date: 2012-08-29
forum: Networking &amp; Wireless
---

### Post by ganga1234 on 2012-08-29
hi ,I dont use any other connection except this wired one...:)..Sometimes i am unable to use this wired connection (i thought eth1 may cause problem)....Here i put down my output..

code: ifconfig
[PHP]
Output:eth0   Link encap:Ethernet  HWaddr 00:0c:f1:5e:46:c3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Memory:c0200000-c0200fff 

eth1   
          Link encap:Ethernet  HWaddr 58:2c:80:13:92:63  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5a2c:80ff:fe13:9263/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:122833 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93435 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:144500933 (144.5 MB)  TX bytes:10378403 (10.3 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1986 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1986 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:325649 (325.6 KB)  TX bytes:325649 ([/PHP][PHP][/PHP]325.6 KB)
Code:Route
Output:
[PHP]         Kernel IP routing table
Destination     Gateway         Genmask       Flags   Metric   Ref    Use   Iface
192.168.1.0      *                   255.255.255.0   U       1          0        0    eth1
link-local         *                   255.255.0.0        U     1000      0        0     eth1
default               hi.link           0.0.0.0             UG    0           0        0     eth1
[/PHP]



How can I connect to eth0 instead of eth1?  plz help me....!

---

### Post by dandnsmith on 2012-08-30
At the moment, according to your post, eth1 is UP and has an IP address, while eth0 is UP but doesn't have an assigned IP address.
You should first concentrate your attention on the reason for no IP address.
What is wired to what?
Are you using DHCP (automatic address assignment)?

---

