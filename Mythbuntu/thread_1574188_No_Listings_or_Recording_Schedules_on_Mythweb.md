---
title: "No Listings or Recording Schedules on Mythweb"
date: 2010-09-13
forum: Mythbuntu
---

### Post by tim273 on 2010-09-13
Here's what lead up to this problem.  I had a working Ubuntu server, and installed mythv on it from the repositories.  I had mythtv, and all plugins (including mythweb) working fine.  This pc had 2 hard drives in it, one for the OS and one for recordings.  I got a larger hard drive which replaced the OS drive and decided to install Mythbuntu instead of Ubuntu.  I got everything up and running except for Mythweb.

Since the new install there is NO DATA on the Listings page in mythweb, there is also no results on the Recording Schedules page.  I also don't have any functionality for weather, there's no video's data, or pictures.  All of these I have setup and are working on the TV frontend.  After doing a google search, I tried deleting the capture card, video source and recreating them and running mythfilldatabase, but no dice.  I tried creating a test recording schedule and looked in the DB and it wasn't in the same table as the others (record).  

I do get a full list of Upcoming Recordings and Recorded Programs. Backend Status also seems to work. If I try to click on any of the recorded programs I get "Unknown recording requested."

That's as far as I've looked at it so far.  Any suggestions are welcome.

Thanks,
Tim

---

### Post by tim273 on 2010-09-14
So I did a little debugging and it appears as though the query that the listing page uses returns no data (no surprise there). I tried printing out the MySQL errors, but there were none. I logged the query and ran it in phpMyAdmin and it worked fine, so maybe there's a problem with the DB connection or something?  The odd thing is some queries return data and some don't and it doesn't seem to make a difference the size of the dataset. If it makes a difference, I have the MySQL database on a different server (version 5.1.48, running Fedora 13) from the Mythbuntu frontend/backend server.

---

### Post by alien878 on 2010-09-15
Just a thought.  Execute "locate mysql.txt" and make sure that all mysql.txt files contain a valid DB userID and password.  Also make sure you have a /etc/mythtv/mysql.txt.

---

### Post by tim273 on 2010-09-15
Yep, all mysql.txt files look good.  Thanks for the idea!

Tim

---

### Post by tim273 on 2010-09-18
Figured it out, turns out I had the wrong database host in /etc/apache2/sites-available/mythweb.conf, problem solved.

---

