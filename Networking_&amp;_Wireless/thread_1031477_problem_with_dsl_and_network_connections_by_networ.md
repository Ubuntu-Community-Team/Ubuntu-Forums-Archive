---
title: "problem with dsl and network connections by networkmanager 0.7.0"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by saygin on 2009-01-05
I've been using ubuntu since edgy. Until Intrepid, I used to configure my pppoe settings with pppoeconf tool in terminal. After that, it used to connect to the internet automatically after boot and networking was working with samba. However, in Intrepid, I wanted to use networkmanager applet to handle my pppoe internet and network configurations. I added a DSL connection for internet and It self-created a network connection named "Ifupdown (eth0)". DLS connection can access to the internet when selected but can't access to (also can't see) any computers on network. On the other hand, Ifupdown can see and access to computers on network, it can't connect to the internet. I want to enable them both at the same time but they are made as radio buttons in the applet. Is there a way to enable them both or making a connection which supports both network and pppoe connections? waiting for your help...

---

### Post by saygin on 2009-01-07
nobody?

---

### Post by superprash2003 on 2009-01-07
post output of ifconfig from the terminal

---

### Post by saygin on 2009-01-07
this is with ifupdown (which network works)
> eth0      Link encap:Ethernet  HWaddr 00:1e:ec:3e:47:35  
          inet addr:192.168.4.114  Bcast:192.168.7.255  Mask:255.255.248.0
          inet6 addr: fec0::8:21e:ecff:fe3e:4735/64 Scope:Site
          inet6 addr: 2002:d4ae:fb7d:8:21e:ecff:fe3e:4735/64 Scope:Global
          inet6 addr: fe80::21e:ecff:fe3e:4735/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1799 errors:0 dropped:7270134114 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:162839 (162.8 KB)  TX bytes:10850 (10.8 KB)
          Interrupt:249 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:68:93:30:df  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-68-93-30-DF-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

and this is DSL which internet works but network doesn't

> eth0      Link encap:Ethernet  HWaddr 00:1e:ec:3e:47:35  
          inet6 addr: fec0::8:21e:ecff:fe3e:4735/64 Scope:Site
          inet6 addr: 2002:d4ae:fb7d:8:21e:ecff:fe3e:4735/64 Scope:Global
          inet6 addr: fe80::21e:ecff:fe3e:4735/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4032 errors:0 dropped:16919199085 overruns:0 frame:0
          TX packets:106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:380016 (380.0 KB)  TX bytes:17580 (17.5 KB)
          Interrupt:249 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:88.255.192.186  P-t-P:88.255.192.3  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1488  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:522 (522.0 B)  TX bytes:478 (478.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:68:93:30:df  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-68-93-30-DF-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by superprash2003 on 2009-01-08
which ubuntu version are you using?? try giving eth0 a static ip.. and then connect ppp0 and then try internet and network access

---

### Post by saygin on 2009-01-20
I'm using ubuntu 8.10. By the way I can't give eth0 a static IP because the network I use gives everybody different IP's everytime. Therefore, If I do, there may be conflicts.

---

### Post by japsai on 2009-03-03
Are you able to edit the ifupdown (eth*) connection? If not, you can let NetworkManager manage it by disabling the connection entry in /etc/network/interfaces created by pppoeconf; it should end with something like: ```
iface eth* inet dhcp
``` Put a # (comment) mark before this line. Then restart and NetworkManager won't have this "ifupdown (eth*)" connection anymore. (Which may be interfering with your DSL connection as configured by NM)

I hope this is clear otherwise I can post more.

---

