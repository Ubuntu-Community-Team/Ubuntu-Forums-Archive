---
title: "cannot install mplayer  in ubuntu 6.10"
date: 2007-03-09
forum: Multimedia &amp; Video
---

### Post by smanandhar on 2007-03-09
i installed ubuntu 6.10 recently,
while installing mplayer from source during configure, i et error message of inttype.h not found.
what should i do???

---

### Post by renzokuken on 2007-03-09
i would recommend installing it using automatix to install mplayer instead. installs the latest version but also resolves dependency issues.

that aside, have you installed the necessary packages to be able to compile from source.....namely "build-essential"? if not run

```
sudo apt-get install build-essential
```

and try again

---

