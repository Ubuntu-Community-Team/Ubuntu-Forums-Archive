---
title: "No mysqld.sock file created"
date: 2012-06-07
forum: Mythbuntu
---

### Post by lamogo on 2012-06-07
I attempted to bring up mythweb and received the error today. The local frontend and remote frontend in my house also cannot connect to the database, the error being that it cannot connect through "/var/run/mysqld/mysqld.sock." After performing an ls I can confirm the file is missing. Trying to use the init.d script, no matter the command, also brings up the same error. I cannot login either.

My my.cnf seems fine and the socket under client matches what the error gives. I also did a PS and can confirm mysql is running. I've looked around all the answers refer to the fact there is a setting in my.cnf wrong but after I've looked it shows correct. Since restart doesn't work and status I have done a computer restart with no avail. Thanks for the help and guidance.

---

### Post by superm1 on 2012-06-07
Is the symlink from /var/run -> /run broken or missing perhaps?

---

### Post by lamogo on 2012-06-07
Sorry think I gave some bad info in my first post. I ran PS -A | grep -i mysql and got nothing. I looked in /var/run and while I was there snooped around and say the pid file is not present. I think that means that mysql is not running?

I then ran the command /etc/init.d/mysql start and get the same error that the file is not there. I looked at the folder permissions of where the .sock file should reside and looks ok there too.

edit: after restarting I get a warning to invoke mysql through start mysql rather than the script. I did that but still no dice.

---

### Post by steeldriver on 2012-06-07
I think there were some recent problems with updates producing malformed {...} syntax in the mysqld apparmor profiles (specifically the /etc/apparmor.d/usr.sbin.mysqld file)

The symptom in my case was that apparmor wouldn't let mysqld start even manually via sudo service mysql start, but there are other reports where it starts but presumably with the sock / pid files in the wrong place

[http://my.opera.com/djfake/blog/2011/11/05/ubuntu-11-10-mysql-problem-after-upgrade](http://my.opera.com/djfake/blog/2011/11/05/ubuntu-11-10-mysql-problem-after-upgrade)

might be something to check

---

### Post by lamogo on 2012-06-08
Thank you for the suggestions. I tried the suggested solution with no change. I have reinstalled Mythbuntu 12.04, so I have a working MySQL now. Not sure if I should mark this as solved or not.

---

### Post by lamogo on 2012-06-13
I believe the issue can be contributed to a failing hard drive.

Disk Utility says I have 30 bad sectors, it is standard operation to mount the file system as read-only when something like that happens. The file wasn't showing up cause it couldn't be written despite the permissions.

---

