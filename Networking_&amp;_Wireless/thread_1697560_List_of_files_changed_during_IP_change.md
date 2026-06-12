---
title: "List of files changed during IP change"
date: 2011-03-01
forum: Networking &amp; Wireless
---

### Post by suryateja.sun on 2011-03-01
Hai,

I am using Natty-Narwhal, there is some problem with the GUI network configuration. So I am interested to change my static IP address using command line. My question is which files changed in local folder when we shift from one static IP address to another static address in GUI network configuration?
For example:
I am using r8 nw from ifconfig eth0

```

eth0      Link encap:Ethernet  HWaddr 00:02:3f:ec:8b:1a  
          inet addr:10.104.250.245  Bcast:10.104.255.255  Mask:255.255.0.0
          inet6 addr: fe80::202:3fff:feec:8b1a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79359 errors:3206 dropped:3571 overruns:3206 frame:0
          TX packets:48707 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:96276305 (96.2 MB)  TX bytes:3375082 (3.3 MB)
          Interrupt:21 Base address:0x3000 

```

I need to change this to 

```
eth0      Link encap:Ethernet  HWaddr 00:02:3f:ec:8b:1a  
          inet addr:10.21.250.245  Bcast:10.21.255.255  Mask:255.255.0.0
          inet6 addr: fe80::202:3fff:feec:8b1a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79359 errors:3206 dropped:3571 overruns:3206 frame:0
          TX packets:48707 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:96276305 (96.2 MB)  TX bytes:3375082 (3.3 MB)
          Interrupt:21 Base address:0x3000 

```

If I changed to 2nd configuration, I am not getting internet. So what other files will change?

---

