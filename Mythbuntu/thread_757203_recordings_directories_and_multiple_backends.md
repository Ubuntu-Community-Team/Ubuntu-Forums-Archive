---
title: "recordings directories and multiple backends"
date: 2008-04-16
forum: Mythbuntu
---

### Post by 4dognight on 2008-04-16
I have 3 backends running , 2 secondary and 1 master.
Recodrings are being created on the server that has the tuner that did the recording. I can see the recordings from any of the frontends, but when I try to watch them, it says the file does not exist. Did I not configure something incorrect? I thought I could view  recordings from any frontend, regardless of where it was actually recorded?

---

### Post by tgm4883 on 2008-04-16
You should be able to watch the shows from anywhere without any extra setup (not counting mythvideo, which requires extra setup)

Is this Mythbuntu 7.10 or 8.04

MythTV .20.2 or .21

And can you post your backend log

---

### Post by volkswagner on 2008-04-16
You should be able to watch any recording on any master or slave.  Check the machine status and see if the tuner is avail.  Can you watch live tv from a remote tuner?

May try restarting the backend on the slave???

---

### Post by 4dognight on 2008-04-17
It is looking for the wrong filename. I changed the filename to what its looking for and then it could play it. The first 4 digits of the filename are wrong. Does anyone know what the first 4 digits are supposed to represent?

---

### Post by 4dognight on 2008-04-17
digging around some more on this. It looks like the first 4 digits are the chanid from the channel table. I selected both chanid from the table (the one its looking for and what the file actually has).  I dont see how its getting them mixed up. Im thinking this is data corruption. Short of reinstalling all 3 servers. Is there some way to rebuild the database from scratch?

---

### Post by volkswagner on 2008-04-17
You can try a check/repair if you did not already.
```

mysqlcheck --auto-repair -A -u mythtv -pmysqlpass
```

You can also try to delete your lineups and then add them back.

---

### Post by 4dognight on 2008-04-17
I gave it a try, but it didnt do anything. I think what I am really in need of, is a program that will go through the tables in the DB and validate the data and its relational integrity. 

One question that comes to mind, is whether there is any data stored in the slave backends that is conflicting with the master backend. I know there is only the one DB, but is there any data stored on the slaves, perhaps in a config file?


If there isnt such a beast out there. I think I have no choice but to delete all my tuners and lineups and try that. If that doesnt work then re-install.

---

### Post by volkswagner on 2008-04-18
No errors were found when you ran mysql check?  Did you create all your lineups on the master, or each for thier respective machine?

---

### Post by 4dognight on 2008-04-18
mysql check ran clean. All lineups are created on the master.


So, I went and deleted all capture cards, and sources.
Re added the local capture cards and sources on the master.
Then add ed the firewire tuner on each slave.
ran mythfilldatabase on master.

Under tuner status and myth webackend status, it only shows the tuners from the master backend. No slave tuners.
I check the tables in the database and ALL tuners, including the slaves are in the tables. Hmmm.

I then reboot one of the slaves. Bingo, its tuner now shows up,

Then reboot the master backend. Now the other slave tuner shows up but unavailable.

 then reboot the last slave. 

Bingo. All tuners showup and available.

It seems like the you have to reboot for the slave tuners status to be presented to the master backend. It isnt very dynamic. It Could be that, the slaves are only presenting their information about their tuners, to the master backend upon initialization to the master backend.

Now to record something and see if it uses the correct filename!

---

### Post by volkswagner on 2008-04-18
You can have the master see the changes on the slaves by restarting Mythbackend on the slave, rather than reboot.

---

### Post by 4dognight on 2008-04-18
OK, I think what is happening is the files are disappearing. I set 3 programs to record. They all finished, and then proceeded to get commercial flagged. 

The entry is still in the recorded list, but when i go to view it , I get the message that the file doesnt exisat. Thats because it doesnt. I even did a directory listing while it was running, and it WAS there. But now it is gone! 

It seems to be happening to my kworld dvb tuner recordings.

---

