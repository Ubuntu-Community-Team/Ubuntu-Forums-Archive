---
title: "isolate apache to only LAN access"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by jimmy the saint on 2008-12-28
I am setting up a file server and I plan to install webmin, which requires apache.  I tried configuring ports.conf with 
```
Listen 192.168.0.0/24:80
```

I got an error that it "failed to set up sockaddr for 192.168.0.0/24"
I am assuming that apache cannot understand the /24 part.  How do I isolate the apache server to only listen to the lan?

Thanks

---

