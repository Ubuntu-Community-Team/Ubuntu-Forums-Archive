---
title: "No Video playback on remote frontends - 9.10."
date: 2009-11-08
forum: Mythbuntu
---

### Post by captangrypants on 2009-11-08
I am at a loss at the moment on why I cannot get my frontends to play back videos.

With previous versions: 
I have a file server that I keep all my videos on.  I mount this into the mythtv frontend/primary-backend with a SMB mount into /media and then I would symlink this structure into /var/lib/mythtv/videos.  I would then scan the directory with the frontend/primary-backend machine.

I would repeat this again with the frontend/secondary-backend machines.  I would not scan on the remote machines and the recordings and the videos would work without issue.

With 9.10:
I first started with this exact same setup.  
Recordings will work, Videos will not, though Videos are showing as being selectable but when you tell them to play the screen goes to just the background of mythtv but about 10 second later it will just pop back up with the play screen.

I then just setup remote frontends without the secondary-backends with all else the same.  Same problem.

I then started to read up on the Storage Groups.  I went ahead on the primary-backend and setup the SMB mount point within the Storage Groups.  I removed all the symlinks.  The frontend/primary-backend continues to work without issue.  The remote frontends continue to play the Recordings without issue but the videos are the same, the file listing are there, but they will not start.

I am completely lost here.  Also when I have the symlinks in place on the remote machines, VLC will play the files without issue.

The only thing I can think of is that it is an issue with the SMB mounts but I am limited that the file servers are currently running Windows.  Now I know I can get NFS most likely in place on the file servers but I would rather have opinions before I spend the time and energy on that.

Any and all ideas would be wonderful.

---

### Post by williammanda on 2009-11-08
There is an issue concerning the inability to view iso and vob files in ver .22. To get around this you need to remove the video storage group and then use nfs or samba to make the files avaiable to other FE/BE. This sounds like it could be your issue or at least part of it.

---

### Post by captangrypants on 2009-11-08
Thanks for the reply.

I am actually playing around with that right now, with removing everything from the storage groups.

But these files are avi, mpg, and similar not DVD structures or ISOs.

---

### Post by nickrout on 2009-11-08
> **captangrypants said:**
> Thanks for the reply.

I am actually playing around with that right now, with removing everything from the storage groups.

But these files are avi, mpg, and similar not DVD structures or ISOs.

what do the frontend logs say when you try to play a video?

---

### Post by captangrypants on 2009-11-10
Fought with this for a couple more days and I finally found a working combination.

I went ahead and on the backend I set the Storage Group for Videos to point to /media/null and then I pointed the video locations within the frontends to the place I had the SMB mounted files symlinked too.  This led to me having to file scan the structure on each of the frontend, but it does work now.

Also, I found that if you simply remove the listing for Videos on the backend storage group, it lead to the crashing to desktop of the any and all frontends.

Thanks for the feedback.

---

