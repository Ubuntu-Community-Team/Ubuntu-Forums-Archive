---
title: "Mythbuntu Control Center MySQL Remote Connection Test"
date: 2011-08-04
forum: Mythbuntu
---

### Post by sgunther on 2011-08-04
I am running a clean build of Mythbuntu 10.04 upgraded with 0.24 fixes.

MythTV Backend Version =  v0.24.1-60-gd525265
Mythbuntu Control Center Version = 0.62-0ubuntu1

When I load the Mythbuntu Control Center and try to test the remote connection the screen reports the test failed.

When I manually log into the MySQL database using the same login information found in /home/mythtv/.mythtv/mysql.txt (Same content as /etc/mythtv/mysql.txt) I am successful from both the shell on localhost and the shell on another machine on the local network.

When I run the frontend it is successfully able to retrieve program information and works as expected.

Why might the system appear to be working as expected but the connection tests in Mythbuntu Control Center would be failing?

I tired enabling the MySQL query logs and I checked the MySQL error logs while simultaneously pressing the test button in the MCC console and it almost appears as if it is not even trying to access the database.

Any thoughts as to the problem?  Any ideas on what I might do to further debug?

-Steve

---

### Post by epinephrine_junky on 2011-11-23
No solutions, but I'm having the same problem.  I was unable to get a remote frontend to connect and was surprised to see that mythbuntu-control-center couldn't get a connection even though my combined BE/FE works.

I'm wondering if this might be related to mixing repos?

I have mythbuntu autobuilds but the mythbuntu-control-center from lucid (0.62-0ubuntu1)
MythTV Version   : v0.24.1-107-g088335b
MythTV Branch    : fixes/0.24
Network Protocol : 63
Library API      : 0.24.20110505-1
QT Version       : 4.6.2

---

### Post by nickrout on 2011-11-24
> **sgunther said:**
> I am running a clean build of Mythbuntu 10.04 upgraded with 0.24 fixes.

MythTV Backend Version =  v0.24.1-60-gd525265
Mythbuntu Control Center Version = 0.62-0ubuntu1

When I load the Mythbuntu Control Center and try to test the remote connection the screen reports the test failed.

When I manually log into the MySQL database using the same login information found in /home/mythtv/.mythtv/mysql.txt (Same content as /etc/mythtv/mysql.txt) I am successful from both the shell on localhost and the shell on another machine on the local network.

When I run the frontend it is successfully able to retrieve program information and works as expected.

Why might the system appear to be working as expected but the connection tests in Mythbuntu Control Center would be failing?

I tired enabling the MySQL query logs and I checked the MySQL error logs while simultaneously pressing the test button in the MCC console and it almost appears as if it is not even trying to access the database.

Any thoughts as to the problem?  Any ideas on what I might do to further debug?

-Steve

Does it matter? If the frontend works, by MCC doesn't, who cares. The part that is supposed to work, does.

---

