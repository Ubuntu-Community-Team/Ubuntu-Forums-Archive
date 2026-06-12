---
title: "Jamu confusion"
date: 2010-03-20
forum: Mythbuntu
---

### Post by utar on 2010-03-20
Hi


I'm trying to using jamu manually to update some of my metadata and to be frank the wiki and my Google searches don't really make much sense.

I have downloaded the latest version of jamu (0.6.0) and what I want to do is to rescan one of my media directories.  I have tried:

./jamu.py -I directorypatch

But this doesn't seem to add anything to the myth database.

Can anyone give me some help?

---

### Post by dannyboy79 on 2010-04-13
are you using storage groups for your videos? you have to open the backend with mythtv-setup, set all your storage groups for videos,  coverart, fanart, etc etc. then open the frontend whereever you want, ewnsure that all your directory locations on the frontend are not filled in, it will pull locations from backend, then go into watch videos, then hit "M", hit scan for changes. all your videos will show up. it's my understanding that jamu will populate your metadata and download artwork once you videos are all in the database. good luck.

---

