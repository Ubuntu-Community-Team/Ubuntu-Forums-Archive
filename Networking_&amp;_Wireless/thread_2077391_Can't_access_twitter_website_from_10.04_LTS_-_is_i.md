---
title: "Can't access twitter website from 10.04 LTS - is it network hop limit ?"
date: 2012-10-28
forum: Networking &amp; Wireless
---

### Post by gs76pl on 2012-10-28
hi,
i'm using ubuntu 10.04 LTS with wireless network access. The problem i have is that i can't access Twitter website (i can access any other website no problem). I've run a traceroute both on my Windows & Ubuntu partition and from what i can tell UBuntu can't make the last hop to the twitter server. Am i right here?,, What is wrong with my setup & how can i fix it?

UBuntu traceroute
```

zzz@zz-laptop:~$ traceroute twitter.com
traceroute to twitter.com (199.59.149.230), 30 hops max, 60 byte packets
 1  www.routerlogin.com (192.168.1.1)  0.812 ms  1.303 ms  1.905 ms
 2  * * *
 3  109.255.253.254 (109.255.253.254)  33.924 ms  34.070 ms  34.167 ms
 4  84.116.238.38 (84.116.238.38)  134.530 ms  131.386 ms  134.102 ms
 5  84-116-130-237.aorta.net (84.116.130.237)  134.920 ms ch-zrh02a-ra1-xe-2-0-0.aorta.net (84.116.130.110)  128.105 ms  133.783 ms
 6  us-was03a-rd1-xe-0-3-0.aorta.net (84.116.130.66)  131.832 ms us-was03a-rd1-xe-1-3-0.aorta.net (84.116.130.70)  130.350 ms  130.554 ms
 7  us-was03a-ri1-xe-0-1-0.aorta.net (84.116.130.166)  131.686 ms us-was03a-ri1-xe-0-3-0.aorta.net (84.116.130.106)  104.867 ms us-was03a-ri1-xe-0-1-0.aorta.net (84.116.130.166)  104.889 ms
 8  eqix1.cr1.iad1.twttr.com (206.223.115.97)  110.794 ms  159.311 ms  156.292 ms
 9  ae60.pao1-cr1.twttr.com (199.16.159.85)  186.784 ms  176.722 ms  229.801 ms
10  xe-10-0-0.smf1-er1.twttr.com (199.16.159.49)  179.710 ms  184.957 ms  176.913 ms
11  * * *
12  * * *

```

Windows traceroute
```

C:\Users\xx>tracert twitter.com

Tracing route to twitter.com [199.59.149.230]
over a maximum of 30 hops:

  1     4 ms     1 ms     1 ms  www.routerlogin.com [192.168.1.1]
  2     *        9 ms    18 ms  **** [my router IP]
  3     9 ms     9 ms     9 ms  109.255.253.254
  4   117 ms   105 ms   105 ms  84.116.238.38
  5   109 ms   107 ms   108 ms  84.116.134.121
  6   108 ms   106 ms   109 ms  84.116.136.153
  7   105 ms   138 ms   105 ms  us-was03a-ri1-xe-0-1-0.aorta.net [84.116.130.166]
  8   103 ms   106 ms   121 ms  eqix1.cr1.iad1.twttr.com [206.223.115.97]
  9   170 ms   199 ms   177 ms  ae60.pao1-cr1.twttr.com [199.16.159.85]
 10   176 ms   179 ms   175 ms  xe-10-0-0.smf1-er1.twttr.com [199.16.159.49]
 11   180 ms   173 ms   190 ms  www4.twitter.com [199.59.149.230]

```

---

