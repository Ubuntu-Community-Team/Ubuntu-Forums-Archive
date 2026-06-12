---
title: "mencoder problems.."
date: 2010-07-31
forum: Multimedia Software
---

### Post by GlazedWicker on 2010-07-31
I've been trying to rip a dvd to Xvid format with mencoder. I have confirmed that the entire movie is on title 1, but the resulting .avi file excludes the last 20 or so minutes of the movie. here is the code I used...

```
mencoder dvd://1 -o movie.avi -ovc xvid -oac mp3lame -xvidencopts bitrate=2000

```

---

