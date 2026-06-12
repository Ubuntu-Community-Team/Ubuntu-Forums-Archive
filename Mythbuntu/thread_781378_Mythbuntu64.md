---
title: "Mythbuntu64?"
date: 2008-05-04
forum: Mythbuntu
---

### Post by Al_Vampyre on 2008-05-04
Just about to upgrade my myth box to

Asrock 939 Dual Sata 2
OPteron 165@2.4
2 x Nova T 500 PCI
2 X WD 500Gb Sata 2 
4Gb DDR400

Obviously with the 4gb I would prefer to use Mythbuntu64 - are there any issues I should know about?

Also is there any way I can upgrade my current 8.04 setup non-destructively? Do I just backup the recordings folder and the home folder and replace them when I have installed Mythbuntu64?

Thanks in advance

Al

---

### Post by superm1 on 2008-05-04
Well there is no non destructive way to upgrade.  I'd either of these is your best bet :

**Option A**
1) Make 2 backups.  1 of the whole system, and 1 of the SQL tables, settings, and recordings you want to keep.

2) Wipe all other data.  Warning: if your recordings are on the same partition as the OS, it will require you to format that partition during install due to technical limitations.

3) Restore the smaller backup.  If things worked right, profit.  If not, then restore your whole backup and return to drawing board.

Option B
1) Install 64 bit 8.04 to a new hard drive
2) Copy over contents from the old one (SQL, recordings if necessary, settings etc).
3) Wipe old drive.

---

### Post by Al_Vampyre on 2008-05-05
Thanks for the info, I suppose there is also option C which would be just to do a fresh install and feel the wrath!:)

---

