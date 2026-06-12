---
title: "Samba mounting by regular users not browsing in nautilus"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by ksadil on 2009-08-25
Hi,

Nautilus with bookmarks is great for browsing/drag & Drop my samba shares  (on the other machine) but I would love a way to mount them in my /home/user account by the user. Other applications cannot get to these shares for saving & backups, etc. I know I can edit fstab to make them system wide, but I would like to know if there is an equivalent to "map network drive" (from another system) so I can do this more elegantly. Ideally it would mount the share  some like /home/user/smb_shares. 

Thanks,
Kim:confused:

---

### Post by dmizer on 2009-08-25
See the 2nd link in my sig.

Add these options to the examples outlined under the permanent mount section:
```
noauto,users,exec,dev
```

Then a regular user will be able to mount the share without having to enter a root password.

---

### Post by ksadil on 2009-08-25
Thanks dmizer. If I am going to set up a permanent whole system connection, fstab edits are clearly the way to go. And your howto's are excellent.

My question though was trying to see if there was a user interface driven way for a user to connect to a share, and make that share reconnect when that user logs back in next time. Bookmarks are good but not accessible by other applications. It would probably best be done by a new feature in nautilus' "connect to windows share" features, like a checkbox to remount on login, as an alternative to a bookmark. And I am thinking that the mount point would be within the users home directory structure would be best. It would make users less dependant on a system administrator.

I was just checking if I was unaware existing features in the user interface.

Thanks,
Kim

---

### Post by dmizer on 2009-08-25
Humm, you probably want PAM mount then. PAM mount allows you to mount shares per user on demand. I've only played with PAM mount on a couple of occasions and don't have a solid howto for you, but this is where I usually start and it seems to get most people pointed in the right direction: [http://www.kroon.co.za/howto.php?howto=cifs_pam_mount](http://www.kroon.co.za/howto.php?howto=cifs_pam_mount)

---

### Post by ksadil on 2009-08-26
Looks interesting. It may take me some time to absorb though

---

