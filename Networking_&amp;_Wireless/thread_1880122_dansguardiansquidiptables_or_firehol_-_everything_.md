---
title: "dansguardian/squid/iptables or firehol - everything is blocked"
date: 2011-11-13
forum: Networking &amp; Wireless
---

### Post by RyanGT on 2011-11-13
I have been using dansguardian for years.  I have it working correctly on my laptop using squid and firehol.  For some reason, I am having trouble setting it up on my desktop.  I am trying to follow this tutorial:
[https://help.ubuntu.com/community/DansGuardian](https://help.ubuntu.com/community/DansGuardian)
which uses iptables rather than firehol.  After I finished the tutorial, I cannot access any webpages.  How do I trouble shoot this?

Thanks,

Ryan

---

### Post by furything on 2013-01-15
I am guessing you are setting this up as a standalone box with one nic?

Have you configured your iptables? Then tried your web access to check it works.

Once you have them working you will need to save them and restore them on reboot.

---

### Post by furything on 2013-01-16
Try looking here for iptables setup with squid
[http://wiki.squid-cache.org/ConfigExamples/Intercept/IptablesPolicyRoute#Routing_Setup](http://wiki.squid-cache.org/ConfigExamples/Intercept/IptablesPolicyRoute#Routing_Setup)

The dansguardian link you refer to is about routing between 2 lan cards on the same box
so eth0 is out to the internet and eth1 is shared to the internal network you create. (This is my setup and works fine for wired lan)

From my previous post I asked if you are just trying to filter on the local box and have just 1 lan card. If so you need to follow the squid examples in the above link.

---

