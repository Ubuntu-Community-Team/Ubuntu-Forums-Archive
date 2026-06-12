---
title: "Likewise and pam_mount on Jaunty?"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by ykill on 2009-05-11
Hi,

Since 2 weeks ago, I try to automount network drives via pam_mount.
On my local profile, it tries to connect (but I don't need it) and on my AD profile, there aren't any log of pam_mount trying to mount the network drive.

I tried everything I could but it never works.

Anyone has an idea?

Thanks!

---

### Post by ndijkstra on 2009-11-10
Have you tried moving [FONT="Courier New"]pam_lsass.so[/FONT] after [FONT="Courier New"]pam_mount.so[/FONT] in [FONT="Courier New"]/etc/pam.d/common-session[/FONT]
```

session optional pam_mount.so
session sufficient pam_lsass.so

```

It seemed to work for me. Hope it does for you too! :D

---

