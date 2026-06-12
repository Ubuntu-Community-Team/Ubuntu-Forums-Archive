---
title: "some program can play sound, some others can not"
date: 2006-07-16
forum: Multimedia &amp; Video
---

### Post by zealubuntu on 2006-07-16
The Ubuntu 6.06 works fine on my Laptop T-43 for quite a while. However, since I upgraded the softwares recently. I got problem with sound.

Now some of my programs can play sound: for example, the system startup,and logout, mplayer, rhythmbox player, etc. They all works fine.

But some others can not, for example, xmms, which complains that the sound card may be blocked by another program. More critical, my firefox can not play any embeded sound any more. When I watch videos from youtube, there is no sound.

Any ideas to solve the problem?

Thanks.

zealubuntu

---

### Post by bluecherry on 2006-07-16
I had a similar problem, try:
```

killall jackd

```

Does this work?

---

