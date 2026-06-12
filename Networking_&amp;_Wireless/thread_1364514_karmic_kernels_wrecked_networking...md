---
title: "karmic kernels wrecked networking.."
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by bender1234 on 2009-12-26
So the release of karmic didn't go as good as expected. I've sat up 5 different systems, and all but one had issues with 802.11 and even lan. The only system that worked straight out of the box was my trusty 9.5 y.o. P3 box with an old 3Com 802.11b only usb dongle. Hehe this fella has to be like 99 y.o in computer years ;).

I've managed to get networking to work on all but one of the boxes, as I haven't had time to fix it yet.

On this box an acer aspire 6930G I'm running the fixed .15 kernel. The regular .14, .15 and .16 kernels all fails on both wired and wireless networking. intel 5100(iwlagn) and aerthos lan(hope im not confusing it with the dell box here :))

Have anyone with intel or broadcom tested the .17 kernel? Is it true that this kernel is fixed for these drivers, and is up and running? I need a confirmation before I upgrade :)

Cheers,
Stian

---

### Post by bender1234 on 2009-12-26
Confirmed.

2.6.31-17 has fixed intel 5100 issues.

---

