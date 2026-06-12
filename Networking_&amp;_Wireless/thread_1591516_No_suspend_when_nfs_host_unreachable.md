---
title: "No suspend when nfs host unreachable"
date: 2010-10-09
forum: Networking &amp; Wireless
---

### Post by drhex on 2010-10-09
Ubuntu 10.04 with the latest updates on an Amilo M3438G.
Suspend normally works fine on this machine (but requires the proprietary nvidia drivers to wake up properly).

However, if there is a directory mounted over nfs or samba and the network host sharing the files is unreachable when suspend is attempted, then suspend fails (i.e. screen shows funny patterns for a while and blanks out for a few seconds after which it comes back with a password dialog)

Is there a way to automatically make suspend succeed even if an nfs/samba host is unreachable?

---

