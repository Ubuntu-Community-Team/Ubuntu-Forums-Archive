---
title: "How to make the vlc index fix permanent?"
date: 2009-12-07
forum: Multimedia Software
---

### Post by newbuntuxx on 2009-12-07
I have a few .avi files which have a small problem with sound/video synchronization. I use vlc to watch the avi's. vlc is nice enough to fix that issue, but the fix is temporary.

Is it possible to make it permanent? And how?

---

### Post by newbuntuxx on 2009-12-09
Any idea guys?

---

### Post by SlugSlug on 2009-12-09
are the files writeable?
chmod 777 them

---

### Post by SeanHodges on 2009-12-09
VLC allows you to stream it's output to your hard drive. You could try setting up VLC to sync up your movie's sound/video, and have it write the result to another file:

[http://www.videolan.org/doc/streaming-howto/en/ch02.html](http://www.videolan.org/doc/streaming-howto/en/ch02.html)

If you're adventurous, you could write a script (or search for one) that does all your broken movies automatically. Though for just a few files you might find it just as easy to do them one-by-one.

---

### Post by FiReSTaRT on 2011-01-17
Taken from [http://ubuntu.sun.ac.za/wiki/index.php/Mencoder](http://ubuntu.sun.ac.za/wiki/index.php/Mencoder)
> mencoder -idx input.avi -ovc copy -oac copy -o output.avi

---

### Post by TruePurple on 2011-11-10
This does not work on mkv files, how do I repair indexing for those?

---

### Post by oldos2er on 2011-11-10
Closed, please start a new thread for your question.

---

