---
title: "Ike tunnel causes system crash and hang"
date: 2012-12-10
forum: Networking &amp; Wireless
---

### Post by cyb0rgb0rg on 2012-12-10
Hello.

Trying to pass traffic through a tunnel provided by ike causes my system crash and burn.

Please instruct me what diagnostics to provide.

I did a...

```
tail -f /var/log/messages
```

...and I do see some mysterious stuff before it freezes.

I'm running 10.04 with 2.6.38-16 on an Alienware m14x 1st gen. I've done this setup many times on this hardware and Ubuntu version so it puzzles me why it crashes. I install ike through the software center, import my site, fix the rpfilter and usually it just works. Now it connects, gets tunnel, and I can leave it there for hours, but as soon as I pass a packet, the system gets choppy and then dies. Seems to me like something with the wlan driver but what hey do I know?

---

### Post by cyb0rgb0rg on 2012-12-19
Weekly bump. Does anybody know where and how to start debugging this?

---

### Post by cyb0rgb0rg on 2012-12-30
:-s

---

### Post by cyb0rgb0rg on 2013-01-08
Have to keep bumping this. Soon, I'll probably try to reinstall the OS but then all the testdata is gone. (Unless I can replicate it).

Did try reinstalling ike though. Same problem.

---

