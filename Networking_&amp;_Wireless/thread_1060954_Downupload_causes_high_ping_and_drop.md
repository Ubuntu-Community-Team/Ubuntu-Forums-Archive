---
title: "Down/upload causes high ping and drop"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by Whelk on 2009-02-05
When downloading or uploading from Ubuntu, my ping times will get very high (starting from the 20s, ping times will go up to the thousands) and my connection will drop.  I'll get "Destination Net Unreachable" for about 5-10 seconds, then the connection will restore itself.  After a little more time, the download/upload will continue, causing the ping times to spike again and repeat the whole cycle.

Does anyone know what might be the cause of this?  If I boot up the same machine in Windows I have no problems with upload or download.  Could it possibly have to do with my provider (Roadrunner)?  Could it be related to some providers limiting bandwidth usage for torrents and such?

Wired connection, by the way.  Here are my ifconfig results:

```

eth0      Link encap:Ethernet  HWaddr 00:17:31:35:a8:8b  
          inet addr:192.168.2.107  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe35:a88b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30638990 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30643362 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3604698303 (3.6 GB)  TX bytes:2727681588 (2.7 GB)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1100 (1.1 KB)  TX bytes:1100 (1.1 KB)

```

---

### Post by Whelk on 2009-03-04
Looks like the problem was that Ubuntu didn't like the router I was using.  For reference, the router was an SMC Barricade Plus SMC7004FW.  Worked great when booting into Windows, but if I booted into Ubuntu I'd have the problem mentioned in the previous post.

I just switched to a D-Link EBR-2310 and Ubuntu handles larger downloads just fine - ping times only rise slightly while downloading.

Huge relief.  Very happy I can be a dedicated Ubuntuer now.

---

