---
title: "Using Ubuntu for URL filtering"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by hansonian on 2010-03-22
I'm sure this can be done but I don't know how to get started on it or even if I'm heading in the right direction. 

I'm trying to setup a Linux machine (running Ubuntu 9.1 Karmic Koala at the moment) to sit between my router and the rest of my network. I want to use the Linux machine to do some URL filtering (it's a work network and we're trying to cut down on wasted bandwidth and productivity). Since this is the first time I've tried something like this I'm not too sure what direction I should be heading with it. The machine currently has two, Gigabit NICs in it and I have a solid connection to the outside world but I can't figure out how to setup the second NIC to push that connection to our switch. We're currently testing this on a small network of machines we had laying around. 

If anyone has any idea on how to get me started with this I would greatly appreciate it.

Thanks!

---

### Post by suseendran.rengabashyam on 2010-03-22
Hi,

I guess you are looking out for some kind of proxy server. SQUID is an excellent proxy server and you can visit the official site, [http://www.squid-cache.org/](http://www.squid-cache.org/) to get more details about deploying it in your network. There are some SQUID HowTo's in the Community Ubuntu Documentation for further help.

---

### Post by zeroseven0183 on 2010-03-22
You can also try [openDNS]("http://www.opendns.com/"), a free web content filtering service.

---

