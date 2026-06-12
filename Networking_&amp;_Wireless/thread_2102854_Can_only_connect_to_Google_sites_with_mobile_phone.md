---
title: "Can only connect to Google sites with mobile phone"
date: 2013-01-08
forum: Networking &amp; Wireless
---

### Post by TheFoxy on 2013-01-08
Hey. I'm on Ubuntu 12.10 (using xubuntu) and I'm trying to surf the web using my mobile phone. For some reason I can only connect to google.com and other google sites (gmail, youtube, etc.), but I get a timeout when I try to connect to any other site.

I can ping any website just fine, I get the IP address and no package loss, etc. Just in case, I changed the DNS to Google's DNS, but that didn't change anything.

I'm going online with an old HTC Diamond (Windows Mobile 6.3) and a prepaid plan (Simyo), if that's relevant. The connection works on Windows XP just fine.

I found [this thread]("http://ubuntuforums.org/showthread.php?t=893355"), which led me to [this thread]("http://ubuntuforums.org/archive/index.php/t-619531.html") with a very similar problem, but the solution did nothing for me. Changed the MTU both on the phone and on the laptop to 1492, nothing.

I also made sure that there's no IPv6 problem. "dig AAAA heise.de" gives me back an IPv6 address just fine.

Probably of interest is that using traceroute both on sites that do work (google.com) and do not work (most anything else) gives the same result.
```

conti@kleinerfuchs:~$ traceroute google.com
traceroute to google.com (173.194.65.100), 30 hops max, 60 byte packets
 1  * * *
 2  10.32.144.85 (10.32.144.85)  750.096 ms  750.048 ms  750.020 ms
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
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
conti@kleinerfuchs:~$ traceroute heise.de
traceroute to heise.de (193.99.144.80), 30 hops max, 60 byte packets
 1  * * *
 2  10.32.144.85 (10.32.144.85)  689.215 ms  689.186 ms  689.139 ms
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
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
conti@kleinerfuchs:~$

```

I have no idea what could be the issue here, and what else I could do, so here I am. Help!

---

### Post by MSPdwalt on 2013-01-08
> Hey. I'm on Ubuntu 12.10 (using xubuntu) and I'm trying to surf the web using my mobile phone. 

I'm going to do my best to make sense of this.  Are you tethering to a mobile phone? Or are you thinking that xbuntu on a different device is magically affecting your phone's ability to surf the web?

---

### Post by TheFoxy on 2013-01-08
> **MSPdwalt said:**
> I'm going to do my best to make sense of this.  Are you tethering to a mobile phone? Or are you thinking that xbuntu on a different device is magically affecting your phone's ability to surf the web?
No magic involved. :) My phone's connected to the laptop via USB, probably should've mentioned that. So yeah, tethering.

---

### Post by MSPdwalt on 2013-01-08
Have you tried disabling/re-enabling the cell radio on your phone? I'm not very familiar with windows mobile.  I use wifi tethering with my android quite a bit and for some reason every once and awhile I have to just disable/re-enable my 4g and then the magic happens.

Are you running any kind of firewall on your xbuntu machine?

---

### Post by TheFoxy on 2013-01-08
> **MSPdwalt said:**
> Have you tried disabling/re-enabling the cell radio on your phone? I'm not very familiar with windows mobile.  I use wifi tethering with my android quite a bit and for some reason every once and awhile I have to just disable/re-enable my 4g and then the magic happens.

Are you running any kind of firewall on your xbuntu machine?

No firewall, and I turned off/turned on my phone a couple of times to no avail. Also, my regular wifi connection to my router works just fine on the laptop, too.

---

