---
title: "[SOLVED] Building Rhythmbox from Source"
date: 2009-07-22
forum: Multimedia Software
---

### Post by UnsafeData on 2009-07-22
```
john@john-desktop:~$ rhythmbox
rhythmbox: error while loading shared libraries: librhythmbox-core.so.0: cannot open shared object file: No such file or directory
john@john-desktop:~$ 
```

So how do I get this **librhythmbox-core.so.0** and what do I do with it? Or what else is the problem?


I am building the latest Rhythmbox from source, and I'm running Ubuntu 8.10.

---

### Post by UnsafeData on 2009-07-22
**I GOT IT WORKING USING THIS COMMAND**:



```
sudo cp /usr/local/lib/librhythmbox-core.so.0 /usr/lib
```

---

