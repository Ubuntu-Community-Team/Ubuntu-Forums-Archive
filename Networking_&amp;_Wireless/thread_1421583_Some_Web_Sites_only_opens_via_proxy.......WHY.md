---
title: "Some Web Sites only opens via proxy.......WHY ????"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by linuxyogi on 2010-03-04
Hi, my problem is that some web sites for example the "youtube-dl" 

downloading site "http://bitbucket.org/rg3/youtube-dl/wiki/Home" 

only opens when browsed via a proxy. 

I used [http://www.wattproxy.info/](http://www.wattproxy.info/).

I use the following (3) DNS servers 4.2.2.1, 4.2.2.2, my ISP's DNS.

Not only [http://bitbucket.org/rg3/youtube-dl/wiki/Home](http://bitbucket.org/rg3/youtube-dl/wiki/Home), a few other web sites, are also not responding.

I tried 3 browsers (a) Firefox, (b)Opera, (c) Google Chrome. None were able to open [http://bitbucket.org/rg3/youtube-dl/](http://bitbucket.org/rg3/youtube-dl/)

I am quite sure that my ISP is not blocking any pages.

Please help.

---

### Post by psusi on 2010-03-04
Try a traceroute.

---

### Post by linuxyogi on 2010-07-20
Finally after 100 years I have found the solution !!!

Its all about setting the correct MTU value while configuring your pppoe connection.

Mentioning my MTU value here will be of no value because MTU values as I have learned recently varies with each ISP.

:D:D:D:D:D

---

### Post by wacky_sung on 2010-07-20
Usually the MTU setting is 1500.

[http://en.wikipedia.org/wiki/Maximum_transmission_unit](http://en.wikipedia.org/wiki/Maximum_transmission_unit)

[http://en.wikipedia.org/wiki/Jumbo_Frames](http://en.wikipedia.org/wiki/Jumbo_Frames)

---

### Post by linuxyogi on 2010-07-20
> **wacky_sung said:**
> Usually the MTU setting is 1500.

[http://en.wikipedia.org/wiki/Maximum_transmission_unit](http://en.wikipedia.org/wiki/Maximum_transmission_unit)

[http://en.wikipedia.org/wiki/Jumbo_Frames](http://en.wikipedia.org/wiki/Jumbo_Frames)

My MTU value was set to 1500 too.
Changing it to 1400 corrected the problem.
As I said MTU settings varies with each ISP.

---

