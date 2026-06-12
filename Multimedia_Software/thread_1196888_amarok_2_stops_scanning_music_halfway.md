---
title: "amarok 2 stops scanning music halfway"
date: 2009-06-25
forum: Multimedia Software
---

### Post by yon2501 on 2009-06-25
i just installed amarok 2 on a fresh build of ubuntu and for no apparent reason it stops scanning my music directory after about 78%, my music directory is on a shared partition tho this is the same setup i had with my previous ubuntu install and it worked then so i dont think this is the problem.

---

### Post by bnuytten on 2010-01-16
I'm having a similar issue. It freezes after scanning about 44% of the collection. I've switched using an external MySQL database now but it seems to be stuck at 44% again. It's memory usage is still increasing however (123MiB) while the progress bar appears to be stuck.

My best guess: Amarok is scanning all your music and storing the results in memory. Once it finished scanning all your music, it puts the results in the data source (MySQL in my case). If you have lots of music It might help if it was multithreaded: both scanning and inserting in the database simultaniously. Another advantage of multithread aproach: you can already play music while it's scanning your collection.

Anyway, you may try to select a subdirectory with fewer music items at first. Adding other subdirectories later on.

---

