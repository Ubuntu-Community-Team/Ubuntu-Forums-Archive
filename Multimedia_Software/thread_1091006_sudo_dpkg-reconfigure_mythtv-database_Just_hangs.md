---
title: "sudo dpkg-reconfigure mythtv-database Just hangs"
date: 2009-03-08
forum: Multimedia Software
---

### Post by ant2ne on 2009-03-08
Working through the troubleshooter [here]("https://help.ubuntu.com/community/MythTV/Install/Troubleshooting#head-df84859e9b132318b445ffa967e76acdfc207177"). It says to do a ```
sudo dpkg-reconfigure mythtv-database
```Which I do. I choose Ok for "mythdb" as host reside, admin account "root", a blank password, and "Yes" I will be using other computers. It then returns to my terminal, but never completes the command and never gives me back my prompt. There are not error messages, no nothing. Just a blinking cursor. I can then kill the process, but that defeats the purpose

UPDATE: I let it hang for like 15 to 20 minutes and when I came back
```
ant2ne@2ne-buntu:~$ sudo dpkg-reconfigure mythtv-database
[sudo] password for ant2ne: 
Failed to connect to database: Can't connect to MySQL server on 'mythdb' (110) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database
ant2ne@2ne-buntu:~$ 

```So at least that is something.

---

