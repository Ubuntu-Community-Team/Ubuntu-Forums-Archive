---
title: "Websense replacement"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by e24ohm on 2009-09-08
Folks:
I am looking for an opensource solution that will replace Websense, which is a website monitoring/content filter that blocks websites from network users. I have looked at the FAQ for Squid; however, does anyone use/deploy Squid for this solution?



Thank you,
J

---

### Post by i.r.id10t on 2009-09-08
I used squid to block *all* domains and then allow a certain few for kiosks (*.edu, etc)

Not sure if it can look at the content of a page and block based on that... it can blacklist or whitelist by domain with no problem.

---

### Post by e24ohm on 2009-09-08
> **i.r.id10t said:**
> I used squid to block *all* domains and then allow a certain few for kiosks (*.edu, etc)

Not sure if it can look at the content of a page and block based on that... it can blacklist or whitelist by domain with no problem.hey thanks...I will fight through the install instruction, and deploy on a test domain. Websense is nice, but having to need to be purchased per-seat license, is a little rough. If I can block traffic based on domain, then i think i have found a winner...thaks for the help mate.

cheers!!!

---

### Post by MauroD on 2009-09-13
It is the right solution as it is all the features on Websense, and it works better.
I am in the same situation and squid works well, although I have some problem with WCCP at the moment.

I need to find out a good reporting system for squid, but this seems ideal for a websense user
[http://sarg.sourceforge.net/sarg.php](http://sarg.sourceforge.net/sarg.php)

---

