---
title: "mythfilldatabase problem"
date: 2011-03-05
forum: Mythbuntu
---

### Post by Chewiesw on 2011-03-05
Hello

I am having trouble running mythfilldatabase. I am getting the following errors.



```
root@dvrbox:~# /home/andrew/Documents/myscript.sh 
/usr/bin/diff: /home/andrew/za.old.xml: No such file or directory
/usr/bin/diff: /home/andrew/za.xml: No such file or directory
Running mythfilldatabase since file changed
2011-03-05 12:24:57.112 Bypassing grabbers, reading directly from file
2011-03-05 12:24:57.112 Using runtime prefix = /usr
2011-03-05 12:24:57.112 Using configuration directory = /root/.mythtv
2011-03-05 12:24:57.113 Unable to read configuration file mysql.txt
2011-03-05 12:24:57.113 Empty LocalHostName.
2011-03-05 12:24:57.113 Using localhost value of dvrbox
2011-03-05 12:24:57.120 New DB connection, total: 1
2011-03-05 12:24:57.124 Unable to connect to database!
2011-03-05 12:24:57.125 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2011-03-05 12:24:59.172 UPnPautoconf() - No UPnP backends found
2011-03-05 12:24:59.173 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  n
2011-03-05 12:25:14.840 Deleting UPnP client...
2011-03-05 12:25:15.247 Failed to init MythContext, exiting.
2011-03-05 12:25:15.247 DataDirect: Deleting temporary files
root@dvrbox:~# 
```

Thanks in advance.

---

### Post by ian dobson on 2011-03-05
Hi,

Looks as if the mysql.txt configuration file is missing for use root. Mythfilldatabase uses this file to "know" the login name/password to use to access the databse.

Just have a look at the file /etc/mythtv/mysql.txt or /home/mythtv/.mythtv/mysql.txt and add the information to the  file in /root/.mythtv/mysql.txt

Regards
Ian Dobson

---

### Post by nickrout on 2011-03-05
> **Chewiesw said:**
> Hello

I am having trouble running mythfilldatabase. I am getting the following errors.



```
root@dvrbox:~# /home/andrew/Documents/myscript.sh 
/usr/bin/diff: /home/andrew/za.old.xml: No such file or directory
/usr/bin/diff: /home/andrew/za.xml: No such file or directory
Running mythfilldatabase since file changed
2011-03-05 12:24:57.112 Bypassing grabbers, reading directly from file
2011-03-05 12:24:57.112 Using runtime prefix = /usr
2011-03-05 12:24:57.112 Using configuration directory = /root/.mythtv
2011-03-05 12:24:57.113 Unable to read configuration file mysql.txt
2011-03-05 12:24:57.113 Empty LocalHostName.
2011-03-05 12:24:57.113 Using localhost value of dvrbox
2011-03-05 12:24:57.120 New DB connection, total: 1
2011-03-05 12:24:57.124 Unable to connect to database!
2011-03-05 12:24:57.125 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2011-03-05 12:24:59.172 UPnPautoconf() - No UPnP backends found
2011-03-05 12:24:59.173 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  n
2011-03-05 12:25:14.840 Deleting UPnP client...
2011-03-05 12:25:15.247 Failed to init MythContext, exiting.
2011-03-05 12:25:15.247 DataDirect: Deleting temporary files
root@dvrbox:~# 
```

Thanks in advance.

run it as the proper user!

---

### Post by tgm4883 on 2011-03-05
> **nickrout said:**
> run it as the proper user!

+1. Why are you running it as root anyway? 

It's clear that you don't understand permissions.

---

### Post by Chewiesw on 2011-03-06
@TMG4883 , very perceptive of you, my lack of understanding. I think you should add an addendum to your signature.

Please don't threaten to go back to Windows. It does not increase your chances of receiving help and we will help you either way. Of course being as **patronising **as possible.

---

### Post by tgm4883 on 2011-03-06
> **Chewiesw said:**
> @TMG4883 , very perceptive of you, my lack of understanding. I think you should add an addendum to your signature.

Please don't threaten to go back to Windows. It does not increase your chances of receiving help and we will help you either way. Of course being as **patronising **as possible.

Really.....


So I'm guessing that running it as your regular user worked then?

---

### Post by Chewiesw on 2011-03-07
Yes...

---

### Post by tgm4883 on 2011-03-07
> **Chewiesw said:**
> Yes...

Great, quick tip on permissions. Don't use root unless you absolutely need to. If something doesn't work with regular permissions, ask yourself why it should need root permissions.

---

