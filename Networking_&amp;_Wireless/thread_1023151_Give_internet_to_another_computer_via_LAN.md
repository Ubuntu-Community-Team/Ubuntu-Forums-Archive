---
title: "Give internet to another computer via LAN"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by Dbugger on 2008-12-27
Hello guys,

I am using a USB DSL modem to get internet in my ubuntu directly, and Im in a wired LAN with my brother's computer (which runs windows, but I dont think this matters)

Is there anyway I can give him internet access?

Thanks!

---

### Post by Iowan on 2008-12-27
[https://help.ubuntu.com/community/Internet/ConnectionSharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing")

---

### Post by Dbugger on 2008-12-27
this guide is good for standar situation but It gets kinda confusing in my case
when I make a "ifconfig" i get all this interfaces:

wifi0, ppp0, nas0, lo, eth0, ath0

which should I use for each thing??

Edit:
> 
dbugger@laptop:~$ ifconfig 
ath0      Link encap:Ethernet  HWaddr 00:16:e3:a8:2f:ce  
          inet6 addr: fe80::216:e3ff:fea8:2fce/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:13:77:33:cc:1c  
          inet6 addr: fe80::213:77ff:fe33:cc1c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5382 (5.3 KB)  TX bytes:4230 (4.2 KB)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

nas0      Link encap:Ethernet  HWaddr 00:0e:50:d7:d3:22  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:50ff:fed7:d322/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:900 errors:0 dropped:0 overruns:0 frame:0
          TX packets:955 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:809879 (809.8 KB)  TX bytes:233200 (233.2 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:88.25.52.224  P-t-P:192.168.153.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:882 errors:0 dropped:0 overruns:0 frame:0
          TX packets:926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:802055 (802.0 KB)  TX bytes:201517 (201.5 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-16-E3-A8-2F-CE-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:2144
          TX packets:154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1274 (1.2 KB)  TX bytes:7084 (7.0 KB)
          Interrupt:16 


---

### Post by Iowan on 2008-12-27
Just guessing at this point:
eth0 = wired connection
ath0 = ???
ppp0 = DSL device?
lo = loopback device
wifi0 = wireless (tough to guess ;) )
nas0 = ??? NAS storage device?

Interesting to note - besides standard lo, only nas0 and ppp0 have IP addresses.

---

