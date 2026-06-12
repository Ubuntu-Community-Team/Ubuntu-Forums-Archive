---
title: "'banshee --play' from crontab opens a new instance"
date: 2012-12-04
forum: Multimedia Software
---

### Post by Tk0680 on 2012-12-04
What I'm trying to do is have Banshee (which you can assume is already running) start playing at 8:45.

Here's my crontab line:

```
45      8       *       *       1-5             banshee --play
```

Running this command manually through a terminal works fine, it does exactly what I'd hope. However, when cron tries to run it, it just opens a new instance of Banshee and nothing more.

I've tried adding "DISPLAY=:0" just in case, but it didn't make a difference.

Can anyone help?

---

### Post by Tk0680 on 2012-12-12
Bump :(

Anybody able to shed any light on this?

---

