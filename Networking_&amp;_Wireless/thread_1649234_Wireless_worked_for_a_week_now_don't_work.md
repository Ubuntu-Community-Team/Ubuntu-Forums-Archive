---
title: "Wireless worked for a week now don't work"
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by tanveers on 2010-12-19
**[FONT=Century Gothic][SIZE=3]I have Ubuntu 10.10 running on a Dell Optiplex GX280 Desktop. I installed [/SIZE][/FONT]****[FONT=Century Gothic][SIZE=3]Rosewill RNX-G300LX wireless adapter. It worked quite well for about a week. It even worked today morning but all of sudden in the evening it stopped working. Even though I see signal strength of 60% or above (same as before) and I see the wifi connected but it takes ages to load any webpage - most of the time I see timeout. I rebooted, disabled/enabled the wireless connection but still same result.[/SIZE][/FONT]**[B][FONT=Century Gothic][SIZE=3]

Could anyone tell me what could be wrong? Why I have connectivity but webpage won't load?

Thanks!

TS

[/SIZE][/FONT][/B]

---

### Post by tgalati4 on 2010-12-20
Open a terminal:

ping [www.google.com](www.google.com)

It should look something like:

pbook:~ Gman$ ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (66.102.7.99): 56 data bytes
64 bytes from 66.102.7.99: icmp_seq=0 ttl=53 time=52.982 ms
64 bytes from 66.102.7.99: icmp_seq=1 ttl=53 time=53.867 ms
64 bytes from 66.102.7.99: icmp_seq=2 ttl=53 time=54.206 ms
64 bytes from 66.102.7.99: icmp_seq=3 ttl=53 time=52.850 ms
^C


Control-C to quit.

If your ping times are greater than 100 ms, then you or your internet provider has a problem.

---

### Post by tanveers on 2010-12-20
> **tgalati4 said:**
> Open a terminal:

ping [www.google.com]("http://www.google.com")

It should look something like:

pbook:~ Gman$ ping [www.google.com]("http://www.google.com")
PING [www.l.google.com]("http://www.l.google.com") (66.102.7.99): 56 data bytes
64 bytes from 66.102.7.99: icmp_seq=0 ttl=53 time=52.982 ms
64 bytes from 66.102.7.99: icmp_seq=1 ttl=53 time=53.867 ms
64 bytes from 66.102.7.99: icmp_seq=2 ttl=53 time=54.206 ms
64 bytes from 66.102.7.99: icmp_seq=3 ttl=53 time=52.850 ms
^C


Control-C to quit.

If your ping times are greater than 100 ms, then you or your internet provider has a problem.

Thanks, I will do the ping test. But I don't think there is anything wrong with my ISP, as my macbook, mac mini, and windows 7 machine are working fine.

---

