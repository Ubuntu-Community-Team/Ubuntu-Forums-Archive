---
title: "[SAMBA]Help with samba configurations"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by konichiwa13 on 2009-07-31
I have a little problems with samba here. I have a lot of configurations in a smb.conf, permissions are set correctly,I guess. But now everyone seems to be able to browse that folder. Weird.. I've checked with the other settings, samba did actually stopped me to access other folders but this only..I attach the exact chunk of smb.conf for reference. Please tell me what have I done wrong here. Hmm..```
[Full Samba]
	browseable = no
	writable = yes
        revalidate = yes
	write list = @mis
        read list =  @mis
        guest ok = no
	path = /media/disk/Network Sharing
	comment = Full Samba Folder
	valid users = @mis


[Full Samba1]
	browseable = no
	writable = yes
	read list = @mis
        guest ok = no
	path = /media/disk/Network Sharing2
	write list = @mis
	comment = Full Samba Folder
        revalidate = yes
	valid users = @mis
```

All help are greatly appreciated

---

### Post by Iowan on 2009-07-31
Dunno if the spaces in the sharename/pathname might cause problems...

---

### Post by dmizer on 2009-07-31
> **Iowan said:**
> Dunno if the spaces in the sharename/pathname might cause problems...

Yes, the spaces in the path will cause problems. I suggest renaming the share so that there is no space in the path.

---

### Post by konichiwa13 on 2009-08-07
I haven't try that yet but..  Here's a few other configurations that worked.
It prompt users for password when opened.

```


[Study Assistance]
comment = Study Assistance Document
path = /media/disk/Network Sharing/Management/Study Assistance
valid users = @management
read only = no
read list = @management
write list = @management
browseable = yes
guest ok = no

    [MIS-General]
    comment = MIS-General
    path = /media/disk/Network Sharing/MIS/General
    valid users = @mis
    read only = no
    read list = @mis
    write list = @mis
    browseable = no
    guest ok = no

```

Now may be it isn't about the filename? Could it be folder permission thing? I thought Samba would override this. Well at least, there should be a password prompt.. Will try to change the name but it's part of the daily backup. So I needed to change a few things
Thanks for your attention!

---

### Post by konichiwa13 on 2009-08-07
Gosh.. That worked. It also means a bad news for me. Cause now, I need to change every path.....All...... Gooosshh....
Thank you guys!Or girls? =D

---

