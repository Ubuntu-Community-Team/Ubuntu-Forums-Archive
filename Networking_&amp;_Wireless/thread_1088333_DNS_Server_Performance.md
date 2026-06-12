---
title: "DNS Server Performance"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by kaibob on 2009-03-05
My ISP is Roadrunner (Time Warner). For the past few weeks, they have had significant issues with DoS attacks that have made their DNS servers almost unusable. I switched to Open DNS and then Level 3 public DNS services, which cured the problem.

Out of curiosity, I wrote a small script to check ping times and traceroute hops for these three DNS servers, and the following results are pretty representative:

Level 3 (4.2.2.2)
Ping (ms): 20.350
Traceroute (hops): 10

Open DNS (208.67.222.222)
Ping (ms): 27.857
Traceroute (hops): N/Av

Roadrunner (66.75.160.63)
Ping (ms): 71.887
Traceroute (hops): 11

I was curious whether ping times or traceroute are meaningful measurements of DNS-server performance and whether there is some other tool that might be more helpful. Now that the DoS attacks on the Roadrunner DNS servers have subsided, I can't say I notice much difference between the three.

---

### Post by lykwydchykyn on 2009-03-05
You could always time a host lookup:
```

time host www.google.com

```

---

### Post by kaibob on 2009-03-06
> **lykwydchykyn said:**
> You could always time a host lookup:
```

time host www.google.com

```
Thanks! I ran the time host command on google and yahoo, and the results would seem to confirm the ping times as to relative rankings. I discovered that Steve Gibson has written a small Windows utility called DNSbenchmark.exe. Perhaps I'll give that a try.

Thanks again.

```
TIME WARNER DNS SERVER

bob@dell:~$ time host www.google.com
www.google.com is an alias for www.l.google.com.
www.l.google.com has address 209.85.171.147
www.l.google.com has address 209.85.171.104
www.l.google.com has address 209.85.171.103
www.l.google.com has address 209.85.171.99

real	0m0.215s
user	0m0.008s
sys	0m0.004s

bob@dell:~$ time host www.yahoo.com
www.yahoo.com is an alias for www.wa1.b.yahoo.com.
www.wa1.b.yahoo.com is an alias for www-real.wa1.b.yahoo.com.
www-real.wa1.b.yahoo.com has address 209.191.93.52

real	0m0.310s
user	0m0.000s
sys	0m0.016s

OPEN DNS SERVER

bob@dell:~$ time host www.google.com
www.google.com is an alias for google.navigation.opendns.com.
google.navigation.opendns.com has address 208.67.219.230
google.navigation.opendns.com has address 208.67.219.231

real	0m0.203s
user	0m0.000s
sys	0m0.016s

bob@dell:~$ time host www.yahoo.com
www.yahoo.com is an alias for www.wa1.b.yahoo.com.
www.wa1.b.yahoo.com is an alias for www-real.wa1.b.yahoo.com.
www-real.wa1.b.yahoo.com has address 209.131.36.158

real	0m0.213s
user	0m0.008s
sys	0m0.012s

LEVEL 3 DNS SERVER

bob@dell:~$ time host www.google.com
www.google.com is an alias for www.l.google.com.
www.l.google.com has address 209.85.133.147
www.l.google.com has address 209.85.133.99
www.l.google.com has address 209.85.133.104

real	0m0.220s
user	0m0.000s
sys	0m0.004s

bob@dell:~$ time host www.yahoo.com
www.yahoo.com is an alias for www.wa1.b.yahoo.com.
www.wa1.b.yahoo.com is an alias for www-real.wa1.b.yahoo.com.
www-real.wa1.b.yahoo.com has address 209.131.36.158

real	0m0.072s
user	0m0.000s
sys	0m0.008s
```

---

