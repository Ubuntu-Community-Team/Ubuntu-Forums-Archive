---
title: "temporary cifs file"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by kellemes on 2009-06-26
Working from Arch..

Mounting my nas using cifs like so..

```
/PathToNas /PathToMountPoint cifs user,uid=1000,rw,suid,credentials=credentialsfile 0 0
```
All is fine..

It's just that often temporary files are written to the directories (on the nas) I'm working on.. that I can't get rid of.
They are named like so.. *cifs69c7*. When I delete such a file, immediately a new file is created with another name..
This means I can't get rid of the directory these files are written to..

Does anyone know why these files are created?
Is there a way to stop this from happening?

---

### Post by kellemes on 2009-06-27
bump

---

### Post by kellemes on 2009-07-01
No clue?

---

### Post by kellemes on 2009-07-03
Well.. my tmp environment-variables where not set.
And krusader's tmp directory pointed to a non-existing location.
Guess this fixed the issue.

---

