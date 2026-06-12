---
title: "No wired network connection"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by YourSurrogateGod on 2011-08-02
Hey all,

   I have a System 76 laptop.  I hooked up a wired connection to it today and I get absolutely no data sent from it to the outside.  This is a simple connection without a router.  I cannot ping or browse the web.  When I tried running the package manager, this is what I got:
```
W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/z/zeroc-ice/ice33-slice_3.3.1-12_all.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
```

```
eth0      Link encap:Ethernet  HWaddr 00:1a:92:46:8c:66  
          inet6 addr: fe80::21a:92ff:fe46:8c66/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:8493 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:615765 (615.7 KB)  TX bytes:13465 (13.4 KB)
          Interrupt:16 Base address:0x4c00 

eth0:avahi Link encap:Ethernet  HWaddr 00:1a:92:46:8c:66  
          inet addr:169.254.7.63  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:222593 (222.5 KB)  TX bytes:222593 (222.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:10:ce:4e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Any ideas?  Any more info I can provide?

---

### Post by YourSurrogateGod on 2011-08-02
Mind you, my laptop has no connectivity at this point and I am typing this on a different comp, so if I need any tools to make this connection work, I would appreciate links from where I can download the tarballs :) .

---

### Post by YourSurrogateGod on 2011-08-02
Yes, the cable is plugged in.  I rebooted my PC.  No idea what to do next.

---

