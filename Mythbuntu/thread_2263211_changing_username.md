---
title: "changing username"
date: 2015-01-30
forum: Mythbuntu
---

### Post by deanie44 on 2015-01-30
Hi everyone.  I installed a fresh install of Mythbuntu 14.04 and I want to use the old database from Mythtv.  I changed my username from deanie56 to sakkie56.  I tried to restore the old database to the new system, but the it will not connect to the master backend.  The old database is under the username of deanie56.  What am I doing wrong?  I have researched this issue and I cannot find a solution.  I tried to change the hostname, which is localhost.  On the new installation the hostname is localhost.  I do not see the problem.  Any help will be appreciated.  deanie44

---

### Post by Lester_Burnham on 2015-01-31
> **deanie44 said:**
> Hi everyone.  
I installed a fresh install of Mythbuntu 14.04 and I want to use the old database from Mythtv.  I changed my username from deanie56 to sakkie56.  I tried to restore the old database to the new system, but the it will not connect to the master backend.  The old database is under the username of deanie56.  What am I doing wrong?  I have researched this issue and I cannot find a solution.  I tried to change the hostname, which is localhost.  On the new installation the hostname is localhost.  I do not see the problem. 
Any help will be appreciated.  deanie44

Have a look in your /home/sakkie56/.mythtv/config.xml or /etc/mythtv/config.xml and use user "mythtv" and password from in config.xml on the new machine.

What have you actually been following?
I don't really think you need to log into mysql, as the script does it for you from memory.

---

