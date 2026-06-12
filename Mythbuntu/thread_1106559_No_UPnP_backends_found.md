---
title: "No UPnP backends found"
date: 2009-03-25
forum: Mythbuntu
---

### Post by Nobodyspeshul on 2009-03-25
So, I've got this issue and I don't know how to resolve it.

I was attempting to do the auto IMDB update script located here:
[http://ubuntuforums.org/showthread.php?t=938760](http://ubuntuforums.org/showthread.php?t=938760)

And it looks like I screwed up my mythbox somehow.

I changed the DBPassword located in /etc/mythtv/mysql.txt last night, when I rebooted my mythbox this morning I got the
```
No UPnP backends found
```
message.

At the end of configuring the file to what I thought was the MYSQL password I'm still getting the
```
Cannot login to Database?
```
error at the end.

So how can I sync up what my Database passwords are?  Or do I have a larger issue?

I don't think mythbackend is running, and I'm trying to get the frontend working.

Please help!

---

### Post by teet on 2009-03-25
You might need to manually change the password in your /home/<username>/.mythtv/mysql.txt file too.

Just a thought.

Also, if the backend isn't running, the frontend (of course) will not be able to connect to it.  Just open up a terminal and type 'sudo mythbackend'.

-teet

---

### Post by nickrout on 2009-03-25
> **teet said:**
> You might need to manually change the password in your /home/<username>/.mythtv/mysql.txt file too.

Just a thought.

Also, if the backend isn't running, the frontend (of course) will not be able to connect to it.  Just open up a terminal and type 'sudo mythbackend'.

-teet

no no no the way to start and stop mythbackend is to run the script ```
/etc/init.d/mythtv-backend stop|start|restart
```

---

### Post by Nobodyspeshul on 2009-03-25
Neither of those worked, the password is the same as /etc/mythtv/mysql.txt

sudo mythbackend just tries to access the database which doesn't work because of the password.

I think I'm just going to say F it and reimage.  I wasn't impossibly far into the process.

Lesson learned, any system generated password gets a backup file made, written down, or I'm never going to touch it.

---

### Post by nickrout on 2009-03-25
> **Nobodyspeshul said:**
> Neither of those worked, the password is the same as /etc/mythtv/mysql.txt

sudo mythbackend just tries to access the database which doesn't work because of the password.

I think I'm just going to say F it and reimage.  I wasn't impossibly far into the process.

Lesson learned, any system generated password gets a backup file made, written down, or I'm never going to touch it.

sudo dpkg-reconfigure mythtv-database will reset the password.

---

### Post by Nobodyspeshul on 2009-03-26
Hopefully I'll never screw it up again, but I'll try that if I ever screw it up again.

Thanks!

---

