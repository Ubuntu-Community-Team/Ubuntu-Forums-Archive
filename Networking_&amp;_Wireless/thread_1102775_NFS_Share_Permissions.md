---
title: "NFS Share Permissions"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by bigbencg on 2009-03-22
I have been playing around with NFS between my kubuntu boxes and a mac mini.  I can set up the share and mount the share on the client computers.  My issue is PERMISSIONS!!!!!

Permissions in linux are frustrating at best

When I create a folder in the root directory /thor, the default owner is root.  Mounting this share on other systems gives me the ability to see the share, but no files or folders can be created in the share.  Not even on the host computer with a sudo command.  I made the share work by creating a new user on the host computer and using chown to change ownership of the folder.  Presto, the share works.  

Is there a built-in group or user that I can assign a shared folder to?  One that would give a remote user the permissions I assign the share in exports.

P.S.  I have another question about NFS [http://ubuntuforums.org/showthread.php?t=1102722]("http://ubuntuforums.org/showthread.php?t=1102722")

---

