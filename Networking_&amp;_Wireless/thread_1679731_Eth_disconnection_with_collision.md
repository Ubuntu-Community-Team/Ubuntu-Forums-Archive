---
title: "Eth disconnection with collision"
date: 2011-02-01
forum: Networking &amp; Wireless
---

### Post by snarf77 on 2011-02-01
Hi all,

I encounter this problem since around 2 months but I just can't figure out what's going wrong, so perhaps you can help.

I'm running ubuntu 10.10 x64 on a Acer Aspire 4820TG laptop and my network is working well normally (both eth and wifi connected behing a local server).

But sometime, my normal connection (eth2) suddenly hangs and I have a new eth3 connection available in the applet notifier (but not working..). I'm unable to restore the network unless rebooting the machine (/etc/init.d/networking restart is useless...)

I got the following trace (involving collision that I don't understand):
> 
eth3      Link encap:Ethernet  HWaddr c8:0a:a9:64:ff:00  
          adr inet6: fe80::ca0a:a9ff:fe64:ff00/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:502513202757 erreurs:3015067041090 :1005022347030 overruns:502511173515 frame:2512555867575
          TX packets:502512210013 errors:2010044694060 dropped:0 overruns:502511173515 carrier:1005022347031
          collisions:2512555867575 lg file transmission:1000 
          Octets reçus:505581276862 (505.5 GB) Octets transmis:502580999957 (502.5 GB)
          Interruption:48 

Does some of you already encounter this phenomenon (eth connectino disappear and a new one (inactive and collision full) magically appearing). What can I do to diagnostic / fix this problem

Thanks in advance for you help

Snarf

---

