---
title: "No more dnsmasq, back to normal"
date: 2012-06-14
forum: Networking &amp; Wireless
---

### Post by lisanels47 on 2012-06-14
With the recent changes in Ubuntu, I've wanted to get back to the normal operation of how /etc/resolv.conf works.  I have no need for dnsmasq, and my local DNS server is fast.  So switching back to the way things were is something I wanted to do.

First, comment out this line in /etc/NetworkManager/NetworkManager.conf

#dns=dnsmasq

Then use "apt-get remove resolvconf" to get rid of the resolver.  Restart, and things are back to normal and working great.

Hope this helps others.

---

