---
title: "DNS issue on reboot"
date: 2011-03-02
forum: Networking &amp; Wireless
---

### Post by axy666 on 2011-03-02
I've got an issue with my 10.10 server that after it's rebooted it's unable to ping any external IP at all, however after restarting the networking service it can do so. 

Any help would be appreciated, I've checked everything and it looks fine, but there could be something I'm missing.

---

### Post by axy666 on 2011-03-03
I think I may have cracked it. I'm thinking it's down to the resolv.conf file not being populated by resolvconf on reboot. I'm going to try and prepend the DNS servers to see if that works, else I'll just uninstall resolvconf and manually enter the DNS servers. Will update when I try.

---

### Post by axy666 on 2011-03-03
This is now resolved - seeing I run on a static IP I've removed the resolvconf program so my resolv.conf is now manually created.

---

