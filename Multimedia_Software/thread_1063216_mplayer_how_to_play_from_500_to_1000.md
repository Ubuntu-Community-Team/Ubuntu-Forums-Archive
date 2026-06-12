---
title: "mplayer: how to play from 5:00 to 10:00?"
date: 2009-02-07
forum: Multimedia Software
---

### Post by hardysummer on 2009-02-07
What is the command to get mplayer to play a video from 5:00 to 10:00?


Solved.  Thanks andrew.46

---

### Post by andrew.46 on 2009-02-07
Hi,

I assume you mean starting 5 minutes into the movie and ending at 10 minutes into the movie? For this you need -ss and -endpos:

```
mplayer -ss 00:05:00 -endpos 00:05:00 myfile.avi
```

Hopefully this is what you mean :-).

Andrew

---

