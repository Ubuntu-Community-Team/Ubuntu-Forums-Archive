---
title: "Multiple TCP and mDNS connections when no application is open"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by Truthiswithin on 2009-08-14
I've recently noticed that my Internet is constantly working, and opening connections at an alarming rate; it seems to have an adverse effect on my Internet speed as well, though I'm not exactly sure.  Please take a look at the attached screenshot (EtherApe) and let me know why so many connections appear when I am doing nothing.  Thanks in advance.

---

### Post by nixscripter on 2009-08-15
You can narrow it down by identifying which application has all the connections open. Run this in the command line:

```
lsof | grep IPv4
```

Hope this helps.

---

### Post by Truthiswithin on 2009-08-15
> **nixscripter said:**
> You can narrow it down by identifying which application has all the connections open. Run this in the command line:

```
lsof | grep IPv4
```

Hope this helps.

Thanks a bunch, that is the sort of command I was looking for... I figured out the problem, I think... I had a port open for BitTorrent, and after closing down BitTorrent, all of the ex-peers were still trying to contact me... or something like that.  Does that make sense?

Anyway, when I closed the port on my router, it all disappeared.  Is there any way to stop that once I've closed down Transmission, or am I misinterpreting things?

---

### Post by nixscripter on 2009-08-16
It's a side effect of the TCP protcol, depending on how the client closes. If the ports were just closed, then the "hey guys, hang up now" message (FIN-ACK) was dropped. It should time out eventually.

Glad I could help. Don't forget to mark this thread as Solved (under the thread tools menu).

---

