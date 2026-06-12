---
title: "ISO creator"
date: 2008-11-24
forum: Multimedia Software
---

### Post by jptelthorst on 2008-11-24
What is a good app for creating .iso's?  I've tried right clicking on a disc-> clicking copy disc, and then then selecting copy disc to file image, but the file image that is created is unreadable.  Any help would be appreciated.

---

### Post by cariboo on 2008-11-24
Open a Applications-->Accessories-->Termianl and type:

```
dd if=/dev/scd0 of=cdimage.iso
```

where /dev/scd0 is your cdrom drive and cdimage.iso can be the name of you cd. This will create an exact duplicate of your cd/dvd.

Jim

---

### Post by jptelthorst on 2008-11-24
How do I determine what path my cdrom is at?  I entered the code as you posted, and I get the error:

```

dd if=/dev/scd0 of=cdimage.iso
dd: reading `/dev/scd0': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00662263 s, 0.0 kB/s

```

The location of my cdrom as listed in nautilus is: cdda://scd0/

---

### Post by srt4play on 2008-11-24
If you want a graphical app for this, try isomaster.

---

### Post by jptelthorst on 2008-11-24
I think that the reason I am having troubles is because it is an audio cd.

---

### Post by srt4play on 2008-11-24
I think you're right. If you are trying to copy an audio cd, you might use sound juicer to rip the tracks and brasero to burn them onto a blank disc.

---

