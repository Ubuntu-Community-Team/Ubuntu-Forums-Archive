---
title: "Blank DVD not recognized by Ubuntu 9.10."
date: 2009-12-28
forum: Multimedia Software
---

### Post by dln9 on 2009-12-28
I am running Ubuntu 9..10.  

I don't understand why, when I insert a blank DVD-RW, Ubuntu doesn't recognize it - it does nothing, it does not mount it, nor can I manually force it to be mounted.  

If I start Brasero 2.28.2, it has no idea that a blank DVD-RW is loaded in the drive.  

But - If I start GnomeBaker 0.6.4, it knows there is a DVD-RW in the drive, and it lets me burn files to it.  Then, since it is no longer a blank DVD-RW, Ubuntu then realizes that there is a DVD-RW in the drive, and will mount it.  And, Brasero also then knows there is a DVD-RW in the drive.  

I don't understand this behavior, nor how to fix it.  I will appreciate any help.  

dln9

---

### Post by the.bobas on 2009-12-28
I had the same problem. I found out, that GnomeBaker can burn the empty DVDs that won't mount. Since the DVD is filled, it mounts normally. And a tip: don't erase DVD+-RWs like CD-RWs. You can overwrite them without erasing (just delete the unwanted files - Remove all in Brasero)...

---

### Post by dln9 on 2009-12-28
Thanks for the reply.  

I don't understand the part in your posting about deleting stuff in Brasero using the "Remove All" function.  My understanding is that function removew files from a *project*, not from the disc itself.  

In fact, I now have some data files on a CD-RW disc, and in Brasero I can't figure out how to delete these files from the disc - other than blanking the disc.

---

### Post by Dave4077 on 2010-04-13
Hi I have the same problem with CD/DVD being recognised... I have been able to clear all data on a DVD-RW and upload data files to it, well so it appears, but now I can not read to the DVD to see what is on it... Having read the other enqiuries... and on other replies... I'm not sure we are doing the right things... can any of you bright sparks give us a hand in sorting the problem out please... Many thanks regards Dave...

---

### Post by carolinason on 2010-05-13
to make things even more odd. i didn't have this issue before in 9.10. when 10.4 was released i loaded it, but couldn't watch flash, which i need for tv shows. so, i reloaded 9.10 fresh and this bug magically appeared. i get an error message and will post it. i think we might need to look in launchpad for this. 

if i have to run 10.4, i'll have to boot into windows xp to watch flash, since my ancient ahem 8 year old 2.0 GHZ machine with an ati radeon 9600 is now obsolete. what happened to linux?

i'm obviously running 32bit see -> [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/486780]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/486780")

it says triaged, in other words won't get fixed.

as said earlier i can write to the dvd+rw in brasero. i don't write to any rw unless it's temp. otherwise i would use an r disk as an extra backup. two hard drives take care of most of my back up. i label my cd-rw's with a sharpie and they usually are the latest systemrescuecd and latest ubuntu.

an error after writing dvd 
> Error mounting: mount exited with exit code 1: helper failed with:
mount: /dev/sr0 already mounted or /media/cdrom0 busy

---

