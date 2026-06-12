---
title: "Distributed hdd access (is it possible?)"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by jimsmithkka on 2009-04-14
I am curious if it is possible to share hdd's from multiple linux systems at the lowest level possible (block)

My thoughts are to use NBD on each of the drive hosts, 
Connect them together logically on a dedicated system, probably with an LVM, 

Then share them with an iSCSI target as a single drive

I would try this myself, but I do not have enough spare unused hdds to put in each of my test systems.  

if my understanding of NBD is correct, and my assumtion on LVM works, than it should be possible

I have setup linux iSCSI targets from a single system before so that part at least i understand.

I currently am not concerned about speed, just curious if it would even work. 

My end goal is to setup a poor mans SAN for home use and experimentation, possibly later rolling out in production (if i ever get out of school) [http://ubuntuforums.org/images/smilies/star.png](http://ubuntuforums.org/images/smilies/star.png)

---

### Post by jimsmithkka on 2009-04-15
bump

I also am not sure if this is even the correct place for this thread

---

### Post by jimsmithkka on 2009-04-15
I have it working, but am using iscsi on both layers so it is setup like this (currently using a single drive)

```
DRIVE HOST      CONCATINATOR HOST     END SYSTEM
hdd shared      iscsi connection      iscsi to CAT host
over iscsi      to drive host
                drive formated and 
                used in an LVM setup
                can add more DRIVE
                HOSTS later to disk
```

further improvments would be a deticated gig link between DRIVE host and CAT host

---

