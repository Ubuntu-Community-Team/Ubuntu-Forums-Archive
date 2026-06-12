---
title: "Print Amarok Library"
date: 2006-10-17
forum: Multimedia &amp; Video
---

### Post by gibbylinks on 2006-10-17
Does anyone know, is there a way to print the contents of my Amarok library. Is there a database somewhere I can open with Open Office Base for example, to print a list off.

I have several groups listed twice because of slightly different spellings and I want to work my way through them, but I'd rather do it with Tag & Rename in windows than use Amarok.

Thanks

---

### Post by adwait on 2006-10-17
If you are using MySQL for your collection backend, you could look at the database in mysql. The name is normally amarok.

---

### Post by mitch.c on 2006-10-17
With amarok running, you can call a DCOP function from the command line like this:
```
dcop amarok collection query "SELECT title FROM tags" > mycollection
```
That will give you the titles in the collection. You can change up the query to extract more specific results.

---

### Post by gibbylinks on 2006-10-17
Thanks Guys will give these a Whirl

Cheers

---

