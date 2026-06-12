---
title: "Optimising storage for mixed local (SSD) / remote storage"
date: 2016-11-25
forum: Mythbuntu
---

### Post by bernard2 on 2016-11-25
I've been running MythTV for some time now: my current machine is running 0.27.6 frontend and backend on Ubuntu 14.04 (home-brew, silent HTPC). It has a 60GB local SSD for everything except media storage - which is Samba-mounted on a server. I'm currently using 1.1TB of a 1.5TB partition for Myth storage.

The main weakness in this setup is the network connection between the MythTV machine and the server, so I have just ordered (thanks to Black Friday and falling tech prices) a new 750GB SSD to go into the HTPC. I intend this to be the new main storage location for MythTV, while keeping the server space available so I can access old recordings and also use it if necessary for overflow.

I'm using two DVB-T2 tuners and it's quite common for there to be three or four recordings going on at once, especially during the start/end overlap times at peak hours like 21:00.

So, my question is, how should I set up the SSD storage area for best performance? After knocking off some space for root, home, swap etc I will have about 700GB left over. Should I set this up as one partition, or two, or more?

Which Storage Group Scheduler option should I go for?

The outcome I'm trying to achieve is that all new recordings go to the SSD, unless it fills up, when the server space will be used. While being able to access old recordings on the server.

I've been reading this: [https://www.mythtv.org/wiki/index.php/Storage_Groups](https://www.mythtv.org/wiki/index.php/Storage_Groups) (including the "advanced" topics) ... it suggests that "Combination" will give priority to local drives, which is what I want.

But I'm not sure how smart the scheduler is about "drives": it says that if there are two recordings going to one local disc, then a third recording would go to the remote disc. But will the scheduler realise that two partitions are on one disc and calculate accordingly?

Do I need to fiddle with SGweightLocalStarting ?

Comments welcome.

---

### Post by bernard2 on 2016-12-09
Well, I have fiddled with SGweightLocalStarting (here is a helpful thread on how exactly to do that - [http://lists.mythtv.org/pipermail/mythtv-users/2008-October/235698.html](http://lists.mythtv.org/pipermail/mythtv-users/2008-October/235698.html) ) and for the moment set it to -39, which I think means that the first four concurrent recordings will be sent to the local disc, other things being equal. A quick test suggests this might be working.

However I've not been able to work out whether the scheduler would treat a folder on /dev/sdca as being on the same "disc" as one on /dev/sdcb for load balancing purposes. They are different partitions, but the same spindle... Can anyone help me with this one?

---

### Post by kpatz on 2016-12-09
I don't know offhand how the scheduler works, but it's simple to tell if a partition is on the same drive or another.  2 partitions on the same drive would be /dev/sdb1 and /dev/sdb2, for example.  2 partitions on 2 different drives would be /dev/sdb1 and /dev/sdc1.  It's possible the scheduler knows this, but you can always try it as a test.

There's no benefit to creating 2 data partitions on the same drive for MythTV though.  Just make it one big partition, makes managing the setup and space better.

If your file server is Linux, NFS is more efficient than CIFS/Samba.

EDIT: Reading the link you provided, it seems that in the combination mode the scheduler only weights based on local/remote, then utilization, then free space.  So by default it should record to the local filesystem first, and then the remote.  Now if you have 3 recordings going to the local filesystem, will it send the 4th to the remote?  Depends on the weights.  There are suggestions on the advanced section on how to set the weights to ensure that the local filesystem will always be used until it fills, then it goes to the remote.

> So, if you have less than 4 tuners and 2 local drives, then the default should already give you what you are looking for. If you have more than 4 tuners or want to guarantee that all recordings go to the local drives unless they fill up, you can do so using the undocumented SGweightPerDir setting.
In order to make MythTV not use a filesystem/directory, we need to artificially inflate the starting weight for that directory. We can do this by inserting a setting in the database.
The key for the setting is SGweightPerDir:HOSTNAME:DIRECTORY. The hostname is the hostname that sees the directory. So if the directory is actually on the fileserver which is server1 but is mounted via NFS on server2 which is running mythbackend, we'd use server2 here. The directory is the local path on HOSTNAME, so you'd put /mnt/video or whatever you use here for the remotely mounted directory.
   ```
SGweightPerDir:server2:/mnt/video
```

---

### Post by bernard2 on 2016-12-10
kpatz - thanks for the response.

I'm using Samba, BTW, because I also want the same network shares to be accessible from Windows machines, which is much easier to do with Samba. Yes, I could do both but my life is complicated enough already!

And, if I've read the document correctly, and without having changed any  of the other parameters, each recording counts as a weight of 10 so it  would only be after having four of those that the total weighting of my  local disc (4*10 added to the new starting value of -39) will be greater  than the weighting of an otherwise unused remote disc (0). If I hadn't changed SGweightLocalStarting, it would have switched to the remote disc for the third recording, which is what I was seeing. Not good when you have multiple HD streams trying to fight their way down a dodgy network!

For the moment I have just one large partition on my local data disc. I just found it frustrating to see documentation talking about "discs" when it wasn't clear (to me at least) what they meant by that. I was so desperate I even had a look at what I think is the code - [https://code.mythtv.org/doxygen/scheduler_8cpp_source.html](https://code.mythtv.org/doxygen/scheduler_8cpp_source.html) - this may not be quite the version I have but I guess it's similar. My coding skills aren't brilliant and there is a lot of code here, but I have the impression that it doesn't dig any deeper than file systems - so if /mnt/video1 and /mnt/video2 are on different partitions then it will just see them as being different, regardless of whether they are sharing a spindle or not. I could easily be wrong about that, though.

Having said that, I guess I really only cared because I thought that I might game the scheduler by giving it two partitions, both local on the same "spindle" (actually SSD). If I'm right, then it would by default put two recordings on each of the two partitions, before going to the remote disc for a fifth recording. This would have been easier than fiddling with the scheduler settings (they really haven't made this easy!) at the expense of the inherent inefficiency of managing two separate spaces.  Since I have now gone to the trouble of fiddling with the settings, I suppose I no longer care, but my curiosity is still there!

---

### Post by khPWXxF on 2016-12-15
You will need to fix that network problem, apart from any considerations of SSD vs HD.
 
In considering using two devices you have opened up an interesting discussion.  I looked at the possibilities of having a hierarchical system with Mythtv a while ago.  My thinking went along the lines of have two storage partitions:  a smallish one on fast SSD, a bigger one on slower HD or NAS.  All recordings would be created initially on the fast SSD.   Then, run a daily job to:
 

[LIST=1]
[*]Check how full the HD is and remove oldest recordings to free up space:
[*]Check how full the SSD is and move older recordings to HD to free up space.
[/LIST]
 
That would allow most disk traffic to be concentrated on the SSD, would keep it fairly full, and only put older stuff on the HD.   You could modify stage 2 to copy (not move) new recordings immediately then delete the file from SSD when it fills.  This would duplicate the most recent ones and provide some backup against device failure.
 
Initially it all sounded pretty straightforward (scan database via API, scan folders, sort, decide cut-off points, move or expire, report – job done).  It was only when I started writing code that the complexities popped out.    Issues such as

* If you use the delete recording API then I think it would only mark the recording as deleted, and not actually remove it from the HD partition.  Doesn’t actual deletion only take place prior to a fresh recording to the HD (which isn’t happening here)?  Would we need a third step to overwrite the ‘deleted’ file with a zero byte file?

* What if there were inconsistencies which really need sorting out with find-orphans and human intervention?   All hell could be let loose if any of this were to be automated and there were a minor glitch (eg disk not found) or in the middle of doing a transition from (say) 0.27 to 0.28.

* Once the code had decided what should be the destiny of each recording it became complex to implement –  32 initial states (on SD, on HD, deleted, zero length, ‘do not expire’) and five actions (copy, move, remove from SSD, expire, set length zero).

* The sort of recordings by ‘desirability’ for retention on SSD/HD is an interesting area in its own right once the above points are resolved.  A simple sort on age is an obvious start but would age * size be better?; Can we be more subtle about the ‘keep 3 latest’ recordings that swmbo wants but never plays?;  should series have special treatment, etc?
 
Any views appreciated.
Phil
 
PS The idea of hierarchical storage is not new - look up ICL George 3 in the wiki.

---

