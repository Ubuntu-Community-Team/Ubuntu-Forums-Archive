---
title: "Restart needed when changing wireless network"
date: 2010-06-04
forum: Networking &amp; Wireless
---

### Post by prvteprts on 2010-06-04
I don't know if anyone else has noticed this, but whenever I try to switch to a different wifi network, it won't work unless I restart. I think this has been a problem since 9.04, I'm not really sure. Am using 9.10 now, though. Oddly enough, the problem only surfaces when there is a security-enabled network involved.

Here's the setup: I have two routers RouterA and RouterB, where RouterA doesn't have any security, and RouterB requires a WEP key.

Scenario 1:
1) Boot up
2) Connect to RouterA; ok
3) Connect to RouterB; ok
4) Connect to RouterA again; not ok
5) Connect to RouterB again; ok

Scenario 2:
1) Boot up
2) Connect to RouterB; ok
3) Connect to RouterA; not ok
4) Connect to Router B again; ok

So it looks like once I connect to a security-enabled network, I'm stuck with that unless I restart the computer. I think this is also the case when you have two security-enabled networks. I noticed though, that even if I try to connect to RouterA after connecting to RouterB, the message that gets displayed is "RouterB Disconnected". Seems rather strange.

Any ideas on this?

---

