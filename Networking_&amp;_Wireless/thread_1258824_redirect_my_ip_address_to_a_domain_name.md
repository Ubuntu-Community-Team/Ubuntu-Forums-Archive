---
title: "redirect my ip address to a domain name"
date: 2009-09-05
forum: Networking &amp; Wireless
---

### Post by pythonscript on 2009-09-05
Is there software (or some code for a script) that will let me route a domain name to my ip address? I own a top level domain name, and I'm wondering if there's a way to have some script/program, maybe that runs on startup, to bind my current ip address to that domain name. 
I'm doing this because I ssh into my laptop quite a lot while teaching a class, but my university just switched our networks to dynamic ip allocation... which makes it hard to ssh into my laptop because I don't know the ip address at any given moment. If there's a way (possibly using nmap?) to search for a certain host name on a network and return its ip address, that would be good too. Any ideas would be greatly appreciated. Thanks!

---

### Post by pythonscript on 2009-09-05
Maybe something using apache?

---

### Post by falconindy on 2009-09-05
[www.dyndns.com](www.dyndns.com) and [www.no-ip.com](www.no-ip.com) (and there's others) provide dynamic DNS services which allow you to route a DNS name to a dynamic IP.  I believe they provide a client which will update the server (of the dynamic dns provider) when your IP changes.

This is a free service. I presume if you gave them some money they would be able to route your IP to a machine name on your TLD. You'd probably have to declare a new CNAME record on your TLD's nameserver for this to work as well (e.g. laptop.myowndomain.com).

---

### Post by pythonscript on 2009-09-06
I'll take a look at those. Thanks!

---

