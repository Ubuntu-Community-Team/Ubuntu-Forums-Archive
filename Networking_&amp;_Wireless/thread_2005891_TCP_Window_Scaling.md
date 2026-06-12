---
title: "TCP Window Scaling"
date: 2012-06-18
forum: Networking &amp; Wireless
---

### Post by csete on 2012-06-18
Hello,

I have a dual-NIC Ubuntu (12.04) box at the edge of my network that acts as a file server, firewall and router combination between my private network and the public internet.  A few months ago, I started having trouble with devices on the private network that would cause them to slow down and eventually stall during downloads.  I finally figured out that it was the automatic TCP window scaling somewhere in the network path causing issues.  At the time, I disabled scaling on the various machines and those all work fine.  However, I've recently picked up an iPad and it is behaving as if it is having the same issue.  I don't believe I can disable window scaling on an iPad.  Is it possible to have my Ubuntu router "fix" the packets in some way that this is not an issue?  Are there any settings that would help me with that?

Thanks in advance,
Craig

---

