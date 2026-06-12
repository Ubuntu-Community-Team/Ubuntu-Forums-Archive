---
title: "Music Library App that can import from Banshee?"
date: 2018-08-03
forum: Multimedia Software
---

### Post by paulakreuzer on 2018-08-03
I migrated from Mac and iTunes to Ubuntu and Banshee end of last year. I chose Banshee because it can import the library from iTunes and I love how it works.
I only learned that it was no longer actively developed later, but that was no problem for me as it worked so well - until now.

Since yesterday Banshee crashes whatever I do. I already tried reinstalling, but no change. (PS: See [https://ubuntuforums.org/showthread.php?t=2397781&p=13789066#post13789066](https://ubuntuforums.org/showthread.php?t=2397781&p=13789066#post13789066))

Now I hope there is another - actively developed - app that is able to import the whole library from Banshee (including ratings and plays).
The media consists of mp3 files and ogg files the latter of which have ratings and play counts saved in the file tags.

Can anybody recommend an app that can handle that?

---

### Post by TheFu on 2018-08-03
Did you try cleaning up your banshee config files?  The easy way to test if that is the issue is to just move them somewhere else
or 
create a new userid, login with it, and see how well banshee works.

Sorry, I don't have suggestions that I know use existing play counts or ratings. I use **cmus** myself.  You might look at Clementine. It is big and heavy like banshee or itunes - though nothing except  Eclipse is really as heavy as iTunes. ;)

---

### Post by paulakreuzer on 2018-08-05
Thanks, I fixed the banshee issue. See other thread: [https://ubuntuforums.org/showthread.php?t=2397781&p=13789592#post13789592](https://ubuntuforums.org/showthread.php?t=2397781&p=13789592#post13789592)

So now that Banshee works again I'll just continue my long-term plan to convert all my songs to ogg and store all the metadata in the files so I can't loose them again. And one day I'll switch to an actively maintained music app that can also store and read plays and ratings in the file.
Oh and also I'll do regular backups of the banshee.db file. ;)

---

### Post by TheFu on 2018-08-05
You should do regular backups for all things you can't afford to lose, not just the .db.

**EasyTag** can move tags into files based on the directory structure or the opposite.  That can be handy.  I don't know about ratings or play counts. Most of my audio files are available read-only to prevent dangerous things by all the different clients.

---

