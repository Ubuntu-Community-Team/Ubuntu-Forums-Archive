---
title: "Banshee will no longer start - Ubuntu 13.04"
date: 2013-08-13
forum: Multimedia Software
---

### Post by chrisco23 on 2013-08-13
I've been using Banshee on Ubuntu for years, and on 13.04 specifically since 13.04 was released.
I update my system regularly but can't think of anything likely to cause the error, which is:

```
Unhandled Exception: System.IO.FileNotFoundException: No such file or directory ---> Mono.Unix.UnixIOException: No such file or directory [ENOENT].
```

I googled the error and found threads dating back to 2005 but none of the answers has worked for me.

I also uninstalled and reinstalled banshee with no luck.

Any ideas what this is about?


Thanks,
Chris

---

### Post by Yellow Pasque on 2013-08-13
If you start with --debug, does it give more verbose output?
```
banshee --debug
```

Another you could try is creating a new user and see if banshee works for them. If so, it's probably an issue with your user's banshee config.

---

