---
title: "DNS Server - Help with Redirect traffic of a specific url to a Local IP address"
date: 2013-05-31
forum: Networking &amp; Wireless
---

### Post by alee6179 on 2013-05-31
Hello 

I've been working on this problem for the past week and still can't solve it.  

I want to setup something probably a CNAME record or an A record that will help me with redirecting traffic from an external url to an internal ip address. 

I want all request for the following url: vc.example.com to be forwarded to a local IP address (10.8.8.5).  If the request for anything else that has the same domain, it will still go externally like: web.example.com.  

Is this possible?  Any assistance is appreciated.


Alee6179

---

### Post by linuxtechguy on 2013-05-31
CNAME is only to point one host to another host. You can point an A record to point the host to an ip though.

---

