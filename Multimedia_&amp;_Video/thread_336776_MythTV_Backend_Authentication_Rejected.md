---
title: "MythTV Backend Authentication Rejected"
date: 2007-01-12
forum: Multimedia &amp; Video
---

### Post by MetalSlugX on 2007-01-12
Whenever I try to set up the MythTV backend I get this

```
root@ben-desktop:/home/ben# /etc/cron.daily/mythtv-backend
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
```

so I checked the log files. Here is what was there.

```
more /var/log/mythtv/mythbackend.log
2007-01-12 01:34:31.407 Using runtime prefix = /usr
2007-01-12 01:34:31.583 Unable to read configuration file mysql.txt
2007-01-12 01:34:31.780 Trying to create a basic mysql.txt file
2007-01-12 01:34:31.807 Could not create /home/mythtv/.mythtv
2007-01-12 01:34:31.809 Failed to init MythContext, exiting.
2007-01-12 02:00:55.588 Using runtime prefix = /usr
2007-01-12 02:00:55.607 Unable to read configuration file mysql.txt
2007-01-12 02:00:55.608 Trying to create a basic mysql.txt file
2007-01-12 02:00:55.610 Could not create /home/mythtv/.mythtv
2007-01-12 02:00:55.612 Failed to init MythContext, exiting.
```

I followed the instructions and this troubleshooting page [https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting) by typing in exactly what they told me (I didn't change the directory) and I still get the same error when trying to configure the backend.

What am I doing wrong here?

---

### Post by cfcubed on 2007-01-16
I had a similar looking problem.  Not that I know what I'm doing with this & this for sure not the proper way to run it, but something like this worked for me:

1)  **May not be necessary - Try starting @ step 2 first**  Set the mytv sql user password to something you know (both by running a MySQL password set & in /etc/mythtv/mysql.txt):

DBHostName=localhost
DBUserName=mythtv
DBName=mythconverg
DBPassword=mythtv

2)  Assuming you have run mythtv setup & have a channel feed ID setup, try:

sudo mythfilldatabase

let it complete

3)  Then:

sudo mythbackend & 

(or run in the foreground & open a new Term window)  let it get going.

4)  Then:

sudo mythfrontend

And see what you get.   I did other steps, like copying around the mysql.txt file & running a SQL script involving mythconverg, but I think the above *may* have got around this auth error for me.  Just playing around w/MythTV now, so I'll be going back & properly setting up the mythtv user so that this stuff is not running as root.  IOW, I think my related problem involves not having setup my mythtv user rights, etc. properly, so running as root is just a hack to get it going.  Using a KSC 110 (?) card & everything works (except sound) at the moment.  Probably have to play w/mixer settings to get sound going...

Good luck.

---

### Post by MetalSlugX on 2007-01-16
I was running everything as root using the super user terminal just to make sure. And out of total frustration I logged into in as the root user and got those same errors.

---

### Post by cfcubed on 2007-01-16
> **MetalSlugX said:**
> I was running everything as root using the super user terminal just to make sure. And out of total frustration I logged into in as the root user and got those same errors.

OK, but did you try mythbackend instead of the cron script mythtv-backend?  Seems for me that mythbackend by itself didn't get the errors & mythtv-backend did.

---

### Post by majoridiot on 2007-01-17
> **MetalSlugX said:**
> Whenever I try to set up the MythTV backend I get this...

you did run mythtv-setup, right?

> **cfcubed said:**
> OK, but did you try mythbackend instead of the cron script mythtv-backend?  Seems for me that mythbackend by itself didn't get the errors & mythtv-backend did.

agreed.  i had so many with the cron script, that i removed it completely and use a custom 
mythbackend script exclusively. you can try this to see what you get:

```
sudo killall myth*
mythbackend &  (so you can read the output)

```

^C if you need to stop it to get back to the command line.

---

