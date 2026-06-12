---
title: "[SOLVED] Question about Mplayer volume"
date: 2008-07-24
forum: Multimedia Software
---

### Post by Domas on 2008-07-24
Hi all,

My default audio volume is so low on Mplayer while watching movies, so I found the solution in terminal writing:

mplayer -af volume=20:1,channels=2 movie.avi

Now it's just perfect. Question is - how can I save this setting next time I open Mplayer? No idea what to write in .mplayer config file.

Thanks in advance.

---

### Post by Domas on 2008-07-24
Anyone?

---

### Post by soxs on 2008-07-24
I am suffering from low audio too, but always appending 10 signs just for audio raise isn't "that" funny...
waiting for an persistent answer

---

### Post by shirilover on 2008-07-24
Try this:

```

af=volume=20:1,channels=2

```
or
```

softvol=yes
softvol-max=1000

```

---

### Post by Domas on 2008-07-24
Worked like a charm !

Thanks a lot shirilover !

---

### Post by Alistair George on 2008-08-22
Or try this:
[http://ubuntuforums.org/showthread.php?p=5640858&posted=1#post5640858](http://ubuntuforums.org/showthread.php?p=5640858&posted=1#post5640858)

---

