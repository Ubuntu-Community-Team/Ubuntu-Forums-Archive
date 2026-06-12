---
title: "Facing problem in network config."
date: 2013-01-01
forum: Networking &amp; Wireless
---

### Post by gauravjain on 2013-01-01
I am facing 1 problem. i installed ubuntu server 12.04.1 in my server  pc. and connected with ethernet connection. It should take network  configuration automatically but it does not do that and i dont have  internet access evenif ethernet connection. So can u plz guide me what  to do so that it configure network setting automatically ?
I have TP-link TL-WR740N router.

Output of ifconfig : 

Link encap:Local Loopback  
          
inet addr:127.0.0.1  Mask:255.0.0.0
          
inet6 addr: ::1/128 Scope:Host
          
UP LOOPBACK RUNNING  MTU:16436  Metric:1
          
RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:0 
          
RX bytes:580 (580.0 B)  TX bytes:580 (580.0 B)

---

### Post by 2F4U on 2013-01-01
The address 127.0.0.1 is a kind of dummy IP address, so I am assuming that your server is not properly connected to the router. It may be a hardware problem (cable, network card, etc.), or a software problem (wrong driver for network card, dhcp misconfigured, no dhcp server reachable, router blocks, etc.).
Do you connect by cable or wireless? Is your network card recognized by Ubuntu?

---

### Post by gauravjain on 2013-01-01
This is not a problem of any hardware that i m sure. bcoz once  i attached  another harddisk ( in which windows is installed ) and in windows i can connect to internet without any problem. ubuntu doesnt recognize my ethernet network. i use cable to connect network.

---

### Post by steeldriver on 2013-01-01
If you are using the server version of Ubuntu, then you need to configure network connection in /etc/network/interfaces. That *should *have been done at install time - but the first thing is to check the contents of that file

```
cat /etc/network/interfaces
```If that looks OK then you will want to check the hardware / driver detection e.g.

```
sudo lshw -C network
```Post the results back here if you need help

---

### Post by gauravjain on 2013-01-04
I have solved that problem by replacing another ubuntu server. Now its working fine. BDW thanks for your support

---

