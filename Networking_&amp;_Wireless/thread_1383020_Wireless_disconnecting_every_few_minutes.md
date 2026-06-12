---
title: "Wireless disconnecting every few minutes"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by MissingHorcrux on 2010-01-16
I have a Toshiba Satellite M55-S325 (as it came from the factory, no mods), a Linksys WRT54G router, and Ubuntu 9.10/Karmic with all updates. I've had issues since I upgraded from 9.04/Jaunty to 9.10/Karmic. It did work for awhile (I think a few days), but then it suddenly just couldn't find our wireless network. I reformatted (with 9.10) thinking it had just been a bad install - now I can connect to our network, but it throws me off every two minutes. My roommate (Dell laptop, Vista) has no problems with the internet, and I've visited a friend (in another state) and used her wireless internet without issues (though I couldn't tell you which router they were using). I've gone into our router's settings (with both my laptop and my roommate's) to reset the router or change the security settings, but with no real progress. I'm just at my wit's end, because I can't figure out what's causing the problem, or how to solve it.

Here is my ifconfig results:

```
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:87:b3:80  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:b8:7b:43  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:feb8:7b43/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1484 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1362 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1265293 (1.2 MB)  TX bytes:240564 (240.5 KB)
          Interrupt:22 Base address:0xa000 Memory:b8006000-b8006fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

If I can clarify anything, or provide you with any more terminal details, please let me know. Thanks so much in advance!

---

### Post by MissingHorcrux on 2010-01-17
So, it turns out I was connecting to the wrong "linksys" network. I went into our router's settings, changed the name of our network from the default to something more customized, and chose that one instead.

I am marking this thread as solved. ID10T error.

---

