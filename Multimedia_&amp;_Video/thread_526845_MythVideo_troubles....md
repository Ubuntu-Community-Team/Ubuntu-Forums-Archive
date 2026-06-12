---
title: "MythVideo troubles..."
date: 2007-08-15
forum: Multimedia &amp; Video
---

### Post by Protoss on 2007-08-15
So I just combined my desktop and mythbox into one super-powerful mythdesktopbox, but all did not do smoothly. I should point out that firstly, I didn't backup the database into a nice clean .sql file, but moved the raw .MYI, .frm files to the same directory on my desktop, which couldn't have been the best move, and might be causing this problem. Whenever I go into Mythvideo, I get 
```
2007-08-15 22:48:04.563 DB Error (Querying video metadata):
Query was:
SELECT title, director, plot, rating, year, userrating,length, filename, showlevel, coverfile, inetref, childid,browse, playcommand, category, intid FROM videometadata
Driver error was [2/1017]:
QMYSQL3: Unable to execute query
Database error was:
Can't find file: './mythconverg/videometadata.frm' (errno: 13)

```
I've checked and double checked that videometadata.frm is indeed in its place (/var/lib/mysql/mythconverg) place, even tried copying the file again, but no dice. 
Could this be a permissions file, since I had to copy the files as root?
Thanks guys.

---

