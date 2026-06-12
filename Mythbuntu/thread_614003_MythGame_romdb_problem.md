---
title: "MythGame romdb problem"
date: 2007-11-15
forum: Mythbuntu
---

### Post by ghuber on 2007-11-15
Ok, so I have MythGame loaded and working with MAME.  Got a wireless Rumblepad  2 working with it as well.  The problem is the names displayed.  

I downloaded romdb-20031116-01.sql and ran it.   The first time I ran it I got an error that the table already existed so I removed the create table from the script and ran it again.  It completed with no errors.  I can do a select with mysql and see that the rows are populated with all the data from the script.  

Next I changed MythGame to do a in-depth scan.  cleared the myth data and scan for games again.  

Still nothing.  No descriptions.  Just the plain file names in MythGames.

Any ideas?  Is it a bug in the new version?  Did the table names change?

Geoff

---

### Post by ghuber on 2007-11-15
Ok...  A little more info I did not notice before....  When I go into MythGame...  and sort by name..  they are the file names...  not the long names from the DB.  But if I sort by year or category they show up correctly....

---

### Post by ghuber on 2007-11-15
Ok...  I see now that if I scroll down in the list...  some of the games are working..   just the ones at the top......

Is there  a tool to find out what the hash number is for a rom so I can see what these are hashing out to vs what they should be in the DB?  Penguin Kun Wars is one example of a game that is not showing up in the DB...

---

### Post by OffAxis on 2007-11-16
hash tool?
if it's just an md5 checksum in the db you can run 
```
md5sum [FILENAME]
```

---

### Post by ghuber on 2007-11-16
Thanks...   Does the scan for games output to the log files?  (not at home to look)

---

### Post by OffAxis on 2007-11-16
I don't know. I haven't installed my roms under mythbuntu yet (I previously installed them under fiesty with no problems so I never bothered to look at the logs).
I would expect errors to be in the 
**/var/log/mythtv/mythbackend.log**
or possibly the 
**/var/log/mythtv/mythfrontend.log**

but that's just a guess.

---

### Post by newlinux on 2007-11-16
When I have scanned roms the frontend has given me useful output before. I used to have some problems scanning some roms, but I don't remember what those problems where anymore, and my backends are on edgy and feisty.

---

