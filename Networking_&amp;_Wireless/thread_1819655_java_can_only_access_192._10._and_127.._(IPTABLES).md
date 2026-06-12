---
title: "java can only access 192.* 10.* and 127.*. (IPTABLES?)"
date: 2011-08-06
forum: Networking &amp; Wireless
---

### Post by hoink on 2011-08-06
Other applications can access the internet just fine, but for some strange reason, not java.  I'm running Lucid 10.04

As far as I can tell, I don't have a firewall running, but iptables is installed.  I just have a wi-fi connection to my router and that is shared via ethernet connection to another PC.  

I've set my router to make my Lucid box the DMZ, so port-forwarding isn't an issue, and I confirmed that by getting the same  internet-works-but-not-for-java problem problem with my neighbors unsecured wireless connection.  heh

Even simple java "Ping" examples don't work, unless they point to private networks.

I found this bug...

[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/486215](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/486215)

...but the fix didn't apply to me, even though the behavior seems identical.

Are there some config files regarding routing or permissions I can check?

Or maybe this strangeness is because Ubuntu/java gets confused about the two interfaces and routing internet IPs (even though all other apps don't).

Also, if anybody could recommend any java applications that connect to internet IPs, I could further test my theory.

---

