---
title: "Ping spikes with Dell Studio XPS 16 wireless (Maverick)"
date: 2011-07-21
forum: Networking &amp; Wireless
---

### Post by zemulii on 2011-07-21
I'm currently using Ubuntu 10.10 on a Dell Studio XPS 1647. I have upgraded the kernel to 2.6.38.

I noticed this problem a few weeks ago when trying to stream music from my home network server (wireless). The music would "lag" or become choppy every few seconds. I don't get this problem on the same system with Windows 7 so I ran a ping to the server. Consistently every 6/7 seconds the latency would spike up from 1 or 2 ms to over 100 (also for about 6 seconds)!

I tried the same ping on Windows 7 and over a cable connection and also with other laptop models also running Ubuntu 10.10 and none of them have this problem. They all stay consistently at around 1 ms (aside from the cable which is obviously much quicker). However I do get the same problem with Elementary OS Jupiter (based on Ubuntu) which I have on a separate partition on my laptop.

Strangely (and I'm not sure whether this is related). Sometimes starting up the laptop the pings instead go from around 20-30 ms to 200-400 :S..... I don't know what's going on there, but it seems in each case, the spikes are around 100 times slower.

Browsing the net and streaming media from my server is very unpleasant and I'm really hoping I can get this sorted out soon so I can go back to enjoying Linux!

Wireless chipset is a Broadcom BCM5784M.

The only possible solution I came up with through searching was to disable IPv6. But that did nothing, so I've switched it back on.

Any ideas (thanks!)?

---

### Post by zemulii on 2011-08-01
So no one has any ideas what could be causing this? Is it likely to be driver related or some software misbehaving?

Edit: And I might also mention that the wireless takes an unusually long time to connect at startup (about 30 seconds to a minute after the rest of the computer is ready).

---

