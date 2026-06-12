---
title: "gvfs-afc-volume frequently using up 100% cpu"
date: 2012-04-03
forum: Multimedia Software
---

### Post by IsmAvatar on 2012-04-03
I'm running Ubuntu 11.10 (2 users, each with a user account), and I also have an iPod Touch which I occasionally plug in (pretty much for the sole purpose of recharging).

As a result, I'm frequently encountering extreme sluggishness of my desktop during normal non-intensive usage, which is unusual since I have 4 gHz dual-core processor with 6 GB of RAM.

Going into the terminal and typing `top` reveals the culprit:
gvfs-afc-volume is using 100% cpu. I kill the process, and suddenly everything is running smooth again. At least until the next time.

Any way to stop it from doing this? I've read up on it a little, and found reports going back to 9.04, mostly just saying "don't uninstall it because it's for your ipod".

---

### Post by IsmAvatar on 2012-04-04
Help please?

---

### Post by IsmAvatar on 2012-04-07
I'm still having this issue. Here's the top process information from `top`:

```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
26901 ismavata  20   0 21008 3740 3156 S  100  0.1  48:46.97 gvfs-afc-volume    
26648 ismavata  20   0  832m 403m  45m S   14  6.7   3:47.41 firefox         
... several other processes listed with %CPU below 10
```

I would greatly appreciate any ideas.

---

