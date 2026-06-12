---
title: "Can't get rid of Neighbor table overflow messages even after tuning"
date: 2012-07-27
forum: Networking &amp; Wireless
---

### Post by MechaMechanism on 2012-07-27
[FONT=-moz-fixed]Logs are getting clogged with Neighbor table overflow messages.  Even after tuning I'm still getting the log entries.  My sysctl.d setup. >  # Prevent "Neighbor table overflow" messages from clogging the logs. net.ipv4.neigh.default.gc_thresh1 = 4096 net.ipv4.neigh.default.gc_thresh2 = 8192 net.ipv4.neigh.default.gc_thresh3 = 8192 net.ipv4.neigh.default.gc_interval = 86400 net.ipv4.neigh.default.gc_stale_time = 86400 net.ipv4.neigh.default.base_reachable_time = 8640 [/FONT]

---

### Post by MechaMechanism on 2012-07-31
Bump.

---

