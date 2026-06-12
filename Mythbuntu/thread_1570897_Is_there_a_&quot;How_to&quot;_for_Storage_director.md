---
title: "Is there a &quot;How to&quot; for Storage directories?"
date: 2010-09-08
forum: Mythbuntu
---

### Post by Panhead Bill on 2010-09-08
Or at least a good example?

Mythbuntu 10.4 64bit
80 gig Ide drive (for OS, Swap, and any other overhead"
1.5T Sata drive (for content)

After partitioning the IDE drive and setting up Mythbuntu, I have a functioning system with almost no content storage.

I went to Backend setup #6 Storage directories, but all that seems to do is create new group names, change existing group and default names, and create new default names.  Since no drive is referenced this is only part of what is needed to set up my SATA drive as the content location.  Everything else that I have worked with in mythbuntu has been well documented or intuitive.

(HELP!)

---

### Post by tgm4883 on 2010-09-08
nope, no how to.

You will need to mount the drive somewhere in your filesystem, then create the storage groups in the backend setup.

The easiest method to do this on a new install is to 

1) Check the directories and permissions of the directories in /var/lib/mythtv/

2) Mount your storage drive at /var/lib/mythtv/

3) Recreate the folders and reset the permissions inside /var/lib/mythtv/ (these would now be created on your drive)

4) Since the folders are in the same place they were before, no need to alter anything in mythtv-setup. If you simply enter and exit mythtv-setup it should check if it is writable.

---

