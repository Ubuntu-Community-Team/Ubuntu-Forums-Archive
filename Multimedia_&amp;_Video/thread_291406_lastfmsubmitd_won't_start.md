---
title: "lastfmsubmitd won't start"
date: 2006-11-02
forum: Multimedia &amp; Video
---

### Post by Hairy Dude on 2006-11-02
I just upgraded from Dapper to Edgy (using the recommended method). It failed trying to upgrade lastfmsubmitd. I think I probably got my old package from Debian, but in any case, when I try to start it, I get this:

```
Starting Last.fm submission daemon: Traceback (most recent call last):
  File "/usr/bin/lastfmsubmitd", line 13, in ?
    import lastfm.config
ImportError: No module named config
```

The package in Debian Testing also has this problem. I'm sure it can't have got into Testing (or indeed Edgy) if everyone is getting this, so what am I missing?

---

### Post by Hairy Dude on 2006-11-02
Oh yes, purging the package and reinstalling it doesn't help.

---

