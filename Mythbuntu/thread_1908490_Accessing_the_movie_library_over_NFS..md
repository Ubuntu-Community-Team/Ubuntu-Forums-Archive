---
title: "Accessing the movie library over NFS."
date: 2012-01-13
forum: Mythbuntu
---

### Post by TheFuzz4 on 2012-01-13
So at home I have a NFS share that is running on one of my other linux VMs.  The NFS contains our entire movie library that up until I started down the MythTV path we've used Mediatomb and MiniDLNA to stream the movies to our PS3s and WD Live boxes.  But since Myth also functions as a DLNA server there is really no reason for me to leave these other DLNA servers running.  The problem is that I cannot for the life of me get Myth to do a directory listing on the movies in the folder.  I've setup a mount point on the backend (which is just that I'm not running front and back together)  and added the mount point to directory list for Videos in mythtv-setup.  I've checked the perms of the NFS its set to 777 and the user/group is nobody:nogroup so I can't imagine it being a permissions issue.  Is there something special that I need to do, to get Myth to go dive into the dir?  I set Myth up with a sym link to the Movies because of the fact that I named my Movies folder Movies and the such (From my winders days) If myth has an issue with the spaces in the folder name through a sym link than I'll just change the dir name.  But myth is configured to hit /media/Movies.  So I'm kinda at a loss here as to what I need to do, in order to get myth to see it.  Thank you in advance for your help with this.

---

### Post by nickrout on 2012-01-14
> **TheFuzz4 said:**
> So at home I have a NFS share that is running on one of my other linux VMs.  The NFS contains our entire movie library that up until I started down the MythTV path we've used Mediatomb and MiniDLNA to stream the movies to our PS3s and WD Live boxes.  But since Myth also functions as a DLNA server there is really no reason for me to leave these other DLNA servers running.  The problem is that I cannot for the life of me get Myth to do a directory listing on the movies in the folder.  I've setup a mount point on the backend (which is just that I'm not running front and back together)  and added the mount point to directory list for Videos in mythtv-setup.  I've checked the perms of the NFS its set to 777 and the user/group is nobody:nogroup so I can't imagine it being a permissions issue.  Is there something special that I need to do, to get Myth to go dive into the dir?  I set Myth up with a sym link to the Movies because of the fact that I named my Movies folder Movies and the such (From my winders days) If myth has an issue with the spaces in the folder name through a sym link than I'll just change the dir name.  But myth is configured to hit /media/Movies.  So I'm kinda at a loss here as to what I need to do, in order to get myth to see it.  Thank you in advance for your help with this.

You have pressed menu|scan for changes?

If so, what does the frontend log tell you when this is happening?

---

### Post by TheFuzz4 on 2012-01-16
Yeah so I'm going to mark this as solved because I forgot to press menu and scan for changes.  I'm used to using services like MediaTomb so I thought that Myth worked the same way.  Thanks for shining the light on this one.

---

