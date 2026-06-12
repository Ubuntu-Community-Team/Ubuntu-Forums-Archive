---
title: "Help on copying DVD to Hard Drive without compression using K9copy"
date: 2011-06-02
forum: Multimedia Software
---

### Post by aoniumo on 2011-06-02
I finally got K9copy to work and I'm using it to extract DVDs  to my hard drive.  I extract a dual layer DVDs it becomes a 5GB DVD.  In the settings, I have DVD size as 9GB because I assumed this would not cause any compression.  When I use k9copy assistant to change the shrink factor before ripping, I can only change the shrink factor of some titles to **1.67 from 2.50.** I want the shrink factor to be **1 **since this seems to ensure that the output of the file is the same size as the title on the dvd.  I want the copied DVD to be the same size as the original.  I have no problem with hard drive space since I have 6 terrabytes of free space.  Any help would be appreciated.

---

### Post by handy on 2011-06-02
You could probably use DVDShrink, as you can set the size of the output (amongst other things).

It is a treat to install & use with Wine, & is so simple to configure, & as reliable as they get.

---

### Post by andrew.46 on 2011-06-02
If you were after a complete copy, mirroring the dvd structure, I would suspect that a better strategy would be to use libdvdread, libdvdcss and vobcopy. The command to copy the dvd would then be:

```
vobcopy --mirror
```

---

### Post by shantiq on 2011-06-02
also if you want **exactly** the dvd disc the simplest route i know is   (with no software)

places/computer/right-click on dvd/pick open/highlight/right click/ pick copy to home folder



and you have the whole thing takes 15 minutes on my machine

---

### Post by coffeecat on 2011-06-02
I think the answer is not to use k9copy assistant. I can only change the shrink factor down to 1.4 with the DVD I tried in it. However, if I open k9copy direct and put a DVD in the drive with the DVD size set to 9000MB, if I highlight each title in turn in the main k9copy window, the shrink factor defaults to 1.

In fact I hadn't noticed the shrink factor before I came across this thread. I've always had DVD size set to 8000 or greater and never bothered with K9copy assistant, and I've always managed to get a copy the same size as the original.

---

### Post by handy on 2011-06-02
One of the things that I really enjoy about GNU/Linux, is that there are so many ways to skin the same cat. :)

Glad I'm not a cat.

---

### Post by coffeecat on 2011-06-02
> **handy said:**
> Glad I'm not a cat.

Speak for yourself! :wink:

---

