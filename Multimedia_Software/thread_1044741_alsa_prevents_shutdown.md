---
title: "alsa prevents shutdown"
date: 2009-01-19
forum: Multimedia Software
---

### Post by gene02 on 2009-01-19
After upgrading my system to 7.10 I've been unable to bring the system down using the shutdown command.  I discovered that it was alsa-utils that was preventing shutdown and manually killing it would allow shutdown to proceed.  This is what I see in ps:

```
root     19513 19120  0 23:50 ?        S      0:00  \_ /bin/sh /etc/rc6.d/K50alsa-utils stop
root     19523 19513  0 23:50 ?        D      0:00      \_ alsactl store

```

Does anyone have any suggestions for fixing this problem?  
Thanks

---

