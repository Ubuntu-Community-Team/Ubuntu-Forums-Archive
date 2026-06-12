---
title: "Wake on lan using Dlink 530tx (and 3Com)"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by P86 on 2008-12-16
I'm having a problem getting Ubuntu to start using wake on lan. I have two NICs that support WOL: a Dlink 530-tx (rev. A3) and a 3COM 3C905B-TX. I'm pretty sure the driver for the 3COM doesn't currently support WOL because when I issue the command "ethtool -s eth0 wol g" I get an error something like, "operation not supported".

However, the Dlink driver seems to support WOL because I can get it set to "wake on: g". I've put the Dlink in a system that I have used WOL successfully before (using FreeNAS), put no luck. I've tried it in using Ubuntu server 8.04.1 and 7.10 desktop (liveCD).

I could use some suggestions. Thanks.

---

