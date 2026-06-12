---
title: "How to create a domain?"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by Reiger on 2009-02-24
To create domains (I assume you want to be able to visit [http://my-real-domain-name/path/to/file](http://my-real-domain-name/path/to/file) in a browser) you will need to setup/configure a DNS server.

---

### Post by Reiger on 2009-02-24
> **u.lover said:**
> I installed ubuntu 8.10 on my server. Now I need to know how can I make it a domain in my network? I've 10 PCs network

IF you are willing to do the neccesary configuration for all 10 PC's ;) .. you can get by /etc/hosts as well.
For instance:
(a template you could use for automated-installation):
127.0.0.1   localhost
192.168.1.2 wwwdomain # dedicated www server
192.168.1.3 fileshare # dedicated ftp server
192.168.1.4 localmail # dedicated mail server
192.168.1.5 localcups # dedicated print server

Or:
127.0.0.1   localhost
192.168.1.2 allserver # if everything runs on this machine

---

