---
title: "Requesting Advice: Domain Naming Scheme"
date: 2012-03-14
forum: Networking &amp; Wireless
---

### Post by bkann on 2012-03-14
Hi -

I have a domain name and some 3rd-party host space on which I run a small site that I use for personal purposes, like sharing photos and so forth.  Let's call it mydomain.com.  It has some associated DNS entries like [www.mydomain.com](www.mydomain.com), ftp.mydomain.com and db.mydomain.com.

I was hoping to bring my home machines together onto a domain for a number of reasons.  I'm wondering what best practices would suggest...

1.  Should the entire home network be called something like home.mydomain.com (such that I might then have a machine named laptop1.home.mydomain.com)?

2.  Should I build the home segment at my top domain level (laptop1.mydomain.com)?

3.  Should I name it something else entirely -- maybe even something unrelated (eg., another-domain.local)?

4.  Should I do something else that I'm not even thinking about?

Thanks in advance for any feedback.  I appreciate your help!

---

### Post by redmk2 on 2012-03-15
> **bkann said:**
> Hi -

I have a domain name and some 3rd-party host space on which I run a small site that I use for personal purposes, like sharing photos and so forth.  Let's call it mydomain.com.  It has some associated DNS entries like [www.mydomain.com](www.mydomain.com), ftp.mydomain.com and db.mydomain.com.

I was hoping to bring my home machines together onto a domain for a number of reasons.  I'm wondering what best practices would suggest...

1.  Should the entire home network be called something like home.mydomain.com (such that I might then have a machine named laptop1.home.mydomain.com)?

2.  Should I build the home segment at my top domain level (laptop1.mydomain.com)?

3.  Should I name it something else entirely -- maybe even something unrelated (eg., another-domain.local)?

4.  Should I do something else that I'm not even thinking about?

Thanks in advance for any feedback.  I appreciate your help!
I think this is more a matter of administrative control.  If you have DNS subdomains then you can have an administrator for each DNS subdomain (your.domain.com or my.domain.com).  

If you are the administrator over all of the domain (i.e. mydomain.com) then it really doesn't matter whether the name is host.domain.name or host.sub.domain.name.

Ultimately DNS is just a tool to map names to IP addresses.  DNS is flexible enough to do whatever you want.

---

