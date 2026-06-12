---
title: "Unable to reach Ubuntu Guest OS in VirtualBox from OSX Host."
date: 2011-05-18
forum: Networking &amp; Wireless
---

### Post by RFrenette on 2011-05-18
Recently I've been unable to load web pages, hosted on my Ubuntu Guest  in Apache, from my OSX Host. In fact, I can no longer even ping the  Guest OS from the Host.

In the past, when I did ifconfig on the  Guest, I got an IP of 10.0.1.n. Now I'm getting 10.0.2.15--the default  NAT Address. The thing is, I didn't change any settings recently. What I  did do is run software update for OSX, Ubuntu, and updated VirtBox.

Current Versions:
VirtBox 4.0.8 r71778
Host: OSX 10.6.7
Guest: Ubuntu 11.04

Doe  anyone have any idea why I can no longer access my Guest OS from my  Host? I spent hours on this last night, to no avail. I guess another  question would be: What would cause the Guest IP to change from 10.0.1.n  to 10.0.2.15? As I say, I manually made no config changes.

Thanks much for any guidance!

Rob

---

### Post by RFrenette on 2011-05-18
The solution turned out to be rather simple: Change the Network Adapter to Bridged.

Apparently the VirtBox upgrade reset my existing network setting to NAT. :o

---

