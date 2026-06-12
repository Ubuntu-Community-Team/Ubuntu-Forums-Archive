---
title: "Can't access some samba shares using [homes]"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by Huufarted on 2009-03-04
I'm using samba because I do have a handful of PCs that are running Windows XP.  Below is my super complicated /etc/samba/smb.conf file.

```

art@atom1:~$ cat /etc/samba/smb.conf
[global]
workgroup = WORKGROUP
interfaces = eth1 lo
bind interfaces only = yes

[homes]
guest ok = no
read only = no
; valid users = %S
art@atom1:~$

```

Here's my issue.  I have 2 users set up in the system and in Ubuntu.  art and don.  user 'art' was set up when ubuntu was installed.  user 'don' was installed strictly to allow for samba access.

The following commands were ran to set them both up:

```

sudo smbpasswd -L -a don
sudo smbpasswd -L -a art

```

Permissions on their respective home directories are as follows:

```

art@atom1:~$ ls -l /home
drwxr-xr-x 32 art  art      4096 2009-03-01 00:19 art
drwxr-xr-x  3 don  don      4096 2009-03-04 17:31 don

```

My problem is that user 'art' cannot log in at all from a Windows machine to the samba shares.

---

### Post by Huufarted on 2009-03-05
Any ideas?

---

### Post by Huufarted on 2009-03-05
little bump?

---

### Post by Iowan on 2009-03-05
You disabled the "valid users = %S"? 
User "don" *can* login from Windows machine?

---

### Post by Huufarted on 2009-03-05
correct, Iowan.  I have no problems re-enabling that option if you'd like me to try it again.

---

### Post by Iowan on 2009-03-05
I have it enabled on my server under the (questionable) notion that it enables/limits directory access to the named user.  My Samba Unleashed book, however, has %S meaning "Current Service Name".

---

