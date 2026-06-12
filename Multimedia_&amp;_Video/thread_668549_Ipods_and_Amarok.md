---
title: "Ipods and Amarok"
date: 2008-01-15
forum: Multimedia &amp; Video
---

### Post by Rabidmonkey1 on 2008-01-15
Hi all,

I've been helping a friend make the linux switch from XP.  Specifically, I installed Linux Mint on his system.  He has an Ipod that was working with Amarok, until one day he received an error concerning ituneslock.

The computer recognizes and mounts the Ipod.  Amarok can see the ipod as well.  It just can't upload files to it because Ituneslock is a piece of code Apple designed to prevent other (non-apple) software from interfacing with the ipod.  

I've gone in and deleted the ituneslock file inside the ipod,but the ipod actually regenerates the file.  I'm not sure how to get around this so that he can use Amarok to manage the Ipod.  Any suggestions?

Thanks!

---

### Post by barney_1 on 2008-01-15
I've had a lot of problems using my ipod with Ubuntu.  I have had troubles with it losing connectivity during transfers and giving me the itunelock problem.  I have also had troubles with 3-5 seconds of a different song appearing in the middle of a song during ipod playback.  These issues don't happen in Windows.

I believe that your ipod is being mounted as read-only (on the ipod end of things, not on the linux end of it).   You need to get it to mount in a writeable format in order to actually delete the lock file.

At the least, you should connect the ipod and try deleting the lockfile, then try to connect to it with Amarok:
```
rm /media/IPOD/iPod_Control/iTunes/iTunesLock
```

Hopefully it's that easy but sounds like you already tried that one out.

---

### Post by Rabidmonkey1 on 2008-01-15
Hmm, I didn't try an rm or sudo rm, I was just deleting thru the gui... I'll try that soon.  Does anyone else have any other suggestions while we are here?

This post seems relevant for anyone having a similar problem as me: [http://ubuntuforums.org/showthread.php?t=497201&highlight=ituneslock](http://ubuntuforums.org/showthread.php?t=497201&highlight=ituneslock)

---

