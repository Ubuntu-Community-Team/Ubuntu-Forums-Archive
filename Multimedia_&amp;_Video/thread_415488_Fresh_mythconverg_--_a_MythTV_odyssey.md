---
title: "Fresh mythconverg -- a MythTV odyssey"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by barney_1 on 2007-04-20
I have been running a stable MythTV box for some time now.  Over the past few months I have mucked around in my mythconverg database for one reason or another and I feel I have broken a few things.  Most importantly, I think I messed up the commercial flagging options.  This is an account of what I did to start over with a fresh database while still retaining some of my database information.

I started out by backing up some of the records.  I used phpmyadmin for this and exported the following tables:  
oldrecorded
recorded
recordedprogram

I want to make sure that I don't start recording previously recorded (and or deleted) shows.  I'm not sure how well this will work so I also made a full backup of my database.  I can always restore it if I have a problem or if I need to get one more table to import into a fresh database.

I also made a printout of my recording schedules using mythweb.  I will enter these by hand at the end of this project.  Now back to dealing with the database.

I found this blog to help with some mysql commands:
[http://moosy.blogspot.com/2006/04/mythtv.html](http://moosy.blogspot.com/2006/04/mythtv.html)

and used:
```
mysqladmin -u root -p drop mythconverg
```

This asked for the mysql root password and then confirmed that I wanted to drop the database.  Once dropped, everything's gone, time to start over.

I needed to create a new mythconverg database and after searching around I found that there is a template file called mc.sql.  I restored it like this:
```
mysql -u root -p < /usr/share/mythtv/sql/mc.sql 
```

Now, stop the backend:
```
sudo /etc/init.d/mythtv-backend stop
```

Time to run the setup:
```
mythtv-setup
```
I used this page as a guide: [https://help.ubuntu.com/community/MythTV_mythtvsetup](https://help.ubuntu.com/community/MythTV_mythtvsetup)

Populate the database:
```
sudo /etc/cron.daily/mythtv-backend
```

Restart the backend:
```
sudo /etc/init.d/mythtv-backend start
```

Now I'm going to use phpmyadmin to export this "fresh" mythconverg in case I screw it up later.

It's time to restore the tables that I backed up.  I did this using phpmyadmin as well. In order to import the tables the existing ones have to be dropped.  I selected each table one at a time from the left hand column and clicked the "drop" tab.  Once I had dropped them all I imported each table with the "import" tab in the main window.  

Now that I have done that, I can see my recordings in the media library, and previously recorded shows listed under manage recordings.  It's time to put my recording schedules back in.  I prefer to use mythweb for this.

Everything seems to be back like it should be.  I don't know if my problems are fixed, but I'll post back later with an update.  I hope some might find this useful.

---

### Post by raghav on 2008-01-26
Thank you so much for this post. I was finding it difficult to get the mythTV going, but with your post, I could get it started. 
Thanks a ton!
-raghav

---

