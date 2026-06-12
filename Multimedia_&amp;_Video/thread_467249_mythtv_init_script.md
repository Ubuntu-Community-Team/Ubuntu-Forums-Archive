---
title: "mythtv init script"
date: 2007-06-07
forum: Multimedia &amp; Video
---

### Post by bnuytten on 2007-06-07
The current init script of mythtv does not check if the backend is really started. So when you execute ```
/etc/init.d/mythbackend start
``` you are never sure if it is started or not. I partially rewrote the script to detect if it started correctly or not. I would like to share that code with the developers so everyone can enjoy iy. Where can I post it or send it to?

PS: Yes I know this message does is not really Ubuntu related :twisted:

---

