---
title: "MTD broken after updating mythbuntu 8.04.19(amd64)"
date: 2008-10-01
forum: Mythbuntu
---

### Post by hempar on 2008-10-01
i have little knowladge of mythbuntu. I have freshly installed mythbuntu 8.04.1 four times and getting same problem that MTD did not start after running update manager and installing updates. following error i am getting.

[COLOR="Red"]2008-10-01 01:00:58.406 Using runtime prefix = /usr, libdir = /usr/lib
xxxx@yyyyy:~$ 2008-08-01 01:00:58.489 Empty LocalHostName.
2008-10-01 01:00:58.489 Using localhost value of chimera
2008-10-01 01:00:58.531 New DB connection, total: 1
2008-10-01 01:00:58.559 Connected to database 'mythconverg' at host: localhost
2008-10-01 01:00:58.561 Closing DB connection named 'DBManager0'
2008-10-01 01:00:58.562 Connected to database 'mythconverg' at host: localhost
QServerSocket: failed to bind or listen to the socket
2008-10-01 01:00:58.579 MTDServerSocket Something is wrong trying to start with port=2442
You've probably got another copy of mtd already running.
You might want to try "ps ax | grep mtd".
This copy will now exit ...[/COLOR]

Steps i did to install mythbuntu 8.04.1(amd64)
1. Intalled freshly mythbuntu 8.04.1(amd64)
2. Installed w64 and libdss2 codes
3. Setup backend and frondend and checked all works well
4. run MTD -n and port 2442 is working well
5. run UPDATE MANAGER and installed all update

here i am getting problem. after update installed MTD is not working and getting above message. May be bug in updates? if anybody have same problem please report bug to fix it. but mean time i need big help to fix this problem onece at all. 

For temporary solution i found is i change mythtranscode port 2442 one less or one higher and it works well untill i reboot computer. then i can transcode(rip dvd) in excelent or lower mode.

---

### Post by laga on 2008-10-01
Do you have anything related in ~/.xsession-errors?

---

### Post by hempar on 2008-10-01
no error in xsession

---

### Post by laga on 2008-10-01
Does /var/log/mythtv/mtd.log exist? If it doesn't, can you create it as your regular user?

---

### Post by hempar on 2008-10-03
I have /var/lib/mythdvd/temp/mtd.log not at /var/log/mythtv/mtd.log. If i need to create how to create it? 

I installed fresh mythbuntu 8.04.1 (AMD64) fifth time and it was same problem. Any idea what causing it? My hardware spec are as follow

Motherboard : Abit IP35 Pro
CPU : Intel E4500
Video Card : Redaon HD 2600XT
RAM : 4 GD
Harddrive : WD 400 GB
( All hardware are recognizes by mythbuntu and works great)

Googling this issue i cannot find any satisfying answer so far. Please need help.

---

### Post by laga on 2008-10-03
Are you using the weekly builds?

---

### Post by hempar on 2008-10-03
I guess yes. I downloaded and installed mythbuntu 8.04.1 insted of mythbuntu 8.04. So that means 0.21 built in to it. but after i install i only updated with update manager.

You give me new idea. now i will download 8.04 insted of 8.04.1 and try again.
thank you laga.

---

### Post by laga on 2008-10-03
No, please don't do that.

If you use 8.04.1, you don't automatically use the weekly builds. I'm referring to this: [http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds)

In any case, the logs indicate that mtd is already running. What does "ps aux | grep mtd" return?

---

