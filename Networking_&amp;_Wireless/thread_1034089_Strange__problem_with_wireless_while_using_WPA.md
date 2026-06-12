---
title: "Strange  problem with wireless while using WPA"
date: 2009-01-08
forum: Networking &amp; Wireless
---

### Post by gnufied on 2009-01-08
Hi,

I am having a weird issue on my Dell Inspiron 1520 running Ubuntu 8.10 when my laptop boots up and attempts to connect to wireless network during Gnome (or other Window Manager startup).

With network-manager it used to take a real long time and many attempts to connect and Network manager is affected by a bug where it was asking WPA passphrase on each attempt. Now I replaced network-manager with WICD and it doesn't ask for the password on each attempt but it still takes a real long time to connect. When I check the syslog, I see following messages:

```
Jan  8 10:16:50 shire kernel: [ 1512.804145] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jan  8 10:16:51 shire kernel: [ 1513.838642] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:16:51 shire kernel: [ 1513.838674] eth1: privacy configuration mismatch and mixed-cell disabled - disassociate
Jan  8 10:16:51 shire kernel: [ 1513.840052] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:16:51 shire kernel: [ 1513.840077] eth1: privacy configuration mismatch and mixed-cell disabled - disassociate
Jan  8 10:16:51 shire kernel: [ 1514.040084] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:16:51 shire kernel: [ 1514.040123] eth1: privacy configuration mismatch and mixed-cell disabled - disassociate
Jan  8 10:16:51 shire kernel: [ 1514.240162] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:16:51 shire kernel: [ 1514.240201] eth1: privacy configuration mismatch and mixed-cell disabled - disassociate
Jan  8 10:16:51 shire kernel: [ 1514.440096] eth1: authentication with AP 00:1b:2f:fe:14:aa timed out
Jan  8 10:16:51 shire kernel: [ 1514.440113] eth1: privacy configuration mismatch and mixed-cell disabled - disassociate
Jan  8 10:16:54 shire kernel: [ 1516.871655] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:16:54 shire kernel: [ 1517.069057] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:16:54 shire kernel: [ 1517.268089] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:16:54 shire kernel: [ 1517.468084] eth1: authentication with AP 00:1b:2f:fe:14:aa timed out
Jan  8 10:17:01 shire /USR/SBIN/CRON[11539]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  8 10:17:12 shire kernel: [ 1535.351802] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:17:12 shire kernel: [ 1535.352437] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:17:12 shire kernel: [ 1535.552154] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:17:13 shire kernel: [ 1535.756103] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:17:13 shire kernel: [ 1535.956491] eth1: authentication with AP 00:1b:2f:fe:14:aa timed out
Jan  8 10:17:31 shire kernel: [ 1553.831870] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:17:31 shire kernel: [ 1553.832443] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:17:31 shire kernel: [ 1554.032155] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:17:31 shire kernel: [ 1554.232153] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:17:31 shire kernel: [ 1554.432115] eth1: authentication with AP 00:1b:2f:fe:14:aa timed out
Jan  8 10:17:49 shire kernel: [ 1572.312112] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:17:49 shire kernel: [ 1572.512216] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:17:49 shire kernel: [ 1572.712169] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:17:50 shire kernel: [ 1572.912172] eth1: authentication with AP 00:1b:2f:fe:14:aa timed out
Jan  8 10:18:08 shire kernel: [ 1590.791944] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:18:08 shire kernel: [ 1590.988156] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:18:08 shire kernel: [ 1591.188175] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:18:08 shire kernel: [ 1591.388165] eth1: authentication with AP 00:1b:2f:fe:14:aa timed out
Jan  8 10:18:26 shire kernel: [ 1609.271890] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:18:26 shire kernel: [ 1609.274729] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:18:26 shire kernel: [ 1609.472182] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:18:26 shire kernel: [ 1609.672180] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:18:27 shire kernel: [ 1609.872184] eth1: authentication with AP 00:1b:2f:fe:14:aa timed out
Jan  8 10:18:44 shire kernel: [ 1627.752058] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:18:45 shire kernel: [ 1627.952174] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:18:45 shire kernel: [ 1628.152156] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:18:45 shire kernel: [ 1628.352189] eth1: authentication with AP 00:1b:2f:fe:14:aa timed out
Jan  8 10:19:03 shire kernel: [ 1646.232036] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:19:03 shire kernel: [ 1646.432179] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:19:03 shire kernel: [ 1646.632157] eth1: authenticate with AP 00:1b:2f:fe:14:aa
Jan  8 10:19:04 shire kernel: [ 1646.832155] eth1: authentication with AP 00:1b:2f:fe:14:aa timed out

```

Whereas Vista connects pretty quickly. I should also mention that once connected Wireless works flawlessly, but it does take real long time to connect and after many failed attempts.

---

