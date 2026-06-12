---
title: "kdenlive - audio problems, can't make fix work"
date: 2008-03-06
forum: Multimedia &amp; Video
---

### Post by anewguy on 2008-03-06
I have kdenlive installed, and noticed that the sound ends up way ahead of the video.  After some searching, I found this post which seems to point at a solution:

[http://www.kdenlive.org/bbforum/viewtopic.php?f=16&t=92]("http://www.kdenlive.org/bbforum/viewtopic.php?f=16&t=92")

It in turn had a link to the following:

[http://en.wikibooks.org/wiki/Kdenlive/Getting_and_installing#Ubuntu]("http://en.wikibooks.org/wiki/Kdenlive/Getting_and_installing#Ubuntu")

Basically, it sounds like you have to recompile ffmpeg, mlt and kdenlive, using some special config commands.  I tried things as mentioned on the last website, but kept coming up with problems.  Finally I just downloaded the sources for ffmpeg, mlt, mlt++ and kdenlive.  I put the special config options on the ./configure for ffmpeg, mlt and mlt++ and got the make/make install done for all 3.  I am down to kdenlive, and the makes aborts.  If I try my existing kdenlive, it still has the problems (maybe the modules are linked when kdenlive is made?).

Any help in this would be greatly appreciated!  :)

---

### Post by anewguy on 2008-03-07
bump.

---

### Post by anewguy on 2008-03-08
bump - any help with kdenlive compilation would be GREATLY appreciated!:)

---

