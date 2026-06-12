---
title: "Marvel Fast Ethernet 88E8038 problem"
date: 2011-10-09
forum: Networking &amp; Wireless
---

### Post by nh7o_hi on 2011-10-09
I have a laptop with the above ethernet device, that connects to an older, and presumably slower HPNA router. When I plug in via a 250' ethernet cable, all works fine, as evidenced by me typing this post. The connection is at 100Mb/s, using the sky2 driver.

When I plug in with the same gear, but using a 6' cable, the ethernet ports do not connect, i.e. no connection lights at either end. I have swapped cables and boxes, so I am sure that they are OK.

Any ideas on why this happens? Ethernet has always "just worked" so I never encountered this before.

Thanks!

---

### Post by rjbl on 2011-10-09
> **nh7o_hi said:**
> I have a laptop with the above ethernet device, that connects to an older, and presumably slower HPNA router. When I plug in via a 250' ethernet cable, all works fine, as evidenced by me typing this post. The connection is at 100Mb/s, using the sky2 driver.

When I plug in with the same gear, but using a 6' cable, the ethernet ports do not connect, i.e. no connection lights at either end. I have swapped cables and boxes, so I am sure that they are OK.

Any ideas on why this happens? Ethernet has always "just worked" so I never encountered this before.

Thanks!

Crossover cable? Dud connector(s) on the 6' cable? If the 250' works ok and the 6' doesn't then you must have a dud 6' cable.

Hope this helps
rjbl

---

### Post by nh7o_hi on 2011-10-09
I definitely swapped things back and forth with other gear. The 6' cable works fine with another laptop that has a RealTek chip as network adapter, plugged onto the HPNA router. Tried other cables as well. Wiggled, pulled, all of it. The problem is repeatably down to the Marvel chip with a short cable.

---

