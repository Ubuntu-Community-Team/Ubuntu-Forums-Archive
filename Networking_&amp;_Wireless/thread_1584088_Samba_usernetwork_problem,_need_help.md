---
title: "Samba user/network problem, need help"
date: 2010-09-28
forum: Networking &amp; Wireless
---

### Post by gunnarflax on 2010-09-28
Hello! I just want everyone to know that I'm a linux beginner and have just started learning beyond the very basics. The problem I'm having is that only one account can access the shared folders (and it's not root) and I've been searching the internet like crazy but still haven't managed to fix it.

The thing that complicates the whole process is that I'm sharing an external hard drive and I have finally managed to get it to work, but now I've ended up with an account problem... I think.

I've set up the samba server to share 3 directories. You can see my whole config here:
```

[global]
;    netbios name = fileserver
    server string = Filer och Serier
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast
    printcap name = CUPS
    syslog only = yes

#[print$]
#    path = /var/lib/samba/printers
#    guest ok = yes
#    write list = root
#    create mask = 0664
#    directory mask = 0775
#;    writeable = No
#    browseable = no
#
#[printers]
#    path = /tmp
#    printable = yes
#    guest ok = yes
#    browseable = no

[Niklas_Video]
    comment = Filmer och serier
    path = /media/niklas_media/Video
;    writeable = No
;    browseable = yes
    valid users = niklas, root, account2

[Niklas_Musik]
    comment = Musik
    path = /media/niklas_media/Musik
;    writeable = No
;    browseable = yes
    valid users = niklas, root, account2

[Niklas_Media]
    comment = Niklas_Seagate
    path = /media/niklas_media
    writeable = yes
;    browseable = yes
    valid users = niklas, root
```And the file hierarchy is as follows:
```

Niklas_Media
---Niklas_Video
---Niklas_Musik

```I Want Niklas_Media to only be accessible, with read/write permissions, from my account (niklas), while Video and Musik should be accessible from account2 with read-only permission. So I want to be able to administrate the whole disk through the niklas account and then let others access Video and Musik from account2.

If it is of any interest, my fstab entry for the external hard drive (NTFS formatting) looks like this:
```
UUID=B698D46698D426A1   /media/niklas_media   auto   rw,nls=iso8859-1,_netdev,umask=000,user,owner   0   0
```I've tried doing this with both the samba gui and GADMIN-SAMBA and I created account2 via GADMIN with smbguest as template - meaning: Home Directory = /dev/null, Shell = /dev/null, group = nobody, user privileges = none. This account can access both Video and Musik, but not Media, while niklas and root (administrator) fails logging in on all of them with an error stating that it wasn't possible and you should ask the administrator.

I hope someone can help me solve this or getting me on the way to solving this! Thank you very much for your time!

---

### Post by IcarusR on 2010-09-30
As far as I know all users have to exist on the server box. So maybe you should create an account for each of the users you wish to access shares.

Test your smb.conf, this will tell you if any options are not valid.

```
testparm
```

I suggest setting all shares to 'writeable' then using 'read list' option on each share to prevent users from writing to them. 

Read the smb.conf man page.

```
man smb.conf
```

The 'browsable' option has nothing to do with access control, but controls whether this share is seen in the list of available shares in a net view and in the browse list.

---

### Post by DJonsson2008 on 2010-09-30
I've found it helpful when setting up and testing
HD shares to make sure the file server and client 
machine/s at least share one account with exactly 
the same username and password.

---

### Post by luvshines on 2010-10-01
Have you added both 'root' and 'niklas' as Samba users(ie in Samba tdb's)

smbpasswd -a <user-name>

---

### Post by gunnarflax on 2011-03-07
The problem was solved by using **net usershares** instead of samba-classic-shares. By the time working with this problem I didn't know the difference. Just for anyone not knowing:
Samba-classic-shares is the way of sharing folders you find when searching the internet but that method is considered legacy now. Now you use "Right Click"->"sharing options" when you want to share a folder. Instead of finding the shares in /etc/samba/smb.conf you will find the share definitions in /var/lib/samba/usershares/. But don't manually edit those files, use the GUI provided with nautilus.

Global options is still put in /etc/samba/smb.conf. E.g. I have the following settings set in /etc/samba/smb.conf to prevent that when windows users accessing the smb-shares don't set other file/folder permissions automatically due to windows configuration:
```
    security mask = 0770
    force user = my_user_name
    force group = my_group_name
    create mask = 0770
    force create mode = 0770
    directory mode = 0770
    force directory mode = 0770
```

I also had a problem with the flow of permissions when working with this and the solution to that can be found in this thread:

[http://ubuntuforums.org/showthread.php?t=1699453](http://ubuntuforums.org/showthread.php?t=1699453)

---

