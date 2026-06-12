---
title: "Mythtv Stopped Recording"
date: 2016-11-11
forum: Mythbuntu
---

### Post by stroupman on 2016-11-11
For weeks now, since installing, Mythtv has been reliably recording several regularly scheduled programs selected from the program guide. 2 days ago I went to play a news report. It hadn't recorded. I tried live tv which worked ok. Entering program schedules, I noticed that the news was no longer highlighted for recording. When I tried to select it again for recording, it did not flag (change color). Going to the "Scheduled Recordings" menu page I saw "You haven't scheduled any programs to be recorded". I ran the software updater to see if there was maybe a software fix. I tried scheduling the news again with the same results. The frontend log showed a database error that I was trying to schedule a duplicate entry. :confused:

---

### Post by aelfric55 on 2016-11-13
Most of the time this is just a simple crashed table in your mythconverg database.

```
$  mysqlcheck -A -e --auto-repair -u mythtv -p
```run on the master backend, where the password is the mysql password, not your user password, should fix things. Depending on the size of your database, the command may take some time to finish.

---

### Post by stroupman on 2016-11-13
Thanks for replying. I ran the command, everything came back OK. Only took a couple of minutes. But I still have the problem. Is there more I can do to help debug? Logs for example?

---

### Post by aelfric55 on 2016-11-13
Assuming the problem persists after running the repair **and restarting both mysqld and the backend**, you'd proceed by checking the backend log for an error at the time you tried to set up a recording. Mysql's ".err" file under /var/lib/mysql/ may have an error pertaining to your particular problem at the times when you have attempted to schedule something. If the issue  is a crashed table, you'll also notice that none of your automated mythconverg backups scripts will have created a successful full-size mythconverg backup since the problem started, since mysqldump won't complete on a  crashed  database.  Instead you get a small text file with a message that mysqldump can't complete until the database is repaired.

---

