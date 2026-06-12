---
title: "How to restart, reset, or restore routing"
date: 2011-07-22
forum: Networking &amp; Wireless
---

### Post by Skaperen on 2011-07-22
I'm looking for a root shell command which can be executed to completely reset/restore the entire routing table to reflect the configuration.  This needs to include all the LAN routes (e.g. the ones with gateway 0.0.0.0) and default gateway routes (e.g. the ones with network 0.0.0.0).  It would need to delete every route in the kernel's routing table that would not be there after a reboot.

If I reboot, everything is fine.  But if I do restarts on the various network init scripts, I end up with excess junk in the routing table if changes were made which would change what the routing table should be.  Basically, these scripts just add to the table, whereas a reboot obviously clears it out then adds the needed routes.

FYI, these are servers with static IPs and more than one ethernet.

---

