---
title: "IPW2200 injection in 9.04, with kernel 2.6.30?"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by DejitaruJin on 2009-08-07
Yes, that's right, yet another topic on the IPW2200. I'm sure we all wish it just didn't exist by now.

A guy elsewhere on the forums told me that, in kernel 2.6.30, the IPW2200 wireless driver module actually comes pre-patched, and with working packet injection enabled (where in 2.6.28, I've yet to see a single report of success getting a patched driver to work). So, I spent the night upgrading the kernel manually. When I got Linux working again (hey, first time compiling a kernel, people forget things, like IDE support), this *seems* to be accurate, as the rtap0 interface is already there.

However, using...

```
sudo aireplay-ng -9 eth1
```... gets me about as far as it did with kernel 2.6.28. Which is, just short of nowhere. Broadcast probe returns nothing, and the individual AP tests return nothing. If I add an "-i rtap0" in there, it also tests attacks, which again return no positive results.

I want to hear if anyone, anyone at all, has gotten this to really, truly work with the newest kernel. If they have, then we'll get into exactly *how*. If not, it's time for a new card.

---

