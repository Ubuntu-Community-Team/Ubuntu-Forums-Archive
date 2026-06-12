---
title: "Amarok postgresql"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by grogger13 on 2008-01-23
I nead a walkthrough or some kind of explanation of how to configure amarok with postgresql.

Amarok is always way to slow and i did a search and found out switching to postgresql could speed it up.

My problem is that all the walkthroughs i have found are incredibly criptic and don't go step by step and assume you know how databases work.

I don't even know what a database is, i have no idea how they work and can't figure out anything and just typing in random commands in the terminal if there not explained i feel like it just screws up my system.

---

### Post by Steveway on 2008-01-23
Well I used this tutorial: [http://amarok.kde.org/wiki/Postgresql_HowTo](http://amarok.kde.org/wiki/Postgresql_HowTo)
It's the official one and pretty detailed, just keep in mind that we don't use su we use sudo.
It's actually not very hard and the speedincrease is it worth (for me at least).

---

### Post by grogger13 on 2008-01-23
the first two commands don't work.

I also hate that they don't tell you how to install postgresql. i followed the ubuntu guide but i don't know if i have everything

---

### Post by Jewfro_Macabbi on 2008-02-02
to install postgresql:

sudo aptitude install postgresql

to start it:

sudo /etc/init.d/postgresql-8.2 start

---

