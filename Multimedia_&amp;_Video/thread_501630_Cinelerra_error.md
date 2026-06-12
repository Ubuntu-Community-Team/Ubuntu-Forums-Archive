---
title: "Cinelerra error"
date: 2007-07-15
forum: Multimedia &amp; Video
---

### Post by zhinker on 2007-07-15
Hi, I'm trying to run Cinelerra but I keep getting this error:

```
void MWindow::init_shm():WARNING:/proc/sys/kernel/shmmax is 0x2000000, which is too low.
Before running Cinelerra do the following as root:
echo "0x7fffffff" > /proc/sys/kernel/shmmax
```

I tried doing "sudo echo "0x7fffffff" > /proc/sys/kernel/shmmax" but it says 
"bash: /proc/sys/kernel/shmmax: Permission denied"

I've already tried the fix kr152ta suggests [here]("http://ubuntuforums.org/showthread.php?t=399941").  It didn't do anything for me.

Could someone help me out here please?

---

