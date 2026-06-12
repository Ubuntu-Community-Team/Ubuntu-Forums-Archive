---
title: "SAMBA - Nautilus files permission error"
date: 2011-03-11
forum: Networking &amp; Wireless
---

### Post by Dragmah on 2011-03-11
Hey all,

i have been having issues with my networking since an update of SAMBA about a week ago. I have adjusted corrected, etc. everything i could until i found that the files that i am 'shares' i am unable to access over network were all external hard drives. I can see each of the files in the network but as soon as i try and access them it says i do not have permission, despite adding all permissions as normal in SAMBA.

I went deeper and found that the file permissions are not setup to allow external access, so i naturally tried to change them but it didn't work, so i used the command;

sudo nautilus

To access the files as root owner, but found that these externals are all owned by my user/ computer name (server - Daniel). as such i went back into nautilus the normal way but noticed that where i could normally change the owner it was un-editable text, and if i tried changing any of the drop downs it would automatically change back.

Any help would be much appreciated.

D

---

### Post by Morbius1 on 2011-03-11
I'm guessing that the external USB drive is formatted in NTFS or FAT32. If it is then they will auto mount with you as owner and access permitted to you and only you. The remote user is not you so samba may authorize someone else to access the drive but it can't override Linux file permissions.

One way out is to make everey remote user appear to be you by adding the following line in /etc/samba/smb.conf:
```
force user = morbius
```[COLOR=Blue]*Change morbius to the login user name of the of the user that owns the drive.*[/COLOR]

No one ever states in this forum how they created the samba share so:

If you used Classic share then add the "force user" to the share definition itself in smb.conf.

If you used Nautilus to share the drive then add it to the [global] section of smb.conf.

Then restart samba:
```
sudo service smbd restart
```

---

