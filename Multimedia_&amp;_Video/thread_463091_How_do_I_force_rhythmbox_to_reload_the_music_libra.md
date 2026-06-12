---
title: "How do I force rhythmbox to reload the music library?"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by the_it on 2007-06-03
I'm sure it's very simple, but I'm mssing it somehow.

---

### Post by isecore on 2007-06-05
I'm kind of wondering the same thing. I've been using Banshee for some time now but decided to give Rhythmbox another go since I've been getting very frustrated with Banshees slow handling and lack of automatic library watching. Rhythmbox however is annoying on the other end of the spectrum - sometimes it imports files in the watched directory and sometimes it refuses to import files even if I specifically tell it to!

The only real way to forcing it to reload the library is to delete it, it's in ~/.gnome2/rhythmbox/ and is called rhythmdb.xml - do that and restart Rhythmbox and it will initiate a rescan.

Be aware though that you lose anything you've done to your collection, if you've rated music with stars then you'll have to do it over again. This is why I want to find some other way since I don't want to lose that rating.

---

### Post by davidpodhola on 2008-02-17
Great, works, thanks!

---

