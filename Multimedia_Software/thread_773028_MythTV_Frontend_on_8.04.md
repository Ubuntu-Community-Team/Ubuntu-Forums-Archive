---
title: "MythTV Frontend on 8.04"
date: 2008-04-28
forum: Multimedia Software
---

### Post by Nrgh on 2008-04-28
I'm trying to get the MythTV Frontend to connect to a backend on another machine.  I had this working in 7.10, so I know all the configuration on my backend is setup to connect over the network.  The backend is KnoppMyth R5F27 running MythTV .20.  After installing the frontend from synaptic, I ran 'sudo dpkg-reconfigure mythtv-common' and entered all my configuration information.  Trying to run the application from the GUI did nothing, so I ran it in a terminal to see what errors popped up.  I get the following:

2008-04-28 17:10:50.373 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-28 17:10:50.689 XScreenSaver support enabled
2008-04-28 17:10:50.689 DPMS is active.
2008-04-28 17:10:50.690 Empty LocalHostName.
2008-04-28 17:10:50.690 Using localhost value of me
2008-04-28 17:10:50.692 Testing network connectivity to mythtv
2008-04-28 17:10:50.712 New DB connection, total: 1
2008-04-28 17:10:50.716 Connected to database 'mythconverg' at host: mythtv
2008-04-28 17:10:50.728 Closing DB connection named 'DBManager0'
2008-04-28 17:10:50.730 Primary screen 0.
2008-04-28 17:10:50.732 Connected to database 'mythconverg' at host: mythtv
2008-04-28 17:10:50.734 Using screen 0, 1920x1200 at 0,0
2008-04-28 17:10:50.748 New DB connection, total: 2
2008-04-28 17:10:50.750 Connected to database 'mythconverg' at host: mythtv
2008-04-28 17:10:50.753 Unexpected DB Schema version.  Waiting to see if DB is being upgraded.
2008-04-28 17:10:55.775 Timed out waiting.
2008-04-28 17:10:55.775 This version of MythTV requires an updated database schema. Please run mythtv-setup or mythbackend to update your database.

I noticed the frontend in 8.04 is MythTV version .21 while my backend is running .20.  The 'updated database schema' message leads me to believe the two versions are not compatible?  Couldn't find anything to confirm this with google searches, but I probably wasn't asking the right question.  Anybody out there knows why this isn't working?

Thank you.

---

### Post by jelofson on 2008-04-28
Have you tried upgrading to .21 on the backend machine? It's pretty straightforward to do. I was running .21 on my backend and installed 0.20 on a frontend. I had to upgrade the frontend to 0.21. Now they are fine.
Let me know if you need help upgrading to 0.21

---

### Post by volkswagner on 2008-04-28
> **Nrgh said:**
> I'm trying to get the MythTV Frontend to connect to a backend on another machine.  I had this working in 7.10, so I know all the configuration on my backend is setup to connect over the network.  The backend is KnoppMyth R5F27 running MythTV .20.  After installing the frontend from synaptic, I ran 'sudo dpkg-reconfigure mythtv-common' and entered all my configuration information.  Trying to run the application from the GUI did nothing, so I ran it in a terminal to see what errors popped up.  I get the following:

2008-04-28 17:10:50.373 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-28 17:10:50.689 XScreenSaver support enabled
2008-04-28 17:10:50.689 DPMS is active.
2008-04-28 17:10:50.690 Empty LocalHostName.
2008-04-28 17:10:50.690 Using localhost value of me
2008-04-28 17:10:50.692 Testing network connectivity to mythtv
2008-04-28 17:10:50.712 New DB connection, total: 1
2008-04-28 17:10:50.716 Connected to database 'mythconverg' at host: mythtv
2008-04-28 17:10:50.728 Closing DB connection named 'DBManager0'
2008-04-28 17:10:50.730 Primary screen 0.
2008-04-28 17:10:50.732 Connected to database 'mythconverg' at host: mythtv
2008-04-28 17:10:50.734 Using screen 0, 1920x1200 at 0,0
2008-04-28 17:10:50.748 New DB connection, total: 2
2008-04-28 17:10:50.750 Connected to database 'mythconverg' at host: mythtv
2008-04-28 17:10:50.753 Unexpected DB Schema version.  Waiting to see if DB is being upgraded.
2008-04-28 17:10:55.775 Timed out waiting.
2008-04-28 17:10:55.775 This version of MythTV requires an updated database schema. Please run mythtv-setup or mythbackend to update your database.

I noticed the frontend in 8.04 is MythTV version .21 while my backend is running .20.  The 'updated database schema' message leads me to believe the two versions are not compatible?  Couldn't find anything to confirm this with google searches, but I probably wasn't asking the right question.  Anybody out there knows why this isn't working?

Thank you.

Confirmed, yes you need .21 on all networked machines. If you don't want to mess with your backend.  Install mythbuntu 7.10.  It includes mythtv .20.  You will need to be careful on your sources.list.  Ask over on mythbuntu forums how to avoid .20 to .21 update.  You may need to comment out backports.

To answer your question.  They are not compatible.

---

### Post by Nrgh on 2008-04-29
Thanks for the replys.  Looks like the backend needs to go to .21.  I haven't tried Mythbuntu yet, but if I need to do some work on the backend, now might be the time to switch from KnoppMyth...

---

