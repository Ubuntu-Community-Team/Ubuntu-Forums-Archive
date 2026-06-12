---
title: "moving sqlitedb to shared directory"
date: 2011-05-18
forum: Multimedia Software
---

### Post by foodmonkey on 2011-05-18
[B]a lot of ubuntu apps seem to use sqlite3 to store the metadata. some noticable are firefox, shotwell and banshee.

can understand firefox keeping it separate but what if i want to share the music and photos between two users on the same machine.

i've set up a user group (call it "two") that has two users
have set up a shared dir under /content/twousers
set permissions chgrp & chmod & flicked the sgid bit so that everything is owned by the group.

can then run banshee (or shotwell for that matter) under the primary user (the group owner) and import data (music pictures et al).

try a second user on the same local machine and can see the directories and files - just cant see the metadata in the sqlite db.

any way to get these apps to look for their metadata in the shared directory - doesn't seem like sqlite has a distributed db node mechanism available.

is there any way of assigning a unix evironment variable to do some sort of "directory redirection" - for want of a better term - or an sqlite trigger in the db that connects to the common sqlite?

cheers,
simmo
[/B]

---

### Post by eric-yorba on 2011-05-18
Sqlite database files are just like any other file. Why can't you just use a link?

However, I should warn you that doing this could have all kinds of horrible consequences.  For example, Shotwell is designed to have one process open at a time only.  If two users are writing to the same db file at the same time, it's very likely that bad things will happen.

---

### Post by foodmonkey on 2011-05-20
this has been solved - sort of - see thread on sharing music and photos between multiple users on single machine

---

