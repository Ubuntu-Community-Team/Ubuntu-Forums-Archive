---
title: "smb shares to windows machine: can't get write permission"
date: 2010-03-22
forum: Mythbuntu
---

### Post by rienzio on 2010-03-22
hello, trying to copy music to my mythbox. I can share /var/lib/mythtv/music, but it is a read-only share. When I try to change permissions, i get the message that it is owned by "mythtv" and I can't change permissions. 

Your help is appreciated, as always!

---

### Post by stevanbt on 2010-03-23
Hi,
Have you checked the permissions in your samba config file on the ubuntu machine?  I'm not at my ubuntu box now so can't say what's in mine, but have a look in /etc/samba/smb.conf for the permissions.

Thanks, Steve.

---

### Post by singedwings on 2010-03-23
One way is to open a terminal and enter```
sudo nautilus
```Be careful as you can do damage if you delete things in this mode as none of the system files will be protected! Right click on the folder you want to share and select sharing options. You will now be able to share the folder.

---

### Post by rienzio on 2010-03-23
singedwings, thanks! That did the trick, and I will use judiciously. 

Steve, I opened my smb.conf, and didn't find anything immediately obvious to this n00b. But I do understand a bit more about how samba works. Thanks!

---

