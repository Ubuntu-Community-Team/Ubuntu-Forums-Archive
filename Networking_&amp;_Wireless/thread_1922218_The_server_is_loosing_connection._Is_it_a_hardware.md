---
title: "The server is loosing connection. Is it a hardware issue or a software issue?"
date: 2012-02-08
forum: Networking &amp; Wireless
---

### Post by THPubs on 2012-02-08
I have a proxy server (with Squid3) setup in an old machine. Recently, while downloading, I loose the connection. At that time, I can't even SSH into the proxy... But when I press a key in the keyboard (of the proxy server) the connection comes back! I tried with Ubuntu 11.10 and Debian 6... Both have the issue!

I also checked the "ifconfig" result... It showed 1269 dropped packets :

```
eth0      Link encap:Ethernet  HWaddr 00:0c:76:c2:de:ef
          inet addr:10.0.0.100  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:76ff:fec2:deef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:964533 errors:0 dropped:1269 overruns:0 frame:0
          TX packets:1183810 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:925950757 (883.0 MiB)  TX bytes:926726143 (883.7 MiB)
          Interrupt:23 Base address:0xe400
```

I checked again after another connection drop and the dropped count increased to 1701. When I issue "ip -s link show eth0", it gave me this :

```
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:0c:76:c2:de:ef brd ff:ff:ff:ff:ff:ff
    RX: bytes  packets  errors  dropped overrun mcast
    941833855  980298   0       0       0       0
    TX: bytes  packets  errors  dropped carrier collsns
    942639027  1201568  0       0       0       0
```

I like to know whether its a hardware problem or a software problem... If its the software, how can I fix this?

Thanks in advance...

---

### Post by THPubs on 2012-02-09
PS : I just changed the network card and still the problem is there!

---

