---
title: "TCP Window Scaling Problem - Better Fix?"
date: 2012-04-29
forum: Networking &amp; Wireless
---

### Post by csete on 2012-04-29
I've recently been struggling with a problem of stalled downloads (see [http://ubuntuforums.org/showthread.php?t=1963965](http://ubuntuforums.org/showthread.php?t=1963965) for details).  I finally managed to figure out that the problem I've been seeing is due to TCP Window Scaling.  For instance, I came across [http://serverfault.com/questions/117319/linux-servers-seeing-bad-download-performance-behind-sonicwall-firewall/264815](http://serverfault.com/questions/117319/linux-servers-seeing-bad-download-performance-behind-sonicwall-firewall/264815) and realized this was the problem I've been fighting with.

My network is relatively complex for a home network:

Motorola SB6120 <-> Vonage Adapter <-> NIC 1 <-> Ubuntu 12.04 Router <-> Linux Bridge (including eth2 and Windows KVM instance) <-> private network <-> Ubuntu 12.04 laptop

Based on the various references, I've now disabled TCP Window Scaling on both Linux machines and things seem to be working much better.  However, I'm not sure if this is the best solution?  What do I lose by doing that?  Is there a way to fix this without completely disabling window scaling?  

Thanks for insights,
Craig

---

