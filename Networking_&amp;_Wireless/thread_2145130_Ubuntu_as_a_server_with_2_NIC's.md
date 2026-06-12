---
title: "Ubuntu as a server with 2 NIC's"
date: 2013-05-14
forum: Networking &amp; Wireless
---

### Post by wossen on 2013-05-14
Hi there,
Appologies as I am a newbe, but I wanted to use ubuntu installed on my dell pc as a server for sharing files and internet connection. I also have a wiki installed on the server. I have 2 NICs for that purpose and I know the second one is not being recognized by the system! restarting the network wont work. One NIC was connected to the LAN and was working fine until I messed up a lot of things. I want to start fresh.
For now getting back the LAN I have would be of great help as I want printing and file sharing active.
I have edited a lot of files that I cant keep track. Is it hopeless?

here is my ifconfig -a file incase

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:19:66:e7:a0:a0  
          inet6 addr: fe80::219:66ff:fee7:a0a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10284 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1037548 (1.0 MB)  TX bytes:12595 (12.5 KB)
          Interrupt:42 Base address:0x2000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:91 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7857 (7.8 KB)  TX bytes:7857 (7.8 KB)


ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.182.120.15  P-t-P:192.168.50.12  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:18543 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15818 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:21420182 (21.4 MB)  TX bytes:1646333 (1.6 MB)

thanks in advance.

---

### Post by praseodym on 2013-05-14
Hi,

how do you connect? Via Router or pure modem? Please show:
```

uname -a
lspci -nnk | grep -iA2 net
cat /etc/udev/rules.d/70-persistent-net.rules
cat /etc/network/interfaces
cat /etc/resolf.conf
route -n
```

---

