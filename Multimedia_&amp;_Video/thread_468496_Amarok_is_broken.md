---
title: "Amarok is broken"
date: 2007-06-08
forum: Multimedia &amp; Video
---

### Post by Rhapsody on 2007-06-08
Recently, I started using the Medibuntu repository since I wanted the things on there. Things have mostly gone to plan, but the update it downloaded for Amarok seems to have broken it. Nothing happens when trying to load through the K Menu or via a terminal (it just keeps loading indefinitely until I kill it with Ctrl+C). On the advice of someone else, I tried an strace on Amarok, which revealed it getting stuck in an infinite loop with the following two lines:

```
nanosleep({0, 100000}, NULL)            = 0
waitpid(5978, 0xbfc709c0, WNOHANG)      = 0
```

I have no idea what's happening here.

---

### Post by trippinnik on 2007-06-09
Try a sudo aptitude purge amarok
then install it again.  It may be a configuration thing...

---

### Post by qrees on 2008-05-20
> **trippinnik said:**
> Try a sudo aptitude purge amarok
then install it again.  It may be a configuration thing...

Tried this, but didn't solve the problem. I've tried running amarokapp instead of amarok and this helped. Also selecting correct sound engine helped. Anyway, seems that this haven't been corrected for almost a year :(

---

