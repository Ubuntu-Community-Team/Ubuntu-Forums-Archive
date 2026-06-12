---
title: "Getting one domain to work on two different servers"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by [compactwelve] on 2010-11-01
Background info:
I have a domain through google (enom)
I have one website which I host web forums
My friend has a website which he hosts the frontpage
We're on two separate hosts

We're trying to combine the websites together and my friend wants to utilize his hosting.

The question:
Is it possible to get this one domain to work on two webservers without doing a redirect?
For exmaple:
have
Domain.com be the frontpage and
domain.com/forums be the forums

---

### Post by SeijiSensei on 2010-11-02
Just assign the machines different hostnames in the same domain, like "www.example.com" and "forums.example.com".  In your DNS create A records for www and forums that point to the machines' respective IP addresses.  That's it.

Just make sure that references on the www server to the forums site use the hostname, forums.example.com, rather than a directory entry like [www.example.com/forums](www.example.com/forums).

---

