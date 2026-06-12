---
title: "slow LAN transfers in one direction"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by graysky on 2008-12-08
I'm having very slow LAN transfers from problematic machine to other boxes (some Debian/some Ubuntu).  ALL the machines are running with the identical gigalan NIC behind a gigalan switch.  What I can't understand is why I'm only getting ~4-6 MB/s when I scp a file **from** this particular machine to ANY other machine on my LAN.  The problem only occurs in one direction - speeds are on the order of 30-31 MB/s when that same machine downloads from any other machine on the LAN.

This the true if I use scp or samba.

All machines are using the skge driver.  I would really appreciate any info you guys can provide that would help me tweak the network settings.  I'd be glad to post any config file or log.

Thanks!

---

