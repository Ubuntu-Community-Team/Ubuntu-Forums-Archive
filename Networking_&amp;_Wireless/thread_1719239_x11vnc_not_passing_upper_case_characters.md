---
title: "x11vnc not passing upper case characters"
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by tiggyboo on 2011-04-01
Using 10.04 and x11vnc I'm finding that upper case characters are being sent as lower case.  I've tried multiple keyboard configurations with no success - any suggestions?
Thanks,
Al

---

### Post by krunge on 2011-04-05
Maybe try the "-xkb" x11vnc option.

If that doesn't work, add "-dk -dk" to the x11vnc cmdline, reproduce the error by connecting and typing, then attach the full log to this thread.

---

