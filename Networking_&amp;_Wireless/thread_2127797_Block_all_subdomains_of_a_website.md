---
title: "Block all subdomains of a website"
date: 2013-03-21
forum: Networking &amp; Wireless
---

### Post by jirikadlec2 on 2013-03-21
Hi, 
I need to block access to some websites from all browsers on my ubuntu 12.04 machine.
For example I need to block idnes.cz and all its subdomains (blog.idnes.cz, fotbal.idnes.cz, news.idnes.cz....)

I tried to edit the file /etc/hosts and added
idnes.cz 0.0.0.0
[www.idnes.cz](www.idnes.cz) 0.0.0.0

This blocks the main page (idnes.cz) but it does not block the subdomains (I can still access blog.idnes.cz)

How do I easily block a domain (such as example.com) and all its subdomains (site1.example.com, site2.example.com, ..........)?

---

### Post by SeijiSensei on 2013-03-21
Short answer is that there is no simple solution to block *.idnes.cz.

You can extend the method you describe by adding every hostname you might need to block to /etc/hosts.  Otherwise you'd have to install something like Squid as a caching proxy and write "access control" rules to block the domain.  In squid you can do this:

```

acl idnes dstdomain idnes.cz
http_access deny idnes

```

which defines an "access control list" for the domain idnes.cz, then adds a rule to block access to any URL that points to that domain.  You'd then have to configure the browsers to use the proxy or set up Squid for "transparent" proxying and add an iptables rule.

Another, simpler solution is to use a browser add-on like [AdBlockPlus]("http://adblockplus.org/en/firefox") for Firefox and add a rule to block anything from idnes.cz.  This is easy to thwart, though, since the user can simply disable or delete the rule.

---

