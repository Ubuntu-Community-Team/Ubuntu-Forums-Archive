---
title: "Samba's fault, or Windows Vista?"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by mbelos on 2008-12-08
Hi all,

I had a really strange issue. In my samba config, I have 4 shared folders - 3 of them have ```
guest ok = yes
```, while the other doesn't (requiring users to authenticate before they have access to the folder). For some strange reason, if you map a network drive to the location, then try to access the private folder, all authentication attempts fail. If you disconnect the mapped drive, then everything is ok. You can then map the drive without issues after...

Is this Vista misbehaving, or samba?

---

