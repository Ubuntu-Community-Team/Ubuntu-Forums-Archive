---
title: "Upcoming Recording List Empty"
date: 2007-12-27
forum: Mythbuntu
---

### Post by captangrypants on 2007-12-27
So the other night, I decided to rename my myth box.  I quickly used Webmin on the machine to do this task as I did with the rest of my machines.  A couple days later the machine is rebooted and my frontend isn't talking to the backend.  (Same physical machine)  I pulled up the control center and ran the myth setup to find that the IP for pointing to the backend had defaulted to 127.0.0.1 .  I changed this back to my internal IP for the machine.  At the same time, I had to remount an NFS mount and remake some symbolic links from the /var/lib/mythtv to this NFS mount.  I deleted the previous links first though.  I started up everything and I can watch live TV without an issue, watch older recordings without issue, watch video files without issue.
  
I checked to see what the machine had queued via mythweb to find that my upcoming recordings and my backend status queues were empty.  I have triple checked all my settings on the machines and everything seems to be in order.  I have checked the logs and the only thing that seems to be out of place is an error on a MythSocket line.

So being at the end of my knowledge with this problem.  I decided to backup my database, unmount my LVM which is placed at /var/lib/mythtv, and then reload the main OS boot drive of the machine.  After a reload, the machine was working properly across the board for all the basics.  I decided to remount the LVM and press up the old DB.  The problem with the missing upcoming recordings  has returned.  So I am guessing it is either a file that is housed under /var/lib/mythtv or something in the DB.

Anyone have any clues on this one?  What to repair? What I can try?  Mythweb is still reporting my recording schedule with all my preferences, but there is nothing in my queues.

Any places in the logs that I should look?  I have about 500 GB of recordings that I really would not like to loose my DB information for especially my son's favorite shows.

Thanks

---

### Post by ahood on 2008-01-22
I too have this problem. Mythweb does not list anything in the Upcoming Recordings page. I can see programs that have been recorded, just not what will be recorded. I can also see upcoming recordings on MythTV itself. I am using Mythbuntu on Gutsy.

Any info will be much appreciated.

UPDATE: I was mistaken. The reason I didn't have anything in the Upcoming Recordings part of Mythweb was because there were no scheduled recordings. It was apparent that my spouse removed the scheduled recordings that we had. My mistake....

---

### Post by irwand on 2008-06-28
I had the problem last night. Fortunately I managed to troubleshoot my problem. The problem happened for me when I was trying to configure a separate machine to access the master backend. During mythtv-setup, general setting, I changed the master server IP from 127.0.0.1 to the server machine name, but left the local IP to 127.0.0.1. Because the two IP are different, myth-backend on the master server was launched as a slave. I managed to find out about the problem from the log in the mythweb. I noticed that all mythtv-backend were all slave. Once I went back to mythtv-setup to fix the IP addresses to be the same (the real IP of the master backend machine), everything went back to normal. I don't know if this solution applies to you, captangrypants, but it fixed my problem.

---

