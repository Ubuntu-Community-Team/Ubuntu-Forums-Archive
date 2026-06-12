---
title: "Connect to password-proteced Samba share"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by kaweka on 2009-03-18
Ubuntu 8.10 running on VirtualBox, VirtualBox on WindowsXP.
All that working in LAN controlled by DSL modem-router.
USB mass storage connected to router - Samba share, password-protected.
FTP server enabled as well.
This mass storage should be the only one way both machines can interchange files.

Host has no probs with network, i-net as well lan are working fine.
Ubuntu has no probs with i-net. It can also access the mass storage
by FTP. But not by mounting a network drive.
With following results:
-pyNeighbarhood presents the router IP
-under router IP the share name is presented
-context menu->either "mount smb" or "mount cifs"
  produces error message "failed to mount"

There are plenty of tools and manuals for connecting samba shares.
But I didn't manage to get an overview.

Desired:
-Auto-mount by Ubuntu not allowed
-Accessing password-protected share
-Mounting on demand by admin and/or normal user
-Mounting by use of graphical tools

What can be the possible reason?
What are the best help files for this case?

---

