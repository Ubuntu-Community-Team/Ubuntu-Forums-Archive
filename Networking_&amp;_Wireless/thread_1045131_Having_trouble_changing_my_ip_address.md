---
title: "Having trouble changing my ip address"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by jclmusic on 2009-01-20
When I try to change my IP address using the network config, I lose my connection altogether! Can someone please explain what I am doing wrong?

---

### Post by lovelyvik293 on 2009-01-20
please explain what you did?

---

### Post by tarps87 on 2009-01-20
Can you run and post the output of ifconfig before and after the change. Also can you post what the ip address range and subnet of the network you are connected to.

Thanks

---

### Post by jclmusic on 2009-01-20
ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:08:c7:5a:0d:c8  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:c7ff:fe5a:dc8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53230 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40675 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:62986479 (60.0 MB)  TX bytes:5271290 (5.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6123 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6123 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:233335 (227.8 KB)  TX bytes:233335 (227.8 KB)

```

eth0 is my connection. It is working now as I have changed it back! I can't seem to make it work with a different IP!

---

### Post by tarps87 on 2009-01-20
When you say a different ip do you still mean on of the 192.168.1.* subnet?
Also how are you changing the ip, ifconfig or the network manager?
Could you give me a brief idea of the network i.e. what's connected

---

### Post by Iowan on 2009-01-20
[Here]("http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html") is a How-To on assigning a static IP.

---

