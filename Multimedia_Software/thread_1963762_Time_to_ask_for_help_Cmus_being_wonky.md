---
title: "Time to ask for help: Cmus being wonky"
date: 2012-04-22
forum: Multimedia Software
---

### Post by blithen on 2012-04-22
Heh, the problem keeps changing!
```

mute@SlappyBags:~$ cmus
cmus: connect: Permission denied

```
What is it trying to connect to? :|

---

### Post by blithen on 2012-04-23
After some extensive debugging turns out it was the "roar.so" plugin hanging things up I just removed it from the plugin directory and bam it's fixed.

---

