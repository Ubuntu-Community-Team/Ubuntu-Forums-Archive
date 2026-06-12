---
title: "mythfrontend crash when scanning for new videos"
date: 2011-01-29
forum: Mythbuntu
---

### Post by jakev383 on 2011-01-29
Fresh install of 10.10, done two weeks ago.
When I scan for new videos, it runs through and sometimes when it gets to ~96% complete, mythfrontend crashes and I'm back at the desktop. When looking at the logs, I'm left with this:

```

/var/log/messages
Jan 29 19:32:31 myth-frontend kernel: [29830.872400] show_signal_msg: 9 callbacks suppressed
Jan 29 19:32:31 myth-frontend kernel: [29830.872407] mythfrontend.re[1298]: segfault at cdae000 ip 01eacfd1 sp bfb1fb1c error 4 in libc-2.12.1.so[1e37000+157000]

```

Appears something wonky with libc. It does not happen all of the time - probably 50% of the time.
Any ideas?
Thanks.

---

### Post by nickrout on 2011-01-30
googling finds others with similar problems:

google on mythfrontend.re: segfault  error 4 in libc-2.12.1.so

---

