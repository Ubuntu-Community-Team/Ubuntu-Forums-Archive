---
title: "problem with samba stream"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by dirtrider1 on 2010-01-25
I just set up one of my computers with ubuntu server 9.10 and set up a windows share with samba to the best of my abilities and it works fine I can access my files fine. The only problem is when I go to play a video it says "An error occurred" the stream is encrypted and decryption is not supported, and I have tried to do it on an Ubuntu and Windows computer. And I also tried playing it with several different players. Here is a copy of my smb.conf any help would be great thanks.


[global]
    ; General server settings
    netbios name = ******
    server string =
    workgroup = ******
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = yes
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/


;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = yes


[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no


    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /media/One4
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = ****
    force group = ****

---

### Post by johnson.d on 2010-02-01
You can probably look at a similar thread in this forum:

[http://ubuntuforums.org/showthread.php?t=306829](http://ubuntuforums.org/showthread.php?t=306829)

---

