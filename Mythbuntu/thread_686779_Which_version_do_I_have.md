---
title: "Which version do I have"
date: 2008-02-03
forum: Mythbuntu
---

### Post by uncle hammy on 2008-02-03
Is there a simple way to determine which version of mythtv I'm currently running?

---

### Post by hyperair on 2008-02-03
```
apt-cache policy mythtv
``` 

That should give an output something like...
```
mythtv:
  Installed: (none)
  Candidate: 0.20.2+fixes15513-0ubuntu4
  Version table:
     0.20.2+fixes15513-0ubuntu4 0
        500 http://tw.archive.ubuntu.com hardy/multiverse Packages
```
In my case it shows Installed: (none), but in your case it'll show the version that you have installed.

---

### Post by uncle hammy on 2008-02-03
Thank, worked a charm!

---

