---
title: "Excessive bandwith use with 12.04"
date: 2012-11-15
forum: Networking &amp; Wireless
---

### Post by mahohmei on 2012-11-15
Comcast's website has a feature to allow users to monitor their bandwidth use, which will be useful in a future date when their residential users like myself are capped at 300 GB per month.

According to Comcast's usage meter, starting late in October, I have been sucking down a constant roughly 1 GB per hour, even when I'm not home. After some trial and error (read: disconnecting one device at a time from the LAN while at work and overnight), I have narrowed it down to my desktop running 12.04.

Here's the rub: I can't see where I'm using the bandwidth. I run System Monitor and Wireshark, and when my desktop is sitting idle, network usage is nearly flatlined--nowhere near the roughly 2 mbps Comcast claims I'm sucking down.

Does anyone else have this issue?

Thanks!

Addendum: Someone just suggested to me it could be the NIC. Tonight, I'm going to boot from a 12.04 live CD, let it sit overnight, and see what happens. The NIC is the onboard NIC on an Asus M3N78-VM motherboard.

---

