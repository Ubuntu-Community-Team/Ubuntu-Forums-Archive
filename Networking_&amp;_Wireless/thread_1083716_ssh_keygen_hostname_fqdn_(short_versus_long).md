---
title: "ssh keygen hostname fqdn (short versus long)"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by ear9mrn on 2009-03-01
Hi,

I am trying to set up a host pair for passwordless ssh login. I have it working fine with all my machines (ubuntu, fedora etc) but I have just added a router running tomato and what looks like a ssh daemon called dropbear. The problem (I think) stopping login is when I create a key on my machines it is for user@machinename but I think the router resolves the fqdn, [email]user@machinename.domain.com[/email]. Question is is my Ubuntu machine behaving, should it be creating keys with the short name ? If so how do I fix that or how do I force keygen to create keys with fqdn's ?

Thanks,

Pete.

---

