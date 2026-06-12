---
title: "Weird authentication error when trying to start mythtv"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by jaymode on 2006-10-28
I had mythtv running but I messed up the location when I ran mythtv-setup. So I had to stop the backend. I did that changed the directory and now I can't start the mythtvbackend service. I restarted and it did not start. Here is the error I get:
```

jmodi@mythbox:~$ sudo /etc/init.d/mythtv-backend restart
Restarting MythTV server: mythbackendNo /usr/bin/mythbackend found running; none killed.
.
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
.
jmodi@mythbox:~$ 

```

This is a very weird error.

---

### Post by jaymode on 2006-10-29
Just in case anyone wants to know how I fixed this:
There is a file mysql.txt , somehow the information for the login/password was garbled in one of them. There should be 4-5 copies of this file, so check them all.
Mine were in:
/etc/mythtv/mysql.txt
/home/<your login>/.mythtv/mysql.txt
/home/mythtv/.mythtv/mysql.txt
/root/.mythtv/mysql.txt
/usr/share/mythtv/mysql.txt

---

### Post by superm1 on 2006-10-30
Jaymode,

This error is actually normal.  It happens sometimes when launching mythbackend through sudo.  You shouldn't have to worry about it, unless mythbackend isn't running afterwords.

---

