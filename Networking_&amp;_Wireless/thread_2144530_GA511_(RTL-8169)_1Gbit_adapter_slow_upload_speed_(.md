---
title: "GA511 (RTL-8169) 1Gbit adapter slow upload speed (4MB/s), download speed OK"
date: 2013-05-12
forum: Networking &amp; Wireless
---

### Post by Jasps on 2013-05-12
Hello all,

After having solved the no link detected problem with the help of praseodym ([see other topic]("http://ubuntuforums.org/showthread.php?t=2143973&p=12642361#post12642361")), I'm now having troubles with the upload speed of the adapter. It is around 3.5-4 MB/s while it is connected to an 1Gbit network (copying a large file >1GB). It is even slower than with the on board 100Mbit adapter (uses 8139too driver) with which I managed to get a speed of 11-12MB/s both ways. Copying a file to the server has a speed of 30MB/s, not fast but acceptable as the upload speed is more important. 

I have tried both copying data to my pc (running Windows 7) via samba and SFTP (using fileZilla). 

Below speed return when copying via SFTP:
```

klootzak@Klootzak:~$ ifstat -S
       eth1                eth0
 KB/s in  KB/s out   KB/s in  KB/s out
    0.00      0.00    101.38   3844.61

```

I have tried different cables, setting the speed to 100Mbit, half/full duplex but no improvement so far. 

I hope you can help me out. Thanks a lot for your time and effort in advance! 

Kind regards,
Jasper


Some more info:

```
klootzak@Klootzak:~$ uname -a
Linux Klootzak 3.5.0-27-generic #46~precise1-Ubuntu SMP Tue Mar 26 19:33:56 UTC 2013 i686 i686 i386 GNU/Linux

```

```
r8169 Gigabit Ethernet driver 6.017.00-NAPI loaded

```

```
klootzak@Klootzak:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:2a:bd:cf:2d
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:2aff:febd:cf2d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:235362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:365746 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:18564284 (18.5 MB)  TX bytes:514657000 (514.6 MB)
          Interrupt:22 Base address:0x4000

eth1      Link encap:Ethernet  HWaddr 00:0a:e4:f3:9a:fa
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5628 (5.6 KB)  TX bytes:5628 (5.6 KB)


```

```

klootzak@Klootzak:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised pause frame use: Symmetric Receive-only
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: Unknown
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
                               drv probe ifdown ifup
        Link detected: yes

```

---

### Post by praseodym on 2013-05-12
Maybe a nameserver thing? Try the IP of your router and your domain there. I also recommend static IPs.

---

### Post by Jasps on 2013-05-12
I have installed the 2.3LK-NAPI driver (updated kernel which installed this driver), and now the speed up is 13-14MB/s while the download speed decreased till 13-14 MB/s... 

So it's definitely the driver. Any idea's on how to solve this?


(I'm assigning an IP address in the router to my server)

---

