---
title: "Multiple Wireless CA"
date: 2013-08-26
forum: Networking &amp; Wireless
---

### Post by nixpengu1n on 2013-08-26
Hello, all

I'm using Ubuntu 12.04 LTS and are facing up with some interesting issue: see in my organization corporate wireless access is used to varify domain clients with certificates servers (based on CISCO WCS). Protocols: WPA/WPA 2 Enterprise + 802.11x . On a Windows machine it is working fine, but on Ubuntu is not even if I try to add Ubuntu machine to a domain. 

When I try to connect to our corporate wireless it notifies me that no CA is chosen and accosiation fails even with valid domain credentials. I was trying to get CAs from Windows machine, but the thing is there are 2 certificates to varify and in Ubuntu there is only one to choose. So I have two questions, which depends on each other:

1. Is it possible to use such CA from Windows machine, or it is linked to domain name for example? 
2. If it is possible to do so, how to teach Ubuntu to varify 2 certificates?

Thx in advance

---

