---
title: "Trouble connecting to a vista machine"
date: 2010-04-03
forum: Networking &amp; Wireless
---

### Post by watersa8 on 2010-04-03
Hey ive not used ubuntu in about a year and have just reinstalled it but am having some difficulty getting it to connect to my laptop which i use as a mule for downloading i can access it form xp which is what i dual boot with

my smb.conf file is as follows 
[global]
    ; General server settings
    netbios name = watersa8-desktop
    server string = watersa8-desktop
    workgroup = HOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

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

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = watersa8
    force group = watersa8

I originaly set it up myself then followed the guide found here
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
neither seemed to work is there something i additionaly have to do to get it to work with vista? I ask this as ive had windows networks working fine in the past but only with xp machines

Thankyou for your time and help and sorry if im noobing out a bit

---

### Post by Martje_001 on 2010-04-03
Do you want to connect your Windows-machine from within Ubuntu? Simply click on 'Network' from the places menu.

---

### Post by Morbius1 on 2010-04-03
Double posting eh?

[http://ubuntuforums.org/showthread.php?t=1445860](http://ubuntuforums.org/showthread.php?t=1445860)

---

### Post by Martje_001 on 2010-04-03
Bad bad boy..

---

### Post by watersa8 on 2010-04-03
Sorry i didnt mean to ouble post i just lost the first one and when i click network i get to the section where it says home as in the workgroup click on that wait 10 seconds could not connect

---

