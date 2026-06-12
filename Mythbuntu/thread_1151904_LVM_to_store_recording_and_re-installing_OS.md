---
title: "LVM to store recording and re-installing OS?"
date: 2009-05-07
forum: Mythbuntu
---

### Post by xinix on 2009-05-07
I'm upgrading my storage space and I'd like to set up my recording space to use an LVM made up of my current partition and the new drive. The root and home partitions would not be part of the LVM.  I have one concern about this though.  What happens if I re-install the os?  Would the LVM be lost or would the installer be able to detect it? 

Thanks

---

### Post by Caysho on 2009-05-13
I found that the default install did not find my LVM.
I installed the lvm2 tools (including the lvm setup gui) and after the reboot, the GUI tool could see the LVM.
All that was needed was to set the mount point in fstab and specify the storage group (easier than doing symlinks).

---

