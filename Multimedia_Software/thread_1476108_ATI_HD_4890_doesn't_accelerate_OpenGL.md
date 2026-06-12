---
title: "ATI HD 4890 doesn't accelerate OpenGL"
date: 2010-05-07
forum: Multimedia Software
---

### Post by Overv on 2010-05-07
I've just installed the proprietary ATI drivers from the AMD website and that all went fine. After that I restarted my pc and executed the following in the terminal:

```
atiode -P60 -H localhost:0; echo $?
```

However, that returns 2 which means that a render error occurred. Also, OpenGL reports that shaders are not supported.

What could be the problem?

---

### Post by Overv on 2010-05-11
No-one?

---

### Post by Overv on 2010-05-23
This is keeping me from using Ubuntu, so I'd really like some help.

---

### Post by xzero1 on 2010-05-24
I use a 4770 which I believe is the series chip using the stock radeon driver. Although a bit slow, I can still play *some* games like Nexuiz even though the driver is not complete. Video playback is fine. If you really want to get the proprietary driver working, the xorg log should give you a clue.

---

