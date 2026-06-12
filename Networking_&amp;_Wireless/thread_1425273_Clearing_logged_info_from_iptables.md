---
title: "Clearing logged info from iptables?"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by ownaginatious on 2010-03-08
This is actually for my router, but it's linux based, so I'm hoping someone may be able to help.

Anyway, I currently have a router running tomato linux firmware and at 30 minute intervals I have it send a log file of bandwidth usage to a network drive.

From there, a program calculates the bandwidth used by each IP by adding up all the totals recorded in the log files.

The log files are the output of the router running the command:

```
iptables -L traffic_in -vn
```

What doesn't happen though, which I'd prefer, is that the bandwidth counts inside the router get cleared upon writing each log file. This way, I don't end up counting the same bandwidth use multiple times.

So my question is, is there a way to erase/reset the data count in the iptables?

Thanks,

Dillon

---

### Post by r939ick on 2010-03-08
From `man iptables`:

       -Z, --zero [chain]
              Zero the packet and byte counters in all chains.  It is legal to
              specify the -L, --list (list) option as well, to see  the  coun-
              ters immediately before they are cleared. (See above.)

---

### Post by Rubicon_82 on 2010-03-08
Try the '-Z' flag for iptables:

[quote="man iptables"]
-Z, --zero [chain]
Zero the packet and byte counters in all chains.  It is legal to specify the -L, --list  (list) option as well, to see the counters immediately before they are cleared. (See above.)
[/quote]

---

### Post by ownaginatious on 2010-03-08
Awesome, exactly what I needed. Thanks!

---

