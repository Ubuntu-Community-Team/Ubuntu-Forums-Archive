---
title: "Text too large (wide) on widescreen laptop"
date: 2007-10-07
forum: Multimedia &amp; Video
---

### Post by BlueFusionX on 2007-10-07
Hi there!  My text on my ubuntu laptop is way too wide, even when I hook up a 15" monitor and the screen scales down.  I don't know what to do about it and what is causing the problem.  I really can't describe it very well so I'll show you a screenshot and point out a few problems.  

[IMG]http://img468.imageshack.us/img468/5041/bigtextmo6.png[/IMG]

First of all and most importantly. the webpage in the viewport is using floats.  As the text is getting wider, the right contents must be pushed down.  It is horrible to be a web developer trying to develop on a display that doesn't work right.  Secondly, my firefox toolbar "Web Developer Toolbar" expands past the viewing area.  I really need to know what I am able to do about this.

Thanks,
William

---

### Post by octotom on 2007-10-07
The same thing is happening to me with fire fox.  Web pages look fine, but the toolbars and such on firefox are large.  I read somewhere before that it has something to do with the userChrome file, but I don't know what to put in there to fix it.

---

### Post by BlueFusionX on 2007-10-08
I've tried changing the screen resolution in xorg.conf to 1200 x 800, but the one it detected (1280 x 800) looked better. The resolution is correct I suppose but the text is just way too big! How can I fix this?

---

### Post by BlueFusionX on 2007-10-08
Problem solved!  (Solution: [http://ubuntuforums.org/showthread.php?t=351647](http://ubuntuforums.org/showthread.php?t=351647) )

---

