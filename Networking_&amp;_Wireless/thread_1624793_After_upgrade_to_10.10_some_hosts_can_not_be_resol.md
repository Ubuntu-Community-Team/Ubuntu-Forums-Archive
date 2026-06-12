---
title: "After upgrade to 10.10 some hosts can not be resolved"
date: 2010-11-18
forum: Networking &amp; Wireless
---

### Post by musson on 2010-11-18
After I updated my system to 10.10, using the update manager, some of the hosts became unresolvable. For example, if I open icq.com I see a simple html page without any images, js, css files or other static content (See screenshot attached). 
For now I have found several sites(engadget.com, apple.com etc) that suffer from the same problem when I try to open them - some static content is missing.

This issue is reprodused in all the browsers (FF, Chrome, Opera). Even in FF in Wine. 

I have made some tests and found out that: 
1. Other Linux/Windows/Mac systems that use the same connection (wired and wireles via adsl router/access point) open these sites without any issues.
2. If I copy the direct link to the static content that is missing, for example [http://c.icq.com/homepage/css/content_v2.css](http://c.icq.com/homepage/css/content_v2.css), and paste it in the address bar, the browser sais that Server can not be found.
3. If I try to ping or traceroute this domain  [http://c.icq.com](http://c.icq.com) i see the following output
```

ping http://c.icq.com
ping: unknown host http://c.icq.com

traceroute http://c.icq.com
http://c.icq.com: Name or service unknown

nslookup http://c.icq.com
Server:         172.27.137.30
Address:        172.27.137.30#53
** server can't find http://c.icq.com: NXDOMAIN

```


I have already tried:
1. Delete the existing Wired connection and create a new one
2. Disable IPV6 in FF and in the GRUB loader
3. Change DNS servers

No progress at all - the [http://c.icq.com](http://c.icq.com) still can not be opened.

Please advice.

---

### Post by chili555 on 2010-11-18
I am not quite sure I know the answer to your problem, but here is a clue:> $ traceroute [http://c.icq.com](http://c.icq.com)
[http://c.icq.com:](http://c.icq.com:) Name or service not known
Cannot handle "host" cmdline arg `[http://c.icq.com](http://c.icq.com)' on position 1 (argc 1)

$ traceroute c.icq.com
traceroute to c.icq.com (63.233.110.19), 30 hops max, 60 byte packets
 1  home (192.168.1.254)  6.811 ms  6.930 ms  7.112 ms
 2  68.208.254.3 (68.208.254.3)  16.451 ms  18.369 ms *
 3  * * *
 4  * * *
 5  * * *
 6  * * 12.81.46.5 (12.81.46.5)  18.310 ms
 7  12.81.56.6 (12.81.56.6)  22.030 ms  23.892 ms  25.867 ms
 8  12.81.56.17 (12.81.56.17)  19.995 ms  23.735 ms  25.718 ms
 9  * * *
10  cr2.rlgnc.ip.att.net (12.123.152.110)  45.315 ms  49.573 ms *
11  * * *
12  * 12.122.135.157 (12.122.135.157)  31.141 ms  32.825 ms
13  192.205.34.254 (192.205.34.254)  36.707 ms  34.760 ms  36.674 ms
14  dcx2-edge-01.inet.qwest.net (205.171.251.5)  38.569 ms  40.755 ms  44.176 ms
15  * * *
16  * * *
17  * * 63-233-110-19.dia.static.qwest.net (63.233.110.19)  33.205 msI don't believe the http:// prefix is recognized in ping, traceroute, et al.

---

### Post by musson on 2010-11-18
> **chili555 said:**
> I am not quite sure I know the answer to your problem, but here is a clue:I don't believe the http:// prefix is recognized in ping, traceroute, et al.

Thank you for reply, but this does not change much for ping and traceroute. However the nslookup returned a different reply when I tried without http:// prefix:

```

nslookup c.icq.com
Server:         172.27.137.30
Address:        172.27.137.30#53

Non-authoritative answer:
c.icq.com       canonical name = c.icq.com.edgesuite.net.
c.icq.com.edgesuite.net canonical name = a949.g.akamai.net.
a949.g.akamai.net       canonical name = a949.g.akamai.net.0.1.cn.akamaitech.net.
Name:   a949.g.akamai.net
Address: 80.97.209.25
Name:   a949.g.akamai.net
Address: 80.97.209.24

```

---

### Post by musson on 2010-11-18
Solved. The problem was the Internet provider's DNS servers. Changed them to Google's open 8.8.8.8 and 8.8.4.4.

I have no idea why windows/mac systems continued to work without any problems with the abovementioned sites while using the provider's DNS servers.

---

