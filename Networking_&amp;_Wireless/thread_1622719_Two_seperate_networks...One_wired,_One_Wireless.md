---
title: "Two seperate networks...One wired, One Wireless"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by sr_guy on 2010-11-15
There are two networks in house I rent with other roommates. One wired, the other wireless (two separate routers), long story of why it worked out that way.

For some reason, I am getting the same ip on eth0 and wlan0 even though both connections come from two separate routers, see below:

```

eth0      Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:xx
          inet addr:192.168.1.9  Bcast:192.168.1.9  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe64:ecfb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:245557 errors:0 dropped:0 overruns:0 frame:0
          TX packets:169414 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:354374018 (354.3 MB)  TX bytes:13509229 (13.5 MB)
          Interrupt:25 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6767 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6767 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:13825378 (13.8 MB)  TX bytes:13825378 (13.8 MB)

wlan0     Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:xx
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:3dff:fe85:4a9d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:36538 (36.5 KB)  TX bytes:3060 (3.0 KB)




```

Is there a reason for this, and is there a way for the two get get different ip's, or is there a "bonding" thing going on here?

---

### Post by grahammechanical on 2010-11-16
Are you sure it is actually two separate routers and that only one of them has wireless? 

regards.

---

### Post by pricetech on 2010-11-16
I noticed eth0 has a broadcast address that's the same as it's IP.  Makes no sense.

In answer to your question, whichever network you connect to first establishes your IP.  When it attempts to connect to the second network, it will request the IP it already has and will be granted that IP if it's available.

I suggest you change the subnet of one or both routers.

Also disable one of your network connections.  You'll have problems with two default routes.

---

