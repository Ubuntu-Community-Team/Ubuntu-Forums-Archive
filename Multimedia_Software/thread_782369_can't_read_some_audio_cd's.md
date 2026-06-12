---
title: "can't read some audio cd's"
date: 2008-05-04
forum: Multimedia Software
---

### Post by Pollywoggy on 2008-05-04
Some of my apps can read a certain audio CD while others such as grip and ripperx do not.  Amarok can play it and Sound Juicer can rip it, but I want to get the files in mp3 format and Juicer won't do that.  Grip and ripperx can make mp3 files.

Other CD's are readable by all the apps, it's just this one CD that is 12 yrs old that isn't seen by grip or ripperx.

Any ideas?

---

### Post by billd42 on 2008-05-05
In the out-of-the-box configuration, grip uses cdparanoia to read the CD.  What happens if you use cdparanoia from the command-line to try to read this CD?  Can you paste some sample output?

If this is an older CD it's possible that the CD itself has started to degrade, and cdparanoia is having difficulty reading it.  Some people have found that CDs from the 80s have degraded over the 20+ years since they were manufactured.  ISTR reading something in an audiophile blog about one particular batch from the 80s where the aluminium layer wasn't sealed in properly and CDs in that batch have begun to oxidize.  But you say that this disc is about 12 years old, so it's a bit young for that.

---

### Post by Pollywoggy on 2008-05-05
> **billd42 said:**
> In the out-of-the-box configuration, grip uses cdparanoia to read the CD.  What happens if you use cdparanoia from the command-line to try to read this CD?  Can you paste some sample output?

If this is an older CD it's possible that the CD itself has started to degrade, and cdparanoia is having difficulty reading it.  Some people have found that CDs from the 80s have degraded over the 20+ years since they were manufactured.  ISTR reading something in an audiophile blog about one particular batch from the 80s where the aluminium layer wasn't sealed in properly and CDs in that batch have begun to oxidize.  But you say that this disc is about 12 years old, so it's a bit young for that.

I will try some command line commands today with the CD to try to get some information, but this particular CD does play and some apps such as Sound Juicer and Amarok can read it, but Grip does not.

---

### Post by Pollywoggy on 2008-05-05
> **Pollywoggy said:**
> I will try some command line commands today with the CD to try to get some information, but this particular CD does play and some apps such as Sound Juicer and Amarok can read it, but Grip does not.

cdparanoia is working and ripping the CD, so the problem has to be Grip.
I will need to do some Googling to get a proper command line arrangement for ripping the CD and converting to mp3.  I don't remember how to do it, though I already have Lame installed.

thanks for the help

---

### Post by Pollywoggy on 2008-05-05
Grip is now working with the problem CD.  The machine was off for the night, so perhaps something in the reboot fixed it.

---

