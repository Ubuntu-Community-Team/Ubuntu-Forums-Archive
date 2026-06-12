---
title: "DNS FQDN Naming Convention??"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by East82 on 2009-08-26
Quick question,
Setting up a LAN. Is there an accepted convention for top level domain for the inside network when there is a registered domain name on the WAN side??

For example if my domain is ubuntuforums.org, this would be resolved by DNS servers on the internet, however, what would I use internally to make things run with BIND on the LAN?? Some examples might be ubuntuforums.local, ubuntuforums.home, ubuntuforums.bogus. Question is, is there an accepted standard or is it up to the admin??

Thanks,

---

### Post by TTFN on 2009-08-26
I don't know that there is a standard when it comes to a LAN.  Some people use their registered domain name on the inside as well as the outside without any issues.  I personally use .local for mine as I like to keep things separated.

The main thing is to avoid any conflicts with a domain you may wish to reach outside your LAN.  Beyond that I believe any name you wish to use on the LAN is fair game.

---

