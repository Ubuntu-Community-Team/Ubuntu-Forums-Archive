---
title: "Linksys PCMCIA card issue"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by odin942zx on 2009-12-06
Hello,

I just upgraded a laptop from version 9.04 to 9.10.  I've been using a Linksys PCMCIA card that uses the atheros chipset.  Before the upgrade, this wireless adapter seemed to work fine, but after the upgrade, the laptop will not even recognize the adapter.  It will not show up in 'ifconfig -a' or in any of the networking settings, etc.

---

### Post by chili555 on 2009-12-06
Perhaps we need to remind it what driver module to use to get it going again. Please open a terminal and do:```
lspcmcia -v
```Please post the result.

---

