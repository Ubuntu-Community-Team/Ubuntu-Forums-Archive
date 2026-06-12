---
title: "Adding Ubuntu 12.10 to Windows Domain"
date: 2013-04-29
forum: Networking &amp; Wireless
---

### Post by IJselflearner on 2013-04-29
Hi All,

I am having a hard time finding similar threads, so I thought of posting a new thread for this.

I am working on adding Ubuntu 12.10 into our Windows Domain. Followed some configuration and editing of hosts, nsswitch.conf, resolv.conf, and dhclient.conf.
I was able to successfully added the Ubuntu 12.10 machine into the domain using likewise-open, but when i reboot the system, I was expecting to see the domain login at the startup but there was none.
I was wondering if there are some things that I may have skipped in the configuration.
One thing I noticed in resolv.conf, changes has been overwritten, so instead of searching and pointing to server's IP address it point back to itself 127.0.0.1.
How can we reconfigure the resolv.conf and hold the value we give to it?
Is there any setting that I can reconfigure to show the domain login at the startup? 

Any idea? Thank you so much in advance.

-IJ-

---

