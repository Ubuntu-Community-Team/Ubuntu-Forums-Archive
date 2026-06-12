---
title: "port fowarding to wrong ip?"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by driven1 on 2008-12-05
After right clicking on network manager, I saw that my ip is 10.0.1.4 so I set the router (airport extreme)to forward a port to that ip. Transmission shows the port is still closed. Then, I check the networking tools, and it shows the port open, but on ip 10.0.1.5 which it says is the ip for the local machine. Why does the local machine have an ip different from what the network manager says? Shouldn't they be one in the same? Meanwhile, Transmission will not download at all because the port is "closed". Anyone know what I need to do to resolve this? Thanks.

---

### Post by jmoorse on 2008-12-07
Issue a `ifconfig -a` from the terminal and that will show you your IP.  Make sure port redirection is using that address as the destination.

If that is correct verify you have the correct external/internal ports and protocols (TCP and UDP) selected.

Also if you are using dynamic addressing internally (DHCP) your machine may not always get the same 10.0.1.X address.  If that is so you may need to periodically alter the redirection rule.  Just something to keep an eye out for

---

### Post by driven1 on 2009-01-01
Thanks. I've been away for the Holidays with no time to try out your suggestions. Here are the results of ```
ifconfig -a
```

```
ath0      Link encap:Ethernet  HWaddr 00:18:e7:32:9a:ba  
          inet addr:10.0.1.4  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::218:e7ff:fe32:9aba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:70063 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46992 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:98007416 (93.4 MB)  TX bytes:4284382 (4.0 MB)

eth0      Link encap:Ethernet  HWaddr 00:1f:d0:8c:83:a2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:461644024484 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:253 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:868 errors:0 dropped:0 overruns:0 frame:0
          TX packets:868 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43400 (42.3 KB)  TX bytes:43400 (42.3 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-18-E7-32-9A-BA-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:339708 errors:0 dropped:0 overruns:0 frame:59065
          TX packets:49035 errors:32 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:127877754 (121.9 MB)  TX bytes:5408603 (5.1 MB)
          Interrupt:20 

```

I'm not sure what the loopback is. should I be using that ip instead?

---

### Post by htmlland on 2009-01-01
> **driven1 said:**
> 
          inet addr:10.0.1.4  Bcast:255.255.255.255  Mask:255.255.255.0


Seems to be your address (10.0.1.4) found in the ath0  section. The lo or loopback is your localhost address which is the same on everycomputer. Using that address will "loopback" to your computer.

---

