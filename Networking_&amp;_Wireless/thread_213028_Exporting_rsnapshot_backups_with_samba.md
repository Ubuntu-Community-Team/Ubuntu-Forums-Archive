---
title: "Exporting rsnapshot backups with samba"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by daffy1967 on 2006-07-10
I'm setting up a ubuntu/samba fileserver exporting user home directories to a couple of windows XP machines. I have enabled user level access so if I log on to the windows XP machine as userx I can only access /home/userx on the Ubuntu server. The [homes] section makes this occur on the fly. All was going well :p 

I have setup rsnapshot to perform backups of /home/userx to /backup/localhost/home/userx and would like to export the backup directory for each user (read only), with user level access in a similar way to the home directory.

Is there an easy way to implement this dynamically or do I have to create the individual user backup shares for each user in smb.conf?

Thanks in advance.

---

