---
title: "How to disable pptp client messages"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by Sapfeer on 2009-07-12
Hello!

I'm using 9.04 and I want to change log level of my pptp client or redirect it somewhere else than in system logs... I have the following messages in my system logs:
```
Jul 12 15:53:31 lenovo-y510ka pptp[5369]: anon log[decaps_gre:pptp_gre.c:414]: buffering packet 31077 (expecting 31075, lost or reordered)

```It's fills logs so much that it is begin to annoying me:
```
[ lenovo-y510ka@user Sun 12 Jul 2009 03:58:26 PM MSD ]
/home/user $ grep -c pptp /var/log/syslog*
/var/log/syslog:10598
/var/log/syslog.0:244168
```What config file should I alter to make it out?..

---

