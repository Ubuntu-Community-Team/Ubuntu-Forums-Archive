---
title: "Ubuntu whois package and limitations"
date: 2012-10-31
forum: Networking &amp; Wireless
---

### Post by pydevs on 2012-10-31
I'm writing a django app with a form that accepts an IP and does a whois lookup on the discovered domain names.  I've found the Ubuntu package **whois** which I plan to call from a python subprocess, and read the stdout into a StringIO, then parse for things like Registrar, Name Servers, etc.

My question is, it seems that there are many paid whois services, which means that there must be a reason why people don't just use this Ubuntu package.  I'm wondering if there's a request limit on the number of requests from a single IP to the package's whois server?  I will probably be making 250 domain lookups per IP or maybe more. Also, I've found that some domains aren't searchable:

    qmul.ac.uk is searchable
    kat.ph is not searchable 
    ahram.org.eg is not searchable 

Any particular reason for that?

---

