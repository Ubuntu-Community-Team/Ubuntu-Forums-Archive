---
title: "All networking died"
date: 2009-09-07
forum: Networking &amp; Wireless
---

### Post by lduperval on 2009-09-07
Hi,

For some bewildering reason, all networking died on my laptop (Broadcom wireless). I works on Windows, but nothing happens when I boot Jaunty. When I do a /etc/init.d/network start, I get an OK message but wired and wireless networking show no activity.

When I do lsmod, I see the wl driver (for broadcom) listed, there are no errors in t=messages file, but I still get nothing.

I tried reinstalling the dbus packages, but it says it needs to download information, and of course, I can't do that.

Any idea where to look or where to go to try to fix this?

FWIW, It Was Working Fine Before (tm) and I Didn't Install Anything New (tm). Really... Well, not quite: I installed a bunch of games yesterday, and I rebooted this morning. Before the reboot, all was fine. After...

L

---

