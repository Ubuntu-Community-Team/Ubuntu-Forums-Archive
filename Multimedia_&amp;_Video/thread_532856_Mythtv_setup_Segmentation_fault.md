---
title: "Mythtv setup: Segmentation fault"
date: 2007-08-23
forum: Multimedia &amp; Video
---

### Post by jonim8or on 2007-08-23
Hi,

I've installed mythtv on my Compaq system using adept manager:
Amd sempron 2800+
Geforce 6200 video card
Zolid tv tuner card

Now I had to let it add me to the mythtv group, and then restart the session. Now i have to run mythtv-setup, but it gives me a segmentation fault:
```

jonie@jonie-desktop:~$ mythtv-setup
Stopping MythTV server: mythbackend
No /usr/bin/mythbackend found running; none killed.
.
2007-08-23 14:27:39.340 Using runtime prefix = /usr
2007-08-23 14:27:39.347 DPMS is active.
2007-08-23 14:27:39.373 New DB connection, total: 1
2007-08-23 14:27:39.379 Connected to database 'mythconverg' at host: localhost
2007-08-23 14:27:39.381 Total desktop dim: 2048x1024, with 2 screen[s].
2007-08-23 14:27:39.388 Using screen 0, 1280x1024 at 0,0
2007-08-23 14:27:39.399 Current Schema Version: 1160
Segmentation fault (core dumped)
Restarting MythTV server: mythbackend
No /usr/bin/mythbackend found running; none killed.
.
.
jonie@jonie-desktop:~$      

```

the segfault occurs in the *mythtv-setup.real* part of the program. Any clues on how to fix it?

---

