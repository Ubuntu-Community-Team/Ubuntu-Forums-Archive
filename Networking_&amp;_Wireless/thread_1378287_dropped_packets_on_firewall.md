---
title: "dropped packets on firewall"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by morinpatmorin on 2010-01-11
I've recently installed Ubunter 9.10 Server Edition to use as a NAT firewall for the lab I run.  I'm using iptables to do NAT forwarding and everything works great except that, occasionally, connections seem to break. Ssh connections close with "Connection reset by peer" and HTTP connections just stall out.

I believe this has to do with the firewall's internal network interface occasionally dropping packets:

```
eth0      Link encap:Ethernet  HWaddr 40:61:86:4a:c3:5d  
          inet addr:192.168.123.254  Bcast:192.168.123.255  Mask:255.255.255.0
          inet6 addr: fe80::4261:86ff:fe4a:c35d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30620320 errors:0 **dropped:612** overruns:0 frame:0
          TX packets:19695467 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2408083287 (2.4 GB)  TX bytes:2007533646 (2.0 GB)
          Memory:feae0000-feb00000 

eth1      Link encap:Ethernet  HWaddr 40:61:86:4a:c3:5e  
          inet addr:134.117.27.24  Bcast:134.117.27.255  Mask:255.255.255.0
          inet6 addr: fe80::4261:86ff:fe4a:c35e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19986215 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30527324 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2077601118 (2.0 GB)  TX bytes:2386154947 (2.3 GB)
          Memory:febe0000-fec00000 
```

I realize this is a tiny fraction of dropped packets, but no other machine in my network has *any* dropped packets, and these broken connections didn't use to happen with the cheap network appliance I was using before.

I've tried increasing the values in /proc/sys/net/core/?mem_{default,max} but apparently this does nothing.

Also, I've noticed that, if it happens at all, the dropped packet(s) seem to show up very early in the connection process.  If a connection gets dropped, it gets dropped in the first few seconds.

Any help tracking down this problem would be very much appreciated.

Thanks in advance,
Pat

---

