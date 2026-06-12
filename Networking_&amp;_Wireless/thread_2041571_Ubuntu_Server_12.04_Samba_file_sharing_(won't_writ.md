---
title: "Ubuntu Server 12.04 Samba file sharing (won't write to directory)"
date: 2012-08-12
forum: Networking &amp; Wireless
---

### Post by maticko on 2012-08-12
[LEFT]After almost three days of trying and searching any solution on the net, I still didn't find solution. 
[/LEFT]
 
I set Samba file sharing and in webmin (samba file sharing ) is visible that shared folder is readable and writable to everyone... but it is not.

Also I found that smb.conf file should be edited and I did so, but... same

this is copy of conf file

[global]
    log file = /var/log/samba/log.%m
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    socket options = TCP_NODELAY
    obey pam restrictions = yes
    deadtime = 30
    map to guest = bad user
    encrypt passwords = true
    passwd program = /usr/bin/passwd %u
    passdb backend = tdbsam
    dns proxy = no
    netbios name = linuxserver
    server string = LINUXSERVER
    unix password sync = yes
    workgroup = MATIC
    os level = 20
    syslog = 0
    usershare allow guests = yes
    panic action = /usr/share/samba/panic-action %d
    max log size = 1000
    pam password change = yes
    security = user

........

[share]
    guest account = kristijan
    comment = Ubuntu File Sharing
    writeable = yes
    public = yes
    path = /srv/samba/share


what do I miss, pls help

---

### Post by Iowan on 2012-08-19
It's been awhile since I worked w/ Samba, so I'm a li'l rusty.
I suspect the problem may be with linux permissions - check /srv/samba/share to see if it is writable (by other than root).

---

### Post by Morbius1 on 2012-08-19
> [share]
[COLOR=Blue]**     guest account = kristijan**[/COLOR]
    comment = Ubuntu File Sharing
    writeable = yes
    public = yes
    path = /srv/samba/shareIf you run the following command:
```
testparm -s
```You will get the following error:
> Processing section "[share]"
Global parameter guest account found in service section!And your share will have been interpreted by samba to mean this:
> [share]
    comment = Ubuntu File Sharing
    path = /srv/samba/share
    read only = No
    guest ok = YesSo you might want to put that parameter in the [global] section.

Of course you have to make sure that kristijan actually has write permissions to the folder itself.

---

