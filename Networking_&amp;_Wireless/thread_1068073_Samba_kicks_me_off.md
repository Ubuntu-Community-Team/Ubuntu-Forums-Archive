---
title: "Samba kicks me off"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by dargaud on 2009-02-12
Hello all,
I've a new Kubuntu 8.10 and I want to share a few directories and a printer for a lone laptop running XP. I set it up with System/Samba. There are two users on both systems. Same usernames, same passwords, and I enable only them (but it doesn't change a thing if I allow all).

At first everything works, I can install the printer and print a test page, or browse the shared stuff from Windows explorer, but then after a few minutes, bang, impossible to use it again. The printer has "Access denied, unable to connect". The shared folders ask endlessly for my password, adding MACHINENAME\ in front of the username.

I find plenty of references to those messages but nothing conclusive.
```
==> /var/log/samba/log.winbindd-idmap <==
[2009/02/12 20:46:19,  1] winbindd/idmap_tdb.c:idmap_tdb_alloc_init(371)
  idmap uid range missing or invalid
  idmap will be unable to map foreign SIDs
[2009/02/12 20:46:19,  0] winbindd/idmap.c:idmap_alloc_init(831)
  ERROR: Initialization failed for alloc backend, deferred!
[2009/02/12 20:46:19,  1] winbindd/idmap_tdb.c:idmap_tdb_alloc_init(371)
  idmap uid range missing or invalid
  idmap will be unable to map foreign SIDs
[2009/02/12 20:46:19,  0] winbindd/idmap.c:idmap_alloc_init(831)
  ERROR: Initialization failed for alloc backend, deferred!

```

The samba configuration, as set by System/Samba is thus:
```
$ egrep -v "^;|^#|^$" /etc/samba/smb.conf
[global]
        workgroup = mshome
        server string = %h server (Samba, Ubuntu)
        dns proxy = no
        log file = /var/log/samba/log.%m
        max log size = 1000
        syslog = 0
        panic action = /usr/share/samba/panic-action %d
        passdb backend = tdbsam
        obey pam restrictions = yes
        unix password sync = yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        pam password change = yes
        map to guest = bad user
        usershare allow guests = yes
        username map = /etc/samba/smbusers
        security = user
[printers]
        comment = All Printers
        browseable = no
        path = /var/spool/samba
        printable = yes
        create mask = 0700
[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
        writeable = yes
        valid users = dargaud, jenny
[Large1]
        path = /Terhalf/Large1
        writeable = yes
        valid users = dargaud, jenny

```

The printer is configured through CUPS, does this mean I NEED to use cupsaddsmb ? I fail to understand when it is required or if System/Samba does it.

---

### Post by dmizer on 2009-02-13
Do dargaud and jenny have accounts on the Ubuntu server? If not, try adding them with the following commands:
```
sudo useradd -s /bin/true dargaud
sudo smbpasswd -L -a dargaud
sudo smbpasswd -L -e dargaud
```
Make sure the password is the same as what they use on their computers.

Also, don't forget to give your server a name by adding the netbios name option like so:
```
[global]
        workgroup = mshome
        [COLOR="Red"]netbios name = your-server-name-here[/COLOR]
        server string = %h server (Samba, Ubuntu)
        dns proxy = no
        log file = /var/log/samba/log.%m
<snip>
```
This will allow your Samba server to play nice with winbind and wins.

---

### Post by dargaud on 2009-02-13
Thank you, that worked. So there's probably a bug in the KDE System/Samba utility. If I run it, it drops "netbios name" from the smb.conf file.

---

