---
title: "Slow DNS"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by nathansoz on 2009-12-28
So I have been dual booting windows/ubuntu for a while on my laptop, and have observed something interesting. DNS resolution (I use DCHP to configure all of my ip settings) seems horridly slow on the ubuntu side of my laptop when compared with the windows side. I have solved the problem (I manually set my DNS to use googleDNS service), but I was just wondering if this seems to be a problem with anyone else. Now that I am using googleDNS, the ubuntu side seems just as fast, or maybe a tad snappier at resolving webpages. What's up with the slow dns that I was experiencing before?

---

### Post by adam814 on 2009-12-28
I couldn't say why it was slower than Windows DNS resolution.  I run dnsmasq as a caching-only server to speed up DNS resolution on mine.  After the first lookup subsequent ones take less than 10ms whereas my ISP DNS servers when I set it up were taking up to 500ms.

---

### Post by teachop on 2009-12-28
Look at this and see if it is related:

[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757]("https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757")

---

### Post by nathansoz on 2009-12-29
> **teachop said:**
> Look at this and see if it is related:

[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757]("https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757")

Hmmm interesting. Looks exactly like the problem I was having. Thanks!

---

