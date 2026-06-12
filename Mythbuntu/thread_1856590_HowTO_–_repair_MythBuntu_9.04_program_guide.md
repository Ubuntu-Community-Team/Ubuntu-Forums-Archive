---
title: "HowTO – repair MythBuntu 9.04 program guide"
date: 2011-10-08
forum: Mythbuntu
---

### Post by vlaporte on 2011-10-08
HowTO – repair MythBuntu 9.04 program guide
10/08/11

Problem – program guide not filling after running     $mythfilldatabase   command 
Solution – myth converge data base corrupt  (a Mysql database)
1- exit Mythtv
2- Applications > System > MythBuntu Control Center > Advanced Management > Optimize Tables > QUIT
3- 	$mythfilldatabase
4- restart MythTV front end
6- now Program Guide is filled 

Luck,
Vince

---

### Post by nickrout on 2011-10-08
> **vlaporte said:**
> HowTO – repair MythBuntu 9.04 program guide
10/08/11

Problem – program guide not filling after running     $mythfilldatabase   command 
Solution – myth converge data base corrupt  (a Mysql database)
1- exit Mythtv
2- Applications > System > MythBuntu Control Center > Advanced Management > Optimize Tables > QUIT
3- 	$mythfilldatabase
4- restart MythTV front end
6- now Program Guide is filled 

Luck,
Vince

step 4 is unnecessary.

---

### Post by iamlindoro on 2011-10-08
And step five is invisible.

But more seriously, there are dozens upon dozens of reasons one might have guide data issues-- most of the more common ones are misconfigurations, not crashed DB tables.  That said, it's always good to keep the DB healthy.

---

### Post by thatguruguy on 2011-10-10
Ubuntu 9.04 (and, by extension, Mythbuntu 9.04) is no longer officially supported, and hasn't been for a year now.

Just sayin'.

---

