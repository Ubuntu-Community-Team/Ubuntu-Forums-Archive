---
title: "NYTimes.com Flash slideshow won't play"
date: 2009-01-14
forum: Multimedia Software
---

### Post by igeterrors on 2009-01-14
NYTimes.com has this [_Flash slideshow on their front page_]("http://www.nytimes.com/packages/html/magazine/2009-inauguration-gallery/index.html"). I can't get the gallery to launch. I have Hardy installed and Firefox 3.0.5. Other Flash works, but not this. Just curious if anyone else has this problem, whether it's an Ubuntu issue, or Firefox, or Flash, or maybe just something wrong with the NYTimes.com site.

UPDATE: I would mark this thread as "SOLVED" but the "mark thread as solved" option no longer appears under thread tools.

---

### Post by ajgreeny on 2009-01-14
Works for me with flash 10 installed from the repos at ubuntu partners
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
Try the adobe-flashplugin from there and try again.

---

### Post by igeterrors on 2009-01-14
Perfect. I had to remove the flashplugin-nonfree package, and I restarted Firefox for good measure, and then it worked right away. Thanks!

---

