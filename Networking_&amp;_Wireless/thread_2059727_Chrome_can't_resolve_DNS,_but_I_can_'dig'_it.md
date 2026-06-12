---
title: "Chrome can't resolve DNS, but I can 'dig' it"
date: 2012-09-18
forum: Networking &amp; Wireless
---

### Post by afrosteve on 2012-09-18
I'm using Ubuntu 12.04.

At work, my laptop has a static ip for the wired connection that I have configured through Network Manager. Everything appears correct and I have no trouble accessing anything on the internet. 

On the internal network I can't seem to resolve some local names through Firefox or Chrome. I can ping them fine, and I can dig the dns servers and the name resolves with no issue. 

I have resorted to forcing them in the /etc/hosts file, but I'd like to try and solve the underlying problem. 

I've tried setting the DNS in /etc/network/interfaces and in the Network Manager GUI. It doesn't appear to make a difference.

I'm thinking my resolvconf may need tweaking? 

Any help is appreciated.

---

