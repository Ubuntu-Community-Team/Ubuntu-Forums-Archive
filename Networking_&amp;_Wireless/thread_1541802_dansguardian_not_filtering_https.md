---
title: "dansguardian not filtering https"
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by RyanGT on 2010-07-29
I have used dansguardian with tinyproxy and firehol for several years.  I don't know how long I have had this problem, but I just noticed that https sites are coming through unfiltered.  I have blanket block turned on, and it works fine for http, but I can visit any https.  I would like to change this.

I have these two lines at the top of /etc/firehol/firehol.conf.  Do they only work for http ports?  Do I need additional lines for https?

iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

transparent_squid 8080 "root root"

Thanks,

Ryan

---

