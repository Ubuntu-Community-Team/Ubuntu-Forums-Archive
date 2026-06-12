---
title: "Log in to Win 7 as Samba user profile while offline"
date: 2012-08-27
forum: Networking &amp; Wireless
---

### Post by sgmurphy19 on 2012-08-27
I have a Ubuntu server running Samba 3.4.7 that I am successfully able to connect to. I set the smb.conf to include 
 winbind enum users = Yes
 winbind enum groups = Yes
 winbind offline logon = Yes

but still if I am disconnected from the network I am unable to log in to Windows 7. Is there a way to allow Win 7 Pro to cache the credentials for offline logons?

Thanks,
Sean

---

