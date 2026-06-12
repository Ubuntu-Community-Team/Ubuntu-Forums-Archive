---
title: "headphones not working"
date: 2011-09-15
forum: Multimedia Software
---

### Post by arabookworm on 2011-09-15
I posted about this in an existing thread, but haven't gotten a response, so I'm starting a thread about it in hopes that someone can help me. I installed ubuntu 2 days ago and ever since then headphones haven't been working. I tried adjusting settings in sound preferences and in alsamixer, and nothing has really helped. occasionally they'll work, but they don't mute the speakers even when they do work. I've tried everything I could find in existing threads on the issue, and nothing has worked so far.

---

### Post by Toz on 2011-09-19
Lets have a closer look.

Run this command in a terminal:
```

wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```
...and post back the link it generates.

---

