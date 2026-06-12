---
title: "[SOLVED] What is the best way to splice 2 mpg files toghether?"
date: 2007-12-16
forum: Multimedia &amp; Video
---

### Post by jakev383 on 2007-12-16
I have 2 mpg files that were created by Myth (1 movies, broken into 2 files: one 1G file, and one 612M file) that I would like to splice back together.  After I create the DVD ISO, I move the mpg files over to a NFS share that is mapped for video files for my Myth boxes, so having the movie back in 1 file would be nice. 
Can anyone offer an easy solution to this?
Thanks!

---

### Post by sisco311 on 2007-12-16
you can use the cat command:> cat movie1.mpg movie2.mpg > movie.mpg

---

### Post by jakev383 on 2007-12-16
> **sisco311 said:**
> you can use the cat command:

That worked surprisingly well!  I had though of
cat movie2.mpg >> movie1.mpg
but had not tired it yet.  Thanks!!

---

