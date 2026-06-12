---
title: "Could someone explain this output from ifconfig please?"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by mdurham on 2009-05-14
I understand eth1 but what is ra0?
I have an eeeBox with wired & wireless but am just using wired.
Cheers, Mike

```
mike@karmic32-6:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:23:54:c1:f8:f4  
          inet addr:192.168.0.23  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::223:54ff:fec1:f8f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19843 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12289 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26219539 (26.2 MB)  TX bytes:1186996 (1.1 MB)
          Interrupt:27 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:876 errors:0 dropped:0 overruns:0 frame:0
          TX packets:876 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53308 (53.3 KB)  TX bytes:53308 (53.3 KB)

ra0       Link encap:Ethernet  HWaddr 00:22:43:45:6a:77  
          inet6 addr: fe80::222:43ff:fe45:6a77/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25533 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2264874 (2.2 MB)  TX bytes:332 (332.0 B)
          Interrupt:17 

mike@karmic32-6:~$ 

```

---

### Post by techstop on 2009-05-14
> **mdurham said:**
> I understand eth1 but what is ra0?
I have an eeeBox with wired & wireless but am just using wired.
Cheers, Mike

ra0 is your wireless. Probably a "ralink" chipset in your wireless card.

---

### Post by mdurham on 2009-05-14
> **techstop said:**
> ra0 is your wireless. Probably a "ralink" chipset in your wireless card.

Thanks for your reply techstop. If ra0 is the wireless card, which I'm not using, why should it show more i/o that the eth1 that I'm actually using?
Cheers, Mike

---

### Post by techstop on 2009-05-14
> **mdurham said:**
> Thanks for your reply techstop. If ra0 is the wireless card, which I'm not using, why should it show more i/o that the eth1 that I'm actually using?
Cheers, Mike

It might just be traffic from scanning for available access points. If you're concerned about it, just right-click on the network manager icon and untick "Enable wireless".

BTW, it's not actually showing that ra0 is using more than eth1.

eth1 RX = 26.2 MB (cf 2.2MB for ra0)
eth1 TX = 1.1 MB (cf 332 bytes for ra0)

---

### Post by mdurham on 2009-05-14
> **techstop said:**
> It might just be traffic from scanning for available access points. If you're concerned about it, just right-click on the network manager icon and untick "Enable wireless".

BTW, it's not actually showing that ra0 is using more than eth1.

eth1 RX = 26.2 MB (cf 2.2MB for ra0)
eth1 TX = 1.1 MB (cf 332 bytes for ra0)

Oh yes you're correct techstop, I must be going blind! I thought I had wireless disabled.
Thanks for your help, Mike

---

