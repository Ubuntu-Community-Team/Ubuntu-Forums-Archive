---
title: "Ardour problems with JACK Libraries..."
date: 2008-03-08
forum: Multimedia Production
---

### Post by dbsoundman on 2008-03-08
OK, so I kind of messed up. I had Ardour 2.3 and all was well, then I uninstalled it because I thought I had a problem with it not syncing right with JACK, blah blah blah. I attempted to install the new version of Jack and qjackctl and succeded...sort of. I seem to have BOTH versions of qjackctl now, but only the old version works. The new one (3.2) gives me a similar error message to what I get when I try to start my new installation of Ardour now. This is what it says:
```
dan@blackdiamond:~/Desktop/ardour-2.3$ ardour2
/usr/local/lib/ardour2/ardour-2.3: error while loading shared libraries: libjack.so.0: cannot open shared object file: No such file or directory

```

That file is most definitely in existence, but it seems that something about it isn't right. I'm thinking I need a fresh install of Jack and such, but I'm not quite sure how to get rid of all that in the first place to reinstall. What should I do?

-Dan

---

