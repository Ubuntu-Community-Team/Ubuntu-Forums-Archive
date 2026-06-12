---
title: "Full disk and corruption. . ."
date: 2008-01-28
forum: Mythbuntu
---

### Post by michwill on 2008-01-28
Hi All,

I'm having a bit of a problem with Mythbuntu.  After multiple installs of both MythTV + Feisty Fawn, and Mythbuntu itself, I constantly encounter full disks and corruption.

I have a vanilla Myth install in each case.  I don't have *any* shows set to "keep".  After a fresh install, things always run fine.  Then, a few weeks later, the disk fills up and the entire system is brought to it's knees;  only for me to repeat the process.

As you can imagine, this process is amazingly irritating.  Is there something I'm missing?  Perhaps a magical setting somewhere that tells Myth to "get the lead out!" ?

I have tried different HDs, so I'm fairly confident this isn't a hardware issue.  The current disk is a 160GB Samsung.

I've looked at this various threads, but none seem to speak to this recurring issue specifically.

Please advise.

Best Regards.

---

### Post by stdPikachu on 2008-01-28
What's on the hard drive when it fills up? Where are you storing your recorded programs?

Sounds very like you're using the default at /var/cache/mythtv; if you use the default partitioning setup in Ubuntu (i.e. one big partition for everything) you'll end up with a root drive with no space on it which, eventually, nets you a b0rked system. I'd highly recommend putting myth recordings on their own partition (personally I use a dedicated hard drive mounted at /storage/tvstore) so that even if it does fill up it won't bring down the rest of your system.

Still though, sounds like something is eating disc space when it shouldn't be as Myth is meant to automatically delete things to make space for new recordings. What does an ls -lah /path/to/your/tvstore show?

---

### Post by ubnewbie2 on 2008-01-28
There's also a setting in myth to tell it to leave 'x' amount of space free.  Set that to 5GB or so, and if you still have problems, something else is filling the disk up.

---

### Post by LeDechaine on 2008-02-28
Interesting. This just happened to me too.

I installed MythBuntu on this Ubuntu machine today, and maybe 6 hours later Mythbuntu freaked me out by using the 300+mb that was left of my linux partition. I don't know why, I just know it crashed and I had to kill it, and, seconds later, the partition had 0 octets free. *Ouch.*

If this can help, i've noticed that python was using 70-80% CPU (well, on a P3 866), don't know if it's related... weird coincidence if not. (Also note i've killed this program, I *may* have done a bad thing.. hehe)

Weird! Using the disk analyzer i just found that in **/var/lib/mythtv/recordings** there was a 266mb **1008_20080228041528.nuv** file!

---

### Post by laga on 2008-02-29
That's a very annoying issue. I hope the next myhbuntu installer will be a bit smarter about disk partitioning.

> 
Weird! Using the disk analyzer i just found that in **/var/lib/mythtv/recordings** there was a 266mb **1008_20080228041528.nuv** file!

Well, that's a recording. Why are you surprised? :)

For the other people: what filled up your hard drives?

---

### Post by LeDechaine on 2008-02-29
I'm surprised because I haven't chosen to record anything! I was just configuring MythTv!

---

### Post by laga on 2008-02-29
MythTV will record if you're watching LiveTV. Maybe that's the culprit?

---

### Post by LeDechaine on 2008-03-01
I see, well, uninstalling it soon anyway.

Either my computer is not powerful enough (P3 866) for MythTV or MythTV is buggy enough to make it hang.. So I have to kill it and after I look at my disk space left and the partition is full..

---

