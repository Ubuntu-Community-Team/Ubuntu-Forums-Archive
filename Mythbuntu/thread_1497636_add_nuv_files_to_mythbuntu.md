---
title: "add nuv files to mythbuntu"
date: 2010-05-30
forum: Mythbuntu
---

### Post by linuxhippy on 2010-05-30
I have some nuv files which I'd like to edit to take out the commercials.  They were recorded in mythbuntu 9.10 and the nuv files were put onto an external drive when I installed mythbuntu 10.04.  I am able to play these files with mplayer but the audio and video get out of sync in avidemux for editing.  

Can I edit these with my mythbuntu 10.04 install?  If so how-I cannot see these files in my recorded TV programs in myth.

---

### Post by ian dobson on 2010-05-31
Hi,

If you copy the videos to your recorded directory then run mythcommflag on them, that should add them to the recorded programs table in mythtv.

Regards
Ian Dobson

---

### Post by linuxhippy on 2010-05-31
mythcommflag by kept skipping over the file I wanted to add to the database so I used the -f switch to specify the file name and got this:

tux@FreeVo:/recordings/StarTrekNextGeneration$ mythcommflag -f 1021_20100217020000.nuv
2010-05-31 09:09:10.951 Using runtime prefix = /usr
2010-05-31 09:09:10.951 Using configuration directory = /home/tux/.mythtv
2010-05-31 09:09:10.952 Empty LocalHostName.
2010-05-31 09:09:10.981 New DB connection, total: 1
2010-05-31 09:09:10.986 Closing DB connection named 'DBManager0'
mythcommflag: ERROR: Unable to find DB info for 1021_20100217020000.nuv
QSqlDatabasePrivate::removeDatabase: connection 'DBManager0' is still in use, all queries will cease to work.

It says it cannot find DB info for that file...can I just play it and manually edit out the commercials in mythTV?

---

### Post by ian dobson on 2010-05-31
Hi,

Is /recordings/StarTrekNextGeneration actually a recording directory defined in mythtv?

Regards
Ian Dobson

---

### Post by linuxhippy on 2010-05-31
yes...I found it easier to categorize shows into recording directories which are on a separate partition than my root directory.

> **ian dobson said:**
> Hi,

Is /recordings/StarTrekNextGeneration actually a recording directory defined in mythtv?

Regards
Ian Dobson

---

