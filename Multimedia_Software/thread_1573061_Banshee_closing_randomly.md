---
title: "Banshee closing randomly?"
date: 2010-09-12
forum: Multimedia Software
---

### Post by skawars on 2010-09-12
Ubuntu 10.04 64 bit
Banshee 1.6.1

I've been using banshee happily for a while, but it seems recently that whenever I open the program, it shuts down after playing just 1 track. Also if I click the "Recent Favourites" playlist after opening the program shuts immediately.

The random closing has happened infrequently in the past and I just simply re-opened the program with no problems, but now it just simply won't let me play more than 1 track.

Any ideas?

---

### Post by sikander3786 on 2010-09-12
Deleting all banshee settings worked for me when I was getting that crash problem. In my case it was a corrupt database. The downsides of this method are that you lose everything including your library, playlists and ratings. 

```

cd ~/.banshee

```
```

rm -rf ~/.banshee

```

---

### Post by skawars on 2010-09-12
i've just temporarily migrated to rhythmbox and might just stick with this tbh, it's working nicely.

---

### Post by beefone on 2010-09-12
> **sikander3786 said:**
> Deleting all banshee settings worked for me when I was getting that crash problem. In my case it was a corrupt database. The downsides of this method are that you lose everything including your library, playlists and ratings. 

```

cd ~/.banshee

```
```

rm -rf ~/.banshee

```

Thank you that helped me out!

---

### Post by provatron on 2011-10-17
Same thing happened to me with banshee 1.8 on ubuntu 10.10. I found a related discussion [here]("https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/582743") which led me to the solution at the last question of the [banshee faq]("http://banshee.fm/support/faq/")
So I did this: 
```
$ cd ~/.config/banshee-1 $ sqlite3 banshee.db ".dump" > dump $ mv banshee.db banshee.db.backup $ cat dump | sqlite3 banshee.db
``` which worked for me, keeping my library and settings intact.

---

