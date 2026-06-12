---
title: "Limit amount of data to be received?"
date: 2010-06-30
forum: Networking &amp; Wireless
---

### Post by woodbj on 2010-06-30
Hello,
I was wondering if there was a Windows or Ubuntu way to limit the amount of data that is able to be sent over the internet between certain times,

eg. Between the times of 7am and 7pm can only download 300 MB from the web, when this limit is reached the web is either disconnected or slowed down.

Is this possible?

---

### Post by McRat on 2010-07-01
> **woodbj said:**
> Hello,
I was wondering if there was a Windows or Ubuntu way to limit the amount of data that is able to be sent over the internet between certain times,

eg. Between the times of 7am and 7pm can only download 300 MB from the web, when this limit is reached the web is either disconnected or slowed down.

Is this possible?

It certainly CAN be done.  Satellite providers do it to their customers.  Mostly this is done at the router, NOT the computer.  Some consumer routers/cablemodems/firewalls have it, but it's mostly seen on commercial ISP products.  IIRC, it's called Traffic Shaping.

But it could be done at the computer (it's normally not, because the customer can turn it off).

---

### Post by jonobr on 2010-07-01
I havent tried it , but tc within iproute2 may work for you

For controlling bandwidth you could also try trickle

---

