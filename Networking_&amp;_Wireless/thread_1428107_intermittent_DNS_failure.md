---
title: "intermittent DNS failure"
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by viralmeme on 2010-03-12
Every so often while browsing, DSN fails. The thing is that if I DIG the address at the command prompt the site immediatly pops in in Firefox. Any ideas of what I should do to diagnose the problem.

---

### Post by pricetech on 2010-03-12
Have you tried other browsers ??  Have you tried other DNS servers ??

---

### Post by viralmeme on 2010-03-13
> **pricetech said:**
> Have you tried other browsers ??  Have you tried other DNS servers ??
Yes, the same thing happens. seems to be a problem with the local network configuration. I moved to OpenDNS and it half-solved the problem. The Browser pauses on loading the web site, I DIG the name and do a nslookup, then the page starts to load.
-------

Any suggestions?

Browser pauses, don't even get to 'looking up'. Do a NSLOOKUP at the prompt and the browser completes the DNS lookup and displays the page. Happens on random pages, every so often ...

---

