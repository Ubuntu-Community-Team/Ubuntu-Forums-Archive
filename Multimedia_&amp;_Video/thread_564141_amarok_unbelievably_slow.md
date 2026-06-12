---
title: "amarok unbelievably slow"
date: 2007-09-30
forum: Multimedia &amp; Video
---

### Post by ZeldaFan on 2007-09-30
I previously had amarok installed and it ran pretty quickly. Then just suddenly, it began to run really slow. Basically, it takes for ever to filter to the right artist when I search my collection, skip to the next track, or even try to change the order of my playlist. It freezes up for a second and then after a while applies the operation I've just done. However scrolling and such is still zippy and quick, so its almost just like only searching through and managing my database of songs is very slow.

---

### Post by azkabaz on 2007-09-30
From what you've just described i'd say that you are currently running SQLite as your database method (this is the default database when you first install Amarok) and that you have a significant amount of tracks.

You'll need to set up Amarok to use either MySQL or PostgreSQL to handle your Amarok database.

[http://amarok.kde.org/wiki/MySQL_HowTo](http://amarok.kde.org/wiki/MySQL_HowTo)
[http://amarok.kde.org/wiki/PostgreSQL_HowTo](http://amarok.kde.org/wiki/PostgreSQL_HowTo)

---

### Post by ZeldaFan on 2007-10-02
But I dont think that would solve my problem, because I didn't add any more songs before it became slower. I have around 950 songs, but my song count has been constant. I think a potential problem is that I moved around my actual song files a lot on my hard drive. So maybe Amarok is remembering its old location, but then eventually rerouting to the new location, thus causing the delay. Unfortunately, I have no idea how to solve that.

---

