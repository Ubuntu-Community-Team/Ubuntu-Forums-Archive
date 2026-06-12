---
title: "Serious Installation Issue"
date: 2007-10-17
forum: Mythbuntu
---

### Post by Crashedfiesta on 2007-10-17
I have download the 7.10 rc iso image and written it to a CD.  When I try to boot though my floppy drive goes into meltdown and then the installer crashed out and dumps me back at the command prompt.  

The only hint of what went wrong is a mention that the command :

/sbin/modprobe exited abnormally :confused:

My setup is quite basic:

AMD XP1500 1.3Ghz
Nvidia GeForce2 32mb graphics card
1Gb RAM
40Gb IDE hard disk (hda1, hda5)
10Gb IDE hard disk (hdb1, hdb5)  **<---this is the one I want to use!**
160Gb IDE hard disk (hdd1 - formatted as XFS for use with Mythtv)
Pioneer DVR-105 DVD re-writer (hdc)

I currently have Ubuntu 6.10 installed as my main OS, triple booting with WinXP and Mythdora.  

The only odd thing I've done is written the iso to a CD-RW as I've run out of CD-Rs.... :(

---

### Post by superm1 on 2007-10-17
Can you compare with a standard Gutsy ISO and see if the same thing happens there or if this is mythbuntu specific?

---

### Post by Crashedfiesta on 2007-10-17
> **superm1 said:**
> Can you compare with a standard Gutsy ISO and see if the same thing happens there or if this is mythbuntu specific?

Rats.  Release candidate has been removed to make way for the main release.  Once it's up tomorrow I'll have a go and report the results.

Crashed.

---

### Post by Crashedfiesta on 2007-10-18
Dang nabbit.  Downloaded 7.10 Gutsy and the same thing happens.  I suspect my hardware does not like something in this release...

---

### Post by superm1 on 2007-10-18
Google for noapic, and how to turn off acpi on boot.  These are good starters for nailing things like this.

---

