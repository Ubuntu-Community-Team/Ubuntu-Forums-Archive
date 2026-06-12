---
title: "Connect USB device to remote desktop"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by mad_max0204 on 2009-05-02
Hi guys,

how can I connect my USB printer and USB scanner to a remote computer running WinXP ?

I'm running 9.04 64bit.

I have read that there is some software that does this but I can't find it.


Thanks

---

### Post by dandnsmith on 2009-05-02
You can share the printer on XP, and connect using it as  remote Windows (SMB) printer.

If it's an all-in-one device as printer/scanner/copier, then you're out of luck (I believe), unless the manufacturer happens to support the remote use of scanner.

---

### Post by mad_max0204 on 2009-05-02
How can I share it on XP when its connected to my Ubuntu box ??

My question is how can I use my printer and scanner connected to my Ubuntu box
on remotely connected windowsxp.

---

### Post by dandnsmith on 2009-05-03
Ah! Daylight dawns - wrong interpretation of 'connection' (by me).

Similar response, with difference in detail.
You have to set up SAMBA, and get it to share the printer with the outside world (in a limited fashion). The package installer can do a lot of the work by being asked about packages which involve smb (use this to search on), and then there is a samba.org site (If I recall correctly) which can get you started on the configuration of both ends of the link.

The scanning is still a problem - some years ago I experimented with this using SANE, which is a set of tools to allow uses of scanners where the manufacturers don't provide the environment you want. At the time there was a hurdle I couldn't overcome - but techniques in the computing field advance, and googling may offer solutions.

---

### Post by mad_max0204 on 2009-05-03
Can this be done with other USB devices ??

Memory sticks, cameras, ....

---

### Post by dandnsmith on 2009-05-03
It certainly can - just make sure they are mounted, and then set up shares for the mount point(s).

---

