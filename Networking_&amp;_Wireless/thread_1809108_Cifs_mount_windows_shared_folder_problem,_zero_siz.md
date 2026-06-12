---
title: "Cifs mount windows shared folder problem, zero size and blank icon before refresh"
date: 2011-07-21
forum: Networking &amp; Wireless
---

### Post by n_petr on 2011-07-21
Hello,
there is a problem with cifs mount of windows network shared folder. Mounted folders have zero sizes and blank icons ([MountProblem1.png]("http://ubuntuforums.org/attachment.php?attachmentid=197955&stc=1&d=1311238331")) until refresh (F5 key) is pressed ([MountProblem2.png]("http://ubuntuforums.org/attachment.php?attachmentid=197956&stc=1&d=1311238331")).

**Description**
1. Notebook 10.192.0.2 (Windows)
2. Server 10.192.0.1 (Linux)

_a) Notebook side_
share C drive for user Uss - full control on permissions

_b) Server side_

fstab (main part):
# /mnt/Share was on /dev/md5 during installation
UUID=8bf0d83f-8b95-5f8f-9f1c-e19ffffc2e1d   /mnt/Share   ext3   noatime   0   2

smb.conf (main part):
[share_rw]
    comment = Share
    path = /mnt/Share
    valid users = npetr
    admin users = npetr
    write list = npetr
    force group = npetr
    create mask = 0775
    directory mask = 0775

mount //10.192.0.2/C /mnt/Share/Dell -o iocharset=utf8,user=Uss,password=censored

mstab (main part):
/dev/md5 /mnt/Share ext3 rw,noatime 0 0
//10.192.0.2/C /mnt/Share/Dell cifs rw 0 0

_c) Notebook side_
Open \\10.192.0.1\share_rw\Dell\Windows with user npetr and his password (the opened folder could be whichever - the problem is global)

Mapped folder appears with zero sizes and blank icons of subfloders - please see attached [MountProblem1.png]("http://ubuntuforums.org/attachment.php?attachmentid=197955&stc=1&d=1311238331")

When you hit F5 (refresh window), mapped folder is now OK - please see attached [MountProblem2.png]("http://ubuntuforums.org/attachment.php?attachmentid=197956&stc=1&d=1311238331")

When you go to another folder the problem appears again until you hit F5.

Thanx for any hints
N_Petr

---

