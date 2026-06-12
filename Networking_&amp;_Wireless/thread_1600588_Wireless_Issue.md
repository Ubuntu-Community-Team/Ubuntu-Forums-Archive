---
title: "Wireless Issue"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by amainejr on 2010-10-19
Hey all.  My wireless stopped working yesterday for some reason.  It will actually obtain an IP address from my router, and connect to the router's interface address via HTTP and I can ping any local resources.  However, if say I go to [www.hotmail.com](www.hotmail.com) Firefox continues to say Connecting to [www.hotmail.com](www.hotmail.com).  It seems like a DNS issue to me, but all my other network computers still connect outbound.  The only thing I did yesterday that I can think of that would effect it, is ran 

```
sudo wireshark
```

And started listening on my wireless interface without going into promisc mode.  This has never cause a problem before, but I also updated my system yesterday.  Any thoughts on how to resolve this or commands I need to run?

---

### Post by lovinglinux on 2010-10-19
Have you tried to disable ipv6? See the fifth item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

---

