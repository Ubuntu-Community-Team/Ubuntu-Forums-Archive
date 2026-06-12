---
title: "MythTv database restore failed"
date: 2013-01-14
forum: Mythbuntu
---

### Post by brian_hayward on 2013-01-14
Hello, i was running Mythbuntu 11.10 as my primary backend and frontend.  I run it with 2 hard drives, one which contains all of the OS stuff, and the other is used for storing my recordings, livetv, banner, fanart, database backups, etc, etc.  One day over the christmas holiday i thought i would create a remote frontend on my Mint box in my office so i could watch some tv while i did some work and because it is the room i sleep in when i have company.  I'm not sure what i did but i really hosed up my Mythbuntu box so badly that it didn't work anymore.  So i got scared and re-installed Mythbuntu 11.10 and planned to restore a recent backup of my database (a backup days before my meddling).  That is what i did when i went from Mythbuntu 10.10 to 11.10 so i wasn't worried in the least.  Setting up my Mythbuntu box again i used the same user name and hostname as my previous setup, and i mounted the hard drive which contained all of my recordings to the same mount point as before.  Then i replaced the new database with my backup with the mythconverge_restore.pl script per the mythconverg wiki by using this command:

```
mythconverg_restore.pl --drop_database --create_database --filename mythconverg-1214-20080626150513.sql.gz
```

Then i rebooted my newly installed machine.  After boot up, i made sure my recordings hard drive mounted to the proper location, i went into the mythbackend setup and i made sure that all of the storage locations were pointing to each respective location and everything checked out.  I thought everything was fine because i did not get the error message when exiting the backend setup informing me that mythtv could not write to a certain storage directory; however, when i go to the mythfrontend to watch a recording, nothing shows up.  i can see, in text, the name of the tv show, and each episode, but the thumbnails don't show up, and when i select an episode to watch i get an error message.  i thought something may have been wrong with the database so i opened the command line, and logged into mysql with the login credentials shown in the mythtvfrontend setup; i was able to login no problem and i navigated some of the tables in the mythconverg database and everything looked fine there too, but i am not a MySQL expert so i wasn't real sure what i should have been looking for.  For good measure i even opened the ~/.mythtv/mysql.txt and the username, password and database name were all correct.  Then i backed up all of my recordings to another drive, and i ran the mythrename.pl script to rename all of my recordings and it was successful, i think.  i have a lot of recordings so i didn't go through each one to make sure the titles matched what the file actually was, but the point is the script took the data from the mysql database and renamed all of my recordings.  So now i am stumped and i don't know where to go next.  I upped my log level to log ALL MESSAGES, deleted my previous logs, rebooted and tried selecting an episode to watch.  i have attached the resulting logs in this post.  I really had to pair my logs down so if you notice some inconsistencies in the time stamp of each entry i probably deleted some repeating lines to get the file smaller so i could upload it.  I tried searching google for an answer but failed.  If anybody has had a similar problem and know of some other forum posts that would be helpful please let me know, or if anybody has some other ideas of what i can try i am all ears.  Thanks for the help.

---

### Post by PhilWig on 2013-01-15
A few suggestions to try and diagnose the problem,but clutching at straws really:
1.  Try find_orphans.py to see what discrepancies there are
2.  Did you specify the directory holding the backups - either with --directory or in ~/.mythtv/backuprc
3.  Try --verbose for more information
Phil

---

### Post by klc5555 on 2013-01-15
From the logs, the database seems to be normal. It just can't find the recordings it knows about. On the other hand, you likely added/mounted your storage drive after the main OS/mythtv installation. So:

1) Check that the owner/grp/permissions of your newly-mounted storage directory are correct (i.e. mythtv:mythtv, permissions set (usually) at about 775).

2) Make sure your storage drive/directory is mounted at the exact mount point mythtv backend thinks it is. Make sure the path down down to where the recordings are stored matches up exactly to what mythbackend thinks that path is. 

If mythtv is looking through its storage directories and finds one of them is empty (because your storage directory is mounted at slightly the wrong place), it will still happily use that empty directory. It just won't be able to find any of the recordings that are actually on the mislocated storage disk.

---

