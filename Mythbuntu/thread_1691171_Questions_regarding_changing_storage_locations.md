---
title: "Questions regarding changing storage locations"
date: 2011-02-19
forum: Mythbuntu
---

### Post by nhtrader on 2011-02-19
I am interested in moving my recordings to a new folder.

I know that I can change the backend's default directories and I'd like to move /var/lib/mythtv/recordings to /home/mythtv/recordings.

But I'm not sure what will happen to my existing recordings?

After I change the backend's default storage location/directories ...
1. will this be a problem moving files into the mythtv user space? 
2. Do I need to change permissions? username? groupname?
3. will this move create problems with the MYSQL database?
4. are there any other parameters that need to be changed?

---

### Post by LowSky on 2011-02-19
1. no not a rproblem at all.
2. The folder need to have rights of the mythtv group. Note your current user name is also in the mythtv group.
3. It should not, as long as you keep the recodings names correct and point to the folder location correctly.
4. If you have music and other videos you wish mythtv to see, those directores need to be pointed from the frontend:
utilities/setup>setup>media settings changes directories as needed.

Remeber to create the folder names in the directores needed. best is to copy the folders over from /var/lib/mythtv directly to the new /home location

and to recreate them in the /home dir as well

---

### Post by nhtrader on 2011-02-22
For future reference, I made the following changes while MythTV was not recording.

I had a bit of trouble using the "mv" command, but that's b/c I'm still new at using linux commands. So despite my ignorance, I moved this folders to /home/mythtv as "root" user and the file permissions of those files moved remained intact.

Then I went into the backend and frontend and changed all paths. As "lowsky" instructed, MythTV didn't miss a beat. The database is intact and all metadata tagged to a recording is fine.

This turned out to be a smooth operation. No problems thanks to "lowsky"

Last question, why do suppose the developers chose the default DIR as /var/lib/ rather than putting user data in the /home/ DIR which is by design to separate the OS from user data?

BTW, the only reason I'm moving the recordings is b/c I want to make a LiveCD of my current OS and the 400Gb of user data is preventing me from copying only the OS. Secondly, should I want to swap out a hard drive, I could simply replace my /home/ DIR with a new HDD and the OS would not be removed.

---

### Post by LowSky on 2011-02-24
Um.. ask the devs? I have no idea why they choose /var/lib to be

 fair some people create a seperate partition for the /var folder, maybe that was what was expected early on

Or if you run you OS using the entire hard drive, partition space isn't an issue then too.

---

