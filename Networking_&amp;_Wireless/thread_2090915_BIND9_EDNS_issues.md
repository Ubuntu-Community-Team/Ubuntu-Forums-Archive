---
title: "BIND9 EDNS issues"
date: 2012-12-03
forum: Networking &amp; Wireless
---

### Post by esheesle on 2012-12-03
Just setup Ubuntu server 12.10 and am getting a constant stream of the below:

Dec  3 20:49:33 professorx named[6068]: DNS format error from 192.5.5.241#53 resolving ./NS: non-improving referral
Dec  3 20:49:41 professorx named[6068]: success resolving './NS' (in '.'?) after disabling EDNS


I've noticed quite a few timeouts that I suspect are related.  When I add edns no; to my named.conf things seem to start working much better.  Thoughts?

---

### Post by gnusci on 2012-12-03
Give a look to this post, it may help

[http://www.linuxquestions.org/questions/linux-server-73/dns-format-error-938406/](http://www.linuxquestions.org/questions/linux-server-73/dns-format-error-938406/)

---

### Post by esheesle on 2012-12-03
> **gnusci said:**
> Give a look to this post, it may help

[http://www.linuxquestions.org/questions/linux-server-73/dns-format-error-938406/](http://www.linuxquestions.org/questions/linux-server-73/dns-format-error-938406/)

Not much in the way of fixes or explanations in that post (had run across it prior to posting here.  It also didn't mention the failed queries due to that.  If I go to google.com, once in a while it times out prior to resolving unless i disable edns.

---

