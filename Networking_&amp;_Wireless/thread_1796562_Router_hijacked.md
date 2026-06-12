---
title: "Router hijacked?"
date: 2011-07-04
forum: Networking &amp; Wireless
---

### Post by superbr75 on 2011-07-04
Hello!

Could somebody help me, please?

I use Ubuntu 11.04 and discovered in my network router log these lines below.

Log: Corega Router 150Mbps
+++++++++++++++++++++++++
Tue Jan  1 09:00:21 2008 syslog: [Initialized, firmware version: V1.30]
Sun Jul  3 21:25:07 2011 syslog: [Time synchronized with NTP server]
Sun Jul  3 21:25:09 2011 kernel: dns_hijack forgot to set AF_INET in raw sendmsg. Fix it!
Sun Jul  3 21:25:22 2011 pppd[714]: System time change detected.
Sun Jul  3 21:25:47 2011 crond[844]: time disparity of 1842505 minutes detected
++++++++++++++++++++++++++

My concerns is about "dns_hijack", but my access to internet working well.
My router was hijacked?!?!


Thanks

---

### Post by chili555 on 2011-07-04
[http://en.wikipedia.org/wiki/DNS_hijacking](http://en.wikipedia.org/wiki/DNS_hijacking)> DNS hijacking or DNS redirection is the practice of redirecting the resolution of Domain Name System (DNS) names to other DNS servers. This is done for malicious purposes such as phishing; **for self-serving purposes by Internet service providers (ISPs) to direct users' HTTP traffic via the ISP's own webservers where advertisements are served, statistics can be collected, or other purposes of the ISP;** and by DNS service providers to block access to selected domains as a form of censorship.I assume your router was either provided by the ISP or, undoubtedly connects to a modem or other device provided by your ISP.

Do you ever click Home and instead of finding Google, Ubuntuforums, etc. you see a greeting or sign-in page from your ISP? That's a common form of DNS hijack. Even if the feature is not currently used by your ISP, the feature appears to be built in and not quite configured correctly.

---

### Post by superbr75 on 2011-07-12
Thank you for your explanation!

>>Do you ever click Home and instead of finding Google, Ubuntuforums, etc. >>you see a greeting or sign-in page from your ISP?

No any greetings or sign-in page from my ISP.

---

