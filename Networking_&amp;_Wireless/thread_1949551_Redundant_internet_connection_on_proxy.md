---
title: "Redundant internet connection on proxy"
date: 2012-03-30
forum: Networking &amp; Wireless
---

### Post by Richard Cruise on 2012-03-30
Hi guys,

Been browsing around the forum for some time now but finally had reason to post a question.

I currently have a network which connects to the internet via a proxy server. Recently my connection went down and we were offline for some time. We've decided that this isn't suffucuent so we're considering purchasing a second independent connection from another provider.

Ideally, if the primary connection were to go down then the other should take up the load without any user intervention.

I think having both connections online and load balancing the 2 would be a good place to start, however is there any way to guaruntee that the connection will remain active if one connection goes down?

I know a bit about linux and IP routing, but I'm not a pro by any means, so please give as much detail in your answers as you can.

We're currently running Ubuntu 9.10 with a view to upgrading to 10.04 LTS. I'm sure there is a simle enough way of doing this, I just haven't been able to find any guide to do exactly what I want

Thanks,

Richard

---

### Post by Paddy Landau on 2012-03-31
I know that on my machine, if I connect to two connections simultaneously (one wired and another wireless), it seems to choose just the one. But if that one is disconnected, it automatically reroutes to the other.

However, they both use the same ISP, so I don't know what would happen if using two different connections. Do you download huge amounts of data, or is your connection very slow? If not, you really don't need two different connections.

> **Richard Cruise said:**
> We're currently running Ubuntu 9.10 with a view to upgrading to 10.04 LTS.
I would wait a month or two and upgrade to 12.04 LTS.

---

### Post by Richard Cruise on 2012-04-02
Hi Paddy,

Thanks for the response, can I ask do you use Network Manager or do you setup your networking manually?

We have quite a lot of internet traffic and our ISP has dropped our connection a few times before, hence the need for a second connection.

I might try to get a second connection and plug it into my proxy, just to see if it works with little to no setup, maybe I'm making a mountain out of a molehill!

Thanks for the info on 12.04 LTS, I'll definitely take a look at it.

---

### Post by Paddy Landau on 2012-04-02
> **Richard Cruise said:**
> do you use Network Manager or do you setup your networking manually?
I set up the networking with the Network Manager. It all seems to work well these days for me. If I set up anything, it is through Network Manager. It has been improved nicely since 10.04.

> **Richard Cruise said:**
> I might try to get a second connection and plug it into my proxy...
Yes, experimentation is always the easiest way to proceed.

> **Richard Cruise said:**
> Thanks for the info on 12.04 LTS, I'll definitely take a look at it.
It is still in Beta, so still some significant bugs, but you can test it in a separate partition, Virtual Box, or a Live USB. That would be a good idea anyway, as the interface has been thoroughly modernised with Unity (and done much better than Windows 8, in my opinion), but does take a day or two getting used to. Once you're used to it, though, you'll never want to return to the old way of doing things.

If you stability is important to you, wait until mid-May before upgrading, so that the dust can settle (the first month after release sees the greatest number of bug-fixes).

I strongly recommend a clean installation rather than an upgrade; if you're unsure how to go about that, check the forums or ask.

**Always back up all your data before a new installation or major upgrade.**

---

