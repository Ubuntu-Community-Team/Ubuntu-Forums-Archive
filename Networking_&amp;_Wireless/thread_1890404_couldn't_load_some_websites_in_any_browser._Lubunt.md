---
title: "couldn't load some websites in any browser. Lubuntu 11.10"
date: 2011-12-03
forum: Networking &amp; Wireless
---

### Post by followurdrmz on 2011-12-03
I had this problem in 11.04. I was using a DSL modem back then and going thru the forums i learned that i had to configure DSL using pppoeconf :D. But the problem came back again in 11.10. Now im using a d-link dsl router which dials the connection by itself. I couldn't browse some websites or the websites using the below scripts or apis.

yahooapis.com
thepiratebay.com
icloud.com
jquery.com
static.facebook.com and more

I used some proxy websites for a couple of days. Today i tweaked my router settings and found that I had set up some NAT -- DMZ setting and a reserved ip address for my mac address. also my router's dhcp server was setup to expire the lease in 24 hrs. I cleared the DMZ and reserved ip for a mac address settings and everything is working fine now. I can now browse all the websites above. Initially 11.10 was working fine with the new d-link dsl router. It must be the router settings. Could someone please tell me which solved the problem?? is it the DMZ setting or the expired 24 hr lease IP still hanging on to the reserved mac address? :confused:

---

