---
title: "smbclient command allowing only root?"
date: 2009-07-26
forum: Networking &amp; Wireless
---

### Post by Avinash.Rao on 2009-07-26
Dear all,

I am using samba 3.0.28a on Ubuntu 8.04 and below is my smb.conf file

[global]
    workgroup = sunbox 
    server string = Samba on SUN
    max log size = 500
    log level = 1
    bind interfaces only = True

    log file = /var/log/samba/log.%m
    max log size = 1000

    domain logons = yes
    os level = 65
    prefered master = yes
    domain master = yes
    local master = yes

    add machine script = /usr/sbin/useradd -s /bin/false -d /home/nobody %u
    dns proxy =No
    hosts allow = 127. 192.168.1. 16.181.
    wins support = Yes
    passdb backend = smbpasswd
    
    encrypt passwords = yes
    smb passwd file = /etc/samba/smbpasswd
        security = user
        netbios name = human
    username map = /etc/samba/smbusers   

[homes]
    comment = Home Dir
    read only = NO
    browseable = NO
    valid users = %S
    path = %H
    directory mask = 0700
    create mask = 0700


[share]
    comment = test share
    path = /media/disk
    create mask = 0765

I am trying to connect to share using smbclient command, strangely, it is allowing only root user account and throws "session setup failed: NT_STATUS_LOGON_FAILURE" for any user other than root.

#smbclient //localhost/share -U username 

The user id is entered in /etc/samba/smbusers , I have created other user accounts by using smbpasswd -a and enabled them by smbpasswd -e commands.
But i am still not able to login. I have also changed the permissions of /media/disk directory to access all .

Can anybody help me?
Avinash

---

