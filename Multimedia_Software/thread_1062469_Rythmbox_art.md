---
title: "Rythmbox art??"
date: 2009-02-06
forum: Multimedia Software
---

### Post by freakinjonathan on 2009-02-06
I was having trouble with Rythmbox. I was pleasently surprised when it got a lot of the album art for me for the songs, but then it mixed them all up. Now pretty much all the album art are on the wrong songs!! Is there any way to take away all album art and let it "start over"??

---

### Post by kostkon on 2009-02-06
Yes, go to your home folder, press *CTRL+H* (or select *View &#8594; Show Hidden Files*) to show the hidden folder/files that you have, and then go to this folder
```
.gnome2/rhythmbox/covers
```
and delete everything there.

---

### Post by freakinjonathan on 2009-02-07
```
~/.gnome2/rhythmbox$ ls -al
total 484
drwxr-x---  4 jonathan jonathan   4096 2009-02-07 10:51 .
drwx------ 15 jonathan jonathan   4096 2009-02-07 10:44 ..
-rw-r--r--  1 jonathan jonathan  39373 2009-02-07 10:51 audioscrobbler.queue
drwxr-xr-x  2 jonathan jonathan   4096 2009-02-05 19:22 jamendo
drwxr-xr-x  2 jonathan jonathan   4096 2009-02-05 19:22 magnatune
-rw-r--r--  1 jonathan jonathan   1105 2009-02-07 10:42 playlists.xml
-rw-r--r--  1 jonathan jonathan 426046 2009-02-07 10:51 rhythmdb.xml

```
Theres no covers folder in that dirctory.

---

### Post by freakinjonathan on 2009-02-08
bump

---

