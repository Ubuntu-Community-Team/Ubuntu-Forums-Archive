---
title: "noob help (sql access problems I think...)"
date: 2008-11-17
forum: Mythbuntu
---

### Post by rufty_tufty on 2008-11-17
Hi All,
Long time user of ubuntu, first time myth TV user...

I started from a fresh install of Intrepid and then added the mythTV package from there.
Following the instructions on: [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV) if I run the backend installer and get the following error:
> 2008-11-17 22:39:30.449 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

So a bit of googling later suggested I try:
>  mysql -u mythtv -p

with the password from /home/mythtv/.mythtv/mysql.txt and it failed.
So I had a go at re-setting up the database using  
> dpkg-reconfigure mythtv-common 
to check that the password was indeed correct and then repeated the steps above and it still failed for the same reason.

I fear a little knowledge may be a dangerous thing, so any suggestions welcome :)

Many Thanks

---

### Post by dynamethod on 2008-11-17
you have to create a user 'mythtv'@'localhost' first i think

---

### Post by rufty_tufty on 2008-11-17
The unix user mythtv exists, but I'm not sure about the sql user. As far as I can tell this exists(I can log in without the -p), but I'm still trying to get my head around sql so not sure if this is true...

---

### Post by rufty_tufty on 2008-11-17
Got a fix at last(to this problem):
I needed to remove the user files

> rm ~/.mythtv -rf && rm /home/mythtv/.mythtv -rf

and then re-run the database setup

> sudo dpkg-reconfigure mythtv-database


Thanks for the help!

---

