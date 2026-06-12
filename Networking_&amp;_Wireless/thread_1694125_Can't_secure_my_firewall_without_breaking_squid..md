---
title: "Can't secure my firewall without breaking squid."
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by ant2ne on 2011-02-23
Please review my webmin Linux firewall...



[IMG]http://blog.computerant.com/wp-content/uploads/2011/02/Selection_0011.jpeg[/IMG]
I'm hoping this is enough info to diagnose this problem.

This is a squid proxy / Firewall / Router. Everything works fine until I change that last line to reject or drop all. Then the traffic behind the firewall that is trying to reach the internet gets borked. I can only assume that something is killing the connections to squid. But everything looks right to me.

FYI: Here is my prerouting. (please ignore the green box) The red box is the action to be taken following the given rule. But I don't think the problem is in prerouting.
[IMG]http://blog.computerant.com/wp-content/uploads/2011/02/rampart_FirewallPREROUTIN_SQUID.jpeg[/IMG]

---

### Post by ant2ne on 2011-02-25
nothing?

---

