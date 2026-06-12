---
title: "gtkPod from source"
date: 2010-02-25
forum: Multimedia Software
---

### Post by mastermindg on 2010-02-25
I removed gtkPod and libgpod and installed the newest source manually so that I can have access to the the 3.1.2 filesystem (hopefully). 

I installed libgpod in the default path /usr/local/lib. gtkPod is failing to launch because it's not finding libgpod. Any ideas how I can set gtkPod straight?

---

### Post by Crafty Kisses on 2010-02-26
Can you give me the exact error from the terminal?

---

### Post by nothingspecial on 2010-02-26
Try this

```
sudo ln -s /usr/local/lib/libgpod.so.4* /usr/lib
```

---

### Post by mastermindg on 2010-03-08
I ended up reinstalling from scratch and now I've got gtkPod and RhythmBox up and working fine. RhythmBox is still a little buggy on video transfers, but I can wait for updates.

Thanks. KJ.

---

