---
title: "Ubuntu blocks Windows."
date: 2013-05-26
forum: Networking &amp; Wireless
---

### Post by Teethdude on 2013-05-26
Hello UbuntuForums,
This is an odd error that I don't quite understand.
I can access wireless all around my home like normal, but my brother's windows 7 can't whenever my machine connects. But if I boot Windows 7 also, all machines work fine. Any ideas? Thankyou in advanced.

---

### Post by praseodym on 2013-05-26
Check the MAC-address filter in your router interface

---

### Post by Teethdude on 2013-05-26
well i checked the MAc Filtering. Everything looks ok, seeing i don't filter any MAC addresses. Here's a screenshot of what i have:[ATTACH=CONFIG]243053[/ATTACH]

---

### Post by prodigy_ on 2013-05-26
Is there any error message when Windows can't connect?

---

### Post by Teethdude on 2013-05-26
Sorry, i guess i should have worded it better. Windows will connect, but it will not have access to the internet or any network stuff. Windows claims everything is working fine, but nothing works.

---

### Post by praseodym on 2013-05-26
Is the firmware of the router up to date? Try also a router reset to default settings (see manual)

---

### Post by prodigy_ on 2013-05-26
Could be duplicate IP. Or something is wrong with IP configuration. On the Windows machine open command prompt and run: ```
ipconfig /all
route print
tracert google.com
```

On the Linux machine (in terminal):```

ip addr show
ip route show
mtr -rc 1 google.com
```

Since both machines use the same router, their IP addresses (on wireless interfaces) normally should be on the same subnet but still different (e.g. 192.168.1.2 and 192.168.1.3). Other IP parameters (netmask, default gateway) should be the same.

P.S. BTW, are you sure you haven't installed a DHCP server (perhaps accidentally) in Ubuntu? Unlikely, but still possible. Use ```
netstat -atun | grep ':68[\t ]'
``` command to check.

---

### Post by Teethdude on 2013-05-26
Well, here are the results.
Ubuntu: 
```
 mike@mike-Compaq:~$ ip addr show1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether ac:16:2d:5d:a2:8c brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 08:ed:b9:25:e7:91 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.102/24 brd 192.168.1.255 scope global eth1
    inet6 fe80::aed:b9ff:fe25:e791/64 scope link 
       valid_lft forever preferred_lft forever
mike@mike-Compaq:~$ ip route show
default via 192.168.1.10 dev eth1  proto static 
169.254.0.0/16 dev eth1  scope link  metric 1000 
192.168.1.0/24 dev eth1  proto kernel  scope link  src 192.168.1.102  metric 9 
mike@mike-Compaq:~$ mtr -rc 1 google.com
HOST: mike-Compaq                 Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.1.10               0.0%     1    1.4   1.4   1.4   1.4   0.0
  2.|-- 192.168.0.1                0.0%     1    2.3   2.3   2.3   2.3   0.0
  3.|-- 192.168.0.1                0.0%     1    1.9   1.9   1.9   1.9   0.0
  4.|-- ???                       100.0     1    0.0   0.0   0.0   0.0   0.0
mike@mike-Compaq:~$ 

```
Windows:
[ATTACH]243066[/ATTACH]

Possible DHCP thing: 
```
mike@mike-Compaq:~$ netstat -atun | grep ':68[\t ]'udp        0      0 0.0.0.0:68              0.0.0.0:*                          
mike@mike-Compaq:~$ 

```

---

### Post by prodigy_ on 2013-05-26
> ```
Wireless LAN adapter Wireless Network Connection:
   Media State . . . . . . . . . . . : **Media disconnected**
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Broadcom 802.11n Network Adapter
   Physical Address. . . . . . . . . : 94-39-E5-35-A4-5F
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
```

Media disconnected means that the Wi-Fi connection isn't established at all. If you don't get any error when you're trying to connect yet the interface stays disconnected, it's very strange. I certainly haven't seen anything like that.

---

