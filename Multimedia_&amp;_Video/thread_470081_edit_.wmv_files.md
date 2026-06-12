---
title: "edit .wmv files?"
date: 2007-06-10
forum: Multimedia &amp; Video
---

### Post by oxalá on 2007-06-10
I know that this was sort of difficult to do even on a windows box, but i was wondering if maybe there was someway using Ubuntu that I might edit .wmv files (or at least convert .wmv to .avi or some that I might be able to edit in Ubuntu).

Thanks!  I await collective wisdom.

---

### Post by brownknight on 2007-06-10
You can convert wmv to avi by using this command

**mencoder infile.wmv -ofps 23.976 -ovc lavc -oac copy -o outfile.avi**

After that you can [download]("http://www.getdeb.net/category.php?id=12") install Avidemux.

I dont know a straight forward way to do this yet. Hope this helps.

---

### Post by oxalá on 2007-06-11
> **brownknight said:**
> You can convert wmv to avi by using this command

**mencoder infile.wmv -ofps 23.976 -ovc lavc -oac copy -o outfile.avi**

After that you can [download]("http://www.getdeb.net/category.php?id=12") install Avidemux.

I dont know a straight forward way to do this yet. Hope this helps.

awesome -- that worked!
thank you so much.  i may learn to love the command line yet.

---

### Post by brownknight on 2007-06-11
once you used the terminal a few times - you will love it more than the GUI. much faster.

---

