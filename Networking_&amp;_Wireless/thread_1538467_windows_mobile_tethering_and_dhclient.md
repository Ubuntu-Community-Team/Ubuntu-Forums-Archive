---
title: "windows mobile tethering and dhclient"
date: 2010-07-25
forum: Networking &amp; Wireless
---

### Post by bartounet on 2010-07-25
Hello,

I'm trying to use my phone (Samsung i900) to do some tethering with my ubuntu 10.04.
When I plug my phone to the computer, an "auto eth2" connection is created. Then, I launch the ICS software on my phone and click on "Connect". The ICS software says "Connected".

But, when I do a "ifconfig eth2" on my computer, here is the result :
```

xxx@xxx:~$ ifconfig eth2
eth2      Link encap:Ethernet  HWaddr 80:00:60:0f:e8:00  
          inet adr:169.254.2.2  Bcast:169.254.2.255  Masque:255.255.255.0
          adr inet6: fe80::8200:60ff:fe0f:e800/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:32 erreurs:23 :0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:2908 (2.9 KB) Octets transmis:25065 (25.0 KB)

```

It seems that the interface is misconfigured (auto-configured ip address). When I do a "dhclient eth2", here is the result :

```


xxx@xxx:~$ sudo dhclient eth2
There is already a pid file /var/run/dhclient.pid with pid 7823
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth2/80:00:60:0f:e8:00
Sending on   LPF/eth2/80:00:60:0f:e8:00
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.102 on eth2 to 255.255.255.255 port 67
DHCPACK of 192.168.0.102 from 192.168.0.1
bound to 192.168.0.102 -- renewal in 118040 seconds.

```

It says "bound to 192.168.0.102", but if I do a "ifconfig eth2" again, here is the result :
```

xxx@xxx:~$ ifconfig eth2
eth2      Link encap:Ethernet  HWaddr 80:00:60:0f:e8:00  
          inet adr:169.254.2.2  Bcast:169.254.2.255  Masque:255.255.255.0
          adr inet6: fe80::8200:60ff:fe0f:e800/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:34 erreurs:25 :0 overruns:0 frame:0
          TX packets:197 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:3264 (3.2 KB) Octets transmis:36470 (36.4 KB)

```

I don't understand how dhclient can say that eth2 is now bound to a new IP address, but the IP address is in fact not applied to the eth2 interface.
I think this is why my tethering does not work.

Does anyone have any idea on how to solve this ?

Thanks in advance,
bartounet

---

