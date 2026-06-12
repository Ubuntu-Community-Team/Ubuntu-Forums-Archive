---
title: "Automatic gateway to dialup (autoassigned IP)"
date: 2011-05-07
forum: Networking &amp; Wireless
---

### Post by LancerNZ on 2011-05-07
Any time I connect to the internet in my main computer (intended to be the gateway) using dialup, I have to use ifconfig to find out the new IP address (this changes any time I connect)

```
lancer@lancer-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:02:a5:de:45:fe  
          inet addr:192.168.0.140  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:a5ff:fede:45fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:619 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29439 (29.4 KB)  TX bytes:51243 (51.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4496 (4.4 KB)  TX bytes:4496 (4.4 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:60.234.102.146  P-t-P:222.152.43.193  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:64 (64.0 B)  TX bytes:97 (97.0 B)
```

Then, I have to manually key in what the ifconfig tells me is the IP address for ppp0, in order to make it actually be the gateway.

Like this:
```
lancer@lancer-desktop:~$ sudo route add default gateway 60.234.102.146
[sudo] password for lancer: 
lancer@lancer-desktop:~$ 
```

It's really annoying doing this all the time. If the connection breaks and I have to reconnect, then I have to go through the whole process again just to get my pings, DNS etc up and running.

To make matters worse, if I plug in any kid of ethernet cord (e.g. link to a wireless router to broadcast the internet and actually **be** a gateway, the notorious autodetection problem of Ubuntu (since version 9) kicks in and I have to manally reassign the gateway all over again.

What _should_ happen is this...
Connect to dial up (ISP given IP which can change) => automatic gateway setup
Plug in ethernet => Keep the already assigned gateway etc.

...but how do I get this working in Ubuntu 10.04?

---

### Post by LancerNZ on 2011-05-09
:confused: Hm... was my question too vague?

Please let me know if there's anything I should include that I've missed out.

---

