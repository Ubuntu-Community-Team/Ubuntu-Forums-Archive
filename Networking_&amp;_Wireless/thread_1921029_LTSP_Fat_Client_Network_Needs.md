---
title: "LTSP Fat Client Network Needs"
date: 2012-02-05
forum: Networking &amp; Wireless
---

### Post by jv13613 on 2012-02-05
About how much network bandwidth is used by a LTSP fat client when just browsing the web (minus the bandwidth to connect to the internet)? And is there a way to make the fat client swap to a local hard drive?

Thanks!

---

### Post by yarick on 2012-04-21
Doesn't it work automatically if you create a swap partition on a local disk?

---

### Post by yarick on 2012-04-23
On   [http://manpages.ubuntu.com/manpages/lucid/man5/lts.conf.5.html](http://manpages.ubuntu.com/manpages/lucid/man5/lts.conf.5.html)  One can read:    USE_LOCAL_SWAP            boolean, default False             If you have a hard drive installed in the thin client, with a valid            swap partition on it, this parameter will allow the thin client to            swap to the local hard drive.

---

