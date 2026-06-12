---
title: "iPod Video Rythmbox Sync Issue (HFS writing)"
date: 2010-05-22
forum: Multimedia Software
---

### Post by M1GEO on 2010-05-22
I am trying to sync my Apple iPod Video (not sure which generation) with Rhythmbox.  It was, in a previous life, formatted with FAT32.  However, after deciding to start again (and not having Windows), it is now formatted in Macintosh (HFS) format.

Rhythmbox detects the iPod fine and all appears to work.  However, when I come to dragging the music I wish to sync, I get the error:
> Error transferring track
Error opening file '/media/48c1ebd4-6d27-3147-8020-240daf2e2a5e/iPod_Control/Music/F14/02 Don't Stay.mp3': Read-only file system

I guess is because my computer isn't able to write HFS file systems.  Searching the repos had me install *hfsutils* and *hfsplus*, but to no avail.

*mount* tells me that the device is mounted rw:
> george:~$ mount | grep sdh
/dev/sdh3 on /media/48c1ebd4-6d27-3147-8020-240daf2e2a5e type hfsplus (rw,nosuid,nodev,uhelper=udisks)

Is anyone able to offer advice on how to enable writing to the ipod?

Cheers, George

---

### Post by M1GEO on 2010-05-22
It's okay.  I caved and got a friend to format it in iTunes under Windows XP.

---

