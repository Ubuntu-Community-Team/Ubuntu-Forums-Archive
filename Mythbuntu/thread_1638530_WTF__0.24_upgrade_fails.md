---
title: "WTF?  0.24 upgrade fails"
date: 2010-12-05
forum: Mythbuntu
---

### Post by MonsterMaxx on 2010-12-05
This has been quite the saga.
First I tried to get 10.10 installed only to have it screw the system so badly that nothing worked anymore.

So, off to start from scratch only to find that 10.10 can't address IDE drives (cannot find for partitioning.)  So I had to scrounge a SATA drive from another machine by moving it onto a IDE.
Long story short, I finally got 10.10 running, myth setup and running only to find out the freeking thing is STILL 0.23!!!
WTH?

Ok, off to the next task getting the repro.

Then update and it says I can only do a partial upgrade.  
Whatever, I let it do that.  Big mistake, now myth is gone and update says there's all these myth updates that it can't do.

WTF?  am I starting from scratch again.  This 0.24 upgrade has already cost me every scrap of myth that I've accumulated over the years, 20-30 hours of dicking around with hardware and I'm completely fed up at right now.

Sorry for the rant, but this is getting ridiculous.

WTF do I have to do to get 0.24 installed??>??

---

### Post by thatguruguy on 2010-12-05
See the discussion in [this thread]("http://ubuntuforums.org/showthread.php?t=1634474").

---

### Post by nickrout on 2010-12-05
short answer, 

1. change to the 0.24 repo, stop mythbackend then:

```
sudo aptitude update
sudo aptitude remove libmyth-0.23-1
```

It'll tell you there is a problem and offer to uninstall a whole swag of 0.23 stuff and replace it with 0.24 stuff, accpt the suggested solution.

```
sudo aptitude safe-upgrade
```

---

### Post by MonsterMaxx on 2010-12-06
fyi: tried half a dozen different things (related to the error message) none worked.  Then I tried a 'apt-get dist-upgrade' and it worked.

:)

thanks for the help

---

