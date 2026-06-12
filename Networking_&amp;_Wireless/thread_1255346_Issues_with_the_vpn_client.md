---
title: "Issues with the vpn client"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by dagarshali on 2009-09-01
Hi,
I have asked this question a couple days ago and haven't gotten any response :(

I have a laptop with 4gb ram and i have ubuntu jaunty installed on it. I browsed online including this forum and upgraded to linux server kernel to accommodate the 4gb ram.

I had installed the vpnclient before that and was working just fine. Now, it now longer works via the menu. 

and the menu points to /opt/cisco/vpn/bin/vpnui and when I type that in the terminal, i get gThread error: can be initialized only once. 

Not sure what to do.

Thanks,
Vishwa

---

### Post by dmizer on 2009-09-01
The VPN service may be automatically starting on boot. What is the output of:
```
ifconfig
```

---

### Post by dagarshali on 2009-09-01
eth0      Link encap:Ethernet  HWaddr 00:23:8b:f2:51:1a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1e:65:28:73:30  
          inet addr:129.186.17.238  Bcast:129.186.17.255  Mask:255.255.255.0
          inet6 addr: 2610:130:101:800:21e:65ff:fe28:7330/64 Scope:Global
          inet6 addr: fe80::21e:65ff:fe28:7330/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5046 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3891917 (3.8 MB)  TX bytes:3774087 (3.7 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-65-28-73-30-33-33-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

thanks
vishwa

---

### Post by dmizer on 2009-09-01
Humm, there goes that theory.

I highly suggest bringing this before the Cisco folks here: [http://www.cisco.com/en/US/products/sw/secursw/ps2308/tsd_products_support_series_home.html](http://www.cisco.com/en/US/products/sw/secursw/ps2308/tsd_products_support_series_home.html) or here: [http://forums.cisco.com/eforum/servlet/NetProf?page=main](http://forums.cisco.com/eforum/servlet/NetProf?page=main) as they will be more familiar with the vpn client you're using.

---

