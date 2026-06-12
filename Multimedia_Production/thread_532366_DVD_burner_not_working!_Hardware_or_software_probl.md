---
title: "DVD burner not working! Hardware or software problem?"
date: 2007-08-22
forum: Multimedia Production
---

### Post by endre on 2007-08-22
Hi, I am having problems getting any sort of DVD stuff done on my computer, Windows or Ubuntu, just as FUBAR.

What happens is that whenever I try to do a burn, either in qdvdauthor or straight from nautilus, either nothing happens, or I am told that an "unmanageable problem" has occurred (in nautilus - in qdvdauthor nothing happens.)

In Windows the software complains about the disc not being of the right format...

So, I guess you all  will need some background info to help me with this...

I have an Aopen 1557 with 1 Gb of RAM and 1,6 Ghz processor... so it should be strong enough.

I have a DVD+RW RW8165 drive, that is, it is made by the wonderful people at Ricoh. Ubuntu recognizes it, although I am not sure it has a perfect driver for it. In the Hardware Information section it says that the unit functions are "storage", "block", "storage.cdrom" Maybe that says something to someone...

The disc I am trying to use is a DVD+R 4,7 Gb (single layer) disc, so I don't see any problems there, but then again, maybe someone does. 

As I said in the topic, I am not sure if this is a hardware or a software problem. I have burned dvd's on this computer earlier, but since then I have reformatted it several times to clean up stuff, and it might be that some important parts of firmware have gotten lost in the process....

Thoughts, anyone...?

---

### Post by nalmeth on 2007-08-22
Do you really mean 4.7 gig discs? I didn't know there was such a thing.

I've never had a DVD-burner that "just didn't work" with the linux kernel, so **I** would feel safe ruling that out.

If you didn't make a type-o with the 4.7 discs, judging by the windows error I would say that the discs must be at fault.

Can the drive read media without problems? Does it detect the blank discs you put in there in the first place?

Try installing k3b, perhaps it will give you a more detailed error message. If we need more detail, you can burn with the command line and it should tell you more transparently whats going on.

---

### Post by endre on 2007-08-23
Hey, thanks for your answer!

Yea, I really mean 4,7 Gig. I have the disc in my hand here right now, it is made by TDK, and is labeled "DVD+R 1-16x 4,7GB DATA/VIDEO." I checked in the store, and I got the impression that everything offered around here (in Iceland) seems to be 4,7 GB. (Although I have noticed a lot of the software is written with 4,3 in mind. Different standards?)

I can try K3b, and see what it tells me, but I guess it won't make much difference if it really is the disc. 

And yea, it detects the discs btw, and reads every kind of media perfectly. I have a shining silver disc on my Ubuntu desktop right now labeled "DVD+R" 

Thanks!

---

### Post by trippinnik on 2007-08-23
What version of Ubuntu do you have?  I ran into a problem with edgy where the burner's write access was limited and i had to run as root, or chmod 777 /dev/cdrom(or whatever your burner is located at)

---

### Post by endre on 2007-08-23
Running Feisty.... don't know about the ownership issue, how do I find out? Burn a regular cd maybe and see if it works....?

---

### Post by trippinnik on 2007-08-23
i guess you could start your burning program as root (although feisty doesn't seem to have the ownership problem) gksudo gnomebaker (or k3b) and then try to burn the disk.  
also check the output of dmesg command.  it might show some errors.

---

