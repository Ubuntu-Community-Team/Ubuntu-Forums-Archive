---
title: "Accessing Windows share files...."
date: 2006-07-16
forum: Networking &amp; Wireless
---

### Post by Mia_tech on 2006-07-16
guys I can see all my shares on the network, browsing from my ubuntu box, but Im trying to mount the shares on a windows server on my ubuntu box so I can do backups.
have use mount //computername/share /mnt/share 
with no success, like I said I can browse and connect to the share and that will mount it on desktop but I wanted to automate the task at start with the correct commands....any ideas?

thanks

---

### Post by spd106 on 2006-07-16
Are you using samba?
If so you need to use smbmount or mount -smbfs
Have a look here [https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

---

### Post by Mia_tech on 2006-07-16
when I first installed ubuntu, I also intalled samba, I guess it should install smbfs plugins...I tried smbmount and I get command not found...also tried mount -smbfs with no success...

any ideas
thanks

---

