---
title: "Mythtv borked by edgy update"
date: 2007-03-03
forum: Multimedia &amp; Video
---

### Post by Panhead Bill on 2007-03-03
I just ran the update manager and after restart Mythtv is borked.

The 150gigs of recordings are mno longer visible to mythtv.  "Sorry, no recordings available"

I get frequent errors when checking various items in system status.  "Could not connect to the master backend server -- is it running?  Is the IP address set for it in the setup program correctly?"

I'm assuming that the database is not running based on the above errors and the following output from a terminal:
______________________________________________________________________________________
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-03-03 19:54:03.085 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-03-03 19:54:03.141 Database not open while trying to load setting: QtFontBig
2007-03-03 19:54:03.149 Unable to connect to database!
2007-03-03 19:54:03.149 Driver error was [1/1045]:
________________________________________________________________________________________________

The above is repeated MANY times before it continues on and then I get a lirc failed message, anmd then a timeout error trying to connect to the backend:

___________________________________________________________________________________________________
2007-03-03 19:54:59.188 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-03-03 19:54:59.189 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.

____________________________________________________________________________________________________


HELP!

---

### Post by tgalati4 on 2007-03-03
Was the MythTV system working perfectly before the Edgy update?

---

### Post by Panhead Bill on 2007-03-03
Perfectly?  Not yet.  But getting there until today's update.

 I got lirc to work about 2 weeks ago, and still am adding features to it like video out from the Hauppaug-350, but the record and playback (on the monitor) worked, the 480 gig LVM video storage worked.

Note: this system was using edgy.  The update manager listed 47 packages that there were updates for.

---

### Post by tgalati4 on 2007-03-03
I tried to get LIRC to work but got too many compile errors.  I did get IRDA to work with syncronizing with IR devices.  

I'm sorry hear of your troubles.  Can you boot into a previous kernel to get a working system?

Did any of the updates change to a newer kernel?

My update rule of thumb is not to update a working system unless the update fixes a problem that I am currently having.  I still use Dapper on several of my networked PC's because they are running servers and services that are more convenient to have working all the time, than to try to troubleshoot after each update.

Since MythTV is a dedicated, purpose-built box, I would be shy about updating unless I know exactly what problem is being fixed.  Then you simply have to weigh the risk of rebuilding your system to the benefit gained through the update.  The updates are incremental, but the failures are massive.

---

### Post by Panhead Bill on 2007-03-04
I believe that the linux headers was one of the updates.

I think that I just have to learn what messed up the link to Mysql, and how to fix it.

I guess I'll be ignoring the update manager after this.

---

### Post by tgalati4 on 2007-03-04
The Law of Unintended Consequences.  It's hard to predict what will break when updates go out.  Because of the effort involved with setting up a Linux system, updates have to be weighed carefully.

Let us know what fixed your system, as there will be others after you.

Good luck.

---

### Post by Panhead Bill on 2007-03-06
So far I've been able to establish new contact with the master backend server, but all of my recordings are "gone".  If I exit mythtv and search the drives the recordings are there, so Mysql is not seeing the recordings.  

Another issue is the tuners are now not functioning.  I believe that the setup info in myth has been altered.

Does the mysql database store the myth setup settings?  If not where are they stored?

---

### Post by fenian on 2007-03-07
Did you update your ivtv drivers?If not you need to do so with the following command...

> sudo m-a update,prepare
sudo m-a a-i ivtv
sudo depmod -a 

---

### Post by Panhead Bill on 2007-03-08
I tried that, but no-go.  I still get no video on "watchtv" and error messages in the log about the video cards not working.  (Hpg 150 and Hpg-350)

---

