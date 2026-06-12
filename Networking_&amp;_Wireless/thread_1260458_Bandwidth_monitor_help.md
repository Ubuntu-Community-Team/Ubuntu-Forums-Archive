---
title: "Bandwidth monitor?? help"
date: 2009-09-07
forum: Networking &amp; Wireless
---

### Post by elliotbeken on 2009-09-07
Hi all, 

i have been playing around with webmin which is very good and reliable apart from one thing.

i was told that it was unreliable when it comes to the bandwidth monitoring.
(my webmin says it has used 29mb of bandwidth today and i know it is wrong)

so i will get to the point i would like a monitoring tool which allows me to generate reports just like webmin but one which actually works.

can anyone recommend ???

thanks

---

### Post by puppywhacker on 2009-09-07
Interfaces keep their statistic, with ifconfig you can see the usage since the interface was started.

```
ppp0      Link encap:Point-to-Point Protocol  
          RX packets:29406 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23299 errors:0 dropped:0 overruns:0 carrier:0
          RX bytes:37357535 (37.3 MB)  TX bytes:2140695 (2.1 MB)

```

To measure network usage and speed there are a few tools.

I would use MRTG, a script that creates webpages with the throughput of the network interfaces.

On the gnome desktop you can also use gnome-system-monitor to show current network speed.

On the commandline you can use iptraf which measures all packets

---

