---
title: "upgrade .24 break"
date: 2010-12-04
forum: Mythbuntu
---

### Post by gte451f on 2010-12-04
When installing a fresh copy of MythBuntu I get a working version of .23.

Great!

I then install the AutoBuild package and choose .24.  I get a message about a "Partial Upgrade" complete and upon rebooting, MythTV the front end complains about not being able to access the backend.

ALso, the MythTV Control server -> Mysql Test COnnection fails.

I know the MySQL server is up and I can log in using the MythTV user.

Help!

---

### Post by azmyth on 2010-12-05
I got that message before and I just redid the update and it fixed the packages that didn't upgrade properly and then I just did a reboot and I was good to go.

---

### Post by cstrebel on 2010-12-05
I got the same message when trying to update from mythtv 0.23 to 0.24 using the Mythbuntu-repos package (PPA).

It seems to be a problem with updating libmyth

This procedure was proposed

1) Exit the frontend 
2) Backup the database 
3) sudo apt-get remove mythtv* libmyth* 
4) Install new version of mythtv 
5) Run mythtv-setup 
6) Start the backend 
7) Start the frontend and reconfigure audio as per the release notes 
for 0.24 ;o) 

Copied from:
[http://www.gossamer-threads.com/lists/mythtv/users/462256](http://www.gossamer-threads.com/lists/mythtv/users/462256)

I have not tried it yet.

---

### Post by thatguruguy on 2010-12-05
> **gte451f said:**
> When installing a fresh copy of MythBuntu I get a working version of .23.

Great!

I then install the AutoBuild package and choose .24.  I get a message about a "Partial Upgrade" complete and upon rebooting, MythTV the front end complains about not being able to access the backend.

ALso, the MythTV Control server -> Mysql Test COnnection fails.

I know the MySQL server is up and I can log in using the MythTV user.

Help!

If you run the upgrades from synaptic, it will tell you which programs are causing conflicts. Delete those packages and install the .24 versions.

---

### Post by gte451f on 2010-12-06
I see the pesky message about the Backend REQURING a Capture Card.  I've installed a Dummy pointed to a sample MPEG2 file and success!

---

