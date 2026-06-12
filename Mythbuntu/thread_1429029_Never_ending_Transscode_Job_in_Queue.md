---
title: "Never ending Transscode Job in Queue"
date: 2010-03-13
forum: Mythbuntu
---

### Post by mars76 on 2010-03-13
HI All,

  I have a Job in the Queue which is getting transcoded and it is not getting completed. It shows 95% Complete and won't finish. If i restart the machine it starts from 0% and halts at 95%.

 Using Front End i can only Pause or stop the Job. But cannot delete it ( front end only allows to delete the jobs which are not started). Even if i stop it the other jobs in the queue are not getting picked up..

 I guess i need to go to the DB and remove the entry unless some of you have other ideas..

Note: It's an irony that the show that's causing the issue is "Super Massive Black holes" :o

thanks..

---

### Post by ian dobson on 2010-03-13
Hi,

Just go into the database and delete the job (it'll be in the jobqueue table).

Regards
Ian Dobson

---

### Post by Billsputters on 2011-06-08
I have a similar problem, a transcode that had been stuck.

Could you explain in a bit more detail how you go about this. Never delved into the database, and don;t want to mess things up. Thanks

---

### Post by Dan_R on 2011-06-08
Have your mythtv database password handy.

Go into terminal and type ```
mysql -u mythtv -p 
```After hitting enter it will ask for the mythtv user password
Switch to the mythconverg database by doing ```
use mythconverg
```Then do ```
show tables;
```This is where you should have the screen maximized
Type ```
select * from jobqueue;
```Find the ID of the stuck job and replace <number> with the ID number
```
delete from jobqueue where id=<number>;
```then do \q to quit.

---

### Post by Billsputters on 2011-06-10
Thank you so much for a concise and full reply. Sorted the problem out.

Now I just have to figure out why the MythExport was stalling

---

