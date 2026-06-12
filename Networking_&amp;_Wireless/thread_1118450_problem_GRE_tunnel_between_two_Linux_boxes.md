---
title: "problem GRE tunnel between two Linux boxes"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by fjunibel on 2009-04-07
Hello,

I've set up a GRE tunnel between two Linux boxes and it's working well,
with or without IPSEC (under GRE). The problem is that when I have no
traffic for some minutes, side A cannot communicate to side B any more,
unless side B tries to communidate to side A. The same thing happens in
the other direction.

For example, side A pings side B. No reply. Keep pinging.

Side B pings side A. Reply ok. Side A starts getting reply from side B
too.

Is there a "keep alive method" for GRE tunnels. I know that if I keep a
ping once a minute, that would fix the problem, but I'm looking for
something that isn't a band aid.

Thanks.

---

