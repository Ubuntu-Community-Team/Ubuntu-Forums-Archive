---
title: "Sharing difficulties"
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by deini on 2011-03-21
I am having some difficulties sharing on Ubuntu 10.10

I get this error:

'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Invalid parameter.


My smb.conf:

[global]
    ; General server settings
;    netbios name = ubuntu
    server string = 
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

;    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

;    printing = cups
    printcap name = CUPS

;    syslog = 1
    syslog only = yes
    usershare owner only = false

    usershare allow guests = yes
    guest ok = yes
    guest account = deini
    encrypt passwords = no

server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
;    browseable = yes
    guest ok = yes
;    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /media/DATA/
;    browseable = yes
;    writeable = No
    guest ok = yes
    create mask = 0644
;    directory mask = 0755
    force user = ALL
    force group = DEINI

Please someone help me.

---

### Post by deini on 2011-03-21
Shameless self bump

---

### Post by deini on 2011-03-23
Bumping again.

Please someone help me.

---

### Post by Morbius1 on 2011-03-23
Edit smb.conf and change the following line:
> encrypt passwords = **[COLOR=Blue]no[/COLOR]**To:
> encrypt passwords = **[COLOR=Blue]yes[/COLOR]**Save smb.conf and then restart samba:
```
sudo service smbd restart
```

---

### Post by deini on 2011-03-23
> **Morbius1 said:**
> Edit smb.conf and change the following line:
To:
Save smb.conf and then restart samba:
```
sudo service smbd restart
```


[http://www.millionthankyous.com/](http://www.millionthankyous.com/)

---

