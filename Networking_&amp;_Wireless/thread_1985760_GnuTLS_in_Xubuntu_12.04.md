---
title: "GnuTLS in Xubuntu 12.04"
date: 2012-05-23
forum: Networking &amp; Wireless
---

### Post by forbajato on 2012-05-23
Posted this in the general help forum but it was quickly buried with no responses.  Maybe it is more appropriate here anyway.

I have recently upgraded from Ubuntu 10.04 to Xubuntu 12.04. Along with the upgrade I got new version of Claws-mail (great, light weight mail client!).

Now I am having trouble getting mail in Claws (3.8 ). My new user ID and group ID are the same as the old install, permissions on the .claws-mail directory are 770 (they worked at 700 before, when using claws 3.7.4 but didn't initially with the new version). I have tried replacing the .claws-mail directory with a complete new one, allowing the claws wizard to set it up but no go.

It has been suggested that the problem may be in gnuTLS. When I search my stock Xubuntu install I see there is no gnutls installed (at least gnutls-bin isn't installed by default, maybe something else is handling TLS traffic?). According to the Claws-mail website you need gnutls 2.2 at least in order to use encrypted connections to servers. The gnutls in the repos is 3.0.11+really2.12.14-5ubuntu3. Is there a way to get a real >2.2 version of gnutls via the repos?

thomas

---

