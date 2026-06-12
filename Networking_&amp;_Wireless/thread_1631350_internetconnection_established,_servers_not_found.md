---
title: "internetconnection established, servers not found"
date: 2010-11-26
forum: Networking &amp; Wireless
---

### Post by Achilles124 on 2010-11-26
I have received a new modem from my provider and installed it. No problem with that .... except that there is a problem with my internetconnection. The internetconnection is established. But my computer gives an error every time I want to visit a website:

**Server not found.**

What could be the problem? And what to do to solve it?

Thanks.

---

### Post by d3v1150m471c on 2010-11-26
```

sudo iptables -L # remove your private ip please
ifconfig
ping -c1 www.google.com

```post the output please.

---

### Post by Achilles124 on 2010-11-26
```
sudo ecmpeek@ecmpeek-desktop:~$ sudo iptables -L # remove 192.168.1.6

[sudo] password for ecmpeek: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ecmpeek@ecmpeek-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:92:70:97:77  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:92ff:fe70:9777/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1648 (1.6 KB)  TX bytes:23848 (23.8 KB)
          Interrupt:27 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:126 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12964 (12.9 KB)  TX bytes:12964 (12.9 KB)

ecmpeek@ecmpeek-desktop:~$ ping -cl www.google.com
ping: bad number of packets to transmit.
ecmpeek@ecmpeek-desktop:~$ ping -c1 www.google.com
ping: unknown host www.google.com
```

I didn't know whether it was -cl or c1 (I guess -cl). Well, this is the code. I hope you can make sense out of it.

---

### Post by gordintoronto on 2010-11-26
You need to set up the modem, so it gets DNS servers from your ISP.

---

### Post by Achilles124 on 2010-11-27
The problem is solved. Don't know what happened but I think my provider changed some things. Anyway, thank you for answering, both of you. :p

---

