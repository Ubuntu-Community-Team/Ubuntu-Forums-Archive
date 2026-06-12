---
title: "Changing kernel breaks ethernet aliases"
date: 2010-07-15
forum: Networking &amp; Wireless
---

### Post by msjwozere on 2010-07-15
Hi,

I have a fresh install of Ubuntu Server, I set up the ethernet aliases for the extra IPs we have... they work fine.

When I replace the kernel with a different one (2.6.32-belyayev.1) that supports virtualisation (we're just experimenting), the aliases stop working.

No error messages when doing "ifup eth0:0" etc, just can't ping them:

```
matt@matt-pc:~ # ping 178.63.x.x
PING 178.63.x.x (178.63.x.x) 56(84) bytes of data.
From 178.63.x.x [gateway IP] icmp_seq=1 Time to live exceeded
From 178.63.x.x [gateway IP] icmp_seq=2 Time to live exceeded
```

I know that it will be something odd to do with that kernel... but what really confuses me is that even though I have now removed the kernel and headers, back to the original configuration, the aliases are still broken and won't come up no matter what I try.

My iptables:
```
server5:/boot# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

My ifconfig:
```
server5:/boot# ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:e9:d8:98  
          inet addr:178.63.x.x  Bcast:178.63.x.x  Mask:255.255.255.192
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9213 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9849 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1130780 (1.0 MiB)  TX bytes:1868889 (1.7 MiB)
          Interrupt:10 Base address:0x6000 

eth0:0    Link encap:Ethernet  HWaddr 40:61:86:e9:d8:98  
          inet addr:178.63.x.x  Bcast:178.63.x.x  Mask:255.255.255.192
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1064 (1.0 KiB)  TX bytes:1064 (1.0 KiB)
```

Any help is greatly appreciated.

---

### Post by msjwozere on 2010-07-15
Bump :)

---

