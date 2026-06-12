---
title: "MythTV frontends can't connect"
date: 2007-12-10
forum: Multimedia &amp; Video
---

### Post by josesanders on 2007-12-10
I can't seem to get my remote frontend systems to connect to my new MythTV backend.  I checked the database IP, user name, and password, and all seem correct.  Also, the server is listening on the right ports.  It just won't connect.

Any ideas are much appreciated.

---

### Post by josesanders on 2007-12-11
Any help?

I can log into MySQL manally from the frontend by using the following command:

$ mysql -h 192.168.1.2 -u <username> -p

When I enter the password, it logs in just fine, but when I try to run the frontend, it still says it can't connect to the database.

---

### Post by josesanders on 2007-12-15
Bump

---

### Post by josesanders on 2007-12-21
Okay, figured it out.  It doesn't work to simply add new user names and passwords to mysql.  For some reason, it only seems to work with the "mythtv" user and password created by the mythtv backend.

---

