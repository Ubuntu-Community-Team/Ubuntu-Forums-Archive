---
title: "ethernet acts like it is always disconnected"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by James Paige on 2009-09-24
Has anybody else had this problem?

I had a box with Ubuntu 8.10 desktop installed. It worked fine. it was just a basic installation, and I wasn't really doing anything with it yet, but I had tested it, and the network worked just fine.

But then suddenly the network stopped working. Auto oth0 still showed up in network manager, but it could not connect. if I set it to get a dhcp address, it would try for about a minute and then it would give up. If I gave it a static address, I couldn't ping anything, it would just always say "destination unreachable". Basically it was acting like the ethernet cable was unplugged. I double-checked the ethernet cable with my laptop, and it was still working perfectly.

I finally assumed that it was a hardware failure, and got another box (same model) and the same thing happened. The network worked fine at first, but a couple weeks later, it started acting like the ethernet cable was always unplugged.

So, anybody else seen this?

The hardware in question, by the way, was a built-in Via VT6105 on an Epia Pico-ITX motherboard.

---

### Post by chili555 on 2009-09-24
How about letting us see the result of these two terminal commands:```
sudo cat /var/log/messages | grep -i via
dmesg | grep eth0
```Thanks.

---

