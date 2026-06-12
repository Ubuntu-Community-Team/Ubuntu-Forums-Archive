---
title: "Oh my darling Clementine..."
date: 2019-05-27
forum: Multimedia Software
---

### Post by marino3 on 2019-05-27
System 

Ubuntu 18.04.2 LTS
Kernel 4.154.0.50-generic i686
Mate 1.20.1

Clementine begins to have hiccups on my systems. Some columns are not displayed any more, and I can't get them added (Artist, Date Added, etc) even if they are listed in the box (right-click on a column header) to get the list but clementine's last update was in 2016 (like Banshee). There also some songs which year appears like a six digits figure (?). I've a huge collection (20,000 + ) but that should not ba an issue per se.

Anyone experiencing the same issues. I switched from Banshee to Clementine, and since then, I have not found any player (DeaDBeef, Audacious, Quod Libet, Sayonara - I tested them ALL) with so many features as Clementine (Cover fetching, smart playlist, metadata autocompletion, etc).

I still use it, but like a car on three wheels. She may be lost and gone forever
Dreadful sorry, Clementine

---

### Post by deadflowr on 2019-05-27
There is new fork of clementine called strawberry.
Installable either as a snap or from source:
See:
[https://ubuntuforums.org/showthread.php?t=2419274&p=13860538#post13860538]("https://ubuntuforums.org/showthread.php?t=2419274&p=13860538#post13860538")
Works well enough for me, your mileage may vary.

---

### Post by marino3 on 2019-05-27
Oh, thanks a lot. I'll check that.

---

### Post by marino3 on 2019-05-27
Yrah, OK, no 32 bits .deb available, a cryptic cmake procedure ending with "No CMAKE_CXX_COMPILER could be found."
I'm too old to lose time with that. I'll look for something else.
Thanks anyway.

---

### Post by marino3 on 2019-05-30
Amazingly, Clementine 1.3.1 is now running smoothly using Qt version 4.8.7., which dates back to 2015...
Ticking time bomb ?

---

### Post by Holger_Gehrke on 2019-05-30
The problems you're describing in your first post look like something I encountered a while ago. Turned out to be a broken sqlite-database ($HOME/.config/Clementine/clementine.db). It wasn't broken in the sense of an invalid file, opening it with the command line sqlite3 tool worked. But there was some data in there that didn't make sense. After I renamed that db to 'clementine.db.old' Clementine rebuilt it from scratch and has been working fine for the last 6 month. I lost my playlists and probably some ratings and play-counts, but everything else was rebuilt just the way it was. The database mostly stores the metadata read from the files, you could call it a kind of cache.

And I wouldn't call Clementine a dead project, if you look at the code in the [git-repository]("https://github.com/clementine-player/Clementine") you'll find commits dated from the last few weeks. They just haven't done a new release for a (long) while. There are developer builds available at [http://builds.clementine-player.org/](http://builds.clementine-player.org/) (the last .deb-files for ubuntu/bionic date from 21-May-2019, less than two weeks ago). These builds come with the usual warnings (see the README.md on gitHub) and I haven't tried them myself, but at least it shows that there's still some life in the project ...

Holger

---

