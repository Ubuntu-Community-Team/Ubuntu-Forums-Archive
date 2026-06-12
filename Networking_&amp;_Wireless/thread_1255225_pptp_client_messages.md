---
title: "pptp client messages"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by Sapfeer on 2009-09-01
Hello!

I'm using 9.04 and I want to change log level of my pptp client or redirect it somewhere else than in system logs... I have the following messages in my system logs:
```
Sep  1 15:22:50 lenovo-y510ka pptp[3340]: anon log[decaps_gre:pptp_gre.c:414]: buffering packet 30118 (expecting 30117, lost or reordered)

```It fills logs so much that it begins to annoying me:
```
/home/user $ grep -c pptp /var/log/syslog*
/var/log/syslog:31789
/var/log/syslog.0:27944
```What config file should I alter to make it out?..

---

