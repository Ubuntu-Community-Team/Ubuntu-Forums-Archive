---
title: "Jaunty Internet problem"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by Puzzled Guy on 2009-11-15
Hello,
I have just installed Ubuntu 9.04 yesterday and it seems to be all running smoothly except that I can't connect to the Internet. I can connect in Windows fine. In firefox it says "Address not found". And when I try to connect, it says "Wired network disconnected You are offline." Here is the output of route and ifconfig with the cable connected:
```
route
Kernel IP routing table
Destination        Gateway        Genmask        Flags Metric Ref        Use Iface

ifconfig
eth0     Link encap:Ethernet HWaddr 00:21:85:4c:9b:4a
            inet6 addr: fe80::221:85ff:fe4c:9b4a/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
            RX packets:132 errors:0 dropped:0 overruns:0 frame:0
            TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:14517 (14.5 KB) TX bytes:3888 (3.8 KB)
            Interrupt:253 Base address:0xe000

lo         Link encap:Local Loopback
            inet addr:127.0.0.1 Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING MTU:16436 Metric:1
            RX packets:104 errors:0 dropped:0 overruns:0 frame:0
            TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:7936 (7.9 KB) TX bytes:7936 (7.9 KB)

wlan0   Link encap:Ethernet HWaddr 00:1d:92:cd:3c:f8
            UP BROADCAST MULTICAST MTU:1500 Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0 KB) TX bytes:0 (0.0 KB)
            Interrupt:17 Memory:f7da0000-f7da0100
```

So if this output will help anyone figure out how to fix my connection, good.

If any more information is needed, please post it as soon as possible. (I really need that internet)

---

