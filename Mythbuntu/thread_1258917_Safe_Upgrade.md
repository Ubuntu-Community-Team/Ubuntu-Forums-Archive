---
title: "Safe Upgrade"
date: 2009-09-05
forum: Mythbuntu
---

### Post by itlarson on 2009-09-05
I am wanting to up move to 9.04, but am afraid of breaking my system.  Since I am adding a drive anyway, I thought this might be a way to proceed:
-back up mythtv database
-install new (sata) drive. 
-Set new drive as first in boot order in bios.
-install mythbuntu 9.04 on it's own partition on the new drive
-mount the old storage partition to the same mount-point as before
-restore the database.  
-set the old storage directory up in the back-end as a storage directory (?)
-set up the new storag directory for additional storage

If this goes wrong I should be able to simply restore the boot order and start up my old install.  If it goes right I can use the old root directory to do the same thing next time I upgrade.

here are some questions:
-Is 9.04 working smoothly for HDTV at this time?
-is VDPAU working in 9.04?  Is this upgrade worth it if not?
-what is the default database user-name and password?
-does restoring the database restore all front and back-end settings?  If so I should be able to skip much of the mythbuntu setup- mainly just installing restricted codecs and nvidia drivers. And if the old storage directory is mounted to the same location, I should only have to enter back-end setup to set up the additional storage directory on the new drive.

---

### Post by itlarson on 2009-09-05
Oh- also I need the name of the database.  Is it mythconverge?

---

