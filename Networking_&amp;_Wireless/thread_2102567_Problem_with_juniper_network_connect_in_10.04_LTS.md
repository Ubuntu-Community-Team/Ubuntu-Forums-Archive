---
title: "Problem with juniper network connect in 10.04 LTS"
date: 2013-01-07
forum: Networking &amp; Wireless
---

### Post by r40778 on 2013-01-07
Hello,

I have a problem using Juniper Network Connect in 10.04 LTS.

The script runs fine, initializes the tunnel, but apparently fails to initialize the name servers correctly.
I found it overwrites /etc/resolv.conf, and writes the apparently correct nameserver there, but on my system, the nameservers seem not controlled by this. There are various scripts that take care of it, and /etc/resolv.conf is not the entry point.
Now, how should I fix this ?

Best Regards,

Pete

---

