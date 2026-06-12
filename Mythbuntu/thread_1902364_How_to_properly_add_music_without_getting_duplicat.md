---
title: "How to properly add music without getting duplicates"
date: 2011-12-30
forum: Mythbuntu
---

### Post by Zachary123 on 2011-12-30
Hello I am quite new to this forum and to Mythbuntu but so far I love it!

Here's my probelm:

I have 50 gigs of ogg, flac, mp3, m4a, etc music that I transferred from my laptop to my mythbox via samba.  The first time I tried adding all of the music to my frontend database, the frontend crashed so I am attempting to add all of the files in small increments.

I have them sitting on my desktop organized into seven different folders and one by one I want to add them to the /var/lib/mythtv/music folder and scan them to the database.  I am assuming that it's better to just have the music files in the /var/lib/mythtv/music folder (i.e. not organizing my music into separate Artist, Album folders).

After I dump the first folder of music into /var/lib/mythtv/music, I go to the frontend and select import files in the Music Tools area.  I pick the location as /var/lib/mythtv/music and then click search.  It comes up with about 700 or so files which is correct.  I then go down and click add all.  It adds them but when I go to "play music" almost every song has a duplicate.  Also, when I look in the /var/lib/mythtv/music folder, it seems mythtv has created Artist folders and attempted to organize the music itself.  But in doing this it makes duplicates which take up HD space, which I currently don't have much of.  Is there a simple step I am missing?

Hopefully my problem is clear?

Thank you any input is highly appreciated.

-Z

---

