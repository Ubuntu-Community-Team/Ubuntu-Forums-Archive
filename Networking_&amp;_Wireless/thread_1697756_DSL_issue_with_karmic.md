---
title: "DSL issue with karmic"
date: 2011-03-01
forum: Networking &amp; Wireless
---

### Post by s_ale on 2011-03-01
When I installed karmic DSL was working fine out of the box. At some  point this stopped. Meanwhile this is not an HW issue, because it had  always and still does with my Slack installation on  the same PC.
So I thought I'd just copy  my resolv.conf and rc.inet1.conf from my  slack partition, but there is not even an rc.d directory in karmic. I  also found  "Ubuntu community documentation"  telling me to run  pppoeconf, which I did,  but it still will not work. plog says  lcp  tunnel failed. Meanwhile pppoeconf never asked me about Ip address and  netmask, as rc.inet1.conf in slack. Any suggestions what to try? SHould I  just create an rc.d and copy the slack files or is there something else  to fix  with ubuntu tools alone?

---

