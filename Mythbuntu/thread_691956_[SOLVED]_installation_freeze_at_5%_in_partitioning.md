---
title: "[SOLVED] installation freeze at 5% in partitioning"
date: 2008-02-09
forum: Mythbuntu
---

### Post by Kreker on 2008-02-09
I use the trigger "all_generic_ide" because if not the installation prompt me the busybox.
Now the live cd starts, i click installa but after defining the partition (automatic or manual is the same) the installation freeze @ 5%...!
I think there are some problem with the sata contreller! I try with 1.5 gb or 3.0 sata jumper but no difference. I have nvidia mcp73pv chipset on my mobo!
thanks...

---

### Post by Kreker on 2008-02-10
help please!!

---

### Post by bkr1_2k on 2008-02-11
Mine did that with a parallel ata drive as well.  I had an old drive and assumed the drive was bad.  Maybe try a different drive to see if that works?  It did with mine, though now I'm tempted to see if I can format the old drive some other way and install it as a backup.

---

### Post by volkswagner on 2008-02-11
you can try partitioning the drive first using the live CD environment.  While running the live CD got to sytem>administration>partition editor.

See if you can set up your desired partitions this way.  If you are successful, when you start your install, choose custom partitions.  You should just need to edit the partitions to specify the correct mount points.

Good luck

Note:  If the mythbuntu cd does not have the partition editor, you can try an excellent distro Ubuntu Ultimate Edition.  For the latest version a DVD burn is required.  I am sure there are other distros  which include the partition editor.

---

### Post by Kreker on 2008-02-12
i'm feeling like an idiot....the system doesnì't freeze...only take a bit long...maybe for the 500 gb capacity
i install mythbuntu correctly but now i have started another 3d because i have problems with the skystar2...
thanks

---

### Post by devmodo19 on 2010-10-15
I haven't found a resolution yet to this issue.  I am doing a new install of version 10.10 on an older computer.  It may be that the computer just can't handle it but it did stick at 5% and hasn't moved in more than 30 minutes.  That's what I get for using old hardware I guess.

---

