---
title: "getting warnings root is full but df -H shows gigs free"
date: 2012-12-16
forum: Mythbuntu
---

### Post by dheianevans on 2012-12-16
In the last few days I've had a warning pop over my myth screens telling me that my root filesystem has only about 50 megabytes left and asking if I want to empty the trash.

If I check df -H it shows my root filesystem has about 12 GIGS free. This has only been happening in the last few days.

Wassup? Is there any other way I can debug this?

df -H
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       491G  454G   12G  98% /
udev            1.1G  4.1k  1.1G   1% /dev
tmpfs           420M  1.3M  419M   1% /run
none            5.3M     0  5.3M   0% /run/lock
none            1.1G  103k  1.1G   1% /run/shm
/dev/sdb5       1.5T  1.4T  112G  93% /storage1

---

### Post by nickrout on 2012-12-16
What filesystem is on / ?

ext 2/3/4 have a reserved space of 5% by default, which is far more than needed on a multi GB drive. You can lower it. Google will find the invocation, now you know what you are looking for.

---

### Post by Bashing-om on 2012-12-16
dheianevans; Hi !

du is not lying to you, arithmetic: 491 is to 454 as 100 (%) is to "x" = 92.46, less than 8 percent remaining, root may take another 5 percent... you do not have overhead left to operate with. You need to do some trimming. Done any house cleaning lately ?

I suggest you start with /var/log/ ... one may safely delete any file ending in .gz located in any of the folders within /var/log/. May gain you some significant amount of space.
then there is also orphaned and obsolete files:
```
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean

```You sdb5 storage partition is also running short on room.

[INDENT][INDENT]just try'n to help <==BDQ

[/INDENT][/INDENT]

---

### Post by dheianevans on 2012-12-16
the root drive is ext, the video storage drive is xfs

---

### Post by ibjsb4 on 2012-12-17
> **dheianevans said:**
> the root drive is ext, the video storage drive is xfs

What do you mean ext/xfs?

---

### Post by klc5555 on 2012-12-17
He means ext(4) and xfs file systems, of course.

I agree with everyone else here, of course. The OP's root directory needs to be cleaned out. He's about one runaway logfile away from an unbootable system and a corrupted database.

---

### Post by ibjsb4 on 2012-12-17
But of course  :)

---

