---
title: "Kdenlive crashes too much"
date: 2008-07-19
forum: Multimedia Software
---

### Post by MaxIBoy on 2008-07-19
It crashes while starting up, or it crashes thirty seconds to five minutes after starting up. Great program, but it's unusable. The name implies that it's for KDE, but I'm using Gnome. Also, the error says something about "drkonqi." I tried installing this "drkonqi" and here's what happened:
```
maxtothemax@maxtothemax-laptop:~$ sudo apt-get install drkonqi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package drkonqi is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  kdebase-runtime-data
E: Package drkonqi has no installation candidate
maxtothemax@maxtothemax-laptop:~$ sudo apt-get install kdebase-runtime-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kdebase-runtime-data is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
maxtothemax@maxtothemax-laptop:~$ 

```

---

