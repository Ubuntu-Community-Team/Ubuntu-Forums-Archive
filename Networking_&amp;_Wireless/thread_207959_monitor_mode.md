---
title: "monitor mode"
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by Thund3rstruck on 2006-07-02
How do I exit monitor mode? Kismet warns me that sometimes I does not exit monitor mode cleanly and I'll need to restart or reconfigure the interface.

How do I do that exactly?

---

### Post by tturrisi on 2006-07-02
You should not have to exit it manually, that's just a warning from kismet.  If have to manually exit monitor mode then do this in a terminal:

iwconfig eth0 mode Managed

where eth0 = your interface.  It could be ath0, etho0, eth1, etc etc, depending on your card.

---

### Post by Thund3rstruck on 2006-07-03
Thanks.. thats what I needed. I ran a tutorial yesterday that had me flip into monitor mode but failed to tell how to return from it. (I noticed kismet displayed that warning as well)

appreciate it
T3

---

