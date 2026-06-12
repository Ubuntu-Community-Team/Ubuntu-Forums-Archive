---
title: "Burning CDs and DVDs"
date: 2010-06-01
forum: Multimedia Software
---

### Post by Dmjthomas on 2010-06-01
Hello,

since updating to Lucid I have not been able to properly burn DVDs and CDs.

I have looked everywhere for a solution to this and have been able to get some functionality but not full functionality.
I am using Brasero as I find it nice and easy to use. I read somewhere to get libburn4 and this may help some issues.

Since I did that, I managed to Burn an Audio CD, and today I have managed to Burn an ISO of Ubuntu 10.04, so that is at least some function back.

I can not burn Data CDs or DVDs. I have a few .avi files I wanted to burn on a Data Disc as burning as a movie to DVD means that I would have to waste loads of discs. I can't seem to burn any Data DVDs. To check that this wasn't just a dodgey blank disk I have tried burning data CDs using lots of albums on the CD. Still no luck. What seems to happen is that it generates a checksum then the box with estimated time remaining, write speed and progress comes up. It hangs for a minute then spits the disk out.

Has anyone else had any issues with this? Has anyone tried to fix this, or had any luck fixing this.

I've attached my Brasero Error log.

Thanks

---

### Post by lidex on 2010-06-01
Brasero of late has been problematic. A new bug-fix version was recently added to the repos. What version do you have? Mine is 2.30.1 You'll need to enable 'Pre-released updates (lucid-proposed)' in 'Software Sources' updates tab.

---

### Post by Dmjthomas on 2010-06-02
> **lidex said:**
> Brasero of late has been problematic. A new bug-fix version was recently added to the repos. What version do you have? Mine is 2.30.1 You'll need to enable 'Pre-released updates (lucid-proposed)' in 'Software Sources' updates tab.

I've now done this and ran the updates. I am now running 2.30.1. Still no luck burning Data Disks. When I read the log it says 

BraseroGrowisofs stderr: :-[ WRITE@LBA=0h failed with SK=5h/CANNOT WRITE MEDIUM - INCOMPATIBLE FORMAT]: Wrong medium type
BraseroGrowisofs stderr: :-( media is not formatted or unsupported.
BraseroGrowisofs stdout: HUP
BraseroGrowisofs stderr: :-( write failed: Wrong medium type

I'm guessing this means that the DVD-Rs aren't supported? They were supported before.

---

### Post by robert shearer on 2010-06-02
install k3b from the repos (and accept all the gubbins that comes with it).

Works consistently here, unlike brasero which seems to be a lottery as to if it will work at all when used.

It got to be so bad I gave up and installed k3b and have had no further problems or coasters.

---

