---
title: "Restore a photo with sqlite3 maybe?"
date: 2011-10-28
forum: Multimedia Software
---

### Post by - Lady - on 2011-10-28
Hi linuxfriends,  

does anyone know how to restore a foto in f-spot with the help of sqlite3?  

> "A: As said before, F-Spot uses a sqlite3 database, which is normally placed in ~/.config/f-spot/photos.db. This DB holds all the tags, photo, photo versions and such. Backup this file and you won't loose all your work. Don't forget to backup your photos too! "I wanted to edit a photo and clicked "save" instead of "save as" so the original was overwritten. (Was it?)

Anyone know a command line? 

[PHP]sqlite3 ~/.config/f-spot/photos.db
SQLite version 3.6.22
Enter ".help" for instructions
Enter SQL statements terminated with a ";"
sqlite> sqlitebrowser photos.db
   ...> [/PHP]I don`t know any futher..:(

Could someone help please, or is it impossible?
The photo means much to me, the person on it died some days ago.

Lady

---

### Post by hansdown on 2011-10-28
Hi, - Lady -.

I don't know the answer, but this post will help bump your post, so it may be seen by someone, who can help.

---

### Post by enkay009 on 2011-10-28
I took a look at the schema for each table in photos.db (for f-spot on ubuntu 11.10) and it doesn't look like any field for any table could store the actual image. Unless it's stored as text... but no field name intuitively suggests it stores the image. I also checked the table contents and found no images as base64 or anything similar.

It might be a good idea to go back to whoever you quoted and ask them to explain exactly what they meant.

---

### Post by - Lady - on 2011-10-29
Hansdown, thank you very much!      

My qouting was from here: f-spot.org/FAQ 
I wrote an email to the maintainer. If I find out something I `ll post it here for others.

---

### Post by - Lady - on 2011-10-29
Is it possible to restore the foto with sqlite3?
Answer:
> No, the database only contains metadata, not image data.
Nthless thank you all for your help!

Kind regards,

Margarita
rip J.H.

---

