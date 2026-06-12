---
title: "Avidemux - Combining Multiple Videos Quickly?"
date: 2007-07-25
forum: Multimedia &amp; Video
---

### Post by hooplah on 2007-07-25
Hi, haven't posted in awhile, but .. now ... i need help, again. I was wondering, if there was a faster way to merge video clips in avidemux? Because, Appending one video after the other, and waiting for it all the completely be added, can be a drag, and it takes awhile sometimes. I'm just wondering if anyone's figured out an alternate method, thanks in advance.

---

### Post by tbroderick on 2007-07-26
You can try cat.

```
cat movie1.avi movie2.avi > movie_new.avi
```

Then you have to use mencoder to rebuild the index or else you will end up with garbage.
```
mencoder -forceidx -oac copy -ovc copy movie_new.avi -o movie.avi
```

For mpg, might work for avi too
```
mencoder -oac copy -ovc copy movie1 movie2 -o movie.mpg
```

---

### Post by vanadium on 2007-07-26
<code>apropos avi</code>
learns that there is avimerge on my system. The documentation comes with
<code>man avimerge</code>

Yes, there is mpgjoin for mpg files.

I certainly would not recommend "cat" approach. It just binary combines the files and then you are relying on mencoder to repair the havoc you created in the first place. Moreover, to combine avi's, both video and audio should have exactly the same format. With cat, you can trow anything together.

---

### Post by azdragon on 2007-07-30
OK the CAT method worked PERFECT.     The avimerge program screwed up the audio.  I think that cat is good as long as you use the same camera in the same settings for all the videos.

---

