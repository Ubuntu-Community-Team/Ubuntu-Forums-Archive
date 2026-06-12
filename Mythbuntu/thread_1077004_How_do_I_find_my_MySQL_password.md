---
title: "How do I find my MySQL password?"
date: 2009-02-21
forum: Mythbuntu
---

### Post by ryansebiz on 2009-02-21
*EDIT: Please see my new post (#4) for a more detailed explanation of my problem. Thanks!*

I'm a first time Ubuntu user. I've installed Mythbuntu 8.10 via wubi. I've spent a couple hours Googling, searching the forums and reinstalling and cannot find a way to fix this problem.

During step 11 (of 15) during the MythTV install is the MySQL config screen. I enter the same password I entered during wubi install and that doesn't work (connection failure).

So I try to find my password. I quit setup and open terminal and type:

```
/etc/mythtv/mysql.txt
```

...this gives me "Permission denied" 

How do I open mysql.txt to find my password?

---

### Post by ian dobson on 2009-02-22
Hi,

You might need root access to read the mysql.txt file. Try:-

su 
locate mysql.txt

It could well be that mythtv is using the /home/mythtv/.mythtv/mysql.txt file.

Regards
Ian Dobson

---

### Post by dsauter on 2009-02-22
I understand your frustration.  It's been a long time now, but I remember having a problem with the MythTV setup where it would ask for a MySQL password which, if created, would conflict with some other password.  To get things working, there was some voodoo involved with not setting one of the passwords.

My install was successful following the advice on this guide (which may be outdated by now)

[http://parker1.co.uk/mythtv_ubuntu.php]("http://parker1.co.uk/mythtv_ubuntu.php")

Specifically, the guide recommends:  > It will ask you for a password for the MySQL root user. It is strongly recommended that you leave this blank. Specifying a password here has been known to cause database access problems later on. It may seem insecure, but on your home network should be okay.

If you are using MythBuntu (rather than simply adding MythTV to a vanilla Ubuntu machine), I don't recall the problem occurring.


Anyway, back to the original question, your password should show up in the file the previous poster has you searching for.

Post #3 of the following thread tells you where the file might be located, and goes on to suggest ways to reset some of the passwords, which might be your underlying problem.

[http://ubuntuforums.org/showthread.php?t=658318]("http://ubuntuforums.org/showthread.php?t=658318")

---

### Post by ryansebiz on 2009-02-22
Thanks for the help. After trying your suggestions I'm still stuck.

I uninstalled and then performed these steps:

1. In Windows I double click wubi.exe
2. Installed Mythbuntu 8.10 (and entered a required administrative password)
3. Rebooted into Mythbuntu
4. First screen is step 11 of 15 "MythTV Related Passwords" with these fields:
- MySQL Server: localhost
- MySQL Database: mythconverg
- MySQL User Name: mythtv
- MySQL Password: ********
5. "Test Connection" gives me "Connection Results: Failure"
6. Changing the MySQL Password to the administrative password I entered during Mythbuntu install also fails, as does leaving it blank
7. I hit Quit
8. I launch Mythbunu Control Centre > MythTV Configuration
9 "No UPnP backends found"
10 Database Configuration 1/2
- Hostname: localhost
- Port: (blank)
- Database name: mythconverg
- User: mythtv
- Password: C1RFOKlE
11. Database Configuration 2/2 (both unchecked) > Finish
12. "Cannot login to database?"
13. Cancel

And here's the log:

```
2009-02-22 19:48:36.521 Unable to connect to database!
2009-02-22 19:48:36.521 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-02-22 19:48:36.571 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2009-02-22 19:48:36.621 Cannot login to database?
2009-02-22 19:48:36.621 Cannot login to database?

Cannot login to database?
```

I can access MySQL with:

```
mysql -u root -p
```

...using a password of (blank)

How can I get this working?

---

### Post by dsauter on 2009-02-24
Back when I was struggling to solve the same error, I found that no matter how many passwords I changed or cleared, I could never get my machine to connect if I installed MySQL with a password at step 11.  (even if I removed it later)

What finally worked for me was doing a clean install _and leaving the MySQL password blank on step 11_.  If you haven't already tried this, don't assume that setting one here and clearing it later is the same as starting with a blank password.

Hopefully, you haven't tried installing with a blank password and this works for you too.  Otherwise, I'm at a loss.

Anyone else have any ideas?

---

### Post by ryansebiz on 2009-02-28
> **dsauter said:**
> What finally worked for me was doing a clean install _and leaving the MySQL password blank on step 11_.  If you haven't already tried this, don't assume that setting one here and clearing it later is the same as starting with a blank password.

Hopefully, you haven't tried installing with a blank password and this works for you too.

Unfortunately I've tried this as well with no success.

[LIST]
[*]I've uninstalled and reinstalled
[*]it boots into step 11
[*]I leave the password field blank
[*]I hit cancel (because I can't proceed without a password)
[*]I open mysql.txt and copy the password
[*]I run MythTV setup again and paste in the password
[*]I get a connection failure error
[/LIST]

Could this be a problem with wubi?

---

