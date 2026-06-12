---
title: "How to make Ubuntu, uShare and xBox 360 play nice - Take 2"
date: 2009-11-29
forum: Multimedia Software
---

### Post by sideshowmel on 2009-11-29
In reference to this article:

[http://ubuntuforums.org/showthread.php?t=632428](http://ubuntuforums.org/showthread.php?t=632428)

If you want an easy way to schedule a refresh of the uShare database, add the following to your crontab:

```
*/2 * * * * wget --delete-after "http://127.0.0.1:49153/web/ushare.cgi?action=refresh"
```

It's a pretty good app, and the above has helped me out.

---

### Post by abandonedthe_mulletator on 2010-01-25
I have been running Ushare for over a year now and it works well.  The only problem I have is some videos lag pretty bad.  I have not figured out why.  Anyone else have this problem?

---

