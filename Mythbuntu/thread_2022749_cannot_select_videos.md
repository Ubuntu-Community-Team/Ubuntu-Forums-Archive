---
title: "cannot select videos"
date: 2012-07-11
forum: Mythbuntu
---

### Post by capo1949 on 2012-07-11
Hi All
I would appreciate it if someone would help me with this please

I have not used mythtv for some months, I have donloaded the new videos that I want to watch into the var/lib/mythtv/videos folder. They do not appear in mythtv when I start the front end to play them. then i remembered that the database has to be updated, but I cannot remember how to to do this. I looked into the set up configuration in the front end, to no avail. I beleive it must be in the backend, but I cannot access it

many thanks in anticipation
Graham

---

### Post by tgm4883 on 2012-07-11
> **capo1949 said:**
> Hi All
I would appreciate it if someone would help me with this please

I have not used mythtv for some months, I have donloaded the new videos that I want to watch into the var/lib/mythtv/videos folder. They do not appear in mythtv when I start the front end to play them. then i remembered that the database has to be updated, but I cannot remember how to to do this. I looked into the set up configuration in the front end, to no avail. I beleive it must be in the backend, but I cannot access it

many thanks in anticipation
Graham

Hit M then scan for changes. If you have a remote that key might me mapped to Menu

---

### Post by capo1949 on 2012-07-12
Hi TGM,

Thankyou for you help that worked fine. I have also deleted all the contents of the recording folder, and on using 'm' on selecting recordings in mythtv there are no otions for udate database etc. Please advise how I can update the database. 

Many thanks in anticipation
Graham

---

### Post by tgm4883 on 2012-07-12
> **capo1949 said:**
> Hi TGM,

Thankyou for you help that worked fine. I have also deleted all the contents of the recording folder, and on using 'm' on selecting recordings in mythtv there are no otions for udate database etc. Please advise how I can update the database. 

Many thanks in anticipation
Graham

That is completely the incorrect way for removing recordings (although the correct way for removing videos, which you can also do though the interface).

You'll need to use [http://www.mythtv.org/wiki/Find_orphans.py](http://www.mythtv.org/wiki/Find_orphans.py) to resolve that

---

### Post by anonymousdog on 2012-07-12
> **tgm4883 said:**
> That is completely the incorrect way for removing recordings (although the correct way for removing videos, which you can also do though the interface).

You'll need to use [http://www.mythtv.org/wiki/Find_orphans.py](http://www.mythtv.org/wiki/Find_orphans.py) to resolve that

I recommend you run that script with 'dry run' options first to avoid undesired or unexpected brutalization of your recordings or db.  Do a DB backup first AND I strongly recommend you do a file system backup of your recordings folder(s) as well.

---

