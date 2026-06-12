---
title: "RRAbuntu Rivendell MySQL new user password access problem"
date: 2014-02-11
forum: Multimedia Software
---

### Post by Owen_Dawe on 2014-02-11
Hello,

I'm a recent convert to Ubuntu mainly due to Microsoft pulling the plug on XP.

I'd dabbled with Ubuntu in a half hearted fashion for a year or so, but late last year made a concentrated effort to get my head around Ubuntu. I've found it to be an awesome platform using Ubuntu 12.04 as my internet computer.

I'm in the process of changing over to Linux completely. First comes my low power FM station, which is and has been running on windows for several years. I downloaded the RRAbuntu 1.13 iso, got it installed and working on a older HP 2.80 cpu with 1.5 gig of ram without any problems. Smooth as. I've ripped a cd, imported and converted some mp3 files, all ok.

C drive on the computer is only 40gig of which RRAbuntu (incorporating Ubuntu, Rivendell radio automation and MySQL) has used up about 9gigs. I'd planned on putting all my music on a seperate larger drive. I thought all I'd have to do is point MySQL to the other drive. However. Not as easy as it sounds. MySQL is asking for hostname which I think should be what I called the host. It defaults to port 3306. It also asks for username which I understand is 'admin' and it asks for a password which I understand there is none.

I  get this error message Could not connect to host 'localhost'.
MySQL Error Nr. 1045
Access denied for user 'root'@'localhost' (using password: NO

Or this one
Could not connect to host 'xxxxxxxx'.
MySQL Error Nr. 2005
Unknown MySQL server host 'xxxxxxxxxxxx' (1)

How do I get into MySQL? The answer is probably looking me in the face, but I can't see it.

Once I get this up and running I think I'll switch to Ubuntu Studio for video and give all this Windows/Adobe stuff away.

Thank you in advance,
Owen.

---

### Post by Owen_Dawe on 2014-02-12
Righto. I got it figured out. If any one else has the same problem. Server host name; localhost: Port; 3306: User name; root: Password; rivendell.

---

