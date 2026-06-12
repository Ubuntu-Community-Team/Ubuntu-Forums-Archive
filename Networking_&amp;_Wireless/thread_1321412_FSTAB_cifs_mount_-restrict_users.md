---
title: "FSTAB cifs mount -restrict users?"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by Wmb123 on 2009-11-10
Hi,  I have an Iomega NAS drive.  I want to mount a share from it (in Kubuntu 9.04).  
BUT I want only one user to have access to the mounted drive.

I set it up in FSTAB to mount the drive.  I specified the credentials for the smb share.  I included the uid and group of the user.  I set file_mode=0700,dir_mode=0700.

No matter, it always mounts with full wrx permissions for every user.

What gives?  Thanks.

---

