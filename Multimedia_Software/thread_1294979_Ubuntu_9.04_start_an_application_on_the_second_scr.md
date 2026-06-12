---
title: "Ubuntu 9.04 start an application on the second screen"
date: 2009-10-18
forum: Multimedia Software
---

### Post by andrei.kouznetsov on 2009-10-18
Hello, guys

Before upgrading to Ubuntu 9.04 I had a dual had configuration on my laptop. One screen was 0, another one was 1. So, starting mplayer on the second screen was simple:
```

DISPLAY=:0.1 mplayer -fs myvideo.avi

```

Now I have to use a new driver for my Intel 945GM that handles my second screen differently. In particular, the previous command does not work any more.

I have default xorg.conf and enable my second screen through System > Preferences > Display

How can I start, say, mplayer on my second screen? (I know that I can drag the window using mouse, but I do not like it)

---

### Post by andrei.kouznetsov on 2009-10-19
bump?

---

