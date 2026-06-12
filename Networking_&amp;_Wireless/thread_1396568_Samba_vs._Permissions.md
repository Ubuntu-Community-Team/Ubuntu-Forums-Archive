---
title: "Samba vs. Permissions"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by Beige on 2010-02-02
Having some trouble getting permissions sorted out.

I want newly created files and folder to have the permission 760, rwxrw----

However, I can't make it work, when i create a file over samba it has different permissions...

```
sysadmin@XUbuntu-Server:/media/primary/shared/documents/ice$ ls -l
total 4
-rwxrw-r-- 1 ice ice    0 2010-02-02 13:04 new file
drwxr-xr-x 2 ice ice 4096 2010-02-02 13:04 new folder
```


I'm currently working on the documents share

Heres my smb.conf:
```
[global]
        log file = /var/log/samba.log
        load printers = no
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
        socket options = TCP_NODELAY
        obey pam restrictions = yes
        null passwords = no
        encrypt passwords = true
        passwd program = /usr/bin/passwd %u
        passdb backend = smbpasswd
        dns proxy = no
        netbios name = XUbuntu Server
        invalid users = root
        workgroup = workgroup
        os level = 20
        security = user
        syslog = 1
        panic action = /usr/share/samba/panic-action %d
        max log size = 1000
        log level = 3
        pam password change = no

#Share Definitions


[Web Server]
        force user = www-data
        comment = Files are hosted by Apache2 web server
        writeable = yes
        create mode = 765
        path = /media/primary/apache/
        directory mode = 765


[Movies and TV]
        comment = Commercial Movies and TV
        writeable = yes
        create mode = 765
        path = /media/primary/shared/moviesandtv
        directory mode = 765



[homes]
        browseable = no
        writeable = yes

[Documents]
        writeable = yes
        create mode = 760
        path = /media/primary/shared/documents
        directory mode = 760

[Library]
        writeable = yes
        create mode = 765
        path = /media/primary/shared/library
        directory mode = 765
```

I'm mainly using webmin to configure it, but I've also tried adding leading 0's to show that they are octals, but this doesn't seem to make any difference.

I'm sure it's something simple, just can't see it at the moment :-s

---

### Post by Beige on 2010-02-02
OK, semi solved.

Seems there is some sort of bug that causes this, the fix I found is adding

```
unix extensions = no
```

under [global] in smb.conf


Not ideal, but for this setup will work just fine :)

---

### Post by pdc on 2010-02-02
is this SAMBA guide of any help for further reading?

[http://ubuntu.swerdna.org/ubulanprimer.html](http://ubuntu.swerdna.org/ubulanprimer.html)

---

