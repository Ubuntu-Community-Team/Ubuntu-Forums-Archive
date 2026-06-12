---
title: "I can't access a specific website"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by aiden120000 on 2010-08-08
Hello Ubuntu people. I've been using Ubuntu for about two years now and I've never had a problem like this before. I want to access encyclopediadramatica.com, which I know is up (proxy, isitup.org, etc) but for some reason it just doesn't work chrome gives me this . I've done some research on the Google, they said to flush the dns cache so I sudo /etc/init.d/nscd restart, still no luck. I've changed my dns server manually in my router to 4.2.2.2 as suggested by one forum poster but still no luck. Yes I've cleared my cache, and tried different browsers.
I don't get a response if I ping them either.

Any way here's my traceroute (if it helps at all) 


aiden@ubuntu:~$ traceroute encyclopediadramatica.com
traceroute to encyclopediadramatica.com (208.99.87.133), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  3.088 ms  3.326 ms  3.657 ms
 2  cpc5-sotn9-2-0-gw.know.cable.virginmedia.com (82.6.251.1)  14.791 ms  15.418 ms  16.114 ms
 3  sotn-core-1a-ge-400-1599.network.virginmedia.net (80.4.225.65)  16.602 ms  16.971 ms  17.527 ms
 4  winn-bb-1a-ae1-0.network.virginmedia.net (212.43.163.149)  18.518 ms  27.464 ms  28.044 ms
 5  popl-bb-1b-as5-0.network.virginmedia.net (212.43.162.194)  28.705 ms  29.305 ms  34.844 ms
 6  tele-ic-2-as0-0.network.virginmedia.net (62.253.184.6)  35.435 ms  14.527 ms  15.869 ms
 7  eqix.xe-3-3-0.cr2.iad1.us.nlayer.net (206.223.115.61)  94.698 ms  100.801 ms  100.142 ms
 8  xe-2-2-0.cr1.ord1.us.nlayer.net (69.22.142.27)  174.859 ms  174.367 ms  173.771 ms
 9  po6.ar1.ord1.us.scnet.net (69.31.111.58)  120.552 ms  124.135 ms  124.724 ms
10  61.po1.ar1.ord6.us.scnet.net (75.102.3.226)  127.495 ms  127.916 ms  126.940 ms
11  gige0-51.1000M.aggr.fr143-1.ord6.reflected.net (64.210.153.146)  125.135 ms  125.592 ms  125.932 ms
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

Thanks a lot people. Any help at all that you can give will be much appreciated.

---

