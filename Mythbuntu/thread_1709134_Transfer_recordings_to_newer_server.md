---
title: "Transfer recordings to newer server?"
date: 2011-03-17
forum: Mythbuntu
---

### Post by Panhead Bill on 2011-03-17
Older system 4 120G EIDE drives in LVM  97% full, running Mythbuntu 9.04.

Newer system 1.5TB Sata drive 40% full running Mythbuntu 10.10.

I want to merge the recordings onto the new server (with some duplicated when new system was in testing).  I am concerned that the databases are of different vintages.

Can anyone list the steps to do this (or direct me to a how-to)?

The last thing I want to do is mess either set of recordings up.

The second to last thing is to just SSH the recordings into the video folder and lose all the information. (Been there, and was up to my neck in the long native filenames).

The third to last thing would be to have to watch and delete 200+ hours of recordings to free up the old server. 

Thanks in advance for any assistance.

---

### Post by LowSky on 2011-03-18
This will tell you how to back up the database information so the recordings keep their info
[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

sorry I don't know of a way to merge two lists.

---

### Post by jmeads on 2011-03-18
I've done it several times and it's not too difficult.

1) Copy the old recordings to the new server 
2) Then a some sql on the old server (assuming you are not going to use it again..)
update recorded set hostname = new server;
(where new server is the hostname of the new server)
3) dump the recorded table from the old server that you have just amended
mysqldump -u mythtv -p mythconverg recorded > tmp.recorded
4) edit the tmp.recorded file and remove the drop table and create table sql statements
(there's most likely some command line switches to mysqldump do this)
5) insert the new recordings data into the new servers mysql server
mysql -u mythtv -p mythconverg < edited.tmp.recorded
6) watch your old recordings from the new server...

hope this helps

---

### Post by Panhead Bill on 2011-03-19
It appears that there is a typo in step 2:

2) "Then a some sql" on the old server

---

### Post by jmeads on 2011-03-19
Effectivity in step 2 above you need to update the hostname column in the recorded table and set it to the hostname of the new server - this can be done via sql in the old database (easiest imho) or using sed or similar once the data has been extracted...

It would be worth testing this process on some test data before doing it for really - I guess if you don't feel confident in carrying out these steps then this process isn't for you.

---

### Post by Panhead Bill on 2011-03-28
How I did it (short form): 
mysqldump -u Mythtv -p -t mythconverg recorded oldrecorded recordedprogram recordedrating recordedmarkup recordedseek > oldrecs.sql

mysqldump -u Mythtv -p -t mythconverg recorded oldrecorded recordedprogram recordedrating recordedmarkup recordedseek > newrecs.sql

Desktop Gedit: the two .sql files, copy from each oldrecs table to the end of each newrecs table, find and replace all: oldserver to newserver, find and replace all: INSERT INTO to INSERT IGNORE INTO
save as newrecs1.sql

mysql -u Mythtv -p mythconverg < newrecs1.sql

restart.

(Long detailed version to follow)

---

### Post by Panhead Bill on 2011-03-28
How I did it (detailed version):

Server#1: homer@192.168.0.101  Mythbuntu 9.04  65 unique recordings, several are also on server#2

Server#2: bart@192.168.0.102  Mythbuntu 10.10  199 unique recordings 

_Cleanup and prep:_
1) Delete any duplicate programs from older server, delete any requests for new recordings.
2) Locate recordings on homer: In my case it was /var/lib/mythtv/recordings
3) Locate recordings on bart: In my case it was /var/lib/mythtv/recordings (same as on homer)
4) On homer, distribution upgrade from 9.04 to 9.10, then test.
5) Distribution upgrade from 9.10 to 10.04, then test.
6) Distribution upgrade from 10.04 to 10.10, then test.

_Create dump files for each server:_
7) Open a terminal and enter after homer@server1:~$
.a) mysqldump -u Mythtv -p -t mythconverg recorded oldrecorded  recordedprogram recordedrating recordedmarkup recordedseek > homerrecs.sql 
.b) (enter mythconverg password for server1)
.c) ssh bart@192.168.0.102
.d) (enter user password for server2)
8 ) Enter after bart@server2:~$
.a) mysqldump -u Mythtv -p -t mythconverg recorded oldrecorded recordedprogram recordedrating recordedmarkup recordedseek > bartrecs.sql
.b) (enter mythconverg password for server2)
.c) exit

_Copy recordings from old server to new server:_
9) Enter after homer@server1:~$
.a) scp /var/lib/mythtv/recordings/*.* bart@192.168.0.102:/var/lib/mythtv/recordings/ 
.b) (enter user password for server2)
.c) (you will now wait until all of the recordings and previews are copied from homer to bart)
.d) exit

_Copy dumpfile from new server to old server:_
10) From server2, enter after bart@server2:~$
.a) scp bartrecs.sql homer@192.168.0.101:
.b) (enter user password for server2)
.c) exit

_Edit old and new dump files:_
11) On server1 leave terminal, from the desktop: Applications > Accessories > gedit
12) In gedit, open file: homerrecs.sql 
***(Note:The text file is large, it takes several minutes to load, update, or save - mine took 8 minutes and 20 seconds to completely open)***
13) In gedit, open file: bartrecs.sql  (Again expect a long wait)
***The text file is short, but wide: it is only a couple of hundred lines long, but the data is one HUGE line.  Each entry starts and ends with parentheses, and is separated from the next entry by a comma; within the entry the data is comma delimited.***
14) In homerrecs.sql scroll to the section that lists the 'recorded' table. Single click the cursor starting with the left parenthesis just after: INSERT INTO 'recorded' VALUES   Scroll down to the end of the statement (several screens lower) and "Shift-click" the cursor just after the right parenthesis to select all data in the file. Select copy from the gedit menubar.
15) In bartrecs.sql scroll to the section that lists the 'recorded' table. Single click the cursor just after the last right parentheses, add a comma, and select paste from the gedit menubar.
16) Repeat steps 14 and 15 for the remaining tables: oldrecorded recordedprogram recordedrating             recordedmarkup recordedseek
17) Use the find and replace from the gedit menubar, Find and Replace All: (hostname1) to (hostname2)  ***Note:hostname is the 8th data entry in each line of 'recorded' table***
18 ) Find and replace all: INSERT INTO to INSERT IGNORE INTO
19) Save as newbartrecs.sql, (this will take a while), then close gedit.

_Move edited dump file to new server and upload it._
20) Open a terminal and enter after homer@server1:~$
.a) scp newbartrecs.sql bart@192.168.0.102:
.b) (enter password for server2)
.c) exit
.d) ssh bart@192.168.0.102
.e) (password for server2)
.f) mysql -u mythtv -p mythconverg < bartrecs.sql
.g) (enter mythconverg password)
.h) exit

_Restart and test_
21) On server2, escape from mythfrontend to the desktop, then restart mythfrontend (Applications > Multimedia > MythTV Frontend)  all recordings should now be visible and watchable.

---

