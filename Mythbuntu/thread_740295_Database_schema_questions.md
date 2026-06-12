---
title: "Database schema questions"
date: 2008-03-30
forum: Mythbuntu
---

### Post by ian dobson on 2008-03-30
Hi All,

I'm currently hacking afew scripts (Munin plugins) that read data from MythTV through the XML interface and directly from the database. 

I've got most of the code working but one feature I'd love to implement is the unwatched programs. Digging through the MySQL mythconverg database I see a field "watched" in the recorded table, and looking through the MythTV documentation I see a comment that the watched flag is in MythTV implemented. The documentation also states this flag can be se manually or automatically.  On my system this flag doesn't seen to be set when I watch a program.

So my question is How do I configure the Backend/Frontend to set this flag when I watch a program?

Running Backend ver:-  0.20.20070821-1   14283
Frontend 0.20.20070821-1  15513

Regards
Ian Dobson

---

### Post by tgm4883 on 2008-03-30
This is a feature of MythTV .21 and AFAIK, cannot be set in prior versions.

---

### Post by ian dobson on 2008-03-31
Hi,

OK Thanks, I just find it abit strange that the tabel structure contain fields that are only "used in the next version".

OK, I'll add abit of code to my script to check the mythtv version, and wait for the Hardy Heron release.

Regards
Ian Dobson

---

