---
title: "eb1501 network weirdness"
date: 2010-04-12
forum: Networking &amp; Wireless
---

### Post by Anarchiel on 2010-04-12
Hello,

I just installed Ubuntu 9.10 to my eee box pc (the eb1501) and I noticed that my network transfers were *really* slow. After checking the network-setup with mii-tool and ethtool, I found out that the Ubuntu thinks it's running on 10mbps instead of 100mbps. Which explains the choppy streamed HD-video.

Since this is a rather new pc and 10mbps is kinda outdated, I was wondering if anyone is able to help me out with this problem. If I force mii-tool to use 100mbps, the network gets disconnected. Switching back to 10mbps will fix things, although I won't be able to stream large files. I tried different cables and the switch which I connect this eee pc to is negotiating 100mbps-FD for all my other computers... So I can't figure out what it is that I am doing wrong... Any help would be highly appreciated.

Greets,
Anarchiel.

---

