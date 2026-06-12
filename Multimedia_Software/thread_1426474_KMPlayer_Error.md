---
title: "KMPlayer Error"
date: 2010-03-10
forum: Multimedia Software
---

### Post by leinad177 on 2010-03-10
i just installed kmplayer and when i try to play any kind of file it wont load

so i looked at the console thingy and it said

   */bin/sh: mplayer: not found*

can somebody please tell me how to fix this?

---

### Post by andrew.46 on 2010-03-10
Hi leinad,

> **leinad177 said:**
> 

```
/bin/sh: mplayer: not found
```



I do not use KDE but I can see that KMPlayer is a frontend for MPlayer and perhaps you do not have MPlayer installed? Try running:

```
which mplayer
```

and if it is not found you will need to run:

```
sudo apt-get install mplayer
```

All the best,

Andrew

---

