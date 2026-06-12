---
title: "Evolution w/autofs on laptop: a solution"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by bilkay on 2010-09-04
The problem: When running evolution in an autofs mounted ~/.evolution directory on a laptop, on logout or shutdown, you will lose your wireless connection before your nfs mounted directory unmounts, causing loss of data. This is a result of evolution keeping processes alive after it exits.

A solution: Put the following script named evolution in /usr/local/bin (assuming /usr/local/bin comes before /usr/bin in $PATH):
```
#! /bin/bash

/usr/bin/evolution $*

/usr/bin/evolution --force-shutdown
```

Also, you'll want to shorten the autofs timeout, e.g., this line in /etc/auto.master:

```
/userdirs       /etc/auto.userdirs --timeout=10
```

---

