---
title: "sendmsg: operation not permitted"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by IT-Joker on 2009-05-14
Hi all,
I have a problem that my Ubuntu sometimes won't connect to network. When I run terminal and try to ping anything, I get this message:
```
ping: sendmsg: operation not permitted
```
(it repeats with every ping)

It only happens with Ubuntu 9.04, my previous 8.10 version didn't have this problem.

And what's weird, the problem only shows *sometimes*. It might or might not happen with every reboot. So there's a very ugly workaround: Restart. And if it's still not working, keep restarting until it works.
But I hope you agree that this doesn't solve the problem. 
Only the reboot works, logging out/in doesn't seem to have any effect.

I have integrated and PCI network card, but the integrated one is disabled and doesn't show in Ubuntu, so I only have one network interface- eth1.

Any ideas?

---

### Post by shanix on 2009-09-14
It happens to me on Karmic if I have wire and wireless connection both turn on at the same time.

---

