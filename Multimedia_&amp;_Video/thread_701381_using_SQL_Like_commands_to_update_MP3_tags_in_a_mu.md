---
title: "using SQL Like commands to update MP3 tags in a music library..."
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by Crinos512 on 2008-02-19
I have a large music database, and I find that Genre is one of the least useful tags because just a bout anything can go in it. What I would really like is a SQL-like way to modify the tags in my library. 

Something like:

```

UPDATE <music_library>
  SET Genre = 'Alternative''
  WHERE Genre in ('Alt.',Alternative & Punk', 'Alt. Rock') 

```

Is there currently any system or program that allows this? :confused::confused:

---

### Post by loboc on 2008-02-20
amarok and banshee both have a database based collection. Fire one up and add your collection and wait for it to import them all (I like amarok personally).  Then using the searching capabilities and tagging of selected files so you should be able to this.  Search or create a smart playlist on genre for *alt* or then select all the files and retag them with alternative.

---

### Post by Crinos512 on 2008-02-20
I actually am running Banshee currently, and have done the Smart playlist idea, but I still have over 300 *alt* and relabling them one at a time is tedious. (thus my attempt at automation)

---

### Post by loboc on 2008-02-21
Edit Multiple Tags at once: 

Select all the Tracks

Right Click and select edit tags out of the context menu

All the fields in the tag editor should be blank as none of the tracks have anything in common

Change the genre

Leave all the other input boxes blank

ta-da!

---

### Post by Crinos512 on 2008-02-21
... that's it? 8-[

Thanks loboc!

---

### Post by loboc on 2008-02-21
IGNORE ME!!!!!!!!!!!!!!!!!!  I just killed a few tags in BANSHEE trying that multiple trick across different aRTIsts and albums, you do one album at a time youll be fine.  AMAROK which I use regurlarly  does the blank trick on multiple tag edits.

---

### Post by Crinos512 on 2008-02-22
Whew, you stopped me just in time...

I am planning to make the jump to KDE (and amarok) eventually... I'll hold off until then. Thanks again!

---

### Post by loboc on 2008-02-23
amarok runs fine in gnome it just looks a little different than everything else on your screen

---

