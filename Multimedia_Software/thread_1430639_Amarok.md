---
title: "Amarok"
date: 2010-03-15
forum: Multimedia Software
---

### Post by leon_che on 2010-03-15
Hey People, I have a problem with the lately downloaded amarok.
(my english is bad, i know...:( )
I can't play my music although there is a "mediathek" on the left side of the screen.
If I go to settings-> configure Amarok -> Collection and click on Import Collection, after clicking finish, it says: p, li { white-space: pre-wrap; }  [COLOR=#ff0000]Error:[/COLOR] Database could not be found at: /home/luky/.kde/share/apps/amarok/collection.db
 [COLOR=#ff0000]Error:[/COLOR] Could not open Amarok 1.4 database: Driver not loaded Driver not loaded
 [COLOR=#ff0000]Failed:[/COLOR] Unable to import statistics
And if I just click on an mp3 on the left side, there comes no music and on the timeline it blink blue for one time (like the song isn't longer than 1 sec).




Please Help me and remember my english isn't well

---

### Post by Chronon on 2010-03-15
Hi.  "Import Collection" is meant to scan an existing database (either Amarok 1.4 or iTunes) and merge its entries with Amarok 2's database.

If you just want your music to be cataloged by Amarok then select some locations in "Collection Folders" and then choose "Fully Rescan Collection".

---

### Post by leon_che on 2010-03-16
thank you, but that is not realy my problem. It's more the fact, that it isn't running like it should, for example playing music ;)

---

### Post by Chronon on 2010-03-16
Hmm..  do other applications produce sound?  Amarok should output sound through the phonon backend (usually gstreamer or xine).  Do you have phonon-backend-xine installed?

---

### Post by Fenris_rising on 2010-03-16
and don't forget ffmpeg. I had this 2 days ago after a fresh install an I forgot about this bit =D

regards

Fenris

---

