---
title: "How to backup home movie to .iso? (no GUI)"
date: 2007-08-13
forum: Multimedia Production
---

### Post by LinuxTek on 2007-08-13
I have over a hundred home DVD's and some are getting old.  I want to make a backup copy of my home movies and store them as .iso files so that I can create a new DVD later if the original fails.

What I want to do is to put the DVD in the drive and type a command from the command line specifying where to store the .iso file.

I really do not want to mess around with settings or a GUI of any kind.

I want to be able to make an exact duplicate of the original DVD and have it remove any protection mechanisms so that I can create a new DVD and have it play back on any DVD player without any problem.

Can someone point me in the right direction for a command line utility that will do this (legal or not in the US).


thanks


LinuxTek

---

### Post by 1/0 on 2007-08-13
I would use mkisofs. The following might work, perhaps with some extra flags such as -o or -udf:

```
mkisofs -dvd-video /path/to/directory> DVD_TITLE.ISO
```

Otherwise you might use dvdbackup for that purpose. Its in synaptic. This might do the trick:

```
dvdbackup -M -i/dev/cdrom -o/path/to/your/directory 
```

---

### Post by LinuxTek on 2007-08-13
Will this strip off any copy protection and allow me to make an exact copy of the studio produced DVD?

---

### Post by psusi on 2007-08-13
DVDs do not contain ISO 9660 filesystems; they use UDF.  Also pressed dvds can hold more data than ones you can burn, so you may not be able to make an exact copy.  Also age does not matter for dvds; they do not wear out as a result of time, only physical trauma, i.e. breaking or scratching them.

---

### Post by LinuxTek on 2007-08-14
so if my hard drive can hold all the data that a DVD can how to I make an exact duplicate of the DVD stripping off any copy protection and do it all from the command line?

---

