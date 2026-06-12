---
title: "Organizing files in MythVideo"
date: 2010-07-19
forum: Mythbuntu
---

### Post by mdifabio on 2010-07-19
Finally started backing up Blu-Ray discs on my backend so I added a second hard drive.  I mounted the second drive at "/var/lib/mythtv/videos1" right next to where my other videos are kept in "/var/lib/mythtv/videos".  I have many .iso files already, so when I upgraded to 10.04 I chose to do the work for NFS mounting to my two frontends because storage groups are not yet working for .iso files.  In setting up the NFS, I simply mount both of the videos directories (videos & videos1) at each frontend.  Then on the frontend, in Utilities/Setup, Setup, Media Settings, Videos Settings, General, I put both the directories for videos & videos1 in the "Directories that hold videos:".

This works to make all the videos available at each of my frontend.  However, it is not clean.  By this I mean that at the frontend "Videos Gallery" (where the movies are displayed) I have to scroll through the actual folders on screen var, lib, mythtv, videos & videos1 to get to see the actual movies.  Whereas before, when I only had one hard drive with videos on it, all the movies came up right away in the Videos Gallery and no other folders were there.  That is cleaner.

So what I ask is this.  How can I set up Mythtv so that all the videos on two different drives from my backend can be viewed in one clean Videos Gallery at the frontend?  

I have tried messing around with ln -s with no avail as well.  Each way I tried created at least one extra folder in the Videos Gallery that I would have to click on to view the rest of my videos on the extra hard drive.

I am not the sharpest with Ubuntu and Mythtv, but I have gotten this far, so if someone could be so kind and help me out here.  There is probably a simple answer that I will be thrilled to hear about.

Thanks!

---

### Post by andree_b on 2010-07-22
Not the most elegant solution but you could symlink all files from videos1 in videos

```
ln -s /var/lib/mytthv/videos1/* /var/lib/mytthv/videos
```

and just have the videos directory configured.

You need to update symlinks each time you add files to videos1

---

### Post by chipppy on 2010-07-23
Quick answer is to use the storage groups (not an option due to the .iso files)

I run the same sort of setup as you only i have a few more HDD's in the game.

I have mounted each HDD inside the a seperate directory all together called HDD's.  therefore path is /var/lib/mythtv/HDDs
I have also edited SETUP to point to the aboe path.  When I run front end I get 5 folders Kids, Family, Home movies, SciFi1 SciFi2.  each HDD has its own name for the movies it holds.

At a guess you have not modified your SETUP correctly to points at var/lib/mythtv correctly, and that is you you have to drill through the folder to get to videos.

May i recommend that you change your mount point to inside .../videos for your second HDD this will make things a little easier.
The changen your SETUP to point to var/lib/mythtv/videos
This should then leave you with one folder on the first page and inside that is all the movies on your first HDD + a folder leading to your second HDD.  inside that folder is all the movies on your second HDD.

One thing if you havent full disabled storage groups you will end up on the first page a storage group folder and videos folder.
remember that you are not using storage groups so you will have a folder system if there are any folders inside the .../videos folder as it is still based on the structure and not the overall search functionalitiy of storage groups.

Hope this helps

cheers
chipppy

---

### Post by tgm4883 on 2010-07-23
The correct way to use multiple drives with legacy mythvideo settings (read pre-storage groups) is to configure the local video directory like this


```
/var/lib/mythtv/videos1:/var/lib/mythtv/videos
```

---

### Post by mdifabio on 2010-07-24
> **andree_b said:**
> Not the most elegant solution but you could symlink all files from videos1 in videos

```
ln -s /var/lib/mytthv/videos1/* /var/lib/mytthv/videos
```

and just have the videos directory configured.

You need to update symlinks each time you add files to videos1



AWESOME!!!  This was so simple, but I missed it.  It accomplishes everything I wanted to.

Thanks Andree B

Do you think it is possible to put this ln -s command somewhere so that it will run automatically?  Not sure where I'd put it, but that would make it easier on the wife.

---

### Post by mdifabio on 2010-08-03
> **mdifabio said:**
> AWESOME!!!  This was so simple, but I missed it.  It accomplishes everything I wanted to.

Thanks Andree B

Do you think it is possible to put this ln -s command somewhere so that it will run automatically?  Not sure where I'd put it, but that would make it easier on the wife.
Can I do a cronjob of that ln -s command?

---

### Post by andree_b on 2010-08-03
> **mdifabio said:**
> Can I do a cronjob of that ln -s command?
Why not? Just make sure ln is not configured to run interactive by default on your system (--> asking if link shall be overwritten if already existant).
You could use "ln -sf" but this might overwrite files with same filename on both directories which might not be desired.

---

### Post by newlinux on 2010-08-03
> **tgm4883 said:**
> The correct way to use multiple drives with legacy mythvideo settings (read pre-storage groups) is to configure the local video directory like this


```
/var/lib/mythtv/videos1/:/var/lib/mythtv/videos
```

Not intending to nitpick, just help other users who may come by, but I think the separator is a colon not a semi-colon.

---

### Post by tgm4883 on 2010-08-03
> **newlinux said:**
> Not intending to nitpick, just help other users who may come by, but I think the separator is a colon not a semi-colon.

Yep you are right, fixed. Thanks

---

### Post by mdifabio on 2010-08-10
> **andree_b said:**
> Why not? Just make sure ln is not configured to run interactive by default on your system (--> asking if link shall be overwritten if already existant).
You could use "ln -sf" but this might overwrite files with same filename on both directories which might not be desired.

Not very familiar with setting up a cronjob.  Can you help me a quick step by step that will get me to accomplish what I am setting out to do?  Upon startup, link new files in my ".../videos1" folder to the ".../videos" folder without overwriting anything.

Thanks,
Mike

---

### Post by mdifabio on 2010-08-10
> **newlinux said:**
> Not intending to nitpick, just help other users who may come by, but I think the separator is a colon not a semi-colon.

This way of setup seems like it should work, but no matter how I try to put the location of both folders in that setup menu (I tried your way and others), it gives me all the videos from my ".../videos" folder in "Videos" and a folder link starting with "var" that leads to "lib" that leads to "mythtv" that leads to "videos1" which finally shows the other videos that are in the ".../videos1" folder.  But I don't want my videos separated from view in mythtv which forces me to push a button on my remote a bunch of times to look at the other videos in my collection.

I hope this states what I want.  Sorry if I rambled on too much.

thanks,
Mike

---

