---
title: "Strange problem with mythfrontend"
date: 2008-02-16
forum: Multimedia &amp; Video
---

### Post by m1 grant on 2008-02-16
Recently I reinstalled the mythtv backend, which is located on another computer. After that the mythrontend on my second pc wont connect to the backend even though the frontend on the backend pc works just fine. Ive checked the mysql password on the server and it sitill has the same password as before the reinstall, which is weird because when i run the frontend on the 2nd PC it claims there is some sql issue. 

Here's the terminal output when running the frontend
```


QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on 'glados' (111)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-02-16 20:28:10.898 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-02-16 20:28:10.952 Unable to connect to database!
2008-02-16 20:28:10.955 Driver error was [1/2003]:


```

Anybody have any ideas? I had this same problem before after the server pc froze, but it kinda resolved itself so I never really found out what happened. Any help is appreciated.

---

### Post by m1 grant on 2008-02-17
bump, please some1 must know what kind of problem im having.

---

### Post by m1 grant on 2008-02-18
bump

---

### Post by tps on 2008-02-18
From a terminal window on your frontend, try to :

telnet glados 3306

You should see some kind of message when you connect. If not, you may have a problem with name resolution. Try using the IP address instead of the name, or make sure you have the name and IP properly defined in /etc/hosts

Tim

---

### Post by m1 grant on 2008-02-19
Thanks for the reply,but I have already tried using just the server's IP address, and it gives the same output (except instead of mentioning its hostname it uses the IP address).

---

