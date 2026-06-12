---
title: "Can I Persist TCP Connections When Wireless Drops?"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by dannyman on 2009-08-05
Hello,

So, the wireless setup is nice enough, but occasionally a connection will drop, then re-connect.  This isn't a big deal for web browsing, but when you have remote shells, bastion proxies, VPNs going, it can suck.

Back in the old days I configured PPP on FreeBSD to dial on demand into my ISP, where I had a static IP.  If traffic needed to go to the Internet, the line picked up, dialed, connected.  If there were no traffic, the line dropped.  I had idle SSH connections up for WEEKS at a time over this link.

Can I do with with the wireless?  I like to think I can frob a setting somewhere so that if the link goes down, we won't "clean up" the interface settings but leave them as they are, then when the link picks up with the same AP, assuming I get the same IP and there hasn't been a timeout, my persistent connections will pick up where they left off.

Surely, I am not the first to have desired this . . . can someone give me a tip?  Thanks!

Sincerely,
-daniel

---

### Post by dannyman on 2009-08-05
(Actually, I think my SSH connections ARE persisting . . .)

---

### Post by dannyman on 2009-08-10
They are persisting!

(Can I delete this bogus thread?)

---

