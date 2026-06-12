---
title: "Doc re setup 2 NICs"
date: 2012-07-22
forum: Networking &amp; Wireless
---

### Post by satimis on 2012-07-22
Host - Ubuntu 12.04 desktop 64bit
Virtualizer - Oracle VirtualBox
2 NICs

Where can I find relevant document to set up 2 NICs, one for inward bound and another for outward bound, separate channel, both connected to the same router

Would following document be appropriate for my use?

Network Configuration
[https://help.ubuntu.com/12.04/serverguide/network-configuration.html](https://help.ubuntu.com/12.04/serverguide/network-configuration.html)

TIA

B.R.
satimis

---

### Post by bakegoodz on 2012-07-28
I may be misunderstanding, but Unless you are creating a firewall this will do nothing for you, Ethernet is already Full duplex and seperating it into 2 half-duplex connections will not increase speed.

---

### Post by BkkBonanza on 2012-07-28
You would likely make one heck of mess trying that. You wouldn't have the same IP for the inward interface as the outward interface so traffic would not be able to return to the originating IP without creating some spoofing rules to force outbound packets to say they came from the other IP.

You could configure 2 interfaces to be redundant failover or round robin and have traffic pass both ways thru both interfaces. That's an advanced topic but is doable.

Or are you trying to solve some specific issue that your question isn't making clear?

---

