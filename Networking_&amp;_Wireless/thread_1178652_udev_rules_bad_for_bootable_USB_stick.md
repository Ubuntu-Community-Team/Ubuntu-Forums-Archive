---
title: "udev rules bad for bootable USB stick"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by james_steward on 2009-06-04
Hi,

I did a netinstall of 8.04.2 for a CLI only embedded app.  Everything worked great on the first mobo, but then every other mobo I tried booting on had no ethernet.  Finally I discover that udev is being too smart and renaming eth0 and eth1 to something else, because every mobo has a different MAC addr from the last.

So, I need to tell udev to not mess with the names.  How do I do this?  I've had a quick look at the udev rules files and so on, but don't yet see a way around this problem.

Cheers,
James.

---

### Post by t0mppa on 2009-06-04
Check your /etc/udev/rules.d/70-persistent-net.rules file. Cleaning up the extra interfaces from there helped me, when I had similar issues.

---

