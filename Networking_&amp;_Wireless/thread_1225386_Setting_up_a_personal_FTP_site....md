---
title: "Setting up a personal FTP site..."
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by tylersontag on 2009-07-28
--------------------------------------------------------------------------------

I've got some backpacking pics i want to host on my machine and so do some of my friends. Now these friends all live in different cities around the state and the 3 hour drive to the furthest one facilitates me wanting some sort of virtual connection to share them.

My first thought was: setup and FTP site with write permissions, they dump their files, grab mine, everyone wins.

So I've installed vsftpd and couldn't get it to work.... so i tried something with a frontend GUI, proftpd.... same scoop.... is there something glarring i'm doing wrong? Does anyone have any FTP write-ups (or anything, FTP was just my first thought) i could look at?

Thanks

---

### Post by wojox on 2009-07-28
Have you been here:

[http://www.wikihow.com/Setup-vsftpd-FTP-on-Ubuntu-Linux](http://www.wikihow.com/Setup-vsftpd-FTP-on-Ubuntu-Linux)

---

### Post by tylersontag on 2009-07-28
Yes, but i can't figure out how to connect to the site.  I've tried a windows FTP client on my network with no luck :-/

---

### Post by tylersontag on 2009-08-10
i used this site to get everything setup

[http://www.ubuntugeek.com/setting-up-a-proftp-server.html](http://www.ubuntugeek.com/setting-up-a-proftp-server.html)

in the GUI, i put my private IP of 192.168.1.* as the server address and im trying to connect to my public IP via filezilla but not getting anywhere... anyideas?

---

### Post by tylersontag on 2009-08-10
Im running behind a router and i have port forwarding setup from 21 to 50.

Is there something larger i'm missing here?   Should i not expect to be able to access my FTP within my network by typing in the public address?  Do i need anything more than ProFTPD to get this working?  Its the old addage... if theres not somethign obviously wrong, then obviously i have it setup wrong.

---

### Post by hessiess on 2009-08-10
Use SFTP, much better protocol, and unless you know exactly what you are doing(if you did you probably wouldn't be asking here), do not let other people assess your machine, it has the potential to be a massive security risk, use a cheep shared hosting service.

---

### Post by LarsW_Tierp on 2009-08-10
Since FTP isn't the safest protocol I'll give:[ http://www.howtoforge.com/virtual-hosting-with-proftpd-and-mysql-ubuntu-8.04 ]("http://www.howtoforge.com/virtual-hosting-with-proftpd-and-mysql-ubuntu-8.04")
a try.

---

### Post by tylersontag on 2009-08-10
i just want to let some friends get some backpacking picks off my machine :-/  I don't think i've put anything vulnerable up.

i don't see how setting up a SQL user in proftpd will be any better, since i can't get a generic system user account to work :-/

---

### Post by LarsW_Tierp on 2009-08-11
See this thread: [7765746]("http://ubuntuforums.org/showthread.php?p=429783#post429783")

---

