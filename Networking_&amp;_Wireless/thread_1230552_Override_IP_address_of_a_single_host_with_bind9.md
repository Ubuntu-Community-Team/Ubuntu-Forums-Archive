---
title: "Override IP address of a single host with bind9"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by jkounis on 2009-08-03
I am running an IMAP server on a local small office network (192.168.0.100). I also use dyndns.org to establish a hostname (something like myserver.dyndns.org) so that I can retrieve my email when I travel (my router forwards port 993 to 192.168.0.100).

This works well for most cases. My desktop has the IMAP server set to 192.168.1.100, and my laptop has the IMAP server set to myserver.dyndns.org.

However, when I hook my laptop up to my small office network, it would be great if I could tell bind9 to resolve the hostname "myserver.dyndns.org" to 192.168.0.100, instead of going out to determine the "real" ip address for that host. That way, I would retrieve my email internally on the network, instead of going out through my router and then back in to get the email.

Is there a way to override the IP address for a single hostname using bind9?

Obviously, I do not own the domain dyndns.org, and I want anything else in the format of xxxx.dyndns.org to resolve normally.

Thanks!

---

### Post by CarlesOriol on 2010-12-26
Did you get an answer for this question?

---

