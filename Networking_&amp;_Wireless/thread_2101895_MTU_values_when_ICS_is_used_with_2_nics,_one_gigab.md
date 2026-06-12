---
title: "MTU values when ICS is used with 2 nics, one gigabit, other fast ethernet?"
date: 2013-01-05
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2013-01-05
I was messing with the MTU and used to be able to connect with 7000mtu between an ubuntu PC and win7 pc using gigabyte nics straight connections.

Then I turned on ICS in ubuntu to share internet to win7 pc.
Internet  <-> cable modem <-> router <-> 100mb nic <-> ubuntu pc <-> gigabyte nic -> gigabyte nic -> win7pc

Now when I mess with the MTU settings, I cant enable jumbo frames at all. If I do, the gigabyte lan looses all connections and the ubuntu PC even says the cable is disconnected.

So is this because these cards are now linked by Ubuntu ICS?

some refs
[http://www.kernel.org/doc/ols/2009/ols2009-pages-169-184.pdf](http://www.kernel.org/doc/ols/2009/ols2009-pages-169-184.pdf)
[http://manpages.ubuntu.com/manpages/maverick/man8/ethtool.8.html](http://manpages.ubuntu.com/manpages/maverick/man8/ethtool.8.html)
[http://alliedtelesis.com/manuals/2911_IG_UG_Rev_A/Setting_Advanced_Properties.html](http://alliedtelesis.com/manuals/2911_IG_UG_Rev_A/Setting_Advanced_Properties.html)

---

