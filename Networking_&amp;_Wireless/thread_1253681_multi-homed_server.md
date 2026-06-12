---
title: "multi-homed server"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by peterLinux on 2009-08-30
Hi All,

I've an issue with multi-homing a new server. (never done this before)

I've bonded 2x 2 NICs (Done this a few times)
bond0 192.168.10.200
bond1 10.10.20.200

So far so good, I've tested the fail-over by unplugging cables while ping-ing from the server to a gateway

Problem(s)
From the 192.168.10 network I can ssh into 192.168.10.200
I cannot ssh into 10.10.20.200 unless I take bond0 down (ifdown bond0)

However while both bond's are up I can ssh into 10.10.20.200 from any other pc on 10.10.20.0/24

There is an IPCop sitting between 192.168.10 (green) & 10.10.20 (orange) I am not sure but I don't believe it is causing troubles... is it?

I do not want a bridge between bond0 and bond1.

```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.10.20.0      0.0.0.0         255.255.255.0   U     0      0        0 bond1
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 bond0
0.0.0.0         10.10.20.1      0.0.0.0         UG    100    0        0 bond1


ifconfig 
                                                   
bond0     Link encap:Ethernet  HWaddr 00:22:19:4f:ad:2e    
          inet addr:192.168.10.200 Bcast:192.168.10.255 Mask:255.255.255.0

bond1     Link encap:Ethernet  HWaddr 00:22:19:4f:ad:30
          inet addr:10.10.20.200  Bcast:10.10.20.255  Mask:255.255.255.0
```


How can I make sure my multi-home config is correct before looking somewhere else (ipcop?) for routing issues? 

Thanks

Peter

---

