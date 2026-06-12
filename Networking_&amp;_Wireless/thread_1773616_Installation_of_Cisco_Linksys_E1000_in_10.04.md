---
title: "Installation of Cisco Linksys E1000 in 10.04"
date: 2011-06-02
forum: Networking &amp; Wireless
---

### Post by damnated on 2011-06-02
I can't install/configure this router. I have my PC connected to it via ethernet cable, and Ubuntu sees the connection, but I can't connect to the internet and I can't access 192.168.1.1.
I've searched the forum, and I know there are a lot of threads on this, but neither were helpful and since the CD has only win drivers, I couldn't install anything. 

I can access the internet through a phone using WiFi though, so theoretically everything is working, I just can't use it with the PC.


Please advise!

---

### Post by chili555 on 2011-06-02
> Ubuntu sees the connectionDo you mean in Network Manager or where? Please open a terminal and run and post:```
ifconfig
```Thanks.

---

### Post by damnated on 2011-06-02
Yes, in network manager I have two active connections, eth0 which is the router, and eth1 which is my cable modem. The router gets the internet from the modem, and they are connected through a cable.

```

eth0      Link encap:Ethernet  HWaddr 00:13:8f:ec:0d:f4  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:feec:df4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21450 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35919 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4214366 (4.2 MB)  TX bytes:46883465 (46.8 MB)
          Interrupt:17 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:14:f8:e7:90:6c  
          inet addr:86.125.157.175  Bcast:86.125.157.191  Mask:255.255.255.224
          inet6 addr: fe80::214:f8ff:fee7:906c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:93719 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50581 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:87517084 (87.5 MB)  TX bytes:7494753 (7.4 MB)

ham0      Link encap:Ethernet  HWaddr 7a:c2:34:62:c8:a4  
          inet addr:5.5.64.104  Bcast:5.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1200  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:1869 (1.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27729 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27729 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3456972 (3.4 MB)  TX bytes:3456972 (3.4 MB)

```

---

### Post by chili555 on 2011-06-02
I don't understand. Why are you trying to connect to the internet through the router *AND* through the modem?? > eth0      Link encap:Ethernet  HWaddr 00:13:8f:ec:0d:f4  
          inet addr:[COLOR="Red"]10.42.43.1[/COLOR]  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:feec:df4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21450 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35919 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4214366 (4.2 MB)  TX bytes:46883465 (46.8 MB)
          Interrupt:17 Base address:0x8000 This address is typical of an ad-hoc, that is computer-to-computer setup. Where did this address come from? Did you set it in Network Manager? Maybe not so obviously, an interface broadcasting on 10.42.43.255 can't reach the router on 192.168.1.255.

I'm not quite sure that manual configuration will over-power Network Manager, but you might try:```
sudo ifconfig eth0 down
sudo ifconfig eth0 192.168.1.2 up
firefox 192.168.1.1
```

---

### Post by damnated on 2011-06-02
I'm connecting through both just for the time being.

I previously had a local network set up, perhaps that is why the inet addr is set to [COLOR=Red]10.42.43.1[/COLOR]

---

### Post by damnated on 2011-06-02
Yes, that worked. I am now connected, thank you very much for your help!

---

