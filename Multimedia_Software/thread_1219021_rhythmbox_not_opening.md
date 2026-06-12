---
title: "rhythmbox not opening"
date: 2009-07-21
forum: Multimedia Software
---

### Post by djpalshikar on 2009-07-21
i have been trying to open rhythm box, but each time i launch it, it automatically closes. It was working fine two days ago. i have reinstalled it ,but the problem persists. 
if i run it in the terminal this is the error i get:
(rhythmbox:25231): Rhythmbox-WARNING **: Could not open device /dev/radio0
**
RhythmDB:ERROR:rhythmdb-tree.c:436:rhythmdb_tree_parser_start_element: assertion failed: (typename)
Aborted

There is no device such as /dev/radio0 on my pc;
Help!

---

### Post by Nevermor7 on 2009-07-21
same exact error- it started just freezing while I was Djing a wedding and now wont open at all... and firefox is closing... all after upgrading to Jaunty :(

---

### Post by djpalshikar on 2009-07-22
well i've found some kind of fix, for the problem .
if you`re error is exactly the same then try this:
in terminal type the following command:
rhythmbox --rhythmdb-file

This worked for me , i also changed the launchers command from just rhythmbox to rhythmbox --rhythmdb-file, and even the launcher on my desktop started working. though i think there must be a better way to solve the problem!

---

