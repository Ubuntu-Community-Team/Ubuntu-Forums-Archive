---
title: "MythTV backend mysql access denied for user"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by AndrewWalker on 2007-01-07
I've got MythTV backend running on a Ubuntu box with ip 192.168.0.5 and a front end I want to run on a Gentoo box with ip 192.168.0.3
The frontend works perfectly on the Ubuntu box but not on the Gentoo machine. I can ping the backend ok but can't seem to get access to the mysql database. I tried the following on the Gentoo box and this is what I got

athlon64 mythtv # mysql mythconverg -h cube -u mythtv -p
Enter password:
ERROR 1045 (28000): Access denied for user 'mythtv'@'192.168.0.3' (using password: YES)
athlon64 mythtv #  

I know I'm using the correct password because I get a different response otherwise.
I have commented out the line 
#bind-address				= 127.0.0.1 
in /etc/mysql/my.cnf

Is there something else I need to do?

---

### Post by 454redhawk on 2007-01-07
Maybe this will help

[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop)

bottom of the page

---

